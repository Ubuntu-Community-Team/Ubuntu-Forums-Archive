---
title: "Black screen or just tan loading screen with no full boot"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by saltywalsh on 2009-01-15
Dell Inspiron 1100 
Bios A32
--Blank 60GB hard disk

I installed 8.10.  Installation went smoothly but after reboot the screen would either remain black or would load after about 15 minutes of idleness.  Sometimes it would prompt me for my login but then just hang at a tan screen with only the mouse visible.  

I had to go into the recovery mode and to the terminal and run the following to get the machine to boot and login and run normally:

sudo apt-get remove compiz
sudo apt-get remove compiz-core

Then I would exit the terminal and boot as normal.

This would work until reboot.  The next thing I did was I tried:

sudo rm -rf ~/.conf

This seems to work but I am afraid that something is wrong.  Anyone have any suggestions as to what can be done or even if I should roll back to a previous version?

---

### Post by balak on 2009-01-15
You should check the last tab (called visual effects) in your system->preferences->appearance menu 
Select none.

Do you know what video card your laptop has ? you should check what graphics driver you are using for that card and see if there are any issues with that driver.

---

### Post by cdtech on 2009-01-15
You should edit your "/boot/grub/menu.lst" so that you see the boot up messages and not the splash. This will help troubleshoot the problem.......
```
kernel	/vmlinuz-2.6.27-9-generic root=/dev/sda1 ro quiet hpet=disable vga=792 resume=/dev/sda5
```
This is the way I have mine setup....

---

### Post by saltywalsh on 2009-01-15
> **cdtech said:**
> You should edit your "/boot/grub/menu.lst" so that you see the boot up messages and not the splash. This will help troubleshoot the problem.......
```
kernel	/vmlinuz-2.6.27-9-generic root=/dev/sda1 ro quiet hpet=disable vga=792 resume=/dev/sda5
```
This is the way I have mine setup....

I followed your advice and changed that but it still went to a black screen unless I press ctrl-alt-F1 and then it will show that it is booting in normal mode and it boots just find to the splash screen to login.

I am puzzled.

---

### Post by cdtech on 2009-01-15
When it boots and during lockup have you tried holding the shift key? I had a problem that it would not boot unless I held the "shift" key. I found by adding the flag "hpet=disable" would allow it to boot on its own....:confused:

---

### Post by skern03 on 2009-01-15
> **saltywalsh said:**
> Dell Inspiron 1100 
Bios A32
--Blank 60GB hard disk

I installed 8.10.  Installation went smoothly but after reboot the screen would either remain black or would load after about 15 minutes of idleness.  Sometimes it would prompt me for my login but then just hang at a tan screen with only the mouse visible.  

Anyone have any suggestions as to what can be done or even if I should roll back to a previous version?

A couple things come to mind....
1) 8.10 is a tricky installation/upgrade. You might try 8.04. It took a new DVD drive to get it installed on this system.

2) When you install from CD, right after you select the language, and BEFORE you click the Install menu option, press F6. Type (no quotes) "noacpi" then hit the Install option. This has saved my butt many times, especially on older machines.

---

### Post by saltywalsh on 2009-01-16
> **skern03 said:**
> A couple things come to mind....
1) 8.10 is a tricky installation/upgrade. You might try 8.04. It took a new DVD drive to get it installed on this system.

2) When you install from CD, right after you select the language, and BEFORE you click the Install menu option, press F6. Type (no quotes) "noacpi" then hit the Install option. This has saved my butt many times, especially on older machines.

I wonder if I would have the same issue with 8.04.  I really think it has something to do with "compiz."  The last system I had working on this laptop that was linux was Breezy Badger and that had a resolution issue due to the intel extreme graphics card on the laptop and an issue getting the wireless card to interface correctly.  So maybe I'll give 8.04 a shot and see if it works better but I would rather not go below the 8.04 version.

---

### Post by skern03 on 2009-01-16
> **saltywalsh said:**
> I wonder if I would have the same issue with 8.04.  I really think it has something to do with "compiz."  The last system I had working on this laptop that was linux was Breezy Badger and that had a resolution issue due to the intel extreme graphics card on the laptop and an issue getting the wireless card to interface correctly.  So maybe I'll give 8.04 a shot and see if it works better but I would rather not go below the 8.04 version.

Personally, I would give 8.04 a try. It took more than four attempts to get 8.10 running on this system. I think 8.10 uses Compiz by default and 8.04 does not, but I could easily be wrong.

And as balak pointed out in one of the first replies, don't enable Compiz. On older graphics cards without the speed and memory, it's best to set the Visual Effects to None.

Again, when you install 8.04, during the install, set the noacpi option. I had similar issues as you with nearly every version of Ubuntu I've installed on an older laptop (now dead), and installing with noacpi worked.

---

