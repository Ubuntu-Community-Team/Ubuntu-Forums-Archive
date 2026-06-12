---
title: "No distro will launch on Acer Aspire 9300 Laptop"
date: 2012-03-01
forum: Hardware
---

### Post by Resdayn on 2012-03-01
I have an Acer Aspire 9300 laptop, and I wish to install a linux distro on it, but no distro will even launch. I made Live USB's and none of them worked. I verified that I made the Live USB correctly by trying to use it with my desktop, which worked everytime. I tried Ubuntu, Kubuntu, Lubuntu, Fedora, openSUSE, Mint, Debian, Knoppix and Puppy Linux. None of them worked. I tried normal boot and compatibility boot with each distro, to no avail. 

After choosing an option in the main menu (Launch from USB or Install), it would show a blinking cursor for a while, then show artifacts and do nothing. In compatibility mode the text gets smeared all over the screen and does nothing. I tried using boot options like noacpi and xforcevesa etc. I even tried a Mint CD, didn't work. The only distro that would boot was an old version of Knoppix (CD), version 4 I think.

I simply don't know what to do anymore, I googled for help but I couldn't find any. If anyone could help me find the problem and hopefully find a fix for it, that would be great.

[B][SIZE=2]Help me Obi Wan Kenobi, you're my only hope.

Edit: I tried launching Ubuntu Edgy from a Live USB, which worked. So Ubuntu Edgy works, but recent versions do not. I hope this info helps.
[/SIZE][/B]

---

### Post by dandnsmith on 2012-03-02
Have a look at [this data page](http://www.linux-on-laptops.com/acer.html) where 2 installations are described, together with the problems found.
Maybe it will give you a place to start.

---

### Post by Resdayn on 2012-03-04
I found info for my laptop about a Kubuntu Feisty installation. I will give it a try, but I'm pretty sure it works since Ubuntu Edgy worked aswell. Maybe there's a certain driver that's not included in the newer versions that causes my laptop to space out during boot?

---

### Post by dandnsmith on 2012-03-04
Perhaps you could investigate the boot options.
As a start, trying to remove the splash and quiet might let you see where things go wrong.

---

### Post by phil.lxnet on 2012-03-05
Strangely enough I have this same model in this morning and ran into the same thing.
I tried 10.04.3, 11.10, and beta 1 of 12.04 of Ubuntu.  All no joy with just corrupt x on boot.

But there is joy yet:-

dandnsmith pretty much had it with the removing of the quiet and splash options and I also used the F6 after pressing the space during usb boot when the little keyboard symbol appears at the bottom of the screen to get the additional options.
summary:-

- space bar when little keyboard icon appears at the bottom of the screen
- F6 key to get "Other Options"
-- select "nomodeset" with cursor and space bar
- esc key to get out of that menu
- left cursor to edit the boot line that appeared
-- remove "splash" and "quiet" but leave the "--" at the end
- carriage return to initiate the boot with these options

This works a treat for:-
11.10 64bit
12.04 64bit (beta 1)

Hope this helps.

---

### Post by Resdayn on 2012-05-07
Thanks for your reply! I didn't expect anyone to still reply to this topic.
I will give this a try as soon as possible.
I'll return with the results. ;)

Edit: I read your reply again But the thing is, I have already tried booting it with those boot options, it failed.
I can try again, though.

---

### Post by Resdayn on 2012-05-14
Bump + Update:

I removed my HDD completely, then I plugged in a usb 2.0 pendrive baked with a bootable 32 bit version of Ubuntu 12.04 LTS. And it **WORKED**. It started and entered a live session successfully!
I discovered (a long time ago actually) that My HDD drive (~ 80GB) has one more partition than I thought. It has a C: and a D: partition, but also an inaccessible OEM partition used by Acer for recovery purposes. I think that this hidden partition is making Ubuntu/Mint/Debian/Any other distro go nuts when it tries to mount the partition/drive or whatever it is doing. Could anyone confirm this perhaps?
If the OEM partition is the culprit, then my best option is to back up my Users folder of my Win7 installation, wipe the HDD completely, remove all partitions, then slice it up into two new partitions: One for distribution X and the other for Windows 7.
Or maybe I could just install distribution X to the OEM partition after I have deleted it and used the unallocated space to make an ext4 partition?
I'm very close now guys, your thoughts are much appreciated! :)

---

### Post by roelforg on 2012-05-14
Maybe your usb has problems?

But you can try wubi first to see if you really don't have hw problems.

---

### Post by Resdayn on 2012-05-14
I have tried wubi once before, and it failed. My usb pendrive is fine, I tried several pendrives. The point is, as soon as I remove the HDD, Ubuntu boots, which means I have "removed" the problem. So now I am waiting for someone to confirm my idea about the hidden OEM partition being the cause of this. It sounds very plausible to me. I hope I'm right, so I can finally install a decent OS on my "ye olde laptop". ;)

Edit: I contacted Acer support, asking them what was on the OEM partition, they were unable to answer me and redirected me to Answers By. They are closed right now so I will contact them when they are available. If there's nothing important on the OEM partition, then I might aswell wipe it and make an ext4 partition out of it.

---

### Post by WOteB on 2012-07-18
Run at the startup the setup (the F2 key); In one setting you can choose to display F12 at boot time. Check this on (default is off) and save this setting. Now you can boot everything by pressing the F12 key and choose the pendrive, CD-Rom or your own harddrive as well. Now -YOU- can choose what to boot. I write this on an Acer Aspire 9300 and also had the same problem. So I hope that this will help you

---

### Post by MonsterNRG on 2012-09-16
the laptop will only accept 32-bit versions of linux on it :)just found that out today, no problems installing Zorin OS 5.2 (ubuntu 12.04 without all the crap) on it!!! :)

---

### Post by Bos007 on 2012-11-22
same problem her with an aspire 9303wsmi.

when booting from usb (serveral distros created with unetbootin/pendrivelinux), at a certain point I 've alway got this message :

"unable to find a medium containing a live file system"

guess what : you have to use the usb-port on the back, the rest won't work
now i can install lubuntu12.10\\:D/

---

