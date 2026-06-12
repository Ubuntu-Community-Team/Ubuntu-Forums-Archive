---
title: "Intellistation M Pro stalls at Grub prompt."
date: 2008-11-05
forum: Hardware
---

### Post by nemesis13031 on 2008-11-05
Hello,
I did a quick search and didn;t find an answer so here goes......
I am working on an IBM Intellistation M Pro and I get through the install just fine. The problem I have is when I reboot, Grub counts to the auto start and then stops. Not auto boot, nothing...... If I press ESC I can choose one of the three prompts and it starts just fine.
Here is my hardware.....
Model 6219-48U
P4 with hyperthreading enabled
512M ram
18G Wide scsi
CD-RW on IDE 1-slave
No IDE hard drives only SCSI
built in ethernet
On board sound disabled. It finds it, but no output... Broken driver ;-(
PCI AC97 sound card.
Nvidia Quadro4 980 

Any Ideas?
Thanks,
-N

---

### Post by caljohnsmith on 2008-11-05
It could be that the "default" line in your /boot/grub/menu.lst specifies an OS entry that doesn't even exist; in other words, if you have three OS entries in your menu.lst, and if you have "default 3", that would mean boot the fourth OS entry which doesn't exist. So I would check the "default" line in your menu.lst first to see if that is the issue.

---

### Post by nemesis13031 on 2008-11-06
I checked that and also reset it.. Here is the file that is currently installed.....
-N
```

default 0                                   
color white/black                           

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options     
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.  
## e.g. kopt=root=/dev/hda1 ro                                    
##      kopt_2_6_8=root=/dev/hdc1 ro                              
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro                        
# kopt=root=UUID=5047e86d-88fe-4f76-b699-792876c20f30 ro          

## default grub root device
## e.g. groot=(hd0,0)      
# groot=5047e86d-88fe-4f76-b699-792876c20f30

## should update-grub create alternative automagic boot options
## e.g. alternative=true                                       
##      alternative=false                                      
# alternative=true                                             

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true                                 
##      lockalternative=false                                
# lockalternative=false                                      

## additional options to use with the default boot option, but not with the
## alternatives                                                            
## e.g. defoptions=vga=791 resume=/dev/hda5                                
# defoptions=quiet splash                                                  

## should update-grub lock old automagic boot options
## e.g. lockold=false                                
##      lockold=true                                 
# lockold=false                                      

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=                                                       

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0                                             

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single                     
# altoptions=(recovery mode) single                      

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the     
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=5047e86d-88fe-4f76-b699-792876c20f30 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=5047e86d-88fe-4f76-b699-792876c20f30 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

---

