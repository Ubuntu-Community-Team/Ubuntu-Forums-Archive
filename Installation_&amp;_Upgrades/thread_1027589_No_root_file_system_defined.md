---
title: "No root file system defined"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by hansmax on 2009-01-01
I am trying to install Ubuntu 8.04.1 on my second computer.  I have Windows XP on the C drive, and I have a D drive empty, that is formatted ext3, and a J drive, which is formatted FAT32.  (These are all on one 200 GB hard drive.) I did the resizing, repartitioning and reformatting with PartitionMagic 8.0.  I am now trying to install Ubuntu on the D drive from the live disk, and when I go into choosing a drive to install it on, get a message to the effect that there is no root file system on the drive and I need to establish that, so I tried to edit the partition (which is set to "do not use this partition" by default.  It seemed that choosing "ext3 journaling partition" would be the most logical choice, but it just kicks me back to the "no root filing system is defined" message.  What am I doing wrong?  Any help would be appreciated.

---

### Post by prshah on 2009-01-01
> **hansmax said:**
> It seemed that choosing "ext3 journaling partition" would be the most logical choice, but it just kicks me back to the "no root filing system is defined" message.  What am I doing wrong? 

After setting the type (ext3...partition), you will have an option to set a "mount point", in that, type in "/" (forward slash. no quotes), which will tell the computer to use that partition as a "root" file system.

A word of warning: Ubuntu has no concept of "drives" as in Windows; everything comes under "/" (root). Typically, each partition (what is called "drives" in Windows) will be mounted as a directory under "/media".

Be careful when selecting partitions; choosing the wrong one will (instantly) wipe out all data on the said partition.

---

### Post by hansmax on 2009-01-01
That seems to have done the trick, prshah, and many thanks.  However, I am now being prompted that I have not designated any swap space.  Is there a way to do that from within the CD, or do I have to go back out to XP and Partition Magic to create a new swap partition, and, if so, how large should I make it?

---

### Post by prshah on 2009-01-01
> **hansmax said:**
> I am now being prompted that I have not designated any swap space.  Is there a way to do that from within the CD, or do I have to go back out to XP and Partition Magic to create a new swap partition, and, if so, how large should I make it?

Ubuntu has a very good partition manager at System-Administration-Partition Manager. You can use this to create swap space out of any unallocated space available. If you don't have any unallocated space (different from "free" space) then you need to "shrink" any of the existing partitions to get some unallocated space. You can then create a new "swap" partition. For a more detailed explanation, post a screenshot (Alt+PrintScreen or Applications-Accessories-Take screenshot) of the partition manager window or (if you have more than one hdd) open a terminal (Applications-Accessories-Terminal) and give the command```
sudo fdisk -l
``` and post back the output here.

As to size: Here's some guidelines:

a) If you have RAM less than 512Mb, make swap 1~1.5Gb in size
b) If you have RAM less than 1Gb, make swap 1.1~1.5Gb in size
c) If you have RAM more than 1Gb and..
[indent]i) Plan to use hibernate, make swap 1.1*RAM (eg, if you have 2Gb RAM, make swap 2.2Gb) OR
ii) if you do not plan to use hibernate, 1Gb~1.5Gb swap is fine.[/indent]

If you plan to do a lot of graphic editing, audio / video editing then you will benefit with more swap than mentioned above.

---

### Post by hansmax on 2009-01-01
Thanks for the quick reply.  I will get to work.

---

### Post by hansmax on 2009-01-01
Well, it went well for a while.  It installed the system files, and while it was cleaning up and getting ready to finish up, the screen slowly faded to black and stayed there.  I rebooted,got the MB splashscreen and boot selection screen, then picked Ubuntu to boot into, and again, a black screen.  I shut down and rebooted into Windows XP, which worked fine, so I doubt it's the monitor.  Maybe a conflict between my Intel onboard video and Unbunt?  How the heck would I start to fix something like this?

---

### Post by prshah on 2009-01-01
> **hansmax said:**
> 
rebooted,got the MB splashscreen and boot selection screen, then picked Ubuntu to boot into, and again, a black screen.

Do you have any idea if the installation completed successfully? 

Alternative: When the Ubuntu splash screen is displayed, press Ctrl+Alt+F8; this will let you see details on what the system is doing while loading up. If the screen flickers and goes to black, go back to the Ctrl_Alt_F8 screen and post the last 20 or so lines shown there.

Another alternative: When the screen goes black, press Ctrl+Alt+F1 to switch to a "virtual terminal" command line based mode. Login, and post back the output of the commands```
dmesg | tail -20
```

YAA (Yet another alternative): When the screen goes black, press Ctrl+Alt+F1 to switch to a "virtual terminal" command line based mode. Login, and [Don't ya just love copy/paste] give the commands```
sudo /etc/init.d/gdm stop
sudo chmod a-x /usr/bin/compiz*
sudo /etc/init.d/gdm start
```
...And then press Ctrl+Alt+F7 to see if you have a working desktop (Try F9 or F10 also).

---

### Post by hansmax on 2009-01-01
It just gets stranger.  Ctr+Alt+F1 gives me Ubuntu (I mean what appears to be the operating system.  It seems to be pretty fully functional.  The wireless card does not appear to be recognized, and until I get that, I guess I'm still in the dark, but I do have access to the OS.  I will try to figure out the wireless card issue myself, and then probably be back here in a while.

---

### Post by hansmax on 2009-01-02
I'm going to try reinstalling it the next chance I get, and this time I am not going to import my WinXP settings.  I'm thinking that maybe there was some power management setting or something else related to the display that is conflicting.

---

### Post by hansmax on 2009-01-03
Well, I reinstalled and all went well.  I didn't lose the monitor like last time  (this time I did not import any accounts).  I also did not lose the monitor, and was able to get the wireless card going.  However, when I tried to change the screen resolution, I lost the monitor again, this time apparently for good.  Ctr+Alt+F1 does get me in to a command prompt, though.  Is there anything I can do from it to change the resolution back.  Otherwise I guess I can reinstall again and leave the resolution alone, I guess.

---

### Post by hansmax on 2009-01-03
I tried running sudo dpkg-reconfigure xserver-xorg, but after going through about a half a dozen screens asking me about how I wanted the keyboard, it just dumped me back at the command prompt.  Maybe a reinstall would be easiest, although this is kind of fun and interesting.  I'll wait a while to see if there are any replies.

---

### Post by hansmax on 2009-01-03
Well, I tried the "Try to fix X-Server" option and that did the trick.  The only question I have now is is there any way to reset screen resolution without messing it up again?  Otherwise I'll just live with it until I get a little more expertise.

---

