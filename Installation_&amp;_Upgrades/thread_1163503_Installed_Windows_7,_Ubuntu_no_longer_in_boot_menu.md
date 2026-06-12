---
title: "Installed Windows 7, Ubuntu no longer in boot menu"
date: 2009-05-18
forum: Installation &amp; Upgrades
---

### Post by sixsidepentagon on 2009-05-18
Hi, I just installed Windows 7 RC 1 to my Macbook (Santa Rosa), with Ubuntu Jaunty and OS X already installed. I use rEFIt for my boot menu. However, after installing Windows 7, Ubuntu was gone from my menu options (OS X was still there). I loaded up the Gparted Live CD and found that my partition seems to still be intact (as in Windows 7 didn't accidentally write over it, it's in its own partition).  So my questions are:

How can I boot Ubuntu again?

If I can't, is there a way to access the files on it through Windows or OS X? The cd I got for Jaunty doesn't seem to have a live cd option on it.

Thanks guys!

---

### Post by udippel on 2009-05-18
(This is a question asked over and over again. Maybe it should be made sticky?)

This is what Windows always does: overwriting the Master Boot Record (MBR); only the first 512 Byte of the drive. You simply have to rewrite it, using grub. You could even use the Live-CD, but my favourite is supergrubdisk (search the archives, I answered the same question some 8 hours ago in here).

---

### Post by BZF on 2009-05-18
[SIZE=1][COLOR=Blue]Installing 7 usually does this for some reason, just reinstall the partition. Should be working fine after that[/COLOR][/SIZE]

---

### Post by sixsidepentagon on 2009-05-18
First, sorry, didn't know this question was already asked. I looked around, couldn't find it. Guess I wasn't thorough enough.

Okay, so what happened now is I tried to use the auto supergrubdisk tool. I installed it alright, but when I went in to use it, it told me the disk wasn't bootable, that I needed some sort of Microsoft-compatible fdisk utility. To be on the safe side, I rebooted and tried again, except this time I found in rEFIt something that said it would "update my MBR tables", so I gave it the go-ahead. Except now when I try to boot Windows, it tells me the whole operating system is missing. At least I have OS X...

So when you say reinstall the partition, do you mean Windows or Linux? Or both?

---

### Post by sixsidepentagon on 2009-05-18
Okay, so I've been able now to access my linux partition, which means it hasn't been erased and is hence recoverable. Windows 7 is presumably so too.

So since I can't even boot into Windows now (and my MBR table has evidentally been screwed up now), is supergrubdisk still the way to go? 

Also, sorry for being noobish, but I don't really understand what rEFIt does. Do it still use GRUB and all that jazz?

Thanks for all of your time

---

### Post by sixsidepentagon on 2009-05-18
bump

---

### Post by dipaish on 2009-05-19
The reason for not being able to boot ubuntu is that the MBR boot loader overwrites the grub boot loader.There are several ways to get rid of this problem. One of the easiest way is to download EasyBCD 1.7.2 and then you can manage different Operating systems in your pc. 

Step 1: Boot your windows and then install easy bcd . You can download it from this address : [http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.7.2.exe](http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.7.2.exe)

Step 2: Run Easy bcd. On your left you can see different options. CLick on Add/Remove entries >> On your right under Add an entry there are several tabs. Click on Linux >> Select type: Grub >> Name: linux (it can be anything according to your wish )>> Drive: point out the drive to the root partition.>> Click save which is on top...Restart the computer you will get screen to select either windows or linux . You can now boot to linux by selecting it .......

I hope this works for you.

---

### Post by sixsidepentagon on 2009-05-19
I wish I could try that out, the problem is I can't even boot into Windows at this point. OS X is my last bootable OS now.

---

### Post by sixsidepentagon on 2009-05-19
Just tried the start-up repair tool on the Windows install disk, did not work.

---

### Post by finito on 2009-05-19
I am not sure about Win7

But in XP you can Boot into the Setup CD and go into Repair console. 

From there you can rewrite the MBR via the command

```
fixmbr **device name**
```

if you do not specify a device name, the MBR of the boot device is repaired. i.e. "fixmbr"


you can use the "map" command to find the device name.

also try the "fixboot" command.

I am sure there is a similar repair console for windows7.

P.S. Please use the commands without quotations.

---

### Post by sixsidepentagon on 2009-05-19
Yeah, I tried that with the Windows 7 installation disk, went into repair options, went into the command prompt they had, but fixmbr wasn't a command on it. Bizarre.

---

### Post by finito on 2009-05-19
I believe Windows7 is based on Vista so try this

[http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/](http://www.planetmy.com/blog/how-to-fixmbr-using-windows-vista-bootable-disk/)

---

