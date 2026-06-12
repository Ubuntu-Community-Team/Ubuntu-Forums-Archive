---
title: "ubuntu 9.10 64bit dual boot with windows 7 64bit - sound problem"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by h0ffmeister on 2009-11-03
Hi there,

I've been a long time reader but this is my first post. I have a problem with a new machine I have been building. I've been using Ubuntu for years and decided to build a Windows 7/Ubuntu 9.10 dual boot machine to consolidate my PCs.

I installed windows 7 home premium on a dedicated hard disk. All went fine and did windows update to solve driver issues. At this point I had sound. I then installed ubuntu 9.10 on a separate physical disk without issue. Ubuntu installed Grub which recognised windows 7 and I could boot into both OSes, both working happily, including sound. I then installed some apps in ubuntu (incl. wine and spotify) and now when I boot into windows 7, I don't have any sound. The sound icon is happy, the device manager is happy. I haven't touched the windows disk or installation, yet the sound doesn't work. The sound hardware is a Sound Blaster Audigy PCI card. To get Spotify to behave under wine, I set the Audio to be OSS instead of ALSA and use hardware emulation.

Surely making changes in Ubuntu on its own separate physical disk should have no effect on a Windows 7 installation on a different disk?

Any advice/ideas?

Thanks,

H0ff.

---

### Post by h0ffmeister on 2009-11-05
Hi,
 
I can only assume that something is happening at the OSS/ALSA level with the card which somehow affects the way the Windows 7 driver communicates with the device. I also found this unfortunately:
 
[Sound Blaster Audigy SE OEM]("http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Hardware&p=Creative%20Sound%20Blaster%20Audigy%20SE%20Sound%20Card&v=Creative&uid=70SB057000000&pf=0&pi=6&s=creative%20audigy&os=64-bit")

I didn't even consider this as I tested Windows 7 Ultimate eval for a few weeks on the same hardware without any problems. I only got issues when I dual booted. I've decided to get another sound card - one that is compatible with Windows 7:

[Sound Blaster X-Fi Extreme PCI-e]("http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Hardware&p=Creative%20PCI%20Express%20Sound%20Blaster%20X-Fi%20Xtreme%20Audio%20Sound%20Card&v=Creative&uid=SB1040&pf=2&pi=1&s=creative%20sound%20blaster&os=64-bit")
 
Thanks a lot Microsoft! 

It still doesn't explain why it worked and then stopped when I did "sound" things in Ubuntu.

---

### Post by h0ffmeister on 2009-11-05
Hi,
 
I can only assume that something is happening at the OSS/ALSA level with the card which somehow affects the way the Windows 7 driver communicates with the device. I also found this unfortunately:
 
[Sound Blaster Audigy SE OEM]("http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Hardware&p=Creative%20Sound%20Blaster%20Audigy%20SE%20Sound%20Card&v=Creative&uid=70SB057000000&pf=0&pi=6&s=creative%20audigy&os=64-bit")

I didn't even consider this as I tested Windows 7 Ultimate eval for a few weeks on the same hardware without any problems. I only got issues when I dual booted. I've decided to get another sound card - one that is compatible with Windows 7:

[Sound Blaster X-Fi Extreme PCI-e]("http://www.microsoft.com/windows/compatibility/windows-7/en-us/Details.aspx?type=Hardware&p=Creative%20PCI%20Express%20Sound%20Blaster%20X-Fi%20Xtreme%20Audio%20Sound%20Card&v=Creative&uid=SB1040&pf=2&pi=1&s=creative%20sound%20blaster&os=64-bit")
 
Thanks a lot Microsoft! :mad:

It still doesn't explain why it worked and then stopped when I did "sound" things in Ubuntu.

---

### Post by trevelyan on 2009-11-05
but there is a [windows 7 dirver for that card]("http://support.creative.com/Products/ProductDetails.aspx?catID=1&subCatID=205&prodID=14257&prodName=Audigy%20SE&subCatName=Audigy&CatName=Sound+Blaster")
try installing it and maybe this takes care of the problem under Win 7.

---

### Post by h0ffmeister on 2009-11-05
Already tried that. Uninstalled the Windows Update one and installed the Creative one - still no sound.

---

### Post by trevelyan on 2009-11-05
are you sure its your default device? win 7 is much like the new sound preferences in Karmic and you have to choose your default device to get sound there.

---

### Post by h0ffmeister on 2009-11-05
> **trevelyan said:**
> are you sure its your default device? win 7 is much like the new sound preferences in Karmic and you have to choose your default device to get sound there.

Yes, definitely default device.

---

### Post by trevelyan on 2009-11-06
and all is fine in ubuntu?
to choose your default device under windows 7:
-right click the speaker icon on the taskbar
-left click on "playback devices"
makes sure you choose the correct default device, if not right then
-right click the device you want to be default
-left click on "set as default device".

