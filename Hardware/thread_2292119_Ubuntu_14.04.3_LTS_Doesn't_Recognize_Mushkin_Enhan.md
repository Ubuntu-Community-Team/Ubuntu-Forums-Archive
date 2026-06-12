---
title: "Ubuntu 14.04.3 LTS Doesn't Recognize Mushkin Enhanced ECO2 MKNSSDEC60GB"
date: 2015-08-25
forum: Hardware
---

### Post by bigfish2 on 2015-08-25
I recently had the boot drive fail in my mythbuntu box. I decided to replace the the boot drive with a Mushkin Enhanced ECO2 MKNSSDEC60GB SSD and the data drive with a Western Digital WD Green WD10EZRX HDD just because it's getting a bit old. When I go to do a fresh install the Mushkin drive isn't being recognized. I decided to go right to Ubuntu main LTS and add the myth package later. It's not recognizing the drive either.

Details:
* Mushkin is on the first sata channel/port, WD on the second.
* Live CD: "sudo fdisk -l" shows the WD at sda and that's it.
* Motherboard: NFORCE 680i SLI (PN: 122-ck-nf68-ar)
* Only the drives have changed. Everything else in the box has run fine with previous versions of linux.
* The bios shows both drives.
* UBC utilities show both drives along with S.M.A.R.T info.

This is my first experience with an SSD on ubuntu, any thoughts, advice, or a good idea of a direction I should look in would be greatly appreciated. Thanks in advance.

---

### Post by oldfred on 2015-08-25
Does gparted from live installer show drive & can you partition in advance?
Is BIOS set for AHCI for drives?

---

### Post by bigfish2 on 2015-08-25
Hi Oldfred,

Thanks for your response. Gparted just shows /dev/sda, and it's the WD HDD. I tried refreshing the devices, but that's all it finds.

All the bios allows me to do is enable/disable the sata controller. There isn't an AHCI option to turn on/off. A bit of googling shows that this is the case for an older motherboard that doesn't use the intel chipset. But, also seems to show that SSD should still work without taking full advantage of the drives speed enhancements or hot swap abilities. I even tried a windows install and that saw the SSD and offered to install to it.

Do you think lack of AHCI may have something to do with this? It's not worth rebuilding the whole box for me, but I could probably use just the WD or scrounge up an old HDD. I do like to keep my boot and data separate, but it's not a deal breaker.

---

### Post by oldfred on 2015-08-25
I thought you had to have AHCI on for trim to work. Then once drive gets full of data it will be slow.
My first small SSD with Intel Core2 Duo made me turn on AHCI, but XP would not boot. But that forced me to finally stop using the one last app I was using XP for. :)
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-BIOS-and-UEFI:-set-it-to-AHCI](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-BIOS-and-UEFI:-set-it-to-AHCI)

If the BIOS correctly shows the SSD, I do not know why Linux would not see it. But BIOS does have to report as part of boot which hardware system has and then operating system uses that info.

---

### Post by bigfish2 on 2015-08-25
Yep, that's what I thought. If the bios shows it and UBC utilities show it should be ok. :)

I'll probably try another flavor of linux. If that doesn't work and nobody else has any insight in the next day or so I'll just skip the SSD. I thought it might help with the h.264 transcoding that has to be done for the roku to display the videos. Oh well, as long as the wife and kids an watch their shows they don't care how I do it. ;)

Thanks again for your time. I'll report back if I find anything out.

---

