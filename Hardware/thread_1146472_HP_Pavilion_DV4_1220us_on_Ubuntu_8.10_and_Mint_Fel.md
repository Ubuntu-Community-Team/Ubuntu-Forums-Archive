---
title: "HP Pavilion DV4 1220us on Ubuntu 8.10 and Mint Felicia 6"
date: 2009-05-02
forum: Hardware
---

### Post by zampes on 2009-05-02
Hello everybody.
I have recently bought 2 HP of the model mentioned above, Turion Dual Core X2 64, 4GB ram, 250GB HDD Hitachi and an ATi Radeon HD3200, Vista Preinstalled. Of course, I wanted to get rid of vista pretty quickly, so I only booted into Vista 2 or 3 times before eliminating it. But that's not what this thread's about, I just want to present to you all the solutions to all the problems -I had- on this HP model. So... here it goes.

**_LiveCD 8.10, 9.4 and Mint 6 Install_**: As soon as I got my hands on 9.4, I ran the LiveCD only to find that the screen would flicker -a lot. After installing it anyway, doing a lot of research and realizing 9.4 didn't recognize the ATi right away (there wasn't even the typical "restricted drivers are available thingy"), I decided to install driver version 9.4 -the latest from AMD here: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run) - and after a reboot, it worked just fine, including compiz and the rest of 'em!
My second HP did not suffer from flickering, but also installed the drivers to get fglrx working and stuff.

**_ATi Driver Install_**: I had trouble installing the ATi driver after downloading it. What I did was the following: since for some reason the name "ati-driver-9.4-xsdfsdf-xcfvsrt-zdcfser.run" that is the original seemed to not get ubuntu to read it, I changed its name to "ati.run" on the desktop. On the terminal I typed "cd /home", then "cd yourusername", "cd Desktop", "sudo sh ./ati.run" obviously without the quotation marks. After that, I followed the steps and it installed ok. Then, the necessary reboot and after the reboot there was no need for the infamous "aticonfig --intial -f" in terminal, it just worked. but in case yours doesn't, after the install and the reboot, go to terminal, type 'aticonfig --initial -f' and that'll be it.

**_Sound Card Issues_**
The sound doesn't work out of the box on the HP DV4. I followed several tutorials to make it work, but none worked, until I tried the following:
in terminal type "sudo gedit /etc/modprobe.d/alsa-base", erase EVERYTHING on that file and paste the following lines exactly like this: 

alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1

then, save the file and in terminal type "sudo reboot" or just go to "Sytem, Shut Down, Restart." After restarting, your sound will work. Make sure you adjust volume and stuff... that just happens.

**_Wireless Card - WiFi from BroadCom_**
I've heard loads of bad things about this card, but I've had no trouble with it. In fact, I did not enable the restricted drivers and the card picks up signals much better than my Acer 3050's InviLink-whatever Wifi card. If you're having issues with this, I can't help you, sorry! :(

[U]Now, the Killer Thing. This got me working on the Laptop for hours -yeah, I know, I'm a noob :) -
[/U]:

***_BOOT PROBLEMS!_*** (sorry for the capitals and stuff :) )
I had no trouble with booting on the machine that suffered from flickering, but I had loads of trouble with booting with the machine that didn't suffer from screen flickering...
The hard drive was partitioned the following way: 14GB -or so- for the Windows Vista Factory Recovery thingy and the rest of the drive for Vista use. So, on install I just killed the vista usage partition and left the recovery part there -I mean, you just never know when it might actually come in handy...- The new partition looked like this 4GB for swap -I know, with 4gb of ram, this is excessive-, 30GB for / in ext3 format -ext4 if you're using 9.4- and the rest for /home.
Everything installed perfectly and the first boot went well... after that I installed all the things I mentioned above -ati, sound, crossover, etc. After all that, a reboot... and it didn't boot, it loaded 8.10 and Mint 6 and then showed me all the files that were being loaded until one of the following random dead-ends at:

powernowd................. and never an "ok" it just died there.
or
ata device not ready, soft reset failed, cache write through thingy, etc.

As it would never finish loading, I went "reboot" or sometimes, simple "power button for 5 seconds... off--- power button again. And it went on like this, one boot: ok, next boot: fail, then ok, then fail... you get the drill. I kept on reading other posts -in other forums, and even HP forums. that recommended deleting the recovery partition which was supposedly faulty; unfortunately I actually listened to that **** and erased the partition, loosing the recovery, forever... dummy me! Obviously it continued with the every-second-boot-works thingy--- darn it!
After much reading I found out I had to turn off ACPI, which I did by following these steps: 

In terminal type "sudo gedit /boot/grub/menu.lst"
This would open the GRUB loading list you see at boot, which will allow you to modify something really small that will allow you to fix the boot problem. In this open file, do the following: 
go the part that looks like this:

**title**	Linux Mint x64 Edition, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
**quiet**

title		Linux Mint x64 Edition, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

Copy the firs part from "title" until "quiet" and paste right underneath that 'paragraph', which will make it look like this:

title	        Linux Mint x64 Edition, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title	        Linux Mint x64 Edition, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint x64 Edition, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

So, the first paragraph is repeated, and will will modify it so that the system turns acpi OFF so it doesn't bother us with while booting. Then finally, things will look like this:

title	        MY BOOT (NAME IT SOMETHING COOL, IT'S JUST A NAME)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet acpi=noacpi splash (this line should not be here, understand that "acpi=noacpi" should go between 'ro' and 'quiet' on the line above separated by one space...)
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title	        Linux Mint x64 Edition, kernel 2.6.27-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint x64 Edition, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

I will end up looking like this: 
(see attached pic if the previous was confusing... :( )

That should solve your problems... those were all the problems I faced. Hope they help you enjoy your HP as it did me...
I recognize that posting this is probably plagiarism or something, since I've taken solutions from different places. To the original solution poster, my sincerest thanks and apologies, I'm simply compiling info from different parts so the affected parties may find everything in one place.

Thank you and enjoy. I take no credit for these solutions, as I came up with none of them, except maybe for directly pasting the sound configuration lines instead of following long steps others proposed that included installing and uninstalling ALSA and stuff, which simply ruined MY overall changes.

-Zampes!:guitar:

---

### Post by zampes on 2009-05-02
I forgot to add that I have also found the solution to ZTE modems not working on 8.10. don't know it they work on 9.4 or Mint 6 on plugging in, but if they don't and you want to know, post a quick reply and I'll post it... thanks!

---

### Post by MD Sane on 2009-05-19
thanks dude I finally got it to work I was having issues with other approaches. Just to let others know this works for the HP Pavilion DV4 1220us running Ubuntu 9.04 64bit. Thanks again.

(another thing i should note is that i placed the lines 
"alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1" 

on both files "alsa-base" and "alsa-base.conf")

---

### Post by Manix28 on 2009-05-30
Thanks for the fix, it got my sound working, although plugging in the headphones did not mute the speakers (I had to mute the internal speakers manually when I was going to use the headphones).  I fixed this by editing my alsa-base (or alsa-base.conf in 9.04) so it was like this:

options snd-pcsp index=.2
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
options snd-hda-itnel model=dell-m4-1
optionssnd-hda-intel enable_msi=1


By adding the new lines at the top and bottom, now the speakers mute when I plug in my headphones.  Now all we need is to get the mic working too....

---

