---
title: "Can't read/write my external hard drive with my Ubunut laptop."
date: 2018-01-13
forum: Hardware
---

### Post by monty22 on 2018-01-13
I had a Win 8.1 laptop that would not function due to a busted power button so I took out the hard drive and bought one of those interfaces (with enclosure) that allows it to be r/w with a usb cable.  On my other Win computer (Win 7) it reads/writes fine, but it won't even read on my Ubuntu 16.04 laptop, saying it's in hibernating and is in an unsafe state.  So far, I've read the old threads on this problem but none of the solutions work.  I tried disabling the hibernated state and shutting down when it was mounted to the Win 7 computer but it always gives the same message.  I used the ,remove_hiberfile setting, I tried to force a mount with $ sudo apt-get install ntfs-config and $ sudo mount -o rw /dev/sdXY, and I installed a new file manager, PCmanFM, but the same message always appears.  I have an older hard drive that I did this with, and it works fine with Ubuntu, though for both I had to take command of the drives for them to work on my Win 7 computer.  Is there another possible fix?  I have Ubuntu 16.04 on a USB stick, so is there a way of using that in my Win 7 computer to solve the problem?  Thanks!

---

### Post by yancek on 2018-01-13
Windows 7 did not hibernate by default, windows 8/10 do.  Most likely the problem is that it was hibernated when it was attached to the windows 8 system.  Since it was a drive with the proprietary windows ntfs filesystem on it, it is highly unlikely that you will be able to repair it with Ubuntu or any Linux system.  I'm not a windows user but, from what I have read about it you would need to boot into windows and disable fastboot and turn off anything related to hibernation.  Since the problem is with windows only, have you tried posting at a windows forum?

---

### Post by monty22 on 2018-01-13
Thanks.  Yes, as I said, I tried all the old suggestions (in the Win 7 computer, I went to the the command prompt, switched over to the 8.1 drive (E) and used powercfg -h off.  There was no error message so I assumed it would work.

My thought about the USB drive with Ubuntu on it is that if I mounted the old 8.1 hard drive on the Win 7 computer then went and stuck the USB drive in and brought up Ubuntu that way, it allow me to use $ sudo apt-get install ntfs-config and $ sudo mount -o rw /dev/sdXY, or the  ,remove_hiberfile setting.  Does that sound possible?

---

### Post by yancek on 2018-01-14
My understanding is that there are multiple settings for hibernation/fastboot on windows and they all need to be off before you shut down the system and try to access any such drive/partition on any Linux system.  You might be able to do that by attaching the drive to a windows 7 computer and turning all those options off.  You'd have to do an online search on how to do that, I don't know.  I doubt very much you will be able to do it from Ubuntu or any Linux but I don't use hibernation so am not really sure.

---

### Post by monty22 on 2018-01-14
The best approach at this point might be to move the data I want to save onto another computer, then format the external hard drive with my Win 7 computer, then put the data back on that drive.  If I would have done this initially I'd be done by now!

But what about deleting the all the Windows files on the win 8.1 hard drive?  Since I have taken control of the permissions, this would  be great - I'd get more disk space in the process!

---

