---
title: "How to make boot cd for USB disk drive"
date: 2009-01-22
forum: Installation &amp; Upgrades
---

### Post by doctordruidphd on 2009-01-22
My latop PC has WinXP on its internal drive, which I do not want to touch. 
I need to make a boot cd that will boot ubuntu loaded on an external USB disk drive.
This computer will not boot directly off USB devices.
I followed the instructions in 'info grub' for making a bootable cd, but all I get is "error 25 disk read error", so I did something wrong, or misunderstood.

Xp is on hd0
Ubuntu is on (hd1,3)

Maybe I should set it up to boot XP also, in case I crash the hdd.
When I went into the menu and told it to find NTLDR, same thing, error 25.

So I need to start over from the top.

---

### Post by caljohnsmith on 2009-01-23
Instead of Grub, I would try using the "PLoP" boot manager, because it has better support for booting USB devices when your BIOS does not support USB booting. Just download the [PLoP ISO]("PLoP ISO: http://download.plop.at/files/bootmngr/plpbt-5.0.zip"), burn it to CD, boot it, and select the option to boot from your USB drive. Let me know if that works OK or if you run into problems.

---

### Post by boof1988 on 2009-01-23
> **caljohnsmith said:**
> Instead of Grub, I would try using the "PLoP" boot manager, because it has better support for booting USB devices when your BIOS does not support USB booting. Just download the [PLoP ISO]("PLoP ISO: http://download.plop.at/files/bootmngr/plpbt-5.0.zip"), burn it to CD, boot it, and select the option to boot from your USB drive. Let me know if that works OK or if you run into problems.

Thanks for mentioning PLoP.  I haven't tried it yet...  But will now.

---

### Post by doctordruidphd on 2009-01-23
Thanks for the suggestion, but PLoP didn't work. The bios on this computer does not see the USB devices until their drivers are loaded. That means all the boot files -- vmlinuz, initrd, all that stuff -- has to be on the cdrom. That's how I do it from the internal hard disk, but I am going to remove this disk and replace it with a new one, so it is essential that I be able to boot the system without it. 
Ergo, I need a boot cdrom. Looks like GRUB should do it, but I can't figure out how. Maybe I am burning the iso wrong. Got it to where it almost started, but freezes during the load process. 

Any grub gurus out there can help?

---

### Post by boof1988 on 2009-01-23
Have you looked at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) yet?  They have a download (and tutorial) for a CD iso that can boot Ubuntu-8.10 on USB-flash.  From what I understand, the CD loads the USB drivers so you can boot the USB-flash.

---

### Post by doctordruidphd on 2009-01-23
Thanks, but not useful.
My system is not set up the way they set up a pen drive. So this did not work.
I have read the documentation at the GNU/grub site, and I thought I had followed the directions, but can't get it to work. 

I really don't think "alternatives" are going to work. Besides, I want to learn how to do this. I just can't figure out the grub docs.

Here is what I have done so far:

Create an $/iso/boot/grub tree
Put stage2_eltorito in $/iso/boot/grub
Put menu.lst in $/iso/boot/grub

Menu.lst as follows:

---------------------------------

title           kUbuntu 
root            (cd)    
kernel          /boot/ubuntu/vmlinuz-2.6.27-9-generic root=/dev/sdb4 ro 
initrd          /boot/ubuntu/initrd.img-2.6.27-9-generic                             
savedefault                                                                          

title           kUbuntu (single-user mode)
root            (cd)                      
kernel          /boot/ubuntu/vmlinuz-2.6.27-9-generic root=/dev/sdb4 ro single
initrd          /boot/ubuntu/initrd.img-2.6.27-9-generic                      
savedefault                                                                   

title           Debian/Gnome
root            (cd)        
kernel          /boot/lenny/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro 
initrd          /boot/lenny/initrd.img-2.6.26-1-686                
savedefault                                                        

title           Debian/Gnome (single-user mode)
root            (cd)                           
kernel          /boot/lenny/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro single
initrd          /boot/lenny/initrd.img-2.6.26-1-686                      
savedefault                                                              

