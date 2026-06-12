---
title: "Secondary HDD With win98 Not Detected"
date: 2011-03-27
forum: Hardware
---

### Post by Destructo47 on 2011-03-27
Because of a video card problem I had before, I had to erase my entire Ubuntu install and start fresh.  Before doing that, I used a Karmic Live CD (tried burning a Lucid CD but the md5sums never matched) and moved all of my personal data onto a hard drive with Windoze 98SE on it (it was the only extra I had). The 98 drive is a fat32 IDE drive and the Ubuntu drive I have right now is an ext4 SATA II drive with the swap partition on the end. I'm on an Abit IS7 motherboard with a P4 HT 3.00 GHz.

Now, here's my problem:
     The Karmic CD saw the 98 disk fine. For some reason or another, neither the BIOS nor Ubuntu is detecting the drive with 98 on it. I have looked in the box and am 100% sure that the drive has both the data ribbon and the power connected properly, and that the jumper is set to slave. I have tried changing BIOS settings multiple times and it still will not show up. Trying *fdisk -l* and *mount* will not show the drive's properties, and it is not listed in /etc/fstab. Why is it not showing up?

Before anyone asks, the 98 drive is ***not*** on the same IDE channel as the CD/DVD drive.

---

### Post by tgm4883 on 2011-03-27
> **Destructo47 said:**
> Because of a video card problem I had before, I had to erase my entire Ubuntu install and start fresh.  Before doing that, I used a Karmic Live CD (tried burning a Lucid CD but the md5sums never matched) and moved all of my personal data onto a hard drive with Windoze 98SE on it (it was the only extra I had). The 98 drive is a fat32 IDE drive and the Ubuntu drive I have right now is an ext4 SATA II drive with the swap partition on the end. I'm on an Abit IS7 motherboard with a P4 HT 3.00 GHz.

Now, here's my problem:
     The Karmic CD saw the 98 disk fine. For some reason or another, neither the BIOS nor Ubuntu is detecting the drive with 98 on it. I have looked in the box and am 100% sure that the drive has both the data ribbon and the power connected properly, and that the jumper is set to slave. I have tried changing BIOS settings multiple times and it still will not show up. **Trying *fdisk -l* and *mount* will not show the drive's properties, and it is not listed in /etc/fstab. Why is it not showing up?**

Before anyone asks, the 98 drive is ***not*** on the same IDE channel as the CD/DVD drive.

If the BIOS cannot see the drive then Ubuntu will never see the drive. So you can stop wasting your time with that for now.

If you unplug the rest of your devices can the BIOS see the drive?

---

### Post by Destructo47 on 2011-03-27
> **tgm4883 said:**
> If the BIOS cannot see the drive then Ubuntu will never see the drive. So you can stop wasting your time with that for now.

If you unplug the rest of your devices can the BIOS see the drive?

It will not detect the drive even if the other devices are unplugged. It doesn't matter if it's on IDE channel 1 or channel 2. Could it be corrupted CMOS or BIOS? I have the BIOS set to detect up to 6 drives at once, just to be clear.

---

### Post by tgm4883 on 2011-03-27
> **Destructo47 said:**
> It will not detect the drive even if the other devices are unplugged. It doesn't matter if it's on IDE channel 1 or channel 2. Could it be corrupted CMOS or BIOS? I have the BIOS set to detect up to 6 drives at once, just to be clear.

Hmm, IDK. Try it in another computer maybe?

---

### Post by Destructo47 on 2011-03-27
The only other desktop in the house is our outdated win2k machine. I'd have to burn a bunch of DVDs or use my flash drive to transfer files over, which would take forever. Isn't there a quicker method of doing things?

---

### Post by tgm4883 on 2011-03-27
> **Destructo47 said:**
> The only other desktop in the house is our outdated win2k machine. I'd have to burn a bunch of DVDs or use my flash drive to transfer files over, which would take forever. Isn't there a quicker method of doing things?

Popping the drive into another computer is a way to test if it's an issue with the drive, or an issue with the computer. 

The BIOS isn't seeing the drive, so there is no OS that will be able to see it either.

---

