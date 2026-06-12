---
title: "boot ubuntu from a pen drive????"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by hvacmoose on 2009-05-15
[SIZE=5][FONT=Comic Sans MS]Does anyone know how to install a bootable version of ubuntu on a pen drive.
[SIZE=3]I have a 32Gig Pen drive that I can install Ubuntu on but when I run it it only runs as a persistent live session with no root or sudo privileges...

Any suggestions.  


[/SIZE][/FONT][/SIZE]

---

### Post by dmizer on 2009-05-15
Try here: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Edit:
I don't know of any TRUE install you could do via USB. The best (I know of) that you can do is get a persistent live install. But, all your settings will be saved, and you should have the ability to use sudo.

---

### Post by dmizer on 2009-05-15
> **dmizer said:**
> Try here: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Edit:
I don't know of any TRUE install you could do via USB. The best (I know of) that you can do is get a persistent live install. But, all your settings will be saved, and you should have the ability to use sudo.

---

### Post by majamba on 2009-05-15
don't know but i believe that there is a tool for make ubuntu usb bootable
[http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/)
[http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/ubuntu-810-install-using-the-built-in-usb-installer/)

or
try this
    *  sudo su
    * apt-get install usb-creator

---

### Post by orange-wedge on 2009-05-15
you can also use unetbootin along with the iso of the distribution that you want to install.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by skygazer on 2009-05-15
I have always used a 1GB sandisk pen drive to install Ubuntu on laptops and dektops. The reason is i am cheap and i dont want to waste my set of blank disks:D.. 
Its quite simple actually.. U need a software tool called UNetBootin. Its availabe for linux as well as windows machines. All you need is the .iso image of the distro you want to boot from. These are the steps to follow to create a Ubuntu Live USB (exactly same as a Live CD)..

1.Install unetbootin on your computer
2.Select your distro and type in Unetbootin
3.Select your USB drive in the options (target location where the istallation disk/usb is created)
4.Create the Live USB and when Unetbootin asks you to reboot, DO NOT REBOOT
5.Browse the USB drive and locate a file in it called isolinux.cfg. DELETE this file
6.Locate a folder called isolinux. Copy all the files in it as it is to the top folder. Say your USB is assigned F:/ drive. Then copy all files from F:/isolinux to F:/. 
7.Locate a file called isolinux.cfg in F:/. Rename it to syslinux.cfg
8.Unmount/ remove your USB pen drive..! Its ready for installation

Now, goto your computer bios and change boot order so that the USB drive/ USB key option is having first priority.Insert your pen drive and save the bios settings and let it restart. If everything was followed correctly, you will have the Ubuntu Live USB menu on the screen.

This technique worked for me with Ubuntu Hardy(i386), Jaunty (X64, i386) and Damn Small Linux distros.

---

### Post by shababhsiddique on 2009-05-15
> **skygazer said:**
> I have always used a 1GB sandisk pen drive to install Ubuntu on laptops and dektops. The reason is i am cheap and i dont want to waste my set of blank disks:D.. 
Its quite simple actually.. U need a software tool called UNetBootin. Its availabe for linux as well as windows machines. All you need is the .iso image of the distro you want to boot from. These are the steps to follow to create a Ubuntu Live USB (exactly same as a Live CD)..

1.Install unetbootin on your computer
2.Select your distro and type in Unetbootin
3.Select your USB drive in the options (target location where the istallation disk/usb is created)
4.Create the Live USB and when Unetbootin asks you to reboot, DO NOT REBOOT
5.Browse the USB drive and locate a file in it called isolinux.cfg. DELETE this file
6.Locate a folder called isolinux. Copy all the files in it as it is to the top folder. Say your USB is assigned F:/ drive. Then copy all files from F:/isolinux to F:/. 
7.Locate a file called isolinux.cfg in F:/. Rename it to syslinux.cfg
8.Unmount/ remove your USB pen drive..! Its ready for installation

Now, goto your computer bios and change boot order so that the USB drive/ USB key option is having first priority.Insert your pen drive and save the bios settings and let it restart. If everything was followed correctly, you will have the Ubuntu Live USB menu on the screen.

This technique worked for me with Ubuntu Hardy(i386), Jaunty (X64, i386) and Damn Small Linux distros.

I dont know if this works. I tried with 6.06 and 8.10 but all i got was a bootable live USB disc. 

No change is saved, no root.

If this is what u want, simply try out 
system>administration>Create a USB startup disk

---

### Post by hvacmoose on 2009-05-15
made a usb startup disk  still just alive session.  

I think it has something to do with GRUB location. 

When I do a regular install to my pen drive i just get a usb-zip when i open boot menu

---

### Post by Mighty_Joe on 2009-05-15
I used these instructions to [install ]("http://beastie.cs.ua.edu/cs150/usb-install.html") and [configure ]("http://beastie.cs.ua.edu/cs150/configuration.html") to put a full Ubuntu install on a usb drive.  The configuration includes moving logging and Firefox cache to tmpfs (saves wear and tear and improves performance).  Since the instructions are for an academic exercise, there's some things you don't need to do (like set up vim).

---

### Post by hvacmoose on 2009-05-15
Thanks Mghty_Joe.  That configuration is the stuff i was looking for.  I will try that and get back to you.....

---