title find and load NTLDR of Windows NT/2K/XP
root (hd0,1)                                 
find --set-root /ntldr                       
chainloader /ntldr                           
savedefault --wait=2             

------------------------- (I have esnipped out a lot of commented stuff)

windows is on (hd0,1)
debian is on /sda2
ubuntu is on /sdb4 

(Note: debian calls its drive /sda, while ubuntu calls it /sdb, and calls windows' drive /sda, which debian calls /hd1. go figure)

I have put everything from /sdb4/boot into $/iso/boot/ubuntu, and everything from /sda2/boot into $/iso/boot/lenny

I make the iso file with:
$ genisoimage -R -b boot/grub/stage2_eltorito -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso

burn this, and reboot.
It shows the menu, loads stuff when I hit kubuntu, and then hangs at a black screen.

---

### Post by caljohnsmith on 2009-01-23
> **doctordruidphd said:**
> Thanks for the suggestion, but PLoP didn't work. The bios on this computer does not see the USB devices until their drivers are loaded. 
That's the whole idea of the PLoP boot manager--it comes with its own built-in USB driver. Therefore, you should be able to put all your Ubuntu boot files on your USB drive (including Ubuntu's own USB drivers), and then just boot the USB drive with PLoP. If you really want to put your Ubuntu boot files and USB drivers on a CD and boot the USB drive that way, you might want to check out this link:

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by doctordruidphd on 2009-01-23
I don't know why Plop doesn't work -- I choose USB from the menu, it opens another window and says it is scanning, and does in fact scan, but it ends with a message saying 'no mass storage devices found'. No idea why.

I solved the problem, though. The instructions in 'info grub' do work. The problem was with the menu.lst file.  Too much junk in the original.
This works:

-----------------------------

timeout         30

color blue/black green/black


#
# examples
#         
# title         Windows 95/98/NT/2000
# root          (hd0,0)              
# makeactive                         
# chainloader   +1                   
#                                    
# title         Linux                
# root          (hd0,1)              
# kernel        /vmlinuz root=/dev/hda2 ro
#                                         
title           PLop boot manager         
root            (cd)                      
kernel          /boot/plpbt.bin           


title           kUbuntu 
root            (cd)    
kernel          /boot/ubuntu/vmlinuz-2.6.27-9-generic root=/dev/sdb4 ro splash quiet 
initrd          /boot/ubuntu/initrd.img-2.6.27-9-generic                             


title           kUbuntu (single-user mode)
root            (cd)                      
kernel          /boot/ubuntu/vmlinuz-2.6.27-9-generic root=/dev/sdb4 ro single
initrd          /boot/ubuntu/initrd.img-2.6.27-9-generic                      


title           Debian/Gnome
root            (cd)        
kernel          /boot/lenny/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro 
initrd          /boot/lenny/initrd.img-2.6.26-1-686                


title           Debian/Gnome (single-user mode)
root            (cd)                           
kernel          /boot/lenny/vmlinuz-2.6.26-1-686 root=/dev/sda2 ro single
initrd          /boot/lenny/initrd.img-2.6.26-1-686                      

# This is a divider, added to separate the menu items below from the Debian
# ones.                                                                    
title           Other operating systems:                                   
root                                                                       


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1                                                             
#title          Windows NT/2000/XP                                         
#root           (hd0,0)                                                    

#chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2                                                             
title           Microsoft Windows XP Home Edition                          
root            (hd0,1)                                                    
chainloader     +1                                                         

title find and load NTLDR of Windows NT/2K/XP
root (hd0,1)                                 
find --set-root /ntldr                       
chainloader /ntldr                           


title find and load CMLDR of Windows NT/2K/XP
find --set-root /cmldr
chainloader /cmldr



title commandline
commandline

title reboot
reboot

title halt
halt

-----------------------------------
CD boots just fine now. Hooray! I can remove the hard disk now, once I figure out how to back up windows. That's another trial for another day.

---

