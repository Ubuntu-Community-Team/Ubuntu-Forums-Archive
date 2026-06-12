---
title: "Dell XPS M1330 webcam: How do I get it working?"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by jespdj on 2007-10-24
According to [this Ubuntu wiki page](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1330), the webcam on the Dell XPS M1330 should work, but only with Video4Linux2 (V4L2) and not with V4L.

I tried to use the camera with Camorama, but it doesn't work, I get an error message "cannot open device /dev/video0" when I start Camorama. Does Camorama only work with V4L?

The webpage says "Webcam: Works with Gutsy (select V4L2, V4L is not working!).". How do I "select V4L2"? Does it mean I just have to use a program that supports V4L2?

Which webcam program supports V4L2?

---

### Post by gertin on 2007-10-24
The only programs I've found to work with the webcam on M1330 is Ekiga and aMSN. I couldn't make mplayer, Camorama or any of the other programs that use the V4L2 driver to work. It's weird, because it's the same basic driver.

---

### Post by jespdj on 2007-10-24
Thanks. I tried Ekiga and it works - but Ekiga is a soft-phone program, and I'm looking for a program just to use the webcam, for example to record video with it.

At least I know now that it's not a driver problem...

---

### Post by kENNA on 2008-02-23
You can actually just use the "cheese" app from the add menu.

It dose all the stuff the regular WEB-cam manager did in vista..

---

### Post by komputes on 2008-07-04
cheese is cool (no full screen! :( ) and has great effects but it seems to freeze when attempting to record video.  I've attached a log of what happens. I end up with 0 byte files.

Does anyone know how to get the webcam on the m1330 to work on VLC?

---

### Post by asiakingtravel on 2008-07-04
[http://wwww.asiakingtravel.com](http://wwww.asiakingtravel.com)

---

