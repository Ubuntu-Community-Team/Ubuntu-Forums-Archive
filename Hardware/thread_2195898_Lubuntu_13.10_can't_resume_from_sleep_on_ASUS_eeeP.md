---
title: "Lubuntu 13.10 can't resume from sleep on ASUS eeePC 900"
date: 2013-12-27
forum: Hardware
---

### Post by Azyx on 2013-12-27
Hi.
I have moved from **[COLOR=#ff0000]Ubuntu 10.04[/COLOR]** to [COLOR=#0000ff]**Lubuntu 12.04**[/COLOR] on a [COLOR=#696969]**ASUS eee PC 900**[/COLOR] and have no problem to resume from sleep. then when I upgraded to Lubuntu 13.10 and also maybe with 13.04, my resume from sleep don't work. The **[COLOR=#00ff00]power[/COLOR]** indictor stop flashen and shine constantly **[COLOR=#00ff00]greeen[/COLOR]**, as it should if it on. Also the disk**[COLOR=#ff8c00]activity[/COLOR]**and [COLOR=#336699]**network**[/COLOR] start glow [COLOR=#ff8c00]orange[/COLOR] and [COLOR=#0000ff]blue[/COLOR], but the screen are turned off :( Under x-mas I make a complete new installation of [COLOR=#0000ff]**Lubuntu 13.10**[/COLOR] and formatted the harddisk becourse It maybe was an upgrade efforr someware. But I have still the same error. The computer wake up, but the screen is off, not even back-light shine.

Have seached the internet and find that I could edit grub like this:

[http://askubuntu.com/questions/361547/ubuntu-freezes-crash-after-wake-when-upgraded-to-13-10](http://askubuntu.com/questions/361547/ubuntu-freezes-crash-after-wake-when-upgraded-to-13-10)

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
To the suggestions, whitout any success and have restored the line 
"quiet splash"

After that I also installed **[COLOR=#ff0000]acpi-support[/COLOR]** with packages and tested again, with no success.

I don't think it crash, but just don't turn on the disply? Or? I do not have any othe PC to try to connect true ssh.

---

### Post by coldraven on 2013-12-27
I am running Xubuntu 12.10 and it suspends and awakes with no problems.
Have you got the latest BIOS? It should be version 1006. I don't know if it will help your suspend issue but it definitely will make the fan run less.

Below I've copied an old post of mine which explains how to update the BIOS.

What was the easy way to update the BIOS?
I wasted hours on this so I can say that I'm now an expert :)
Download 900-ASUS-1006.ROM from the Asus site
Rename it to 900.ROM
You need to make/have a USB stick with maximum 512MB formatted to FAT16
I only have a 8GB stick so I used gparted to do the following:
Delete the existing partition.
Create a new one, I chose 256MB to be on the safe side.
Format the partition to FAT16
Leave the rest as "Unallocated"
When gparted has finished, remove and replace the stick so that the file manager detects it.
Copy 900.ROM to the stick
Make sure that the power lead is connected
Boot your eeepc with the stick in holding  Alt+F2 during the POST messages.
(no need to alter the BIOS boot settings)
After a few seconds of black screen you should see the EZflash utility  which will automatically flash the BIOS in about three minutes.
If it gets stuck on "Reading file 900.ROM" then switch it off, something is not working.

I think the fan is running a lot less with this upgrade.
I've not yet had the time to test it with a DVD/video playback to check the battery life.

Don't forget to re-format your stick back to it's original state, mine was NTFS.

If you have "Boot Boost" enabled in the BIOS and you still have a partition labeled "BIOS" you need to overwrite the 900.ROM file that is in that partition with the new version. If that partition no longer exists then just disable the "Boot Boost".

---

### Post by Azyx on 2013-12-27
Thanx coldraven for a very detailed description :) Have done it and remember how hard it was to get it right. By the way I also used the LEFT usb-port, but don't remember if it was crucia or not. But I upgrang is that ded to 1004, so I don't have 1006. But the thing is that suspend and resume work perfectly on 12.04 and probably also on 12.10 Ubuntu.

nyway, when I come home I will try to upgrade BIOS, not for only this, but also that the eee pc 900 don't start every time with a 2GB memory.

Cheers. will send report when finnish.

---

### Post by Azyx on 2013-12-27
Darn :(
Find my 128MB usb-stick, reformated it to FAT16.
Downloaded 900-ASUS-1006.zip unziped and renamed it too 900.ROM and copied it to the usb-stick.

Get stuck on "Reading 900.ROM..."

Get it from here.. [http://update.eeepc.asus.com/bios/](http://update.eeepc.asus.com/bios/)

:( More exactly: Reading file "900.ROM"_

Have downloaded again and unziped an rename again... And tested every usb-port.

---

### Post by coldraven on 2013-12-28
Well that's odd :(
Are there any other partitions on your stick or just the one with the FAT16 on it?
The only thing I can think of is to try a different stick.

---

### Post by Azyx on 2013-12-28
No, It's a usb-disk with only 128MB, same usb-memory I used to upgrade BIOS  from 090x to 1004.  ASUS don't have 1004 any more, probly because there wher problem (I could not use 2GM RAM).  Suspend/resume worked fine with 12.04 and 12.10 Ubuntu. It problem with Lunubtu 13.10, and then I start, there are a lot of problems I have repported, I think.

---

### Post by Azyx on 2013-12-29
Well.. I installed Ubuntu 12.04LTS and ever there, it don't resume from suspend, so there are probably some ting wrong with the hardware :(  By the way, do you run xubuntu 12.10? But do you really run 12.10, it has not security updates any more, or?

---

### Post by coldraven on 2013-12-30
> By the way, do you run xubuntu 12.10? But do you really run 12.10, it has not security updates any more, or?
I have not been using the eeepc for a while because the 4GB drive is full and will not update.(there are ~400 pending!)
I've been meaning to move the /tmp directory to the 16GB drive but have not got around to it yet. In fact I'm not sure how to do it :(
Maybe it would be easier to do a fresh install of a newer release.

---

### Post by mörgæs on 2013-12-30
> **Azyx said:**
> Well.. I installed Ubuntu 12.04LTS and ever there, it don't resume from suspend, so there are probably some ting wrong with the hardware :(  By the way, do you run xubuntu 12.10? But do you really run 12.10, it has not security updates any more, or?

12.10 has updates through april 2014.

---

### Post by Azyx on 2013-12-30
A..so you have the windosversion with a faster 4GB drive? I have the Xandos-version with only one 16GB disk. Have partitioned that drive with swap 1024 MB and approx 7 GB as / and 8GB as /home. The windos-version need a fast ssd. I thougt the windosversion have 4GB+8GB?

---

### Post by Azyx on 2013-12-30
A fresh install of Lubuntu use 2,46GB in /-partition and 267 MB in /home, so if you use the 4GB ssd as / and the 16GB harddisk as /home, there may bee better place?
If you are used with Unity or Gnome 3,  you can make a panel to the left as a launcher, and move the bottom panel to the top.  Lubuntu are far better than Ubuntu and Xubuntu with older machines. I'm really consider to move all my Ubuntu machines to Lubuntu, but still they do not have LTS life cykles as Xubuntu and Ubuntu....

---

### Post by mörgæs on 2013-12-30
Yes, always go for a fresh install. Upgrades are risky.

People are considering to make Lubuntu 14.04 long term support, but don't take this as a promise yet.

A [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall") can be even less than 2.5 GB.

When dealing with a small hard disk it's best to run
```
sudo apt-get clean
sudo apt-get autoremove
```
once in a while to keep the wasted space to a minimum.

---

### Post by coldraven on 2013-12-30
Ooops! Sorry that I did not know about the two versions of this PC.
I just checked and it has indeed a 4GB and 16GB drive. I did not create a swap partition, i read somewhere that SSDs don't like it.
How it manages to suspend I don't know, does it write a temp file somewhere else?
If you know otherwise (about the swap) then let me know because as I said above I might do a fresh install.

---

### Post by Azyx on 2013-12-30
Suspend have the power left on the RAM, so you do not need swap for that, but i think  to Hibernate, but my SSD was so slow to read Hibernate-file, so I could turn it of normaly. My swap are never in use, so I can take it away...

---

