---
title: "Power Management? How to Power Down Hard Drives?"
date: 2007-07-13
forum: Hardware &amp; Laptops
---

### Post by OzzyFrank on 2007-07-13
OK, I've read about bugs in power management, and I've come to realise the little app for power management is next to useless for me anyway, so am looking for a way to power things down myself. Is there a third-party app that handles power management in a meaningful way? Like being able to set the hard drives to power down after a few minutes of inactivity? I saw mention of sdparm for SATA drives, so what do I use for my IDE drives? If it's hdparm, can someone please give me an example of its use?

---

### Post by njparton on 2007-10-29
Did you get any further with this - I'd be interested to know.

I have 3 SATA hard drives, one connected directly to the motherboard and 2 connected to a 3ware raid controller in raid 1.

I run the system as a NAS and as gutsy sleep is broken at the moment I'm looking for other ways to save power in the meantime.

---

### Post by OzzyFrank on 2007-10-29
**[COLOR="Purple"]sudo hdparm -S 120 /dev/sda[/COLOR]**

That's for the first HD, so you can alter that to whatever you want. The **[COLOR="#800080"]120[/COLOR]** means after 10 mins. I use this to power down my Windows drive while in Ubuntu. Hope that helps.

---

### Post by 444 on 2007-10-29
For the main drive you'll need to activate laptop-mode as well, otherwise it'll never have enough idle time to power down.

---

### Post by njparton on 2007-10-30
Great, thanks.

I'll probably just power down my 2 data drives with this. I'm planning on moving my system disk from sata to CF at some point (i.e. when my CF to IDE adapter finally arrives!).

If I do this with sdparm, will it still take effect after reboot or do I have to mod a config file somewhere?

---

### Post by OzzyFrank on 2007-10-31
Not sure I have an answer for that question... I just run the command I gave whenever I want to power down the drive. I wouldn't mind finding out how to get that to initiate at boot, since my Windows drive doesn't need to be running till I want to access files off it.

Now I have a couple of questions: What is a CF drive? And what does "laptop-mode" do and how to you access it (ie: if this is an option for hdparm, what is it? "--laptop-mode"?).

---

### Post by 444 on 2007-10-31
I was thinking /etc/hdparm.conf, but that's obviously for hdparm, not sdparm. So in that case you'd add the command to /etc/init.d/rc.local to get to run at startup.

CF=CompactFlash. As in solid-state flash chips instead of a spinning hard drive.

"laptop-mode" is a combination of a kernel feature and a power management program. It's not controlled by hdparm, It has it's own command called laptop_mode. To manually start it, you run "sudo laptop_mode start". Basically the main HD is going to get accessed every ten seconds or so by system logs or who knows what, laptop-mode takes all these accesses and groups them together so they only happen every ten minutes (or more if you want). To get it to start automatically, you uncomment the line for it in /etc/default/acpi-support. You'd probably want to mess with /etc/laptop-mode/laptop-mode.conf to get it to do what you want, as on a desktop it'll probably sit and do nothing unless you explicitly tell it to in the file.

---

### Post by Rwild on 2008-01-17
Wow... That's very helpful.  Thank you.! :D

---

