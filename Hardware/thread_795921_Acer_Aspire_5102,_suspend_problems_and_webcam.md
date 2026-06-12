---
title: "Acer Aspire 5102, suspend problems and webcam"
date: 2008-05-15
forum: Hardware
---

### Post by phantom0021 on 2008-05-15
My Acer Aspire 5102 worked almost perfectly with Kubuntu Edgy Eft.  Only the webcam and the camera card system didn't work.

I've now installed Hardy Heron and, while the camera cards now work, the suspend mode now has a problem when attempting to restart, and the webcam still doesn't work.

The error message I get when attempting to restart from suspend is: .RS485MC - TEST BIOS BR#18675

In some way this relates to the video chip set, which is an ATI Radeon Express 1100.

The webcam is an ALi 5602 chip set.

Anyone know how to rectify these issues?

Thanks

---

### Post by mavicdog on 2008-05-27
same problem here. no solution yet. looking into bios upgrade but I'm wary of crippling my system....

---

### Post by kayatutun on 2008-06-04
I have the exact same one, aspire 5102, and I share your problems.

Starting with the webcam: it is the Ali Corp. ID: 0402:5602 webcam (you can see this ID using the lsusb command in the terminal)
If you google this ID like I did, you will find a number of forum entries asking for help with this chipset (m560x) in linux, and none of them has a happy ending I'm afraid. There is a guy offering 150 bucks to whoever makes it work on linux but I guess the bounty isn't enough to get anyone into this thing. Finally there are a few projects working on a module but there is no recent activity in any of them. I googled it every month for a year to see if there's anything new but I gave up. Looks like a dead end to me :/

As for the suspend thing I have the same problem. It freezes while checking BIOS while trying to recover from the suspend. Combined with the few lines during boot-up saying "BIOS bug #### found" it looks like a bios issue but what safe and simple solution is there for that???

---

### Post by phantom0021 on 2008-06-06
It's interesting there were no problems with the power manager and suspend mode in edgy, but there are now in hardy.  Perhaps the issue is because something changed, not for the better, in 8.04, or in KDE 3.5.9, the version of KDE in hardy?

Mark

---

### Post by cleopete on 2008-09-18
I have the same prob with the same hardware (ATI Xpress 1100 on an Aspire 5100).  It worked great when I first installed Hardy in April.

I had to reinstall recently when I couldn't find a solution to a thumbdrive auto mount problem (which started for no apparent reason). I went to the 64 bit version, and had a miserable two weeks and multiple reinstalls before I got Compiz/Atheros/Cairo working properly again.  It wasn't that hard the first time.

The suspend error is the last big problem, and kind of important, as my job has me carrying this laptop hither and yon all day.

Reboots are for Windows users.

---

### Post by lusisto on 2008-11-10
I have just installed Intrepid (Ubuntu, not kubuntu, but you should check) and with a little fix listed in the release notes, now my aspire 5102 resumes from suspend flawessly for the first time since i left xp:

"Wireless doesn't work after suspend with ath_pci driver

Wireless devices that use the ath_pci kernel driver, such as the Atheros AR5212 wireless card, will be unable to connect to the network after using suspend and resume. To work around this issue, users can create a file /etc/pm/config.d/madwifi containing the single line:

SUSPEND_MODULES=ath_pci

This will cause the module to be unloaded before suspend and reloaded on resume. "

---

### Post by volaer on 2008-11-11
Guys, I really want to change and use UBUNTU clompletely without windows xp. But I have a little problems that I think more than that of yours and perhaps, there is some there to help me. Here are the specs of my laptop:

Laptop Model: Acer Aspire 4330-592G32Mn
([http://www.acer.com.ph/notebook.php?pkey=123](http://www.acer.com.ph/notebook.php?pkey=123))

Processor Type: Intel Celeron M 575 (2.0GHz, 1MB, 667FSB)
	
Chipset: Mobile Intel® GL40 Express Chipset
Memory: 1GB DDR2 RAM

Video Type: Intel® Graphics Media Accelerator 4500M with up to 1759 MB of Intel DVMT 5.0 (64 MB of Dedicated Memory, up to 1695 MB of Shared Memory )
	
56K Modem and Gigabit LAN
Wireless LAN Built in Wireless LAN (802.11a/b/g/Draft-N) Wireless (Atheros AR5B91 Wireless Network Adapter)

Card Reader:   Built in 5 in 1 Card Reader
Built-in Camera: Acer CrystalEye Webcam

Here are my problems that I really cannot solve why:
1. If I play a movie or a music with the use of visualization, my laptop FREEZES including the DVD player and all programs running, but except the mouse.
2. My wireless LAN does not function.
3. Mic does not function.

Please, anybody can help me how to update or install drivers for my laptop? If all these things functions, I will completely switch to UBUNTU... Why not?:)

please help!!!

Thanks in advance

---

