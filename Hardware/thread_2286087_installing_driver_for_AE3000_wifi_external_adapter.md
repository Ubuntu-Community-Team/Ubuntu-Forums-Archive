---
title: "installing driver for AE3000 wifi external adapter"
date: 2015-07-09
forum: Hardware
---

### Post by micahpage on 2015-07-09
This is with an ubuntu 12.04 OS

I downloaded:
[https://github.com/ashaffer/rt3573sta](https://github.com/ashaffer/rt3573sta)


I did the commands
```
[COLOR=#333333][FONT=Courier New]sudo make -j10
[/FONT][/COLOR][COLOR=#333333][FONT=Courier New]sudo make install[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]
sudo depmod -a[/FONT][/COLOR]
[COLOR=#333333][FONT=Courier New]sudo modprobe -v rt3573sta[/FONT][/COLOR]
```
and they all execute successfully. However when i try it, it no longer works. It did work 6 months or so ago, but the pc restarted and now will not. Is there something i am missing?

---

