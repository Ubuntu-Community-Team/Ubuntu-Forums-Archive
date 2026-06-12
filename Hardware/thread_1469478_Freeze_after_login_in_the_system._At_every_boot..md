---
title: "Freeze after login in the system. At every boot."
date: 2010-05-02
forum: Hardware
---

### Post by iDleR on 2010-05-02
Hi! I have a netbook Samsung N130 with the last Ubuntu release 10.04
I actually had this problem since the previous version so it does anything to do with a specific release.
So basically after I log in to gnome, after some minute Gnome freezes (not the mouse though), the hard disk led is turned on for 10-20 seconds and after that all is ok. 
So I guess it is a process issue. How can I check what the problem is?

P.S.: I talked to a friend of mine yesterday, he's having the same problem with a different laptop, so it must be something wrong with the default installation.

---

### Post by iDleR on 2010-05-02
No suggestion? Please?

---

### Post by Eemeez on 2010-06-02
I have excatcly the same problem. Was with 9.10 and is with 10.04.

---

### Post by linux-hack on 2010-06-02
it is possible that may come from graphic drivers ... try reconfiguring xorg or gnome desktop...

thats a guess so I'm not rely sure...

---

### Post by dino99 on 2010-06-02
sudo dpkg-reconfigure plymouth

or boot without "splash" on the boot screen

might look at logs to know about errors

---

### Post by iDleR on 2010-07-05
> **dino99 said:**
> sudo dpkg-reconfigure plymouth

or boot without &quot;splash&quot; on the boot screen

might look at logs to know about errors

 Hi! Sorry, I'm late. How can I remove the splashscreen? And what exactly should I check on my logs?

---

### Post by iDleR on 2010-07-16
Ok, so I did run ```
 dierre@Molly:~$ sudo dpkg-reconfigure plymouth [sudo] password for dierre:  update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic 
```  but the problem is still there. I've also disabled the splash using this ```
 GRUB_CMDLINE_LINUX_DEFAULT="nomodeset noplymouth 
``` in /etc/default/grub/ but notingh happened. Running out of solution :(

---

### Post by Peter-E on 2011-03-16
Well, I had this probem too, until now. Finally I decided to do an upgrade to Maverick (the standard Ubuntu desktop...) which gave problems at first for the upgrade wanted some answer in a partly obscured screen, so I forced it off via TTY1. After reboot the desktop did not show but a sudo apt-get update in TTY1 showed some errors AND a propsed solution. After that, the upgrade continued and all works well now.... AND the freeze is gone! So this was something in the previous kernels. I'm afraid I don know what.
Regards,
Peter

---

