---
title: "Black screen in Ubuntu 9.10 on Compaq 610"
date: 2010-01-30
forum: Hardware
---

### Post by cyaquino on 2010-01-30
Ubuntu **9.04** worked well in my Compaq 610 notebook with Mobile Intel 965 Express Chipset graphics. But after upgrading to **9.10** I got a black screen and don't know what to do. That happens either from the LiveCD or the hard disk. Any clue please?
I found these and could boot from LiveCD and see the desktop, but I have GRUB **0.97** and seems not applicable the part describing how to apply the solution to the hard disk:
 
[I]launch the livecd
use F6 for other options
use ESC to get rid of the menu which just popped up
but now you have a long line of boot parameters there at the end after "--" leave a blank and add "**nomodeset**"

nomodeset switches the new kernel feature off which configures the mode settings of the graphichip.

now you can boot it - just hit enter

this "nomodeset" needs to be turned on permanently after installation. so just stay in the livecd and mount your harddrive and edit /media/UID-XXXXXX/boot/grub/grub.cfg via a terminal (Application -> Accessoires -> Terminal)

$ gksudo gedit /media/UID-XXXXXX/boot/grub/grub.cfg [/I]
[COLOR=red](In old GRB where should I go? No similar place in menu.lst)
[/COLOR]
[I]here you need to change the following menu entry by adding "nomodeset" - see the line starting with "linux"
[/I]
[I]menuentry "Ubuntu, Linux 2.6.31-14-generic" {
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=5c7c29e4-f877-4e6d-8b20-aed6eacd5ad3 ro nomodeset quiet splash nomodeset
initrd /boot/initrd.img-2.6.31-14-generic
}[/I]
[I]now reboot. we are almost there !!!

after rebooting the system, we again open the terminal and edit the grub default

$ gksudo gedit /etc/default/grub 

here there a two changes which added the "nomodeset": [/I]
[INDENT][I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
GRUB_CMDLINE_LINUX="nomodeset"
[/I][/INDENT][I]after saving the changes execute

$ sudo update-grub

so that is what I have done to get it working. there is still a strange thing that I can not see the grub menu when starting the laptop also the when there is a filesystem check the laptop stays black for very long time. so not perfect but otherwise I am very pleased with ubuntu on that laptop.

I found a bugreport where the fix goes via the configuration of the xserver by turning off KMS (kernel mode setting). [/I][[COLOR=#444444]*https://bugs.launchpad.net/ubuntu/+s...el/+bug/474421*[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/474421")

*but the good thing is that the bug was confirmed - let's see when there will be an update.*
*Last edited by m.kristian; November 22nd, 2009 at 08:57 AM.. Reason: need to finish it *

---

