---
title: "Dell Mini 12 - not detecting hard drive"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by dkoelzer on 2009-03-16
Hi All,

I recently got a Dell mini 12. It came with Windows but i want to make it dual boot. I resized the main partition and created some free space for Linux partitions. I tried Ubuntu 8.10 but could not boot all the way up to the GUI with the LiveCD and the install would not complete it would just stop at a command prompt. 

I tried 8.04.2 and got much farther. I could boot from the liveCD and get all the way in. However when I tried to install onto the hard drive either from the "install" icon from desktop or by "Install Ubuntu" from the boot sequence, it does not detect any hard drive. I make a LiveUSB and got the same results except the install will detect the USB drive as /dev/sda but will not detect any hard drive. I also tried a mount /dev/sda1 /XXX but with no luck

The drive works fine and I can boot into Windows. I also tried Mandriva 2009 and it finds the hard drive and installs just fine. Also the Parted Magic utility(which is Linux base) I used to resize the main partition detects the drive and its partitions just fine. 

Any body have any ideas? I would rather have Ubuntu rather than Mandriva if I can get it to work.

---

### Post by dkoelzer on 2009-03-17
Any ideas? :(

---

### Post by Neil_J on 2009-03-17
I'm having the same problem with my Mini 12.  After a few hours of research, I haven't found any helpful information yet but will report back here if I do.

---

### Post by dkoelzer on 2009-03-19
Thanks Neil,

I'll open a ticket with Dell and let you know what I find out

---

### Post by brianchidester on 2009-03-19
This is because the Dell Mini 12 uses GMA 500 graphics and requires the proprietary Poulsbo driver which has not been integrated into Intrepid yet. It will be in Jaunty but I am not sure if it will make it in for the April release, and it will get into Intrepid at some point. I also am not sure why 8.04.2 got it first...

---

### Post by brianchidester on 2009-03-19
Two more things: first it appears poulsbo is in jaunty now. Second it appears I didn't address your primary concern with the disk, I can't help you there but this is why you can only get to the command prompt in 8.10 or 8.04- no video driver.

---

### Post by dkoelzer on 2009-03-21
Thanks Brian,

I have not gotten any response from Dell's forums. 

Since I have can't install to my hard drive, I think I'll install Ubuntu on a memory card. I have ordered a 8GB SD card. I'll see how that goes.

---

### Post by floquet on 2009-03-22
> **kylecronan said:**
> I was using an 8.04 CD (err, usb stick, actually).  Adding "all_generic_ide" to the kernel arguments allows it to install.  This must be some kind of kernel bug that was fixed by the time 8.10 came out.  Maybe even 8.04.1 would work, I think that's what the Dell website says they're using.  The behavior is very strange: sda cannot even be accessed by fdisk, and sdb1, the fat partition on the flash drive, doesn't mount...

This should solve the detection of the HD problem. You may also want to check this thread
[http://ubuntuforums.org/showthread.php?t=1014534&page=2](http://ubuntuforums.org/showthread.php?t=1014534&page=2)

By the way, did you get the full resolution or just VESA?

---

### Post by dkoelzer on 2009-03-22
Hi floquet,

I was just going through that thread. It is quite extensive and I looks like it will be very helpful but most of it goes over my head. 

I saw the "Adding "all_generic_ide" to the kernel arguments" fix as well but I am not sure what that means exactly. 

Do I need to make a change to one of the USBlive install files? 

If so which one, where in the file and what is the correct syntax? 

Or is this an option I can add at the UNetbootin menu? 

Or is this something else entirely?

Sorry to be such a Linux rookie but I would appreciate any help. 

And I was only getting 1024x768 during the Live boot. I was going to tackle the Poulsbo driver as soon as I could get an install onto my disk.

---

### Post by zacharydanger on 2009-03-31
Just got my Dell Mini 12 (was not happy with Dell's flavor of Hardy). To work around this hard drive detection issue use the ubuntu-8.04.2-alternate-i386.iso. It doesn't do the LiveCD install, but when it comes time to partition it'll ask you about which driver you want to use for the hard disk. Tell it you want to use "ide-generic" and voila! You should be on your way.

I'm installing Hardy right now, I'll let you know if it explodes in my face.

**Update:** Got to 83% install and then died out because it couldn't install kernel package 'linux-generic'. :-/

---

### Post by dkoelzer on 2009-04-02
Thanks zacharydanger, 

I'll give that a try

---

### Post by dkoelzer on 2009-04-04
Well I got a little farther than zacharydanger using his suggestion but I am still not working. The install completes but after I reboot I get: 

Alert! /dev/disk/by-uuid/1caeb1ed-3443-4f0f-9271-887d9160ba4a does not exist. Dropping into a shell!

Not what I was hoping for. :(

---

### Post by dkoelzer on 2009-04-12
hi guys,

I did a little work and I have gotten things working

I installed Ubuntu 8.04.2 but so that it would detect the hard drive, I edited the syslinux.cfg file and to the "default" menu section I added all_generic_ide to the line like "[FONT="Courier New"]/boot/vmlinuz-2.6.24-23-generic root=UUID=9b640f9f-07d7-41d6-82a7-d2c24b240824 ro quiet splash all_generic_ide[/FONT]"

After the install I had to modify the GRUB boot menu similarly adding the all_generic_ide to the /boot/vmlinuz line

I got VGA and wireless working. I still need to get sound working and see if I can get better than 1024x768.

---

