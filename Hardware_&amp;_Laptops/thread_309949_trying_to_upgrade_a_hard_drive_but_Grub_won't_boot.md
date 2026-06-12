---
title: "trying to upgrade a hard drive but Grub won't boot"
date: 2006-11-30
forum: Hardware &amp; Laptops
---

### Post by trstn on 2006-11-30
Ok, I might be over complicating this but here's my problem:

Currently I've got two physical Hard drives, the master has windows server 2003 installed and the slave has ubuntu edgy eft on it. As time's passed I've found less and less need to boot into windows so i'm getting rid and just using ubuntu. Problem is i've a lot of files and stuff on the windows drive i don't want to lose.

Because the master drive is only 40gigs I've gone out and bought a 180gig replacement, thinking i could unplug the windows drive, plug in the new one and boot into ubuntu, format it with ext3, then unplug the ubuntu drive, plug the windows drive back in, boot into windows and copy the files accross before closing my case with the original ubuntu drive as master, and the new 180gig drive as the slave.

I've done this before with windows setups, though obviously it was all within windows and not using a bootloader like grub. Now i can't work out how to swap the drives around.

Basically if i unplug either of the existing drives i get grub error 5, leaving me with no way to boot into windows or ubuntu.

I need to....

Remove hda1 (windows drive) and boot into ubuntu to format the new drive with the ext3 filesystem

Remove hdb1 (ubuntu) and boot into windows to copy files accross to the new drive

Remove hda1 completely and make the hdb1 (ubuntu) the master drive, and the new drive its slave.

I've worked out getting ext3 working in windows so i know i can use the drive once it's formatted for ubuntu, but my pc only appears to accept two hard drives at once, so i'm stuck at the moment and throwing this down to the community for help.

---

### Post by apjone on 2006-11-30
can u plug the new disc in instead o your cd rom drive and just check the bios is set correctly.

---

### Post by trstn on 2006-11-30
Tried that, the computer starts to boot up but there's no option to enter the bios settings before grub pops up with the error.

I think it might be due to the mbr being on hda1 but the grub config files being on hdb1, so if i remove either one grub messes up. Google's giving more questions than answers though :(

---

### Post by trstn on 2006-11-30
Ok apjone, i've plugged the new hard drive into my dvd/cd cable and booted into ubuntu, the new drives shows up as /dev/hdc in `fdisk -l`, So the disk works. 

I should be able to format it and then boot into windows and copy the files accross and get the messing about done, so that's good. But how do i modify grub to get rid of the windows drive and just use ubuntu and the new one?

---

