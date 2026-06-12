---
title: "Fujitsu Lifebook P5020?"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by zetsurin on 2005-10-17
Has anyone successfully installed Ubuntu on this laptop?  I attempted an install, and first stumbled with the 1280x768 res, but I found a solution to that.  Secondly, I had trouble with the broadcom wifi minipci card I have in mine (dell truemobile 802.11a/b/g), but managed to get the driver up and running using ndiswrapper (but then suffered occassional lockups) so no go there.  I also failed to get the sd/ms and cf slots recognised either.  In summary, I had to revert to using 'that mainstream OS', much to my dismay.  I would be encouraged to see if anyone has Ubuntu successfully up and running on this laptop but am not holding my breath.

---

### Post by jas42 on 2005-11-03
I just installed Breezy on my P5020 and am positively surprised. I have the Intel 2100 WLAN (Centrino, 802.11b only), which to my big surprise was correctly detected and enabled during the install. The other surprise was that sound appears to work (that usually doesn't happen!?). Once I figured out how to get the display into 1280x768 mode, it looks really nice, too!

I will have to do some work on suspend and hibernate stuff. Haven't tried the CF or SD slots yet, don't care much about either. Not sure whether I need to do anything about speedstep, or whatever that powersaving stuff is called.

All in all, very encouraging! Works right out of the box. Well, mostly.

---

### Post by zetsurin on 2005-11-27
Nice to see that it went so well for you jas42.  I've just purchased an Intel IPW2200bg MiniPCI 802.11g on ebay to replace the Dell Truemobile, as it's natively supported (I used to have the same 802.11b as you, but really needed g, hence replacing it with the faster card).  No ideas at the moment if it will work in the Lifebook but it was damn cheap so worth the try.  After that I'll attempt to tackle the SD/MS slot (which I actually use regularly).  If I get everything up and running I'll be busy updating the relevant wiki's with the necessary info.

By the way, to compare notes, what did you use to get the 1280x768 res to be supported?  On my system I was able to enable support but only after restarting x-windows with Ctrl+alt+backspace everytime i booted, which was a bit annoying.

---

### Post by zetsurin on 2005-12-01
Ok, I switched out the broadcom a/b/g card for a nice new Intel IPW2200BG and it works flawlessly in the lifebook.  Also, the wireless connection manager from gtkWifi works extremely well with it.  :p

---

### Post by Jubalgunn on 2006-06-08
I have a Fujitsu P Lifebook P5020 and have been using Ubuntu with it since Breezy.
I installed Dapper initially using the upgrade method but it altered my xconfig settings and despite my best efforts I was unable to reset it to the original settings using various methods.I did a fresh install of Dapper tonight and the screen is now working ok.
However I have Never been able to get the screen resolution above 1024 x768.
I have read with interest the above  posts concerning getting the native resolution  working. Has anyone got any settings or methods, I can use to configure my screen resolution correctly.
Would be most grateful for some help!!

jubal

---

### Post by jas42 on 2006-07-11
The program that you need to get the 1280x768 resolution is called 855resolution. The official page is [here]("http://perso.orange.fr/apoirier/"), and there is also a detailled description (for Hoary) [here.]("http://www.ubuntuforums.org/showthread.php?t=24923")

I haven't tried this with Dapper yet, but I see no reason why it shouldn't work. One caveat: This does screw up the resolution of the external monitor. I found a nice widescreen 17" monitor with the same resolution as the native display, but I couldn't get it to work. Alain, the author of 855resolution, confirmed that this was a known problem. I'd love to hear any solutions to that one!

---

### Post by manonabus on 2006-09-06
I have set out the procedure I used to fix this using 915resolution on another post, and thought I should cross-post here:

[http://www.ubuntuforums.org/showthread.php?t=193124](http://www.ubuntuforums.org/showthread.php?t=193124)

---

### Post by jayson23 on 2006-10-18
I'm writing this on a P5020 right now, running Dapper Drake. 
The install was painless, and nearly everything ran right out of the box. Resolution has been a continuing headache, though - I have to run 915resolution every time I start the machine. Putting a startup script into /etc/default didn't seem to do anything.

Also, as far as I've found up to now, the built-in card readers won't work, period. I've seen people ask about them on the forums, but I haven't found anyone who's been able to make them work.

---

### Post by Jubalgunn on 2007-12-06
[http://ubuntuforums.org/showthread.php?t=193124](http://ubuntuforums.org/showthread.php?t=193124)

Follow this thread.
I have been through the pain of trying to get the resolution on the screen set correctly.
The method in the thread works perfectly.
You dont need any kind of startup scripts etc, its pretty simple in the end.
Any problems post again and I will add in my configuration settings.
:guitar:

---

