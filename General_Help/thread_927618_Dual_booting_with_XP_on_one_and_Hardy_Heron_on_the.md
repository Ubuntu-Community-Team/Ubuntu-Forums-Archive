---
title: "Dual booting with XP on one and Hardy Heron on the other!"
date: 2008-09-23
forum: General Help
---

### Post by stereopaul on 2008-09-23
Please, Please help!!!

I have a XP on 320gig (wife) and Ubuntu on 80gig (me) on a Fijitsu Seimens Esprimo 2500 with 1.5 gig RAM and 3 ghz processor, Pheonix BIOS.

I have tried in vain to get a Dual boot screen to appear when loading into the bios. It did appear (once,when I pressed escape during the grub loading) with the option but could not find XP.

Since then I have to disconnect the drive's power to change between the differnt systems. Any help would be appreciated greatly :)

---

### Post by ashmew2 on 2008-09-23
Hi , If you want to add the option for booting XP whenever u are shown the GRUB menu , you might wanna look 
[Here]("http://www.tech-recipes.com/rx/2718/ubuntu_dual_booting_xp_grub_bootloader_editing_bootloader") and [here]("http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/"). 

Plus , If you dont wanna press Esc to see the GRUB menu , do this in the terminal :

```
sudo gedit /boot/grub/menu.lst
```

Find the following section : 

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

And make sure that there is a hash (#) before all three of these lines.
I think that should fix u up!

---

### Post by stereopaul on 2008-09-24
> **stereopaul said:**
> Please, Please help!!!

I have a XP on 320gig (wife) and Ubuntu on 80gig (me) on a Fijitsu Seimens Esprimo 2500 with 1.5 gig RAM and 3 ghz processor, Pheonix BIOS.

I have tried in vain to get a Dual boot screen to appear when loading into the bios. It did appear (once,when I pressed escape during the grub loading) with the option but could not find XP.

Since then I have to disconnect the drive's power to change between the differnt systems. Any help would be appreciated greatly :)



Thanks for the Info, but I new get error21, disc not found!!!!

Its really doing my head in1!!!!!

---

### Post by caljohnsmith on 2008-09-24
First of all, are you getting that Grub error 21 on start up before you get the Grub menu, or after you get the menu and select an OS? And do you have an entry in your Grub menu for Windows? If you can still boot into Ubuntu, it would really help if you could post the following info :
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by ashmew2 on 2008-09-26
If its a problem with ur BIOS , look here : [http://ubuntuforums.org/showthread.php?t=337653](http://ubuntuforums.org/showthread.php?t=337653)

Btw , You quoted yourself in post #3 :P

---

