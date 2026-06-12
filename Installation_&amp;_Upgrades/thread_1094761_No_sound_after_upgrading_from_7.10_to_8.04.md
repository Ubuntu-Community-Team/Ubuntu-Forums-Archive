---
title: "No sound after upgrading from 7.10 to 8.04"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by alayahlan on 2009-03-12
I have a Dell Inspiron 1525 laptop that came with Gutsy Gibbon 7.10. I upgraded to Hardy Heron 8.04 today and all appeared to go well, except I have no sound now. When I use the volume control on the keyboard, I get a blank volume bar as if the colume has been turned all the way down.The buttons do not respond to raise the volume. When I got to System>Preference>Sound and try to test the sounds, I get this "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument".

There is a volume icon by my clock in the top right corner, but clicking it tells me "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I'm a fairly green linux user, so I'm not really sure what to try next. Any help appreciated.

---

### Post by Hutchie81 on 2009-03-20
I have exactly the same problem. I've searched for a fix but I don't know anything about programming or coding so I've drawn a complete blank. Is there not just a place where I can download the correct GStreamer thingy?

---

### Post by avtolle on 2009-03-20
It appears to me that the sound card in your respective computers is not being recognized by the system.

---

### Post by avtolle on 2009-03-20
Take a look at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Hutchie81 on 2009-03-20
Thanks for the reply Avtolle. I followed the steps in the guide and it seems I have to access BIOS to enable the sound card but I don't know how. I tried pressing all the F keys and delete at the log in screen but nothing happened.

Just for a bit of background, I was running 7.10 and the sound worked fine but I upgraded to 8.4 so I could install a better flash player and when the upgrade finished everything was fine, except for the lack of sound.
Any further help gratefully received.
:-)

---

### Post by Therion on 2009-03-20
Normally, when you boot, you get a splash screen that indicates you can press a key, or key-combination, to enter Setup or to Configure or something along those lines.  

Common ones are ESC, DEL, F12 and F10 but really, it could be anything.  

If you don't see anything like directions for entering setup or configuration menus on any of the splash-screens when you boot, post back with the make and model of your PC.

---

### Post by Hutchie81 on 2009-03-20
Thanks Therion, I'm totally out of my depth, I don't know what a splash screen is (black with white code?). :(
I'm on a Dell Inspiron 1525

P.S. any advice on what I should do on entering BIOS? I'm really nervous about fiddling around with stuff I don't understand. Don't want to wreck my laptop!

---

