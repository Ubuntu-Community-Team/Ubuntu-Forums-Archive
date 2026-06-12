---
title: "UNR 9.10 Eee 701 &quot;Disk is being used outside design parameters&quot;"
date: 2009-10-31
forum: Hardware
---

### Post by pjcdawkins on 2009-10-31
Many other people seem to have had this problem in Karmic with the Eee 701 and the Dell Mini 9 but I can't respond to that thread as it's in a closed forum:
[http://ubuntuforums.org/showthread.php?t=1280693](http://ubuntuforums.org/showthread.php?t=1280693)

I installed UNR 9.10 two days ago (a fresh install from USB rather than an upgrade).

Recently it notified me that "One or more disks are failing" and in big red scary letters:

[COLOR=DimGray]4.0 GB Hard Disk - ATA SILICONMOTION SM223AC[/COLOR]
[COLOR=Red]**DISK IS BEING USED OUTSIDE DESIGN PARAMETERS**[/COLOR]

It seems to think this is a serious error. Oddly there's no indication that it's aware I have a solid-state drive.

The filesystem on the disk is the default ext4.

Upon delving deeper into the 'Palimpsest Disk Utility' I get a list of "attributes" shown in the attached screenshot.

Please let me know whether this is as serious as it makes it out to be and/or whether you want more information.

I'm very pleased with Karmic on the Eee in all other respects! Particularly sound support.

---

### Post by pjcdawkins on 2009-11-02
Update: I seem only to get this warning when resuming the Eee from Suspend mode.

---

### Post by jubilantfungus on 2009-11-03
I'm having the same issue with the same computer under the same circumstances. Makes me think this is a bug in 9.10

---

### Post by zob on 2009-11-08
Yeah. Me to. Any news.
Did you notice the installation process was extremely long as well? More than 1 hour. And that there seemed to be problems specifically during installation when gparted had to start.

---

### Post by pjcdawkins on 2009-11-08
Installation was actually pretty quick for me - once I worked out that I couldn't upgrade - did you upgrade from 9.04 or install afresh from USB?

Still no info then...
:popcorn:

---

### Post by zob on 2009-11-08
I've heard somewhere, can't remember where. That people who had ubuntu 9.04 with ext4 and upgraded rather than doing a fresh install (as I did), don't have these problems. Now that's strange.

---

### Post by oimon on 2009-11-12
i get this after resuming from suspend on a UNR 701 clean install running with ext3 filesystem
installing smart-notifier fixes it for me (so far)

---

### Post by webweaver on 2009-11-13
I am having this exact problem also on my Eee PC 701 with UNR 9.10

I have just installed 'smart-notifier' and rebooted.  Will let my Eee go into suspend mode and bring it back to see if that has actually resolved it for me too.  Will report back  :)

Update:  Ok, at first install 'smart-notifier' appeared to fix the problem, as it didn't appear instantly after coming back from being suspended.  It did still appear randomly later on though.  So I guess that solution doesn't work (or at least, not for everyone).

---

### Post by tars_ac on 2009-11-13
Kind of off topic, but do you folks running the Eee 701 have any issues with 9.10?  Both of my Eee 1000 netbooks have had tons of issues with suspending and the wifi and such.  I had to use eee-control on 9.04 to get everything to work, but there doesn't seem to be a real 9.10 version of eee-control, and nothing else wants to work.  Have you had these issues and resolved them?  I'm planning on rolling back this weekend if I can't figure it out.

---

### Post by webweaver on 2009-11-13
> **tars_ac said:**
> Kind of off topic, but do you folks running the Eee 701 have any issues with 9.10?  Both of my Eee 1000 netbooks have had tons of issues with suspending and the wifi and such.  I had to use eee-control on 9.04 to get everything to work, but there doesn't seem to be a real 9.10 version of eee-control, and nothing else wants to work.  Have you had these issues and resolved them?  I'm planning on rolling back this weekend if I can't figure it out.

I personally haven't had any issues so far, besides the one mentioned in this thread.

In fact, I had no trouble with 9.04 on my Eee 701 either.

---

### Post by tars_ac on 2009-11-14
Well, reinstalled 9.10 from scratch today and after upgrading kernels everything seems to work now.  Thanks.

---

### Post by adnd74 on 2009-12-10
Zero issues on my 1000H
seeing this on 701

Both fresh installs

---

### Post by jesselks on 2009-12-12
Got this error on Ubuntu 9.10 desktop i386 on eee 700. Thing is that I installed on an SDHC card. The 2GB silicon motion drive isn't mounted. Not sure, but I believe the error notification and tray icon popped up a little while after resuming from suspend for the first time.

---

### Post by fpeelo on 2010-01-10
I have a 4G eeepc 701, clean install of UNR 9.10, identical message.

What I would love to know is, what are the design parameters that are being exceeded? And if I knew that, would it be possible to change them in the BIOS? Or using hdparm or something like that?

Last summer, I tried to use it in a wifi-enabled pub. It wouldn't boot. Couldn't find the OS. After a drink or two, I tried again, it partially booted but missed some files. I waited a while longer, with the machine close-ish to a radiator, and then I could boot. All of which made me wonder whether the internal flash drive on the eeepc is being a little overdriven, to get better performance. Like overclocking or something. If that were true, the message from UNR is probably something I would want to pay attention to.

It's a machine I use for messing about. I have used several OSes on the eeepc. I don't recall what I was using last summer. Fairly sure it was not UNR, because that was too slow before 9.10.

Frank

---

### Post by RonCam on 2010-06-25
Just joking.

Do you mean to say, after so much time there is no fix? :confused:

Surely I missed it in my search.  Kindly reply to this post with a link to where the problem has been resolved. :rolleyes:

---

### Post by oKtosiTe on 2010-08-09
I found the following tip on a French Ubuntu blog:

Go to **Startup Applications** and disable the **Disk Notifications**.
Still hope somebody knowledgeable cares enough to fix this...

---

### Post by mshenrick on 2010-09-25
> **pjcdawkins said:**
> Many other people seem to have had this problem in Karmic with the Eee 701 and the Dell Mini 9 but I can't respond to that thread as it's in a closed forum:
[http://ubuntuforums.org/showthread.php?t=1280693](http://ubuntuforums.org/showthread.php?t=1280693)

I installed UNR 9.10 two days ago (a fresh install from USB rather than an upgrade).

Recently it notified me that "One or more disks are failing" and in big red scary letters:

[COLOR=DimGray]4.0 GB Hard Disk - ATA SILICONMOTION SM223AC[/COLOR]
[COLOR=Red]**DISK IS BEING USED OUTSIDE DESIGN PARAMETERS**[/COLOR]

It seems to think this is a serious error. Oddly there's no indication that it's aware I have a solid-state drive.

The filesystem on the disk is the default ext4.

Upon delving deeper into the 'Palimpsest Disk Utility' I get a list of "attributes" shown in the attached screenshot.

Please let me know whether this is as serious as it makes it out to be and/or whether you want more information.

I'm very pleased with Karmic on the Eee in all other respects! Particularly sound support.

I get this on the 700 with maverick after about 20 minutes. i assume its overheating and shut it down

---

### Post by Lanser on 2010-09-25
I remember there was a lot of debate on running ext2, ext3 or ext4 on these early SSD's. I have had Ubuntu 10.04 and Mint 9 running on my Eee701, but always used ext2 on the SSD as a cautious approach and kept all data on a HDSC card. Not sure if this links to the design parameter error.

Lanser

---

