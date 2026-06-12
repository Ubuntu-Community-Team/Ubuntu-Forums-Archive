---
title: "Problems with Ubuntu 7.04 on Intel Dual Core 2.66GHz and Intel D102GGC2 motherboard"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by anoopjohn on 2007-05-02
Hardware configuration
Intel Dual Core 2.66GHz 
Intel D102GGC2 Motherboard
512MB DDRII
Hitachi HDS721616PLAT80 160GB IDE Hard disk
I downloaded a copy of Ubuntu 7.04 beta alternate install cd during the last week of beta and tried to install it. The installation used to get hung midway. I then tried ubuntu 6.10 alternate CD and the installation went through successfully. However after installation when i tried to reboot i used to get the error
hda: lost interrupt 
hda: dma_timer_expiry
I did some searching on ubuntu forums and other forums and found that if i put acpi=off in the boot string it could solve the problem. I tried this solution and it worked. 
I then upgraded the system using synaptics to ubuntu 7.04. However the problem reappeared. This time when i put acpi=off in the boot string i used to get the error 
OHCI: BIOS handoff failed (BIOS bug?)
I then fished through forums again and found that if i put 
noapic irqpoll pci=routeirq 
in the boot string instead of the acpi=off i could get the system to boot.
However now when i boot I get a message that says
BIOS bug no explicit IRQ entries,using default mptable(tell ur hw ventor)
The system boots fine. I just wanted to update the community of the steps I took and look forward to any other suggestions. I will try a clean 7.04 install sometime later when i download the release version of the 7.04 cd.

---

### Post by dannyboy79 on 2007-05-02
thank you for your info, there have been major issues with getting many machines to be able to install Feisty from the Ubuntu Live CD so if I were you I would stick with your upgraded from Edgy to Feisty setup and this the latest Feisty and would be no different from doing a fresh install. might be cleaner and no edgy junk laying around but if you had issues with the beta, you'll still have issues. there are many many thread about the live cd not being able to boot up, not being able to install and all that. Basically the boot options you're adding are for "broken" bios's. I don't knwo what that means I just think that is it possible the bios is old? or maybe brand new? the OHCI Bios handoff failed is noting new, I have seen it before and if your system is working than there's nothing to worry about and I am sure it's been repoorted. same goes for the Bios bug no explicit IRQ entries. 

