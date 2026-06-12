---
title: "Grub Boot Loader Issues"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by JohnnyWhite2007 on 2009-10-20
Hello,

I have a problem. Let me explain what I was trying to do before I get to the problem. My laptop has a dual boot of Ubuntu and Vista using grub. I wanted to install Ubuntu on an external hard drive so I could use it with any computer(or at least try). I put the Ubuntu disk in started up the laptop and installed it on the external hard drive. 

Now here is the problem. When I start my laptop, and I don't have the external plugged in, it gives me a error 21 from the grub menu. I did some investigations and found out that when I boot my computer it is pointing the the menu.lst on the external hard drive and possibly other files also do this. I want to be able to use the grub on my laptop instead of the external, this way I can use my computer without having to plug in the external to be able to boot. 

Now for the question, how do I point grub to go to internal for the menu.lst file and whatever other files it needs to start without the external. I have tried copying all the boot files from the external to the laptop but that did not work. I have thoughts of the stage 1.5 needs to be edited, if so how. 

Thanks for all help in advance,
Johnny White.

---

### Post by presence1960 on 2009-10-20
> **JohnnyWhite2007 said:**
> Hello,

I have a problem. Let me explain what I was trying to do before I get to the problem. My laptop has a dual boot of Ubuntu and Vista using grub. I wanted to install Ubuntu on an external hard drive so I could use it with any computer(or at least try). I put the Ubuntu disk in started up the laptop and installed it on the external hard drive. 

Now here is the problem. When I start my laptop, and I don't have the external plugged in, it gives me a error 21 from the grub menu. I did some investigations and found out that when I boot my computer it is pointing the the menu.lst on the external hard drive and possibly other files also do this. I want to be able to use the grub on my laptop instead of the external, this way I can use my computer without having to plug in the external to be able to boot. 

**_Now for the question, how do I point grub to go to internal for the menu.lst file and whatever other files it needs to start without the external. _**I have tried copying all the boot files from the external to the laptop but that did not work. I have thoughts of the stage 1.5 needs to be edited, if so how. 

Thanks for all help in advance,
Johnny White.

That is impossible because menu.lst is in the /boot/grub directory of Ubuntu root filesystem. The way you want to do it you must have Ubuntu installed to an internal hard disk...

But there is another way to be able to boot your machine without the external plugged in. This will be a 3 step process. 

1. Without your external plugged in you need to restore Windows to MBR of the internal hard disk. See [here]("http://ubuntuforums.org/showthread.php?t=1014708") and follow directions for your windows version. Reboot without external plugged in and make sure machine boots right to windows. If so go to #2.

2. Now plug the external in and boot the Ubuntu Live CD to put GRUB on the MBR of your external disk. For specific instructions on how to do this please do this with the external plugged in:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Once I get that info I will give you precise instructions on how to put GRUB on MBR of external disk. if you know how to do disregard the boot info script.

3. lastly after you have restored windows to MBR of internal disk and have also put GRUB on MBR of external disk you need to reboot & go into BIOS. Set your external disk to boot before the internal disk. Save changes to CMOS and exit. When you boot your machine now if the external is unplugged you will boot right to windows, if the external is plugged you will get the GRUB menu and boot into Ubuntu.

---

### Post by JohnnyWhite2007 on 2009-10-20
I would do all that but I have two installments of Ubuntu. One on the internal hd and one on the external. If I restore the windows MBR then I will loose the internal Ubuntu. I want to keep the internal ubuntu.

---

### Post by louieb on 2009-10-20
2 installs of Ubuntu one on internal one on external hdd.
2 MBRs one on internal, one on external.

Boot it and when you get the grub menu press **c **for the **Grub>** prompt  

Fix em both 

```
find /boot/grub/menu.lst
```should return 2 locations in my example it returns  (hd0,2) (hd1,0)
now to fix 1
```
root (hd0,2)
setup (hd0)
```and fix the other
```
root (hd1,0)
setup (hd1)
```your done
```
quit
```and reboot 

Tech stuff from the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")  section [[SIZE=2]Installing GRUB natively[/SIZE]]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively") [SIZE=2]
[/SIZE]

---

### Post by oldfred on 2009-10-20
Then you just need to install grub to the internal hard drive MBR that points to the internal install of grub. 

I would also consider installing grub to the partition PBR so you can chainboot. The reason for chainboot would be if you have your external plugged in you could still select the internal to boot from. This also requires an entry in the menu.lst for the chainboot entry.
When you run the find command in grub you should get two entries one for you external drive and one for your internal. If you boot from the extenal it will be drive 0 and the internal will be drive 1.

In terminal
  sudo grub
  find /boot/grub/stage1  - Should be drive 1 some partition number
  root (hd1,x)    <-- this must point to location of 'stage1'
  setup (hd1)     <-- installs grub IPL to MBR of second hard drive.
  setup (hd1,x)   <-- installs grub to PBR partiton boot

  quit

Reboot

If you need more help follow presence's recommendation and post the script as then we can give exact entries. If you change boot order in BIOS that can also change entries required.

---

### Post by presence1960 on 2009-10-20
> **louieb said:**
> 2 installs of Ubuntu one on internal one on external hdd.
2 MBRs one on internal, one on external.

Boot it and when you get the grub menu press **c **for the **Grub>** prompt  

Fix em both 

```
find /boot/grub/menu.lst
```should return 2 locations in my example it returns  (hd0,2) (hd1,0)
now to fix 1
```
root (hd0,2)
setup (hd0)
```and fix the other
```
root (hd1,0)
setup (hd1)
```your done
```
quit
```and reboot 

Tech stuff from the [GNU GRUB Manual 0.97]("http://www.gnu.org/software/grub/manual/grub.html")  section [[SIZE=2]Installing GRUB natively[/SIZE]]("http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively") [SIZE=2]
[/SIZE]

+1  It would have been nice if you told us that you have 2 Ubuntu installs - one internal disk and the other external disk.

Louie, this is exactly why I almost always ask people requesting help to run the boot info script. For whatever reason it almost invaraiably turns out that their set up is quite different from that which they report to us. I guess I learned my lesson again- get them to run the script!

---

