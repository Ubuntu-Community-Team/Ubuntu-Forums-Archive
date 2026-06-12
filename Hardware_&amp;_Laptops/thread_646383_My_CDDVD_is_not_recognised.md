---
title: "My CD/DVD is not recognised"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by AlanR8 on 2007-12-21
Here's the content of my fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1f78b6ee-fb8f-4635-82ce-3e0f33786247 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=b22b4a9e-7c23-4b47-9002-e4309ea78149 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
\\zeus\public  /home/alan/Backup  smbfs  uid=1000  0  0

The machine is a Sony Vaio VGN-FZ21S laptop and up until last week all was well. Does the content of the above file look OK?

---

### Post by AlanR8 on 2007-12-22
So I seem to have screwed things up here!

The laptop is NOT recognising the CD/DVD/BlueRay drive. It was a week ago.

The upshot is that it won't even recognise the live CD to allow a reinstall! 

Not good. 

My question is, how do I "burn" the ISO image to my 2 gig memory stick? I can set the BIOS to recognise the stick as a boot device. My thinking is that I can re-install and sort the mounting problem, or discover that my 6 week old laptop is sha**ed!

---

### Post by jespdj on 2007-12-22
Have a look at this: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Did your CD/DVD work previously? Maybe something's wrong with the hardware... :(

---

### Post by AlanR8 on 2007-12-22
Yup it worked perfectly. Installed from CD and played DVDs

---

### Post by logos34 on 2007-12-22
> **AlanR8 said:**
> 
The upshot is that it won't even recognise the live CD to allow a reinstall! 


so you're saying the Bios is no longer recognizing the drive?

---

### Post by AlanR8 on 2007-12-23
Not mentioned by name.

The BIOS is very basic on this laptop, the HD is mentioned by size and the internal optical drive is mentioned on the boot options page.

---

### Post by AlanR8 on 2007-12-27
An update

Looks like the CD/DVD/BlueRay disk has failed. Only six weeks old and a Sony. I'm NOT impressed.

Whilst in Comet on Xmas Eve, where the machine came from, I asked about their returns policy and was told bring it in, we'll send it back to Sony, takes about a MONTH!

I think not. 

Has anyone had any similar experience with returns from Comet? I'm thinking Sale of Goods Act and "merchantable quality" and because I bought with a card, Section 75 of the Consumer Credit Act "joint and several liability".

Opinions and thoughts would be very welcome before I take on a giant in the electronics distribution business!

---

### Post by AlanR8 on 2008-01-15
Further update

Machine's got to go back to Sony to be fixed so I had to re-install Vista as it came from the factory. Fortunately I burned the rescue disks, 3 DVDs, and bought an external DVD/CD drive. Switched the BIOS to boot from an external device and 2 HOURS later, yes 2, I logged on for the first time. What a nightmare and I can tell the machine's running a lot slower than under Kubuntu and the cooling fan's on constantly.

This is not good and the sooner it comes back fixed and back to Kubuntu the better

---