Thank you for your info as it may be helpful for other users I merely wanted  you to understand that going from Edgy to Feisty is no different than downloading the released Feisty and installing fresh (except, like I said, this way all your settings and preferences are saved and it's possible that there are some edgy components laying around but nothing that should concern you. you can always do a 

sudo aptitude clean

and 

sudo aptitude autoclean

and this will clean up and remove any unneeded old packages from your system. read the man page for aptitude first to learn something.

man aptitude

---

### Post by anoopjohn on 2007-05-02
thanks for the tip. That will save me a few hours of my time and close to 1GB of my bandwidth.
Cheers
Anoop
[www.zyxware.com](www.zyxware.com)

---

### Post by syndrom3 on 2007-05-31
> **anoopjohn said:**
> Hardware configuration
Intel Dual Core 2.66GHz 
Intel D102GGC2 Motherboard
512MB DDRII
Hitachi HDS721616PLAT80 160GB IDE Hard disk
I downloaded a copy of Ubuntu 7.04 beta alternate install cd during the last week of beta and tried to install it. The installation used to get hung midway. I then tried ubuntu 6.10 alternate CD and the installation went through successfully. However after installation when i tried to reboot i used to get the error
hda: lost interrupt 
hda: dma_timer_expiry
I did some searching on ubuntu forums and other forums and found that if i put acpi=off in the boot string it could solve the problem. I tried this solution and it worked. 
I then upgraded the system using synaptics to ubuntu 7.04. However the problem reappeared. This time when i put acpi=off in the boot string i used to get the error 
OHCI: BIOS handoff failed (BIOS bug?)
I then fished through forums again and found that if i put 
noapic irqpoll pci=routeirq 
in the boot string instead of the acpi=off i could get the system to boot.
However now when i boot I get a message that says
BIOS bug no explicit IRQ entries,using default mptable(tell ur hw ventor)
The system boots fine. I just wanted to update the community of the steps I took and look forward to any other suggestions. I will try a clean 7.04 install sometime later when i download the release version of the 7.04 cd.


I've the same problem with Intel D102GGC2 Motherboard, Pentium D 3.40GHz Dual Core and Kubuntu 7.04 (clean install). With this boot string the problem seems to be fixed. Do you encounter any other problems using this boot string?? 
TIA!

---

### Post by anoopjohn on 2007-06-01
I just updated with the recent updates and the problem reappeared. I checked grub and saw that the boot options were reset even in the previous kernel. I changed it to acpi=off and now it is booting fine except for the warning about mptable at boot time.

---

### Post by compunuts on 2007-06-01
I'm trying to get a new Ubuntu 7.04 fresh install and need to put ACPI=off option. Can you tell me where to put it? I can't find my grub.conf file in /etc as mentioned on many web posts. Is there any Ubuntu specific area? This is rather old box (P233, 256 MB of RAM) for testing of POS softwares. My other Ubuntu works fine on Athlon 64.

TIA

---

### Post by anoopjohn on 2007-06-01
if your system is booting fine why do you want to put acpi=off? 
you can got edit /boot/grub/menu.lst and edit the kernel line and add the acpi=off parameter.
create a backup first before you do this. 
then run 
sudo grub-install /dev/hda (or whichever device you want to install grub to)

if you cannot boot then from the boot menu if you press e you can edit the boot option and directly edit the kernel line and boot after making changes.

once you get you will have to edit menu.lst and grub-install to make changes permanent.

---

### Post by dannyboy79 on 2007-06-01
If he already did the install than I am not aware of any reason to have to run grub-install? If grub is already installed and he merely needs to add a boot option to his menu.lst then all he should have to do is make sure he adds it to the 
#kopt
line as well as each of the boot lines and he should be good to go.

If it's because he can't even start the live cd than I suggest because it's such an old box that he use the Alt Install CD, it's text based and has less problems BUT if you want to stick with the live cd and you can't even boot it, than just do as the previous poster said and when the live cd boots, and you're at the choices menu of what to do, chose F6, this will bring you to a place where you can hit e to edit a boot line, and then add the acpi=off option there. Then once the install finishes, you'll have to hit esc to show grub menu, then e again, to add the acpi=off option so you can get into your installed system, once there just do as a stated above. Good luck

---

### Post by anoopjohn on 2007-06-01
oh so you dont have to redo grub-install to have the menu.lst changes take effect? I didnt know that. Thanks for the information.

---

### Post by dannyboy79 on 2007-06-01
> **anoopjohn said:**
> oh so you dont have to redo grub-install to have the menu.lst changes take effect? I didnt know that. Thanks for the information.

correct, read this and you'll be enlightened.
[http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-using-grub_002dinstall)

---

### Post by syndrom3 on 2007-06-01
> **anoopjohn said:**
> I just updated with the recent updates and the problem reappeared. I checked grub and saw that the boot options were reset even in the previous kernel. I changed it to acpi=off and now it is booting fine except for the warning about mptable at boot time.

So with the latest update you use "acpi=off" instead "noapic irqpoll pci=routeirq" ???
My  system hang up during boot if in the bios settings i choose to use both CPU's core. If i set the option to use only one core the system boot sucessfully.

---

### Post by dannyboy79 on 2007-06-01
instead of doing that, you could also try out the -386  kernel as it doesn't have SMP enabled. Which would take advantage of the both cores. It's the same result in the end I am sure though. WOW, it's really to bad you guys can't take advantage of your dual cores. Have you tried compiling your own kernel?

---

