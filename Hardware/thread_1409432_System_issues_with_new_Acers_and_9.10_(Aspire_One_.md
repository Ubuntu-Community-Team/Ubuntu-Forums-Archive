---
title: "System issues with new Acers and 9.10 (Aspire One 532h &amp; Timeline 1810t)"
date: 2010-02-17
forum: Hardware
---

### Post by Kavinorum on 2010-02-17
There are a few issues that myself and another user have experienced so I'm guessing it is a widespread problem with new Acers. Hopefully a more experienced user can shed some light on these issues. I have an Acer Aspire One 532h netbook and another user indicated having the same issues on a Timeline 1810t laptop.

-Text input randomly stopped working in Terminal, had to restart system in order to use terminal again.
-Synaptic Package Manager hung up in the middle of installation, again had to restart.
-System will not shut down fully, gets hung up on something near the end (I can provide a log later).

It just feels really flaky overall, as a first time linux user I'm not exactly sure what to do.

Can provide more info if needed.

---

### Post by Kavinorum on 2010-02-17
Another issue I've been having, the wifi sometimes has connectability issues.  One of the things it does is randomly drop the connection and freeze everything but the mouse.

---

### Post by Laudanum on 2010-02-24
Same setup. System is stable by and large until you start using it heavily. All the latest updates installed.

Things that are not working are:

--Wifi drops connection with and won't link up again. When trying to shut down the system hangs and only pressing power button for 5 secs will shut it down. This happens mostly during video playback (VLC) or downloading a lot of stuff at the same time.

--Internal mic not working (tried all suggestions that Google can find to no avail).

--SD card not recognized.

---

### Post by Kavinorum on 2010-02-24
Someone told me its probably a problem with the wireless, since it only seems to happen when there is heavy traffic or heavy system load.

Anyways the wireless will lock up and eventually cause a kernel freeze.  I have attached a log of the error, I'm not sure what to do with it.

---

### Post by coldfire2122 on 2010-02-25
When I first got my 532h I was experiencing really flaky wireless and had to reboot to reconnect. After I installed the jaunty backports my wifi signal got higher and it stopped dropping. It did not fix the Mic and I have not experienced the failed shut downs or massive freeze ups. Just speed hickups here and there.

to install the back ports go to terminal and enter:

sudo apt-get install linux-backports-modules-karmic-generic

*sudo apt*-*get install linux*-*backports*-*modules*-*wireless*-*karmic*-*generic*

then 

sudo reboot

Hope it helps!

---

### Post by Noremacam on 2010-02-28
I'm actually having the same connectivity issues in win7 on the new Aspire one 532h, where you have to reboot to get wireless back. It's the same error in linux and win7, which leads me to believe its either a hardware issue, bios issue, or a somehow duplicate driver issue. I updated the bios to the latest and so far my windows hasn't suddenly lost wireless connection, although admittedly I've only used it a couple of hours since I last updated the bios.

Might try updating bios and see if that helps. Get the bios at [www.acersupport.com](www.acersupport.com)

I would however be curious if anyone got the SD working in linux, coz that's what made me put windows back on it, since I wanted to use it with my digital camera, and a usb dongle was inconvenient when I already have an SD slot.

---

### Post by devlin7 on 2010-03-13
> **Noremacam said:**
> I'm actually having the same connectivity issues in win7 on the new Aspire one 532h, where you have to reboot to get wireless back. It's the same error in linux and win7, which leads me to believe its either a hardware issue, bios issue, or a somehow duplicate driver issue. I updated the bios to the latest and so far my windows hasn't suddenly lost wireless connection, although admittedly I've only used it a couple of hours since I last updated the bios.

Might try updating bios and see if that helps. Get the bios at [www.acersupport.com](www.acersupport.com)

I would however be curious if anyone got the SD working in linux, coz that's what made me put windows back on it, since I wanted to use it with my digital camera, and a usb dongle was inconvenient when I already have an SD slot.

How did you update the bios? I tried using Wine but it says I need to be in Administrator mode if running in Windows XP....

The SD slot not working is depressing considering it had been resolved with the previous Aspire One models. Their changing their hardware after it all worked in both enviroments reminds me of Ubuntu itself. Each new edition they break things we spend 6 months fixing.

---

### Post by Noremacam on 2010-03-13
I was running windows at the time that I updated my bios.  My hopes were premature. In Linux and windows my wifi is still having issues. While this could be the placebo effect, I think wifi suddenly stopping working has happened much less after the bios update. 

I believe the bios update has a dos version, you could make a freedos USB key and run the bios updater from DOS. Requires a bit of command line knowledge.

---

### Post by Kavinorum on 2010-03-13
Installing backports seemed to help at first, but the issue still arises sometimes.  Right now it seems to mostly appear after hibernation.  But most of the time coming out of hibernation works fine.

---

### Post by markwalt on 2010-03-31
Thanks for this thread.

I just installed the backports and the first thing I've noticed is an improved wifi signal.  Hopefully this will resolve some of my issues as well.

Cheers
-Mark

---

### Post by markwalt on 2010-04-01
Living with it for a day so far... the hibernate/resume issues have been resolved.

I've got shutdown/suspend issues with a desktop I have, and so now I think I'm going to try the fix on it as well.

---