### Post by oldfred on 2015-08-25
I do not understand this comment #5, it says to use RAID mode?
[http://forums.evga.com/SSD-work-with-680i-SLI-MOB-m31348.aspx](http://forums.evga.com/SSD-work-with-680i-SLI-MOB-m31348.aspx)

This one is Windows issues, but video driver seemed to make a difference?
[http://www.techsupportforum.com/forums/f15/xfx-nforce-680i-sli-and-windows-8-ssd-compatibility-992025.html](http://www.techsupportforum.com/forums/f15/xfx-nforce-680i-sli-and-windows-8-ssd-compatibility-992025.html)

---

### Post by Yellow Pasque on 2015-08-25
I'd look through dmesg to see if there are any errors.

Also, do you have the latest BIOS version? [http://www.evga.com/support/download/showdlinfo.aspx?id=3001&type=N&acctype=BIOS&accversion=P33%20-%20ISO&part_number=122-CK-NF68](http://www.evga.com/support/download/showdlinfo.aspx?id=3001&type=N&acctype=BIOS&accversion=P33%20-%20ISO&part_number=122-CK-NF68)

---

### Post by bigfish2 on 2015-08-26
Thanks for the additional info and ideas.

Oldfred,

I looked into the raid mode setting further. Apparently raid mode turns on AHCI mode when the chipset supports it, and at least an extended function set when the chipset doesn't. Sometimes those extended function are enough to get what you need. Unfortunately, setting raid mode in the bios didn't seem to help with my problem.

The second group of posts are saying that when installing the NVidia drivers it was better to just install the video portion and skip the NForce chipset drivers. The default MS drivers seemed to do better with TRIM.

Temüjin,

I had thought of the bios update. I saw a number of posts where people said that their system became unstable with P33 so they dropped back to P31 (which I have). A post I saw about SSD troubles said that moving to P33 didn't have any effect. Based on that I wasn't sure if it was worth the chance. Most of the problem posts were on overclocker boards so they're probably more prone to stability issues when pushing the chips.

I'm embarrassed to say that I didn't check dmesg. I usually take a look after install, and since I didn't get there, I guess I spaced out that the live CD dmesg would be useful as well. dmesg does give some information. It initially sees the SSD on ata1, but then it seems to fail a few tests before being disabled.
* fail to read native max address
* HPA support seems broken, skipping HPA handling
* failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
Initially it show the drive size as 60Gb, but then says was changed to zero.

What fails seems to change based on how I got there too. For example trying to install, then quitting when the drive doesn't show up will drop me to unbuntu desktop. The tests in dmesg seem different than when just booting into unbuntu live. When I set raid on in the bios the SSD didn't even show up and ata1 just had one entry with the speed of the port being set.

Would it help to post the whole snippet? It's a bit beyond my level of knowledge. 

Let me know if you'd like to trouble shoot the dmesg failures further. Otherwise, I may just write it off to old hardware and stick with the HDD.

I guess I need to decide on whether I want to chance a bios upgrade or not too. I'll wait until after my second cup of coffee for that. :)

I appreciate all the help.

---

### Post by oldfred on 2015-08-26
I might see if Disks and icon in upper right to go to Smart Status shows anything. 

Is the SSD using the latest firmware?
[http://www.poweredbymushkin.com/index.php/support/ssd-firmware-updates.html](http://www.poweredbymushkin.com/index.php/support/ssd-firmware-updates.html)

I might just contact Mushkin to see if they know of issues. But I think it may be more your motherboard.

---

### Post by bigfish2 on 2015-08-26
I updated the bios to P33. It didn't help with the SSD issue, and there appears to be less information in dmesg. It also squawks at me on every boot to move my video card to a different slot. Unfortunately, the new location causes the video card fan to almost touch the back of the tv capture card and blocks airflow.

I couldn't find an exact firmware match to my drive so I really don't want to tackle that one.

At this point I believe we've made a good effort, but it's silly to throw more time at it. I think it's a problem caused by combining old and new tech. I'm going to stick with the HDD and just get it done.

Thanks much for all you're help. It's always good to see a community helping out. :)

---

### Post by Yellow Pasque on 2015-08-26
One last suggestion is to try disabling NCQ. Nvidia chipsets are known to struggle with it from what I've read (and experienced with an nForce4 board about 10 years ago).

```
gksu gedit /etc/default/grub
```
Add 'libata.force=noncq' to the list of parameters on the GRUB_CMDLINE_LINUX_DEFAULT line so it looks something like:
```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash libata.force=noncq&#8221;
```
Save the file, Quit gedit, and run:
```
sudo update-grub
```
Reboot.

---

