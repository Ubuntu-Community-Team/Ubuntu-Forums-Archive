---
title: "USB Contour RollerMouse buttons are not working"
date: 2010-06-20
forum: Hardware
---

### Post by crazyfuturamanoob on 2010-06-20
I have a Contour RollerMouse plugged into a USB port in my PC. The mouse movement works but clicking does not.

I tested this in xev: When I click once, xev reports 2 mouse press/release events.

Using the mouse is annoying as hell because I have to click several times on some UI elements before they work, if they work at all.

In this thread *soknet* wrote that he solved the problem by plugging the mouse into a PS/2 port with a USB->PS/2 adapter:
[http://ubuntuforums.org/showthread.php?t=191082](http://ubuntuforums.org/showthread.php?t=191082)

There is one PS/2 port in my motherboard but it's only for keyboards, so plugging in a mouse doesn't work.

It would be really nice to get this mouse working.

---

### Post by ivref on 2013-02-02
Hello. This has annoyed me for a slight bit of time. So I will reply although it's been several years since the original post.

You can use xinput to fix this.

Do the following from the console:

```
$ xinput list
```
(find your RollerMouse, most likely "Contour Design RollerMouse")

And then
```
$ xinput set-button-map "Contour Design RollerMouse"  1 0 0 4 5 0 0 0 3 0 0
```

Works for both mode A and mode S mouses. I did not get the middle button working properly.

---