if you did this already then i don't know. i don't see why creative would have a driver there and say it works if it doesn't... a quick Google shows people with the card working under Windows 7 (although with other issues instead like no subwoofer output)
[here is a link]("http://www.sevenforums.com/sound-audio/2861-sb-audigy-se-no-bass-redirected.html") to a thread discussing that issue, the last post has a solution. maybe it works for you.

---

### Post by andr0x on 2009-11-06
This is definitely a clear problem, I've also been using ubuntu for awhile and have just recently switched to 9.10, I had previously been using 9.04 with windows 7 but when I installed 9.10 the sound in windows 7 has stopped working. I have an audigy 2 se card. I have tried restarting the creative audio sound service and a variety of different methods, nothing works :(

sound works in ubuntu though. I am running 64-bit btw.

---

### Post by AeroCross on 2009-11-20
After a while of experimenting this issue, the only "workaround" (if it can be called like that) is to shut down (not reboot, but to SHUT DOWN) the computer, wait a bit, then start Windows 7.

It's weird tho, I've read somewhere else that there's a problem in the way Ubuntu releases the Sound Card drivers or hardware itself, and when it reboots, Windows can't grab the device. It deactivates it, in some sort of way.

Turn on PC, boot Windows - Sound Works
Turn on PC, boot Ubuntu - Sound Works
Turn on PC, boot Windows, THEN Ubuntu - Sound Works, both times.
Turn on PC, boot Linux, THEN Windows - Sound Works only in Ubuntu
Turn on PC, boot Windows, then Linux, THEN Windows - Sound works until 3rd reboot.
Turn on PC, boot Linux, then Windows, then Linux - Sound works at 1st and at 3rd time.

If I shut down, no matter what, sound works.

It's a REALLY strange behavior, don't know who to blame in here. Might be faulty code on any of those ends.

Running both 32 bit editions of Ubuntu and Windows 7. Note that this wasn't happening back in 9.04, when the sound system wasn't revamped. Coincidence?

---

### Post by AleFranz on 2009-11-20
I get the problem if I boot to another OS by a reboot, after using ubuntu 9.10.

For example:

Turn on PC -> Vista (audio Ok)
Turn on PC -> Ubuntu 9.10 (audio Ok) -> reboot -> Vista (no audio)

Ubuntu and Vista are all x64
Soundcard: Audigy SE

---

### Post by AeroCross on 2009-11-20
We might be able to discard Windows 7 drivers - Vista drivers aren't beta, are they?
Did you use to have that problem back in Jaunty?

We might have to fill in a bug report.

---

### Post by AleFranz on 2009-11-20
We post at the same time.
btw i found on the net that this problem occurs with different audigy soundcard and drivers.

I think this is related to some switch on the soundcard that windows driver can't control.

Someone said that only the digital output work, but I don't have digital speaker to test with. Btw I tried to switch to/from digital output with no luck.

It's already on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453395)

maybe we can post there more details...

---

### Post by gfajdi on 2009-11-22
Same problem here. Could it be that this is a problem with Ubuntu incorrectly releasing sound card resources?

---

### Post by mrebanza on 2009-12-08
yes that seems to be the problem . . . . now I am scared to dual boot ubuntu with windows 7 . . . . I dont have system restore disks for windows 7 punk *** . . . . they dont include them when you buy a new laptop anymore . .. . wtf

---

### Post by AleFranz on 2009-12-08
You can found the fix on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453395/comments/5](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453395/comments/5)

---

### Post by Kleist on 2010-01-07
I've been looking for a solution for this!

Thanks dudes...it worked for me. I have the same problem with windows xp and ubuntu in my dual boot.

:D

---

### Post by esueeze on 2010-04-04
I am having a similar problem with Windows Vista. I have been running Windows Vista for years and my soundcard has been fine. So please don't tell me it's a Windows driver compatibility problem, that is just a very lazy answer.

Yesterday I installed Ubuntu on my PC to dual boot with Windows Vista. My SB Audigy works fine in Ubuntu but, although it is enabled, installed and configurable in Windows Vista I get no sound from my speakers.

Eliminated a hardware problem by testing the speakers with another sound card on the PC.

I haven't tried powering off completely yet but I have tried several reboots into both OS's.

This does appear to be an issue with Ubuntu and not Windows.

Anyone have any ideas about fixes?

---

### Post by zwastik on 2010-06-25
> I was lucky to find a solution to this problem, when reading about other problem. When you edit /etc/init.d/alsa-utils, and comment the 378th line:

# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1

the sound seems to work properly after restart from Ubuntu to Windows. Hope it will work for you too.

this does not work for me.

ubuntu 9.10 + windows 7 + Audigy SE

---

