---
title: "USB Jump Drive &amp; Other USB Drive Problems"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by muskratfajita on 2005-08-25
Hi.  I would greatly appreciate help with this issue.

I'm running Ubuntu on a Compaq Armada PIII 700 laptop.  I hadn't had any problems with the machine recognizing anything I plugged into my USB ports until recently.  I have an Imation Jump Drive.  The first few times I plugged it into the USB port, it was recognized and I could manipulate files on the drive.  Then one day, it just stopped working (i.e. it doesn't recognize it automatically and I don't see any way to mount it)  The same is true with my digital camera.  I have a Vivitar digital camera and it used to be recognized by Ubuntu as well.  Now, it doesn't recognize it at all and I can't mount it.  

The laptop only has one USB port.  I'm sure that it is still functional because I have a USB mouse that still works as well as a Wacom tablet that works.  But the Jump Drive and Camera don't.

I also know that the devices work because I have a dual boot with Mandriva and Mandriva recognizes both the camera and the jump drive when I put them in.

I've tried booting with the devices attached... I've tried booting and attaching them after.

Is there an easy solution to this problem?

Any help would be greatly appreciated!

MF

---

### Post by s_p_a_r_k_y on 2005-08-25
could be that your hal or udev is screwed up. After plugging in devices try running the command 

dmesg | tail

and post the output so we can see whats happening on your system after you plug it in. Also check your settings in System->Preferences->Removable Drives and Media Preferences and make sure the correct options are still set.

Another trick, check and see if it only affects your user account. Create  a new user and log in as him/her and see if automounting works for their account

---

### Post by muskratfajita on 2005-08-26
Thanks Sparky for replying...

I plugged in my imation USB drive and then typed dmesg | tail...
this is what I got:

:~$ dmesg | tail
SCSI device sda: 64000 512-byte hdwr sectors (33 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
SCSI device sda: 64000 512-byte hdwr sectors (33 MB)
sda: Write Protect is off
sda: Mode Sense: 03 00 00 00
sda: assuming drive cache: write through
 /dev/scsi/host0/bus0/target0/lun0: p1
Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0


I also checked the system, preferences, removable drives and everything looks in order...

Any help you could give will be greatly appreciated!

Thanks in advance!
MF

---

### Post by s_p_a_r_k_y on 2005-08-26
i've had such problems before, but I started using linux before automounting worked : )

check and see if hald and udev are running with the following command

ps aux 

then scroll thru the list and look for them. If they say [defunct] then they crashed and died or something and wont automount.

You can always mount it yourself by sudo mount /dev/sda /media/... and chose a folder there. You may need to mount /dev/sda1 if it has a partition table besides using the whole drive. Play with it : )

---