### Post by Destructo47 on 2011-03-27
If a problem exists on this computer, then it might not exist on the other computer. See what I'm saying? Anyways, I'll see if changing the motherboard changes things.

---

### Post by tgm4883 on 2011-03-27
> **Destructo47 said:**
> If a problem exists on this computer, then it might not exist on the other computer. See what I'm saying? Anyways, I'll see if changing the motherboard changes things.

Thats exactly my point. If it doesn't exist on the other computer, then it's an issue with the first computer. If it does exist on the other computer, then it's an issue with the hard drive.

---

### Post by oldfred on 2011-03-28
Should it be master not slave. Or some drives have a master with slave setting. But the IDE chain will not see the SATA drive. So only the PATA drive & the CD/DVD drive are IDE. 

Are you using a 40 wire cable or the somewhat newer 80 wire cable select  cable. Then the jumpers have to be set to cable select.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Destructo47 on 2011-04-01
@tgm
Trying it on the other computer failed, as for some reason it won't even show a boot display or any display for that matter.

@oldfred
I believe the newer IDE cables you are referring to are called "Ultra ATA", with the older ones providing just a connection with the motherboard. I am using the non-UATA cables, so I set the jumper to slave since the SATA drive is on the same channel.
However, I believe I may have set the UATA cable incorrectly when testing on the win2k machine.
Even after all of this, isn't it possible that the logic board is fried or that I fried it on accident?

EDIT: In the win2k box, I had the slave IDE drive on the master connector, so I switched it. That still doesn't give me a display, however.

---

### Post by oldfred on 2011-04-01
I have set jumpers incorrectly and all it does is not work until corrected. I do not think that would cause a problem, but with older hardware anything can happen.

On newer computer did BIOS see drives? What was the exact issue.

---

### Post by tgm4883 on 2011-04-01
> **Destructo47 said:**
> @tgm
Trying it on the other computer failed, as for some reason it won't even show a boot display or any display for that matter.

@oldfred
I believe the newer IDE cables you are referring to are called "Ultra ATA", with the older ones providing just a connection with the motherboard. I am using the non-UATA cables, so I set the jumper to slave since the SATA drive is on the same channel.
However, I believe I may have set the UATA cable incorrectly when testing on the win2k machine.
Even after all of this, isn't it possible that the logic board is fried or that I fried it on accident?

EDIT: In the win2k box, I had the slave IDE drive on the master connector, so I switched it. That still doesn't give me a display, however.

Set it to master. The drive is not on the same channel as the SATA drive

---

### Post by Destructo47 on 2011-04-03
> **oldfred said:**
> I have set jumpers incorrectly and all it does is not work until corrected. I do not think that would cause a problem, but with older hardware anything can happen.

On newer computer did BIOS see drives? What was the exact issue.

When I booted that computer up, it wouldn't give me a display for some reason. Also, I meant frying it by means of static.

> **tgm4883 said:**
> Set it to master. The drive is not on the same channel as the SATA drive

That would have be in this computer then, since there's some sort of display issue on the other computer.

---

### Post by oldfred on 2011-04-03
If it starts then drive is ok, but display issues are totally separate.

What video  card/chip do you have?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Destructo47 on 2011-04-04
> **oldfred said:**
> If it starts then drive is ok, but display issues are totally separate.

What video  card/chip do you have?

On that computer is onboard video on an Asus M2NPV-VM motherboard. It's not that Ubuntu won't show, but that I can't get ANY display from it.

On this computer, it's a Radeon 9250SE, which is a little annoying because none of the drivers available allow it to run at full capacity (that's ATI for you).

As for tgm's suggestion, that seemed to work for some reason. However, I'm failing to understand why putting the jumper in the master drive position would change whether the BIOS sees the drive or not. Could you enlighten me?

---

### Post by oldfred on 2011-04-04
Depends on BIOS, but old BIOS only booted primary master. Not secondary master nor any slave drives. Four drives was the max.

Newer BIOS with SATA choose boot totally with BIOS since SATA has no jumpers. Depending on BIOS, new have more flexibility with IDE drives, older follow old standard. But generally it is better to have IDE drive as Master.

---

### Post by Destructo47 on 2011-04-04
That makes sense. Thank you for that explanation. :-P

---

