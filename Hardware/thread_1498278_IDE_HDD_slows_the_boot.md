---
title: "IDE HDD slows the boot"
date: 2010-05-31
forum: Hardware
---

### Post by 337Manni on 2010-05-31
I wonder if anyone  would be kind enough to help me.

I have a HTPC currently running XP. I am looking to install Ubuntu on a spare IDE HDD I have and when I'm happy with the set-up I will remove XP.

Some quick specs:
I have an Asus motherboard (P5E3 Deluxe Wifi @n).
 I have my OS (Win XP) installed on a Fake RAID 0 (2 x 150GB Raptor X both SATA 2).
 The system runs fine in this state.
 
The problem I have is when I install the IDE HDD, upon boot, after the POST the Jmicron Controller screen is shown as normal and this time the IDE HDD is seen and recognised. Then the Intel Matrix Screens is displayed as normal showing my SATA RAID 0 set-up, the screen then goes blank, but before XP starts to load there is a 2-3 minute delay. It just looks like my system has froze. No HDD activity, no beeps, no nothing. After this delay XP loads without a fault.
 
I want to keep the XP side running until I have ubuntu fully running as my HTPC, so this time would be a pain to live with.
I have tried the Asus forum and up to now I'm talking to myself. :)

I have set-up the JMicron controller in both IDE and ACHI mode. I have tried a different IDE HDD, tried the jumper in master, C/S and even slave and all give the same result.
 I’ve checked the BIOS and the SATA RAID 0 is set as the boot priority 1.

 Eventually after the delay, when I log  into XP all is fine. The drive is seen. I have formatted it and can use it with no problems. It just causes this delay on boot. If I unplug the IDE HDD all returns to normal and XP boots straight after the Intel Matrix Controller screen.
 

 Any suggestions as to what I can do are welcome.

---

### Post by oldfred on 2010-05-31
Are you using the newer 80 conductor cable select cable - three different color connectors. The old 40 (with master  set should work) but the newer cable may be all the is now compatible with newer motherboards.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

---

### Post by 337Manni on 2010-05-31
Hi Oldfred, thanks for the reply.

Unfortunately I am using the 80 pin type cable. I got this with my motherboard. I forgot to mention that I had tried another cable as well in case this one was damaged / badly made but had no joy with that one either so I refitted the newer of the two.

---

### Post by oldfred on 2010-05-31
I have seen several odd problems/solutions.
 
One user left a CD in CD drive and system was doing fsck on CD. Took forever. Removed Cd and it boot right away.

Some have found BIOS with floppy configured but do not have floppy drives. The changed BIOS setting and boot was much faster.

Some have just removed the search line in grub and it boots quicker.
At grub menu press e and totally edit out the search line. control x to boot.

Various settings in BIOS. IDE compatibility seems to be required.

---

### Post by 337Manni on 2010-05-31
There's no CD in the drive, CD is SATA and has also been removed as a boot device.

I don't have a FDD and there is no floppy configured in the BIOS.

I haven't installed Ubuntu / grub yet on this system.

Anything else you can think of trying / checking?

Everything runs fine when I boot up with the IDE HDD unplugged. I'm starting to think the Jmicron controller on the motherboard is struggling to comunicate with the HDD. Is there anyway to check if the system and the HDD are having any problems? I'm running XP but I have a bootable USB stick with Ubuntu 10.04 on ready to install. I could run it from the USB without installing and use it to trouble shout, but not sure where to begin with the fault finding.

---

### Post by oldfred on 2010-06-01
If your IDE drive is large enough just shrink XP down to about 20% free (minimum required to keep working) and set up / (root), /home and swap partitions. I had partitions set up so there was no resizing required and I think it took 9 minutes to install 10.04. It took longer to download all the updates. I am working on scripts to reload my configuration programs and links to /data, so I have not yet converted to 10.04 but it works once I fixed the nvidia issue.

---

### Post by 337Manni on 2010-06-01
XP is on my Fake RAID 0 setup (SATA hdd’s). I was hoping I could leave this alone, install ubuntu to my spare IDE hdd along with grub. I could then just point my BIOS at the IDE hdd when I have time to play with ubuntu / the setup.
   
  The reason I want to do this is because if I can’t set up ubuntu as I would like, I could just unplug the IDE hdd and, point the BIOS at my SATA RAID 0 setup and I’m away again. 
   
  I have to set-up a dual TV tuner, schedule TV recordings meta date for my films to catalogue. I have the PC hooked up to my TV and had problems with my graphics card over scanning on XP. The same happens in ubuntu so I know it may take me a while before I get it setup just right and I can make the switch. 
   
   
  I tried booting Ubuntu 10.04 from a USB stick and when it was configuring my systems hardware it struggled with the IDE device. It kept trying to communicate with the HDD and failing. Each time it failed it tried again but altered the UDMA. It started off at UDMA / 133, then UDMA / 100, 66, then 33. I missed what was said after that, but when ubuntu finally loaded the IDE hdd was seen and could be used.

I have the 80pin cable and either of the two HDD I have tried are capable of ATA-100.

In XP > Device Manager > Primary IDE Channel > Advanced Settings: the Device Transfer Mode is set to "DMA if available", but the Current Transfer Mode is saying "PIO Mode".
It looks as though the controller is trying to communicate with the HDD, struggling and so lowers the speed until it reaches the lowest. This would account for the long pause.
   
  I am thinking I have a problem with the Jmicron controller on my motherboard. I’m hoping it could be fixed with some kind of firmware or BIOS update, but I have never done either of these before. I have posted the questions below on my thread at the Asus forum, but haven’t got one reply to any of my posts so far.
   
  1. Does anyone know of an issue with the Jmicron Controller that would cause this?
2. How can I check divers/firmware I have for this controller?
3. Is there a good how to for me to update this drivers/firmware?
4. Failing that is there a recommended way to update the BIOS and to what revision would you recommend? - Never done this before.
5. Also what else would you recommend up dating before or after the BIOS update.

---

### Post by oldfred on 2010-06-01
I used to update BIOS regularly but have not for a while. I still have a floppy drive and always just created a DOS bootable with the file on it as it always was a dos executeable.

Most motherboard mfg. have instructions on how to update. I did save this.
HOWTO: Flash BIOS, The Ubuntu Way
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

I also have the jmicron but only used my Pata drive once while building system to copy all the data to my SATA drives. I do not have an ASUS motherboard.

---

### Post by 337Manni on 2010-06-01
Thanks for your help so far Oldfred.

I will start searching in the Jmicron controller and updating my BIOS and let you know how I get on.

Fingers crossed!

---

