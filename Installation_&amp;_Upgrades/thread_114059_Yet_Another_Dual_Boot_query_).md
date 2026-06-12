---
title: "Yet Another Dual Boot query :)"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by metaphorm on 2006-01-07
Hello,

I would like to install Ubuntu 5.10 on my main comp. I have poured over the forums here but still had a coupla queries.

I am running a Windows XP SP2 system on a pentium 4, 2.66GHz, 1GB RAM on my main machine. I just got a Seagate SATA 160GB HD. The primary drive is a Seagate 80GB IDE. On the SATA HD, I have made 3 NTFS partitions and left about 20GB unallocated, hoping to install Ubuntu on it. 

Now I have been reading about some issues with the dual-boot loader (GRUB?) when running WinXP and Ubuntu. I can't afford to have my main machine be crippled, i mean not able to boot into Windows XP. Apparently there is no linux driver availble for my ADSL modem (SMC 7007USB). So if I am not able to even boot into windows, I will have no access to the net to even find solutions. 

So my query is this: Do I need to do anything else, or just go with the Ubuntu installer and install the OS in the free contiguous space--that unallocated partition? 

Also, how is Ubuntu's support for USB peripherals, like storage devices (pen, bakcup etc.)?

Thanks for any help/advice.

---

### Post by Kipper on 2006-01-07
Ok, as you quite rightly don't want your Windowx XP install messed up, this is one possible way to arrange things (It's my current arrangement). 

1. Windows XP on one drive
2. Ubuntu on a second drive on a separate controller.

First hard drive in the boot sequence in the BIOS is set to the second drive. GRUB is installed on the second drive with Ubuntu. GRUB menu is edited to include Windows as an option on booting. So you always boot into GRUB and then select what you want, Ubuntu or Windows.

When you install Ubuntu you can physically disconnect the Windows hard drive. This means Windows cannot be touched. But you will have to edit the /etc/fstab file and GRUB's menu.lst file in Ubuntu before you re-boot the system with the Windows hard drive re-connected.

I don't know what m/board you have, or other drives you have in your machine, so this may not be a feasible suggestion. Let me know, I might have other ideas.

---

### Post by Sef on 2006-01-07
Have you tried using the Live CD to see what problems there are?  Sometimes they will happen even though everything is supposed to work.

---

### Post by metaphorm on 2006-01-07
Hi Kipper,

Thanks for your quick response.

Here is my system config, relevent to my query:

mobo: Intel 865GBF with onboard Graphics And SoundMAX audio. I am using an AGP card though: video card: ATI Radeon 9800 SE 256MB RAM
CPU: Intel Pentium 4, 2.66GHz
I have a TSST H552B DVD writer and a Samsung 252B CD-Writer on my seconday IDE bus. I shall be using the TSST to install Ubuntu.
I have 2 ethernet network adaptors installed. Both are Realtek 8139/810x Family.
Primary Hard Drive is a Seagate 80GB IDE, on the primary IDE bus. With 3 partitions - 1 and 2 are NTFS and the 3rd is FAT32. Windows XP SP2 is installed on the the primary (boot) C: drive.

I connect to my internet broadband using the SMC 7007USB ADSL modem (not a router). I searched but there seem to be no Linux drivers availble for that. My standby connection is a CDMA wireless dialup, which I am not sure I can find Linux drivers for either.

I just got a new hard drive. A Seagate SATA 160GB. I have made 3 NTFS partitions on it for my WinXP OS, but have left 20GB unallocated (unformatted). Ideally what I would like to do is to install Ubuntu (5.10 is what I have) on that unallocated space on the SATA hard drive.

I just need to know if I need to do anything different from the default installation menu that the 5.10 install CD provides? Also, I am concerned about the GRUB issues I have reading in the forums. I hope there are no problems booting into windows, once I have installed Ubuntu. Or is there a more reliable dual-boot loader out there?

Thanks.

-Ani

---

### Post by metaphorm on 2006-01-07
hi Sef,

thanks for your response too. I was typing a reponse to Kipper's post when you posted. So I can run the Live CD to check compatibility issues with my comp components for Ubuntu? I ran it before, but I dont remember finding a menu for checking compatibility problems. Can you please guide me to where/how I do that.

Thanks.

-Ani

---

### Post by Kipper on 2006-01-08
Ani,

First of all, I think Sef simply meant to stick the **Live CD ** in your CD drive and see if your system will boot up without problems. Try this first, if your get as far as the Ubuntu desktop you can also see if your USB modem is detected, can be configured and functions with your ISP. This way you'll know it's worth installing Ubuntu. You should do this with both your hard drives attached so you'll be confident that Ubuntu detects your SATA drive. 

If I've understood your hardware set up correctly you have your existing Windows install on your primary IDE drive and intend to install Ubuntu on your new drive which I assume must be atttached to your m/board's SATA controller. I also assume you have set your BIOS to currently boot from the IDE drive and not the SATA drive. So right now you are just booting into Windows.

I'm not sure what GRUB issues you have read about. I have found GRUB to be  a very reliable bootloader when used correctly and quite versatile. If can be installed in the MBR of a disk, or another partition, or even on a floppy disk. In addition to the fixed boot menu you can create, you can use a command line GRUB interface and type in the boot commands on the fly.

The only way I know of which will ensure your Windows XP install is NOT touched when you install Ubuntu (or any other Linux distro) is to pull the plug on your Winodws disk before you install Ubuntu on your SATA drive.

You will have to set your BIOS to boot from the SATA drive (after CD drive) before you install. And if you did nothing else, you'd end up with the Ubuntu install knowing nothing about Windows. As I said before, you can fix this post install by editing the GRUB menu.lst file and possibly the /etc/fstab if you wish Windows partitions to be mounted on booting Ubuntu. So you can end with a dual-boot system if you wish.

If you follow my suggestion, apart from changing the BIOS to boot first from the SATA drive, and pulling the ribbon cable from your primary IDE drive, the Ubuntu install will procedd as normal, and of course ensure you install on your SATA drive's free space and install GRUB on the MBR of your SATA drive. 

The only gotcha, I can think of is if Ubuntu has a problem detecting your SATA drive. If this happens, it can be a case of just getting the BIOS setting on your SATA controller correct.

---

### Post by Sef on 2006-01-09
> First of all, I think Sef simply meant to stick the Live CD in your CD drive and see if your system will boot up without problems. Try this first, if your get as far as the Ubuntu desktop you can also see if your USB modem is detected, can be configured and functions with your ISP. This way you'll know it's worth installing Ubuntu.

That is exactly what I meant, Kipper.

---

### Post by metaphorm on 2006-01-12
Hi,

Hey Kipper. Many thanks for that wonderfully detailed post. 

The only problem is right now is that my bios doesn't allow me to boot from the SATA drive, in its boot priority list. But it does recognize it! I am guessing there is no problems with the SATA controllers. The drive functions fine in Windaft XP (Pro SP2) as well.

In response to you suggestion of pulling the plug (i could just pull the power cable out, doesnt have to be the IDE ribbon cable), shouldn't the MBR be residing the on primary boot disk, which is the primary IDE 80GB Seagate in my case, in the first place? Otherwise how will a boot-loader even come into effect, since the BIOS is gonna search for it on the IDE during boot time? I am a little confused about that.

I will run the LiveCD again and see if it can detect the modem. It didnt the last time around. But everything else seemed to be working, I think :). 

Thanks.

-Ani

---

