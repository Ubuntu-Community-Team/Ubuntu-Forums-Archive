---
title: "SATA HD prevent computer from booting in 12.04?"
date: 2013-01-10
forum: Hardware
---

### Post by Francis4344 on 2013-01-10
Just installed 12.04 (fresh install). I had remove my second HD for safety reason (The two drive are exactly the same - too easy to mix up- been there done that).

So, all my personal data is on this second drive but when I reconnect it and boot, the computer (HP8020N) will not reboot. I have tried different combination (moving the HD on different SATA on the board, removing the DVD) to no avail. 

The best I got was a purple screem and no more. Both drives and DVD were working flawlessly before on 10.04. 

It is possible that this is a new hardware problem but I doubt it. The second HD has only data on it, no OS.

Any clues?

---

### Post by dannyboy79 on 2013-01-10
which device is set to boot within your BIOS? i am betting when you installed ubuntu it installed on /dev/sda1 but then when you insert your other hard drive /dev/sda1 get bumped to /dev/sdb1 so grub is failing. Also, you may need to add nomodeset to your grub line if it's a graphics issue. try booting to a super grub disk then you could fix grub.

---

### Post by lindsay7 on 2013-01-10
Go into your bios settings and make sure your computer sees both drives. You can also set the booting order of the the drives. The normal setting is to boot from the cd or dvd drive first and then the drive with the OS and then other devices like your second hd. The computer should boot up as long as all the devices on listed.

---

### Post by Yellow Pasque on 2013-01-10
> **dannyboy79 said:**
> i am betting when you installed ubuntu it installed on /dev/sda1 but then when you insert your other hard drive /dev/sda1 get bumped to /dev/sdb1 so grub is failing.
grub and /etc/fstab should use UUID's to avoid this issue.

---

### Post by Francis4344 on 2013-01-11
Thanks to all for the replies. On some tries, the computer would show both HD in the bios, at oter times, non at all. Go figure. I highly suspect my SATA controller is on the fritz. 

Dannyboy79: Good point on the HD. I will look into this.Not sure what is the relationship between how linux see the hard drives and how the BIOS sees them.

At the moment, I installed that second drive in my wife computer and it works fine. As a bonus, I finally figure out how to config that &%## WIN7 so that now, I can see and copy my drive through the network.

Once I got my data all copied and saved, I will give that drive another try.

---

### Post by Yellow Pasque on 2013-01-11
Have you looked at the SATA settings in the BIOS (like AHCI)?

---

### Post by Francis4344 on 2013-02-13
Thanks again to all who weighted in.

It definetely was a hardware problem with the controller.

I dislike the fact that whenever a problem arise with Ubuntu, people - including myself - tend to think about an OS issue instead of a simple hardware issue.

Anyway, I will have to live with 2 sata devices instead of 4 (onboard controller).

---

### Post by oldfred on 2013-02-13
If you are getting purple screen it sounds like you have booted thru grub, but have a driver issue. Video is most common as they moved some video into kernel. With my nVidia I have had to use nomodeset on install and first boot.

       Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply
    
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
            
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Yellow Pasque on 2013-02-13
BIOS upgrade is worth a shot..

---

