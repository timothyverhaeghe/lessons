# Lessons
Coding lessions I've learned.

## Intro
This is a list of lessons I've learned during my time as CTO at Taglayer. If you have tips / trics or additional tips, feel free to contact me at timothy@taglayer.com. Feel free to share your lessons and make the world a little bit better 💪🏻.

## Table of contents
- [Markdown cheat sheet](https://github.com/timothyverhaeghe/lessons#1-great-resources)
- [Fuc*ing encoding Python](https://github.com/timothyverhaeghe/lessons#2-fucing-encoding-python)

## Lessons
### 1. Great resources
- [Markdown cheat sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

### 2. Fuc*ing encoding Python
Because for some crazy reason Python decided to remove the default encoding feature (because this really works in Python 2.7). It really makes my life with Python3.7. So I spent hours / days / weeks on Stack overflow finding and trying any possible line of code to fix this bug. But NOTHING works (or I really suck 🧐).

```bash
# Python 2.7
print('\xe9')
print('?') # Not so ok, but it doesn't crash my entire system.

# Python 3+
print('\xe9')
UnicodeEncodeError: 'ascii' codec can't encode character \xe9 in position 0: ordinal not in range(128)
=> ASSHOLES (ok. probaly I am the one who's causing this problem)

# See your charmap
locale charmap # it works when this command returns 'UTF-8'
```

I tried so many tips. From changing (and fucking up) my locale settings, to encoding / decoding my String in Python. Ending up without any solution. Finally I found that the bug is not only "really" related to Python but to my Ubuntu version. So the solution: fucking my local setting even more. But I found a solution (it's absolutely not the best solution, but it's a solution).

Adding `LC_ALL="en_US.UTF-8"` to `/etc/environment` made it working. I know, it's not the best solution (but it works). It is not the ideal solution for when other people are connecting over SSH (ex. latin1 or windows-1252). I'll keep you posted if one of my employees has this bug again (which another local setting) or if we find a better solution. But meanwhile, this `hack` works.

ps: I am not an encoding / infrastructure / server expert!

Feel free to reach out to me and try to solve this with me :) => me@timothyverhaeghe.com
