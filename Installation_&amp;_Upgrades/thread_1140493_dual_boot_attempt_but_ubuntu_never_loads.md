---
title: "dual boot attempt but ubuntu never loads"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by xiaoxindiar on 2009-04-27
Hi all. I haven't messed around with Linux for a couple of years and I was trying to get back into the mix. I have an ATI Radeon X1650 and read that people who have ATI cards are having trouble with 9.04 so I'm trying out 8 instead. I have Vista already installed on a Sata drive and i am attempting to run ubuntu on a 40  gig ide samsung drive. during install my samsung ide 40 gig comes up as sda, my 320 gig sata drive with vista comes up as sdb, and my maxtor external comes up as sdc. obviosly i installed on sda - the samsung and used the full disk. my install from live cd seemed to go great, but based on suggestions i read before attempting this, I installed grub on sda1 so i could try to boot ubuntu via easybcd in vista. once i got back into vista i ran easybcd and clicked the linux tab and the samsung/linux drive shows as drive 0 with partition 0 and partition 1 for swap. i chose partition 0 - which i assume should be sda1. when i add the entry and restart i choose linux/ubuntu and i get a grub> prompt. try to do "find /boot/grub/stage1" shows nothing but a blinking cursor. i boot into ubuntu again with live cd and if i choose boot from first drive, the windows boot loader shows up, if i boot into live cd, desktop shows but if i try to open /boot/grub/menu.lst, nothing shows. i looked at neogrub's config file in windows and it references /boot/grub/menu.lst. is menu.lst blank because i'm using live cd? or is there really somehow an empty menu.lst file after install? i'm confused but any help / advice would be great.

---

### Post by xiaoxindiar on 2009-05-04
ok, i fixed this. basically i ended up trashing the easybcd program, it totally messed up my boot configuration. it would add entries but not remove them properly, and it kept crashing my system. in the end i used grub. i backed up my vista disk, reinstalled ubuntu - putting grub to the mbr of my samsung drive that it is on, installed my ati driver from AMD, got my system pretty much the way i wanted it, changed drive boot orders to boot to western digital sata drive, and reinstalled vista on that - obviously the vista loader ended up on the mbr for that drive, after install i restarted the vista disk and restored from previous back up file, i rebooted and changed drive orders again to boot from samsung / ubuntu, opened a terminal, did:

sudo gedit /boot/grub/menu.lst

and added this to the menu entries:


title        Microsoft Windows Vista
root        (hd1,0)
makeactive
chainloader    +1

once i did that i rebooted, changed the drive order to boot western digital / vista again, opened up command prompt with admin rights and did:

cd c:\windows\system32

bcdedit.exe /delete {ubuntu id} "This was still in the boot menu from easybcd"
bcdedit.exe /timeout 0

restarted, changed drive order again to boot samsung / ubuntu by default.

now when grub chain loads vista's loader, vista is the only option and i can proceed to boot vista. i set the time out to 0 so i would not have to wait but i don't know if there is a way to bypass the vista boot loader completely. the bottom line is i wasted a lot of time by not trusting grub. if anyone has vista and wants to dual boot it with ubuntu, use grub and if you can, use 2 seperate drives - this keeps you from having to sacrifice disk space, resizing partitions, fighting over boot loaders, etc. you can just change the boot order for each drive to go into the operating system you want to make initial changes / setup in.

---

