---
title: "Installation at an old laptop"
date: 2008-05-13
forum: Hardware
---

### Post by kristoffgr on 2008-05-13
I have a compaq presario 2500 with intel pentium 4 at 2,4 Ghz and ram ddr 256 mb, 333Mhz. At the system properties of windows xp,and in the bios setup screen I see only 192 mb of ram. I've bought additional ram (512 mb) but nothing have changed.
I know that with 192 mb I can not install ubuntu 8,04 (I've tried it anyway)so I looked at ubuntu 6.10. The laptop boots from the live cd, the installation begins and when it reaches the the first desktop screen a small window appears, saying the following:

"There was an error starting Gnome settings Daemon

Some things, such us themes, sounds or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not sent a reply, the message
bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Gnome will still try to restart the settings Daemon next time you login."

It takes a long time to close this window and the install icon does not work at all. Everything stops there. Is it a low ram problem again or something else? Note that I have also tried mandriva 2008 and novell suse 9.3 and they both worked.

Please I can use any help !
thank you !

---

### Post by daemoncat on 2008-08-26
> **kristoffgr said:**
> I have a compaq presario 2500 with intel pentium 4 at 2,4 Ghz and ram ddr 256 mb, 333Mhz. At the system properties of windows xp,and in the bios setup screen I see only 192 mb of ram. I've bought additional ram (512 mb) but nothing have changed.


I assume that you have installed the additional ram, but your system still shows only 192 mb. 64 mb is being used ("shared") by the video chips. But that should still leave you with 768 mb for the system. Try re-installing the 512 mb memory card. Be sure it's properly inserted. Laptops are generally a bit harder to seat properly. If that works, Ubuntu should work. 

For a laptop, I'd recommend Xubuntu. It's designed to take less memory and resources. The trade off is that it doesn't come with all of the software and "goodies" that Ubuntu does. I'm typing the from my Compaq 1500US with only 512 mb total, of which 64 is used for video. Xubuntu does all I need it to. I even have NeverwinterNights I installed and working very well. 

Hope this helps, or at least encourages you!

---

