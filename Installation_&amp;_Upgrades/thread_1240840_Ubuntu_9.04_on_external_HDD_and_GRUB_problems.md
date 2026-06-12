---
title: "Ubuntu 9.04 on external HDD and GRUB problems"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by MindBlank on 2009-08-15
Hello everyone!

I installed Ubuntu 9.04 3 days ago on my external hard disk and being a beginner in all things Ubuntu/Linux related i can't seem to fix this problem I'm having.

Like i said, i have Ubuntu on an external hard disk and Windows 7 on the internal hard disk. GRUB works only when the external hard disk is connected. If it's not plugged it the it says that it can't find Stage1.5 and can't boot into Windows. (or Ubuntu of course, but it can't do that because the hard disk is not connected :D)

I've googled and googled for the last few days and found many solutions to this kind of problem but the ones I've tried don't seem to work for me...

I firstly tried to write GRUB to the MBR on hd0 - my internal drive, and did not proceed with this in the end since I was/am afraid not to screw up my Windows MBR.

I decided to use Windows 7's boot loader and NeoGrub. I copied the contents of my menu.lst to NeoGrub's menu.lst but it doesn't work. I get "*Error 17 : File not found*"
I use "**find /boot/grub/stage1**" in the NeoGrub prompt and it says the same thing : *Error 17 : File not found*. 
However, if i try the same thing in my "original" GRUB it points to my Linux partition - (hd1,4) which is to be expected. For some reason, it doesn't work with NeoGrub and i can't for the life of me figure out why. 
It "sees" my external drive because it responds to "root (hd1,0...6) accordingly but doesn't find /boot/grub/stage1 anywhere.


Anyway, i just want to have the possibility to boot into Windows with the external hard drive disconnected, and the possibility to choose where i want to boot to when i have it connected. Preferably using Windows boot-loader...

Here's my "sudo fdisk -l" output : 

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb2d239e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3917    31457280    7  HPFS/NTFS
/dev/sda2            3917       17099   105881600    7  HPFS/NTFS
/dev/sda3           17099       38914   175228928    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2            3305       10315    56307712    7  HPFS/NTFS
/dev/sdb3           10315       19458    73441280    7  HPFS/NTFS
/dev/sdb4              16        3304    26418892+   5  Extended
/dev/sdb5              16        1260    10000431   83  Linux
/dev/sdb6            1261        1509     2000061   82  Linux swap / Solaris
/dev/sdb7            1510        3304    14418306   83  Linux
```

And here's my NeoGrub menu.lst which sadly doesn't work...

 ```
title                  Ubuntu 9.04, kernel 2.6.28-14-generic
    uuid                 a851b3b2-b702-4751-b5f6-8038d0770995
    kernel              /boot/vmlinuz-2.6.28-14-generic root=UUID=a851b3b2-b702-4751-b5f6-8038d0770995 ro quiet splash 
    initrd               /boot/initrd.img-2.6.28-14-generic
    quiet
     
   
  title                  Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
    uuid                 a851b3b2-b702-4751-b5f6-8038d0770995
    kernel              /boot/vmlinuz-2.6.28-14-generic root=UUID=a851b3b2-b702-4751-b5f6-8038d0770995 ro  single
    initrd               /boot/initrd.img-2.6.28-14-generic
     
   
  title                  Ubuntu 9.04, kernel 2.6.28-11-generic
    uuid                 a851b3b2-b702-4751-b5f6-8038d0770995
    kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=a851b3b2-b702-4751-b5f6-8038d0770995 ro quiet splash 
    initrd               /boot/initrd.img-2.6.28-11-generic
    quiet
     
   
  title                  Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
    uuid                 a851b3b2-b702-4751-b5f6-8038d0770995
    kernel              /boot/vmlinuz-2.6.28-11-generic root=UUID=a851b3b2-b702-4751-b5f6-8038d0770995 ro  single
    initrd               /boot/initrd.img-2.6.28-11-generic
     
   
  title                  Ubuntu 9.04, memtest86+
    uuid                 a851b3b2-b702-4751-b5f6-8038d0770995
    kernel              /boot/memtest86+.bin
    quiet
```

---

### Post by presence1960 on 2009-08-15
I suggest forget NeoGrub. You can install GRUB to MBR of the external drive. GRUB will only come up when the external is plugged in at boot. When you boot with it unplugged Win 7 bootloader will take over.

First you may have to restore windows bootloader to MBR of internal disk if uninstalling neogrub does not let windows boot with external unplugged. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and use instructions for Vista. When complete reboot without external plugged in and see if windows boots. if it does then you are going to install GRUB to MBR of the external disk by doing this with your external plugged in when you boot:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd1,4) or (hd1,6)".  Use whatever your computer spits out for the following lines.
5. Type "root (hd1,4)or (hd1,6) whichever is your ubuntu root partition"
6. Type "setup (hd1)", to install GRUB to MBR, 
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

When you reboot go into BIOS and set the usb drive to boot before the internal drive. This will give you what you want. GRUB will only take over when the external is plugged in and windows bootloader will take over when the external is unplugged.

---

### Post by MindBlank on 2009-08-15
Sounds great. I'll give it a try after i restore the Windows MBR. Can i do that with EasyBCD instead of the Windows DVD?

---

### Post by presence1960 on 2009-08-15
> **MindBlank said:**
> Sounds great. I'll give it a try after i restore the Windows MBR. Can i do that with EasyBCD instead of the Windows DVD?

I don't know about Easy BCD. Why don't you uninstall it (Easy BCD) and see if windows will boot with your external drive unplugged. If it boots then you are ok. If not you will need the Windows CD/DVD

---

### Post by MindBlank on 2009-08-15
EasyBCD/NeoGrub is not the problem. The system doesn't boot into Windows (with the external hard drive disconnected i mean) from the moment i finished the Ubuntu install.
I was just using EasyBCD for the NeoGrub option, thinking i could be able to fix this mess.

---

### Post by presence1960 on 2009-08-15
> **MindBlank said:**
> EasyBCD/NeoGrub is not the problem. The system doesn't boot into Windows (with the external hard drive disconnected i mean) from the moment i finished the Ubuntu install.
I was just using EasyBCD for the NeoGrub option, thinking i could be able to fix this mess.

yes it is because Easy BCD is looking for menu.lst on the external drive.  when you installed Ubuntu GRUB went to MBR of your internal disk wiping the windows bootloader off MBR. Now you have Easy BCD there which looks to menu.lst on the external disk.. Disconnect your external and restore the windows bootloader to the internal disk as I suggested earlier. Then boot the Ubuntu Live CD with your external drive plugged in and restore GRUB to MBR of the external disk as I suggested earlier.

---

### Post by MindBlank on 2009-08-16
Yes! It works just like you said it would :) Thank you very much for your help!

---

### Post by presence1960 on 2009-08-16
Great! Enjoy Ubuntu.

A lot of people like Easy BCD, but GRUB is easy to configure, is more versatile and you don't need another program to boot your OSs.

In my opinion Easy BCD is for those who want to use Linux, but don't want to learn it or take the time to learn it. There really is no need for it. GRUB & Lilo do just fine by themselves.

---

### Post by Bartender on 2009-08-16
The OP is now going to have to fix or reinstall Ubuntu on the external...

---

### Post by presence1960 on 2009-08-16
> **Bartender said:**
> The OP is now going to have to fix or reinstall Ubuntu on the external...

see post # 7.

---

