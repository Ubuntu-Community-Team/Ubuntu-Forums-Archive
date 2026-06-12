---
title: "Using both nvidia discrete and intel integrated"
date: 2011-09-08
forum: Hardware
---

### Post by cavved on 2011-09-08
Hey everyone,

I'm having troubles getting my Asus UL30VT working well with Ubuntu. The laptop is set up with both an nvidia g210m graphics card and onboard intel graphics. I either boot up with both enabled - and then turn off the nvidia card using instructions from [this thread]("http://ubuntuforums.org/showthread.php?t=1366605"). Or I can change a bios setting which turns off the intel integrated graphics and boots using only the nvidia card. This all works fine, but when I install the nvidia proprietary drivers, my configuration is changed somehow so that then I can't use the intel card properly. 

When I'm using the intel card, after installing the nvidia drivers  opengl doesn't work. For example, I get this message when trying to open cairo-dock which uses opengl:

```
Xlib:  extension "GLX" missing on display ":0.0".
```

How can I change the graphics configurations from one boot to the next so that I can use both cards?

I looked for /etc/X11/xorg.conf but I don't have one. Any ideas?

Thanks!

---

### Post by .... on 2011-09-08
[http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/)

---

