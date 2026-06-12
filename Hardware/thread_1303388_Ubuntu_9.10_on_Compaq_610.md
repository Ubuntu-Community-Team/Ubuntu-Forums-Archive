---
title: "Ubuntu 9.10 on Compaq 610"
date: 2009-10-28
forum: Hardware
---

### Post by jomi86 on 2009-10-28
Hi! This is my first post on forum :) Recently I bought HP Compaq 610 laptop with very cool components (15,6” screen, Intel Core2Duo, 320GB, 4GB) but seems graphic card (integrated Mobile Intel GLE965 Express Chipset) is the worst part (I know that in laptops are generally bad graphics, but...).  Anyway, I try lot of Linux distros (SuSE, Fedora, Gentoo, Mint...) but Ubuntu 9.04 performed best. A couple days ago I tried Ubuntu 9.10 RC and find that (like in most distos I mention up) screen is black when try to start Live or Instal from Live. I tried with Vesa driver option in F4 menu, but result is same. CD is loading, but I can't see anything. Does anyone has idea how to start live session or install? I just need to install it on HDD :) I will wait 'till tomorrow for final release, but doubt that this will be fixed... :(

---

### Post by uniomni on 2009-10-29
I am experiencing exactly the same problem.
Hopefully, the final release or an early patch will fix it.

Ubuntu 9.10 beta came up fine on my (Intel Wolfsdale 3.16GHz, Asus mother board) Desktop, though.

I ended up installing Jaunty on the laptop for now.

---

### Post by uniomni on 2009-10-31
The final release of Ubuntu 9.10 is still unable to load onto the HP Compaq 610.
All I get is a black screen and the sound of the CD trying to do something.

It doesn't matter whether I select trying Ubuntu or installing Ubuntu - the black screen is all I get. This is a real shame and I am sure it is something simple that prevents Ubuntu from displaying on the laptop.

---

### Post by m.kristian on 2009-10-31
adding "nomodeset" in boot options from the live CD helped.

but I installed 9.10 with the alternative CD, which produced a blank screen after installation as well. here I added the "nomodeset" in grub boot parameter list in the line starting with "linux "

then I added that "nomodeset" in /boot/grub/grub.cfg at the respective place (as well for the recovery mode)

---

### Post by m.kristian on 2009-10-31
my reference was [http://linux.derkeiler.com/Mailing-Lists/Fedora/2009-09/msg00616.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2009-09/msg00616.html)

---

### Post by minche on 2009-11-05
same problem here =/
when i upgraded all i got was a black screen, so i loaded the old kernel, but there are no drivers =/ not even for touchpad, but with some luck the internet is still working
so i downloaded the image, and booted it, and again - the black screen. 
I really hope they fix this soon, 'cause it's really frustrating =(

---

### Post by TFLuis on 2009-11-08
I'm experiencing the same problem with my Compaq 610. I don´t understand the "nomodeset". Where do I have to write it to try booting with the Live CD without installing?

---

### Post by swwei on 2009-11-16
I believe it is because compaq 610 is a dual CPU machine. And Ubuntu 9.10 live CD can not boot with such hardware configuration. You may try to alter the bios of compaq 610 by  changing the configuration to one CPU mode, and see what happens.
 
It works for my compaq 610 on Kubuntu 9.10 live CD, but I've never tried it on Ubuntu 9.10.

---

### Post by m.kristian on 2009-11-21
launch the livecd
use F6 for other options
use ESC to get rid of the menu which just popped up
but now you have a long line of boot parameters there at the end after "--" leave a blank and add "nomodeset"

nomodeset switches the new kernel feature off which configures the mode settings of the graphichip.

now you can boot it - just hit enter

this "nomodeset" needs to be turned on permanently after installation. so just stay in the livecd and mount your harddrive and edit /media/UID-XXXXXX/boot/grub/grub.cfg via a terminal (Application -> Accessoires -> Terminal)

$ gksudo gedit /media/UID-XXXXXX/boot/grub/grub.cfg 

here you need to change the following menu entry by adding "nomodeset" - see the line starting with "linux"

[INDENT]menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3 ro nomodeset  quiet splash nomodeset
	initrd	/boot/initrd.img-2.6.31-14-generic
}[/INDENT]

now reboot. we are almost there !!!

after rebooting the system, we again open the terminal and edit the grub default

$ gksudo gedit /etc/default/grub 

here there a two changes which added the "nomodeset":
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX="nomodeset"
[/INDENT]

after saving the changes execute

$ sudo update-grub

so that is what I have done to get it working. there is still a strange thing that I can not see the grub menu when starting the laptop also the when there is a filesystem check the laptop stays black for very long time. so not perfect but otherwise I am very pleased with ubuntu on that laptop.

I found a bugreport where the fix goes via the configuration of the xserver by turning off KMS (kernel mode setting). [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/474421](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/474421)

but the good thing is that the bug was confirmed - let's see when there will be an update.

---

### Post by BigEdu on 2009-11-29
when I type $ gksudo gedit /media/UID-XXXXXX/boot/grub/grub.cfg I see an empty file. I am installing ubuntu 9.10 amd64, maybe the adress is diferent.

---

### Post by m.kristian on 2009-11-29
> **BigEdu said:**
> when I type $ gksudo gedit /media/UID-XXXXXX/boot/grub/grub.cfg I see an empty file. I am installing ubuntu 9.10 amd64, maybe the adress is diferent.

please replace UID-XXXXX with whatever you find in the /media directory. it should be your hard disc. in case you have more then one hard disc use the one which has a "boot" directory.

from the command line it is easy to complete it by starting with

$ gksudo gedit /media/
and hit TAB twice which will complete the it if there is only one possibility or gives you the list of possibilities. but in any case you need to mount your hard drive first !! go to "Places => Computer" there you see all hard disks mounted or unmounted.

---

### Post by BigEdu on 2009-11-30
Thanks, still cant do it because i cant save the file (it apears a mesaje whit "read only")

---

### Post by m.kristian on 2009-11-30
gksudo chmod u+w /media/UID-xxxxx/boot/grub/grub.cfg

gives you write access for the superuser.

---

### Post by BigEdu on 2009-12-01
Thanks you all, finally did it.

---

### Post by wgarciamachmar on 2009-12-04
I've just installed the OS last week and worked perfectly. Boot time improved by 20 secs, compared to 9.04.

Everything works, WiFi, camera, sound, video (though i think i'm only working with one of the machine's speakers, but the headphone output works just fine).

---

### Post by pieterkirsten on 2009-12-19
I downloaded Ubuntu Desktop 9.10 (64 bit) ISO image and installed.

My wireless did not seem to work. It was a while before I figured out that the Wireless was actually not working at all. 
As the Compaq 610 can only have a Intel or a Broadcom wireless chip in, I guessed that I must have a Broadcom. The Intel one would probably work fine. 

Found the following drivers from Broadcom: 802.11 Linux STA driver:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Just follow the instructions in the readme file:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

---

### Post by wgarciamachmar on 2009-12-23
Got the Compaq 610 with Interl Core 2 Duo, 3 GB RAM and a 160 HDD. Installed 9.04 and worked just fine, except for the sound, and then made a clean install with 9.10 (so I can get the most of the ext4 file system) and worked fine as well, no sound bug.

Of course, I'm not using the video card to the most of its capacity. Besides, some games just get the system to crash like FreeDM, and sauerbraten.

---

### Post by pwebster25 on 2010-01-24
[QUOTE=m.kristian;8362484]
$ gksudo gedit /media/UID-XXXXXX/boot/grub/grub.cfg 

here you need to change the following menu entry by adding "nomodeset" - see the line starting with "linux"

[INDENT]menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3 ro nomodeset  quiet splash nomodeset
	initrd	/boot/initrd.img-2.6.31-14-generic
}[/INDENT]

m.kristian and Others-
Thanks for your help.  I think I've got it up and running now.  Do I need to modify the lines starting with linux also in the sections for recovery and for the earlier kernals (2.6.31.14 etc)?

---

### Post by crazedidiot on 2010-02-05
Yeah I was confused by UID-XXXXXX aswell. This is actually some sort of ID for your harddrive but I didn't use that. Your harddrive will most likely be hda1 for PATA or sda1 if it's a SATA drive (mine was SATA)

sudo mkdir /media/hdd                                    // make a directory to mount your harddrive to
sudo mount /dev/sda1 /media/hdd                 // mount it there
sudo gedit /media/hdd/boot/grub/grub.cfg  // edit the file

I found that grub.cfg was read only as was the directory that contained it but in any case after making it writable (sudo chmod +w grub.cfg) and editing it the system still booted to a blank screen.

In this case during startup hit ESC to enter the grub menu then use the edit keys listed to add the nomodeset as before. This will allow you to boot up with a writable harddrive. You can then edit the file as described before.

sudo gedit /boot/grub/grub.cfg   // note the new path as the harddrive is now mounted at /
Hope this helps.
Also this problem is not confined to compaq 610 laptops, I had it on a desktop machine with asus motherboard and nvidia GEforce 5200 graphics card.

---

### Post by netlaptop on 2010-02-08
Thanks much!!!!!!!!!!!!!!!!!!!
I have been looking for this nearly 4 months!

This way also works for me:

1- Live CD F6, add nomodeset... like[ #9 post]("http://ubuntuforums.org/showpost.php?p=8362484&postcount=9")

In Ubuntu, active driver in System/Administrator/Hardware Drivers (to prevent Broadcom STA wireless driver problem for my dell studio)

then Install Ubuntu to HDD.

2- When Ubuntu is installed, restart as it asks. At boot menu, let press "e" to edit grub at boot and add _nomodeset_
like:
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=a6850822-f08e-4f11-8cd3-4ce83a864b8a ro nomodeset  quiet splash nomodeset

3- In Ubuntu just edit:

gksudo gedit /boot/grub/grub.cfg

(It helps us pass "mount" or find UID-XXX-XXX-XXX step)

then do as #9 post

 > you need to change the following menu entry by adding "nomodeset" - see the line starting with "linux"

menuentry "Ubuntu, Linux 2.6.31-14-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3 ro nomodeset quiet splash nomodeset
initrd /boot/initrd.img-2.6.31-14-generic
}
now reboot. we are almost there !!!

after rebooting the system, we again open the terminal and edit the grub default

$ gksudo gedit /etc/default/grub

here there a two changes which added the "nomodeset":

    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
    GRUB_CMDLINE_LINUX="nomodeset"

after saving the changes execute

$ sudo update-grub


Thanks much!

---

