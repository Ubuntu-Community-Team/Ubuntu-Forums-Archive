---
title: "Ubuntu 10.04 and Nvidia"
date: 2010-11-22
forum: Hardware
---

### Post by mat2010 on 2010-11-22
Hello all

It's been a while since I have struggled with Nvidia installation. Have used Ubuntu for 3 years now and Linux for 5 years. The click installation has been fine until now 10.04. Currently I run Ubuntu ultimate edition 2.7 (64bit version)

There are many suggested solutions but they do not work. Blacklisting the Nouveau driver does not work and when attempting to install the the Nvidia driver manually it still says Nouveau driver in use.

To start I did 

[LEFT]     sudo rm /usr/share/myspell/dicts/en_ZA.*  {This is because Gedit is also faulty}              sudo apt-get purge nvidia*                                                                                             sudo  gedit [I]/etc/modprobe.d/blacklist.conf  
                       Add to end                [/I]vga16fb
                               nouveau
                               rivafb
                               nvidiafb
                               rivatv[I] 


                      sudo gedit /etc/default/grub 
                              edit the line with "quite splash" to look like   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash blacklist=vga16fb nouveau.noaccel=1 nouveau.modeset=0"
GRUB_CMDLINE_LINUX="nomodeset"
                                   
sudo update-grub

download the nvidia driver from Nvidia website

Then reboot. When error message choose exit to console login
Login and go to folder with Nvidia driver
Then    
         sudo NVIDIA-Linux-x86_64-260.19.21.run         {or whatever u downloaded}
Reboot at end and should work fine    

I think the problem is disabling Nouveau - click click method may also work when disabled this way.           

  
[/I] [/LEFT]

---

