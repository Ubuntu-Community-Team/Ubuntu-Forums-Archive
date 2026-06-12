---
title: "Flexcam 100 / Microone MOWC101 webcam"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by encompass on 2005-12-30
I have this webcam I got for 10 bucks.  Figured, what the heck let me pulls some twonees and get it.  So I got it not knowing if it would work with linux.  Looks like it detected it ok... I can see it in my usb hardware lists.  I can select it as a V4L device.  I can select flixcam 100 from the dropdown list while setting it up for gnomemeeting. 
But when I try to test the device itself, my computer locks are.  The first time it has ever done that to me.  To check if it was a hard hard lock, I press the ussual keys and nothing worked.  I tried to lock it again and play a song and yes the song stick in a small loop when  I lockup.  So yes... BIG lockup.

I then Unplugged my usb mouse and tried running off of the touchpad only.  Still locked up.  It was the only usb device I could have had plugged in.

I figure I could start shutting services like ACPI or APM support too.  But figure I should post this and see if I get any better ideas.
anyone?

I am willing to do anything you need to get this device working.  Including remote access from ubuntu developers or those refered by the developers.  Thanks.

---

### Post by encompass on 2006-01-02
Apparently this is one of those things no one wants to touch.

---

### Post by encompass on 2006-01-10
Got a new cam... but have found a possible solution... the spca5xx... do a search in this forum and they can help you...

---

### Post by az on 2006-01-10
[https://wiki.ubuntu.com/Spca5xx](https://wiki.ubuntu.com/Spca5xx)

There is a howto on the wiki for the spcaxx.  It works.  The shipped modules locks up.

Use the one which uses the linux-headers.  You don't need to become root, as mentioned, though...  Just use sudo like everyone else.

---

### Post by encompass on 2006-01-12
Thanks... wasn't sure where the best wiki was.

---

### Post by chele on 2006-01-14
EasyCam [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam") is a cool utility to download and build drivers for many webcams.

---

