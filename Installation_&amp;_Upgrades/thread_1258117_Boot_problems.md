---
title: "Boot problems"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by mattgiordano on 2009-09-04
Hi,
I am using Win XP on a Dell laptop. I recently partitioned and loaded Crunchbang on my external USB gard drive using the Live CD. All works fine.
But .... If I don't have the external drive connected when I boot it won't boot Windows. I can only get into Windows when the USB drive is connected and I selectit from the Crunchbang boot menu.
How can I get round this please?
Can I delete the partition #! is on and then will it boot Windows as normal?
Many thanks.
Matt

---

### Post by Yvan300 on 2009-09-04
What has happened is that you have installed the boot files for you pc on the flash drive. All you have to do to get back windows, is to get your windows install cd and reinstalll window's bootloader.

---

### Post by presence1960 on 2009-09-04
> **Yvan300 said:**
> What has happened is that you have installed the boot files for you pc on the flash drive. All you have to do to get back windows, is to get your windows install cd and reinstalll window's bootloader.

That is only half the fix. Then you need to install GRUB to MBR of the flash drive. This way when the flash drive isn't plugged in it boots straight into windows. When the flash drive is in you will get GRUB. 

P.S. After installing GRUB to MBR of flash drive go into BIOS and put your flash drive ahead of your internal disk in boot order. if you don't do this GRUB will not take over when you boot with the flash drive plugged in.

To install GRUB to MBR of the flash drive follow this with the flash drive plugged in:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd1)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

In #6 use setup (hd1) assuming all you have is the internal disk & flash drive. if you have other drives you need to know what (hdx) represents your flash drive.


```
Now reboot, go into BIOS and put the flash drive ahead of your internal hard disk in boot order.
Of course you need to be sure your machine is capable of booting from flash or USB media.

---

### Post by presence1960 on 2009-09-04
sorry!! I misread your post. I just noticed you have Crunchbang installed. If Crunchbang uses GRUB then hopefully you can put GRUB onto MBR of the flash media. I thought you had Ubuntu.

---

### Post by mattgiordano on 2009-09-06
Thanks for all your help. I appreciate it. I solved it by deleting Crunchbang. Then I restored the Windows mbr Using Super Grub. Then I put Ubuntu on my PC with Windows. Thanks again. Matt

---

