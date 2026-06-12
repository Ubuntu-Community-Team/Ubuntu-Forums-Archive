---
title: "Lenovo X41 Tablet on 10.10 - Pen problems"
date: 2011-02-20
forum: Hardware
---

### Post by WorkingOnWise on 2011-02-20
I have a Lenovo X41 tablet, fully updated install of 10.10 desktop

I have the display buttons working, and have one assigned to screen rotation, which flips the display by 90 degrees per press.

A minor issue is that I'd love the thing to rotated the display AND pen when I physiclly rotate the display from laptop to tablet mode. 

Tha major issue is that the pen does not reorient itself to match the screen position at all, so if I flop the display to tablet mode with a button press, left-right becomes up-down and up-down becomes right -left.
I have searched and found several howtos that detail how to fix this common problem on these devices, but nothing specific for 10.10, except this, [http://www.mikezazza.com/en/linux/installare-ubuntu-10-10-su-un-thinkpad-x41-tablet/](http://www.mikezazza.com/en/linux/installare-ubuntu-10-10-su-un-thinkpad-x41-tablet/), which did not work. I tried this [http://liken.otsoa.net/blog/index.php?entry=entry080617-120522](http://liken.otsoa.net/blog/index.php?entry=entry080617-120522) which is sighted on many other howtos for this same problem. It didnt work either for the pen. It was useful in getting the display buttons all working.  

Dumb me didnt bookmark the page that did work for me back in December, and now I cant find it. 

Whatever it was, it was simply a script. No compiling was needed. 

Also, it seems that in 10.04 and 9.10 there was an issue with some driver not identifying the stylus as a stylus and that broke something else. On my tablet, xsetwacom list
 returns this:
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet stylus STYLUS 

So it looks like that is ok. 

I am basiclly a really really smart script kiddie who can follow directions with the best of then. What are the directions to follow to get me in screen and pen flipping auto rotating bliss in Ubuntu like this device was designed to do?

Thanks
Keith

---

### Post by Favux on 2011-02-20
Hi WorkingOnWise,

See the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  A method 1 script should work for you.  Also the method 5 automatic rotation script.  As well as Magick Rotation in method 4.

Good luck!

---

### Post by oliwek on 2011-03-04
WorkingOnWise, thank you really much for those links... I have just bought a cheap X41 Tablet myself, and have just tested maverick from a live usb drive... I was really glad to see many things working out of the box (especially pen and wifi), and I intented to search a way to use the hardware buttons near the LCD screen.

=D>

this tablet is really fine for sofa reading (no problem to read the many formats of ebooks and comics I have collected, for example the .djvu files I'm not sure android tablets could handle, or pdf files of ebooks with many color pictures weighing sometimes 100s of MB)

edit : for the rotation issue (screen and stylus together), read this interesting post : 

[http://blog.geekosaurus.net/?p=39](http://blog.geekosaurus.net/?p=39)

---

