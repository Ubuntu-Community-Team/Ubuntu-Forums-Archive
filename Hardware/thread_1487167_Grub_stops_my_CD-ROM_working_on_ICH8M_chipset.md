---
title: "Grub stops my CD-ROM working on ICH8M chipset"
date: 2010-05-18
forum: Hardware
---

### Post by digitalwarfare on 2010-05-18
Hi. 
This is a problem I'v meen trying to solve for some time.
 
This has been an Issue on 3 different laptops with this chipset.
 
laptop 1: samsung R700
laptop 2: Sony Vaio AMR-61
Laptop 3: Samsung M60
 
here's the thing
 
My cd-rom works. I can boot from it. When i have just windows installed (xp / Vista / 7 ) without Grub, my cd rom functions perfectly. Read / Write cds/DVD's/BD-R/RE )
 
Now, if i try to dual boot it, I can install from the linux cd (it boots). once the install is compleat, grub is installed, but my cd-rom dissapears from both windows and linux. the hardware just doesn't exist.
 
If i remove the drive from the laptop, and use a laptop-sized cdrom caddy, and attach it to the usb, it works perfectly reading/writing cds /dvd/bd-r/re in both linux and windows.
 
Next, i remove GRUB, and just allow it to boot into windows (restore the windows bootloader) and boot into windows, with the drive back in the laptop, it works fine, just cant boot linux.
 
This leads me to belive the problem lies with grub, and the chipset in my laptop. There is no option in my bios, to change the mode it works in (IDE/AHCI)
 
My next thing to think of is "well, windows 7 bootloader is ok with the drive, why dont I use that?"
 
So off i go, and try to use EasyBCD to try and configure that. I didnt quite get it to work, but im doing more reading on this, though.
 
I have read in some places that there is a patch for this chipset, and possibly telling grub to not use power managment.
 
Does anyone have any solutions to this? am i just missing a simple option i need to put into grub bootlist?
 
yes, just running Ubuntu without windows is a possible solution, but there are a few things i need to be able to do in linux first.
 
Also, would using LILO solve this problem? or even grub4dos?
 
Sorry about the long post
 
Iv been trying to solve this since ubuntu 9.04 currently using 10.04 now. Its very nice. Thankyou for such a wonderful OS :P
 
Regards, Dave

---

### Post by digitalwarfare on 2010-05-19
Iv managed to stumble on some possible solution, but i require some help, and advice

Iv read that some IDE cd-roms (mine is IDE, not sata, even though I have a sata HD ) require a module called ide-cd to be loaded. possibly ide-generic.

my etc/modules contains only one entry ( lp ) and i have to "modprobe" ide-cd

so when i "sudo modprobe ide-cd"
i get : Fatal : module ide_cd not found

i found my source here: [http://ubuntuforums.org/archive/index.php/t-5369.html](http://ubuntuforums.org/archive/index.php/t-5369.html)

am I on the right track with this?

also, ubuntu is now the only os installed on my laptop. so there is no dual booting. grub is still being used.

Regards, Dave

---

