---
title: "[SOLVED] Sandisk Cruzer Flashdrive"
date: 2008-08-22
forum: Hardware
---

### Post by chono on 2008-08-22
Hey, I switched over to ubuntu a few months ago, and have tried several times to get my flash drive working.Its a sandisk micro cruzer 1gb with some built in security. works fine on xp and i have the security set up with the password. idr everything iv tried but i can see usbdrive when i got to my computer, when i click on it it says:

 unable to mount location
no media in drive

and fdisk -l

chono@chono-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

No flashdrive there, since im still a noob at this, i have no idea where to go from here, any help will be greatly appreciated, thanks



(this is my first post, and i find it ironic how ubuntu is a spelling mistake)

---

### Post by pytheas22 on 2008-08-22
Do you know more about how the security works on Windows?  How exactly does it work there--do you plug the drive in and something pops up asking for your password or what?  Does it work on any Windows computer or only on ones that have software pre-installed for it?

Please tell us that so that we can get a better idea of how it works.  It would also be useful if you could provide a link to a web page describing the product or something, and if you could post the output of this command when the drive is plugged in:
```

lsusb
```

---

### Post by chono on 2008-08-23
its called u3 tech and it pops up on any windows pc and asks for a pass, then gives u a menu with a bunch of apps, almost like an os. heres the link: except its only 1gb

[http://www.sandisk.com/Products/Item(1922)-SDCZ6-2048-A11-SanDisk_Cruzer_Micro_2GB_Black.aspx]("http://www.sandisk.com/Products/Item(1922)-SDCZ6-2048-A11-SanDisk_Cruzer_Micro_2GB_Black.aspx")

and the lsusb

```
chono@chono-laptop:~$ sudo lsusb
[sudo] password for chono: 
Bus 007 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```


(its only 1 gb) 

the fdisk -l in previous post was with it plugged in.

Thanks.

---

### Post by pytheas22 on 2008-08-23
Thanks for the information.  I actually think the mounting problem may not have to do with the programs preloaded on the disk.  I had a similar disk (also Cruzer) and mine mounted without a problem, even though it also had the menu that popped up on Windows and everything.

Please unplug the device and plug it back in.  Then immediately open a terminal and type:
```

dmesg | tail
```

and post the output here.  I think that should provide a clue as to what's going on.

Also, have you tried mounting the device from the command-line, with a command like:
```

sudo mount /dev/sdb1 /media/sdb1
```

If you don't know how to do that and can't find instructions, I can tell you what to use.

---

### Post by maniheer on 2008-08-23
Sorry to say this but U3 security does not work on any OS other than Windows (says so when you enable it in Windows). So I would disable it. I've got one but never used the security and it works fine.

You might be able to find something for security that works on all platforms (doubt it) :)

---

### Post by chono on 2008-08-23
mounting maunally didnt work, mount point does not exist


and the dmesg tail:

```
[14669.058984]
 scsi 7:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  2.21 PQ: 0 ANSI: 2
[14669.061682] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[14669.061763] sd 7:0:0:0: Attached scsi generic sg2 type 0
[14669.090811] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[14669.090936] sr 7:0:0:1: Attached scsi CD-ROM sr1
[14669.091016] sr 7:0:0:1: Attached scsi generic sg3 type 5
[14698.162341] usb 7-2: USB disconnect, address 5
[14700.651532] usb 7-2: new high speed USB device using ehci_hcd and address 6
[14700.720746] usb 7-2: configuration #1 chosen from 1 choice
[14700.721230] scsi8 : SCSI emulation for USB Mass Storage devices
[14700.721740] usb-storage: device found at 6
[14700.721746] usb-storage: waiting for device to settle before scanning

```

theres ALOT before that, but i assume u only need that part. also, sorry for the noob question, but what is the line in dmesg (line) tail and for future reference what do dmesg and tail mean.

Thanks:)




Im going to go disable the security now and see how that works, thanks

---

### Post by chono on 2008-08-23
Works great now, would be nice if someone would find a way to get the u3 working:) thaks all for you help:guitar:

---

### Post by pytheas22 on 2008-08-23
> what do dmesg and tail mean

dmesg prints out messages from the kernel since the last time your system restarted, and piping it to "tail" causes it just to print it the last ten (or so) messages.

Sorry that U3 won't work.  But if you want to store files securely on your drive, you could always use [TrueCrypt]("http://www.truecrypt.org/").

---

