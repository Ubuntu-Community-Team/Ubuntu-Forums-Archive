---
title: "Hard drive not being seen"
date: 2011-07-02
forum: Hardware
---

### Post by xj0hnx on 2011-07-02
I posted this on Techsupportforums also as I have been doing everything in Windows, but I have Ubuntu 11.04 installed on my laptop, so maybe there is something in Linux that can help me recover my hard drive.

Here's the original post ...

So the last few days my computer has been behaving pretty badly. Media players locking up on files I know they can play, sound disappeared today while watching a Youtube video, then Shockwave stopped working, having to close things with the Task Manager, and a problem shutting down. When I shut down it gets to the spinning circle telling me "Shutting Down", but just can't seem to accomplish the mission, I have to do a hard restart. Also my external HDD, the subject of this thread, just started blinking tonight, nothing else. The last few days when I wake the computer up after using the sleep button on the keyboard (this is new, just got the keyboard and tried it out and it worked so I started using it), it's been giving me a message about not recognizing a device plugged into a USB port.

So, I decided to reinstall Windows, and start fresh, but this external hard drive has everything on it, and when I say everything I mean it, all my programs for reinstall, music, family movies, and pictures (these are the really important things), collection of documents from over the years, basically everything I don't want to lose :(


Motherboard is a Gateway TBGM01 from a FX6800-E01
Intel i7 920
6GB Corsair
3 1TB drives (internal)
1 1.5TB drive (internal)
JMicron drives installed
All the OEM Intel drivers
ATI Catalyst 11.5
Lacie 250GB external HDD (A) single drive (this is the one I am trying to rescue)
Lacie 500GB external HDD (B) two drives

So far I have removed the drive from the enclosure (A), and installed it into another external enclosure (B). When I turn that one on, the one that stayed in can be opened, but the disk I am trying to save pops up the "You need to format the disk in drive M: before you can use it. Do you want to format it?" message, so I cancel. When I try it as the only disk in the enclosure (B) nothing happens, also when I have the jumpers set to Master, nothing happens whether it's the only disk or not.

The disk I took out of the enclosure (B) I am using, when I put it in the enclosure (A) for the disk I'm trying to save came from nothing happens, no matter the jumper settings. So I am guessing the original problem is the controller for the enclosure (A), it appears that the disk is still functional.

Is there anything I can do to access this HDD so I can copy at least the pictures? Would Linux not be so picky?

Sorry for the rambling, I tried to explain as best I can, yet be brief.

Thank you in advance. 

As well as the above, I have also used a ByteCC Superspeed USB 3.0 IDE/SATA to USB adapter with both a known good HDD, and the drive I am trying to recover. The known good works fine, the one I am operating on doesn't do anything. The drive does spin up, there's just no output.

**[COLOR="Red"]EDIT: Ok, just in case this ever happens to anyone, don't forget to replace the jumpers on the HDD. It had to be set to Master even though it was all alone on the adapter. Still doesn't work in the external enclosure though, but at least now I can burn all the important stuff to discs.[/COLOR]**

---

### Post by dabl on 2011-07-02
> **xj0hnx said:**
> 

 I have to do a hard restart.

This is a bad thing to do to the filesystem on the drive, even if you feel you "have to".  Whenever you find yourself in that situation, use Alt-SysRq "R S E I U B" (the so-called "magic sysrq" shutdown method).

OK, on the problem.  Is the drive connected to the computer via USB?  If so, you might try unplugging it, then booting a Linux system (could be a Live CD, for example), then plug in the USB connector.  This should trigger the "device notifier".  If that does not work, then after a few seconds, run "fdisk -lu" in a terminal and see whether the drive is listed.

Does that external drive have a conventional SATA or IDE connector on it?  If the USB connection doesn't work, then you might need to connect the drive directly to your motherboard to have it "seen" by the computer.

---

