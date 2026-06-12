---
title: "Sound Problem"
date: 2004-11-13
forum: Hardware &amp; Laptops
---

### Post by spirospr on 2004-11-13
After installing Ubuntu i have no sound. I have installed other linux distros and i always had sound from the begining on my laptop. I don't know exactly what is my audio card but i have a Dell Latitude D800 and i think it is a sigmatel pci. What could it be the problem?

I don't know if there is any connection with the problem but during boot up when enabling hotplug subsystem i get the following errors :

error inserting shpchp
error inserting pci ehp
error inserting hw_random

---

### Post by Ozitraveller on 2004-11-13
Good question I have the same problem! No sound. And I'm not using a Dell. I get a failure for shpchp when the system boots.

---

### Post by TravisNewman on 2004-11-13
The failures you have at boot are known problems, and it basically means you don't have the hardware to support it (I think) but it's not a problem really, and they can be safely ignored. 

I don't, however, know that the problem could be with your sound, but you aren't having sound problems because of the hotplug subsystem I don't think

---

### Post by Ozitraveller on 2004-11-13
I get hotplugin failures on boot, with shpchp and another that I can't remember.

I have a standard SoundBlaster PCI sound card.

---

### Post by spirospr on 2004-11-16
I searched around for solutions making the sound card work. I installed alsa but during boot up i get the message that there is no sound card detected.

Anyone with some solution?

---

### Post by LongTooth on 2004-11-16
Looks like plenty of sound problems with Ubuntu. I too have sound problems. My set up: 500 MHz PIII with 128Mg of ram. I have an onboard sound chip but currently have installed a ISA SB16 sound card. Neither works. I have disabled the intergrated sound. So that can't be the problem. I've tried both without success. I ran Alsaconf. It goes through it's routine and says it configured. Still no sound. I have done some digging and this is what I've come up with. I don't have a mixer that I can use. My results of Whereis: 

longtooth@ubuntu ~ $ whereis alsamixer
alsamixer: /usr/bin/alsamixer /usr/share/man/man1/alsamixer.1.gz
longtooth@ubuntu ~ $ sudo /usr/bin/alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
longtooth@ubuntu ~ $


I can't get it to open using any combinations. alsamixer, /user/bin/alsamixer, sudo alsamixer, or sudo /usr/bin/alsamixer.

So I thought I'd uninstall and reinstall it. Here is what I got: 

longtooth@ubuntu ~ $ sudo apt-get remove alsamixer
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package alsamixer
longtooth@ubuntu ~ $ whereis alsamixer

When I open the Volume control under Applications > Multimedia > Volume control I receive this error message: Sorry, no mixer elements and/or devices found. So it looks like my card is not detected plus I've no mixer. Or am I wrong? 

This is a card that worked with Slackware 10.0 and SuSE Pro 9.1. Where to go now? Can anyone point me in the right direction? Any assistance would be greatly appreciated. Thanks.

---

### Post by oddabe19 on 2004-11-16
I have an audigy... i have no problems (my firewire doesn't work, but that doesn't matter, since i dont use i)

I get some type of similar error at boot too, but i don't have any problems really.

---

### Post by evane on 2004-11-16
add acpi_irq_isa=7 to the default kernel options line in /boot/grub/menu.lst... for example

# kopt=root=/dev/hda7 ro acpi_irq_isa=7

then run sudo update-grub, and make sure you kernel line has that extra statement like so... kernel          /vmlinuz-2.6.8.1-3-686 root=/dev/hda7 ro acpi_irq_isa=7 quiet splash

Reboot and your should issues should be resolved...

---

### Post by spirospr on 2004-11-17
Thank you all for your help. I finally managed to solve my problems with audio and wireless card. Everything had to do with a bug which had to be solved by adding 
"acpi_irg_isa=7" in booting options. 

I had tryed that before but it did not work correct since i couldn't get the right information how to add this. Editing throurh grub is not an option since after boot up it recovers to defaults and it is not saved. It had to be made through command line.


[COLOR=Red]sudo nano /boot/grub/menu.lst[/COLOR] 

and then add in the line of the kernel this:

[COLOR=Red]acpi_irq_isa=7[/COLOR]

Well after that i had my solution.

I will come back for more details.


(well the only thing i have to notice from the moment that i got involved with linux is that everything is meant......... No clear solutions to be understood for someone who will try to find solutions through forums. I think that if someone finds a solution for his problem he should post  detailed how he made it. So that in future sb new in linux will be easier for him . Posts like "I found the solution ..... thank you" and that's it , is out of the spirit of a community.  Posting how you made it in details will make sd's life easier. )

Thank you very much for your contribution......... =D>

---

### Post by ThePrawn on 2004-12-20
Excellent -- this is just the solution I was looking for. It worked brilliantly -- thanks.

---

### Post by norwyn on 2004-12-23
I also have sound problems. But not the same problem as the rest of you above; When I'm listening to music with XMMS and using GAIM at the same time, it sounds like my speakers are cracked. Anyone know what the problem is about? It is like the sound channels fight  8-[

---

### Post by 4ebees on 2005-01-23
[QUOTE=spirospr]

[COLOR=Red]sudo nano /boot/grub/menu.lst[/COLOR] 

and then add in the line of the kernel this:

[COLOR=Red]acpi_irq_isa=7[/COLOR]

Well after that i had my solution.

I will come back for more details.


Thank you very much for your contribution......... =D>[/QUOTE]

Hi,
Very new to Ubuntu. 

I'm wondering if you would be able to more precisely indicate exactly where to make the entry in the file?

Can it be anywhere at the end of the file, or does it have to be on the end of one of the entries that commences:

(eg) kernel                               /boot/memtest86+.bin

I realise this may be a simple enough answer, but I'm loath to make an entry without knowing specifically where and how to make it. 

Thanks.

---

### Post by ronin69hof on 2005-01-23
add it on the line that starts with "kernel"  see my example,

title           Ubuntu, kernel 2.6.10-2-686
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.10-2-686 acpi_irq_isa=7 root=/dev/hda7 ro vga=771 quiet splash
initrd          /boot/initrd.img-2.6.10-2-686
savedefault
boot


hope that helps

---

### Post by ThePrawn on 2005-01-23
You don't actually put it on a kernel line, per se.  It goes in the kopt line.  Search the file for
# kopt=

--append it to the end of that line.  When you run update-grub, it'll take care of appending it to the actual kernel lines.

---

### Post by lukem on 2005-01-23
I have been running ubuntu (warty) for a couple of months and loving it.  Last night I made a couple of changes.  Each of these were from the "unofficial ubuntu 4.10 starter guide"  (http:ubuntuguide.org/index.html).  

First downloaded java and installed it for Firefox.

Second installed numlockx to turn on numlock when booting

Third implemented a fix for the problem that kept my pc from powering off when I shut it down from ubuntu (acpi power off called).

Then I shut down a couple of times and delighted in the fact that the machine actually turned the power completely off.

Then I tried to launch Aucacity and the volume control and that's when I noticed that the sound was gone.  The volume control app said "Sorry no mixer elements and/or no devices found"

Well, the starter guide had a fix for exactly that problem ($ gst-resister-0.8).  Only it didn't work.  

Several hours of poking around and finally I found this thread.  I tried the # kopt=root=/dev/hda7 ro acpi_irq_isa=7  then sudo update-grub, but it never added the acpi_irq_isa=7 to the kernal line.  (I was using hda1)  

Then I tried the sudo nano /boot/grub/menu.lst and added it that way.  

It now works.  

Thanks to everyone for all the help  =D>

---

### Post by ThePrawn on 2005-01-23
The first time I did it, I applied it manually -- the problem is, I lost it the next time I rebooted.  After running update-grub, did you reboot?

---

### Post by 4ebees on 2005-01-23
[QUOTE=ronin69hof]add it on the line that starts with "kernel"  see my example,

title           Ubuntu, kernel 2.6.10-2-686
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.10-2-686 acpi_irq_isa=7 root=/dev/hda7 ro vga=771 quiet splash
initrd          /boot/initrd.img-2.6.10-2-686
savedefault
boot
hope that helps[/QUOTE]

Ronin69hof,
Thanks for that.
Can I ask a related question?
The soundcard is built-in (on the motherboard). I've checked the BIOS and it tells me it's irq 5, so should I change it to:

...acpi_irq_isa=5

or, given that it's not a separate card, does this mean that there is another change required?

Additionally, Alsaconf and alsamixer commands give me a 'not working/no such thing' response too. CD player opens and seems to run fine, but I get no sound either from the CD or from RealPlayer when viewing the news on-line. The speakers are fine (they work on my other machines). I'm not sure what sort of soundcard it is, as I cannot find anywhere on the board to tell me (if it's underneath, then thanks to Compaq, without taking the whole mobo out...

Again, thanks for your help and to everyone else.

PS. I'm installing Ubuntu on a friend's computer and am quite impressed by how fast it runs on a PII, 350mhz, 128M RAM. The sound problem is the ONLY problem I've come across, and apt-get is great  - this from a Mandrake user :)

---

### Post by ThePrawn on 2005-01-23
[QUOTE=4ebees]
The soundcard is built-in (on the motherboard). I've checked the BIOS and it tells me it's irq 5, so should I change it to:
...acpi_irq_isa=5[/QUOTE]

I believe so.

[QUOTE=4ebees]Additionally, Alsaconf and alsamixer commands give me a 'not working/no such thing' response too.[/QUOTE]

Yup, same problem I had before adding the acpi_irq_isa line to the kopts.

[QUOTE=4ebees]CD player opens and seems to run fine, but I get no sound either from the CD or from RealPlayer when viewing the news on-line.[/QUOTE]

Yup, she'll spin but if the sound has nowhere to go . . . :)

---

### Post by 4ebees on 2005-01-24
Just to let people know, I've moved my own thread here:

[http://www.ubuntuforums.org/showthread.php?p=55639#post55639](http://www.ubuntuforums.org/showthread.php?p=55639#post55639)

To avoid crosspostings and confusion for all (including me :))



[QUOTE=ThePrawn]I believe so.



Yup, same problem I had before adding the acpi_irq_isa line to the kopts.



Yup, she'll spin but if the sound has nowhere to go . . . :)[/QUOTE]


Okay, I've done what's been suggested and on rebooting, the changes are still evident in the menu.lst file.

Good so far.

Now, the following commands give me no response:

[COLOR=DarkRed]Alsamixer[/COLOR] – nothing
[COLOR=DarkRed]alsaconf[/COLOR] – nothing

The speaker icon on the top right of the screen does not allow me to change anything. It refuses to move. It will not allow me to make an configuration changes.

I have tried: 

[COLOR=DarkRed]lsmod|grep snd[/COLOR] (read this on another post) – nothing. There is no output at all.

On boot, I was getting a “Modprobe Error”. After going through the Unofficial Starter Guide, this appears to have been resolved.

On boot, I have noticed an error saying: 
[COLOR=DarkRed]
pci address space collision in region 7 of 0000 00 14.3 [f800:f83f][/COLOR]

and:

[COLOR=DarkRed]alsacnt[/COLOR] (I think this is the correct term) [COLOR=DarkRed]state 1134 No soundcard. [/COLOR]



For the sake of clarity, the computer is a Compaq Deskpro DPEND PII with 128M RAM.  I get no sound on boot, I get no sound from the CD player (cable is in place) and I get no sound when viewing the news online.

I'm not sure what sort of soundcard it carries.

Any assistance is, as always, most appreciated.

---

### Post by lukem on 2005-01-24
[QUOTE=ThePrawn]The first time I did it, I applied it manually -- the problem is, I lost it the next time I rebooted.  After running update-grub, did you reboot?[/QUOTE]


Yes, I rebooted and I still have sound.  I did lose my power shutdown though :(

I may go back and add the apm-off, but i'm afraid to add the acpi=off.

I checked the menu.lst and "acpi_irq_isa=7" is still there.

Good Luck

---

### Post by jamaas on 2005-01-26
Silly question here, I'm having the same problem, how do I check the bios to see where the sound card is connected?

Thanks

Jim


[QUOTE=4ebees]Ronin69hof,
Thanks for that.
Can I ask a related question?
The soundcard is built-in (on the motherboard). I've checked the BIOS and it tells me it's irq 5, so should I change it to:

...acpi_irq_isa=5

or, given that it's not a separate card, does this mean that there is another change required?

Additionally, Alsaconf and alsamixer commands give me a 'not working/no such thing' response too. CD player opens and seems to run fine, but I get no sound either from the CD or from RealPlayer when viewing the news on-line. The speakers are fine (they work on my other machines). I'm not sure what sort of soundcard it is, as I cannot find anywhere on the board to tell me (if it's underneath, then thanks to Compaq, without taking the whole mobo out...

Again, thanks for your help and to everyone else.

PS. I'm installing Ubuntu on a friend's computer and am quite impressed by how fast it runs on a PII, 350mhz, 128M RAM. The sound problem is the ONLY problem I've come across, and apt-get is great  - this from a Mandrake user :)[/QUOTE]

---

### Post by 4ebees on 2005-01-26
[QUOTE=jamaas]Silly question here, I'm having the same problem, how do I check the bios to see where the sound card is connected?

Thanks

Jim[/QUOTE]

If using a compaq, press F10 at start up. If another pc, you will see the options come up at boot - I think it's usually 'delete' - anyone can correct me on that :)

The best thing to do is just watch the boot screen and you'll see the options provided.

Someone may be able to direct you to a good "BIOS settings" site (have a google around). 

Just remember - [COLOR=DarkRed]REMEMBER WHAT YOU DID[/COLOR] - and be careful. It's ***_[COLOR=DarkRed]best[/COLOR]_* **to get someone who knows, or do some careful reading first.

---

### Post by jamaas on 2005-01-26
Thanks,

still no luck, I can't find anything in the bios that tells me where it is located.  This is a very new 915 intel chipset motherboard and the bios does not seem to give that sort of information.  Any other way to do it?

Thanks

Jim


[QUOTE=4ebees]If using a compaq, press F10 at start up. If another pc, you will see the options come up at boot - I think it's usually 'delete' - anyone can correct me on that :)

The best thing to do is just watch the boot screen and you'll see the options provided.

Someone may be able to direct you to a good "BIOS settings" site (have a google around). 

Just remember - [COLOR=DarkRed]REMEMBER WHAT YOU DID[/COLOR] - and be careful. It's ***_[COLOR=DarkRed]best[/COLOR]_* **to get someone who knows, or do some careful reading first.[/QUOTE]

---

### Post by 4ebees on 2005-01-26
[QUOTE=jamaas]Thanks,

still no luck, I can't find anything in the bios that tells me where it is located.  This is a very new 915 intel chipset motherboard and the bios does not seem to give that sort of information.  Any other way to do it?

Thanks

Jim[/QUOTE]

Jim,

If I read you correctly, you're saying that you've managed to get into the BIOS, no?

If not, have a quick look at these sites:

[http://www.cyberwalker.net/faqs/reinstall-reformat-winxp/enter-BIOS.html](http://www.cyberwalker.net/faqs/reinstall-reformat-winxp/enter-BIOS.html)

[http://aroundcny.com/technofile/texts/tec020203.html](http://aroundcny.com/technofile/texts/tec020203.html)

If you have managed to get into the BIOS, there **will ** be a place that identified the IRQ's and assigned components, particularly on something so new. The old Compaq BIOSs had very limited modification possibilities. My P4, for instance, lets me play to my hearts content, and even wreck my pc if I wish :)

For more specific information, you're going to have to look for a site that shows detailed information about your system - or someone here who has first hand knowledge.

Sorry I can't help you with more specific info at present, but if you can find a site with the requisite info, let me know and I'll see if I can help further. 

The problem is having to know exactly what *you* are looking at, before I can know how best to advise you.

---

### Post by sputnik on 2005-01-26
[QUOTE=LongTooth]Looks like plenty of sound problems with Ubuntu. I too have sound problems. My set up: 500 MHz PIII with 128Mg of ram. I have an onboard sound chip but currently have installed a ISA SB16 sound card. Neither works. I have disabled the intergrated sound. So that can't be the problem. I've tried both without success. I ran Alsaconf. It goes through it's routine and says it configured. Still no sound. I have done some digging and this is what I've come up with. I don't have a mixer that I can use. My results of Whereis: 

longtooth@ubuntu ~ $ whereis alsamixer
alsamixer: /usr/bin/alsamixer /usr/share/man/man1/alsamixer.1.gz
longtooth@ubuntu ~ $ sudo /usr/bin/alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
longtooth@ubuntu ~ $


I can't get it to open using any combinations. alsamixer, /user/bin/alsamixer, sudo alsamixer, or sudo /usr/bin/alsamixer.

So I thought I'd uninstall and reinstall it. Here is what I got: 

longtooth@ubuntu ~ $ sudo apt-get remove alsamixer
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package alsamixer
longtooth@ubuntu ~ $ whereis alsamixer

When I open the Volume control under Applications > Multimedia > Volume control I receive this error message: Sorry, no mixer elements and/or devices found. So it looks like my card is not detected plus I've no mixer. Or am I wrong? 

This is a card that worked with Slackware 10.0 and SuSE Pro 9.1. Where to go now? Can anyone point me in the right direction? Any assistance would be greatly appreciated. Thanks.[/QUOTE]
 Try this thread [http://www.ubuntuforums.org/showthread.php?t=1805](http://www.ubuntuforums.org/showthread.php?t=1805) for some possible answers to Sound blaster  isa cards.  May need to use isapnp.

---

### Post by maiki_desu on 2005-01-27
i tried the acpi_irc_isa=7 fix to menu.lst, and it seemed to work at first.
  i got sound at the welcome/login screen, but once i'm logged in there is no sound.

i have a C-Media PCI CMI8738
running ubuntu warty 4.1

any ideas?

---

### Post by tjz on 2005-01-29
Another sound problem:

Running gaim alone, it gives me acoustic feedback, but when rythmbox is running the gaim sounds are gone

any way to have both at the same time?

---

### Post by math192 on 2005-01-29
I see some people are having sound problems; I also see that some people have fixed the porblem using the following fix.

[I]add acpi_irq_isa=7 to the default kernel options line in /boot/grub/menu.lst... for example

# kopt=root=/dev/hda7 ro acpi_irq_isa=7[/I]

 Good Jorb guys! I'm trying to follow along, but I'm not sure I understand what's going on. Why should this fix it? What does it do? What do I do to modify it for my particular machine? It seems like we're resolving an IRQ conflict. Anyone know how to do an IRQ lookup unber linux? Is it as simple as choosing one that's not already in use? How about the ISA part. Is that indicating an EISA card? Will it not work for a PCI sound card? 

Please provide some details and background. Thanks much.  ](*,)

---

### Post by cronos01101x5 on 2005-03-01
ok none of that worked for me..... soo i am opting for installing the driver for my soundcard.... although... i don't understand the install instructions.......... help :P

I need a translator!! hehehe very new to Linux....total newb

also.... should i even install this????

[B][COLOR=Navy][SIZE=2]
Linux OSS driver for C-Media audio codec (CMI9738, CMI9739) v0.41

Notes:
1. This version implements GPIO on/off when active/disactive the driver which used for Mitac.

Features:
1. South Bridge: Intel ICH2/ICH4/ICH5, SiS 7012/7018, VIA 8233/82686, ALI 5451, nVidia nForce, AMD 8111.
2. Full-duplex and multiple applications playback and recording.
4. 16 bits 2/4/6 channels mono/stereo playback.
5. 16 bits stereo recording.
6. Support phone jacks configuration.
7. PCM SPDIF IN/OUT (CMI9739 only, recording only support 48 KHz).
8. Support AC3 S/PDIF out ((CMI9739 only).
9. Support analog hardware copy to rear channel.
10.Support xear mode to swap front and surround speakers output.
   For PCCHIPS LCD PC, you should change the following codes in cmaudio.h:

        // For PCCHIPS LCD PC
        #define FORCE_LINEINASREAR_MODE 1
        #define FORCE_XEAR_MODE 1

        //#define FORCE_LINEINASREAR_MODE 0
        //#define FORCE_XEAR_MODE 0

Known issues:
1. This driver only tested on RedHat 7.3.
2. /dev/sequencer is not supported.
3. In RedHat 8.0, gmix can not select recording source correctly.
   Please using aumix.


Installation:
For driver installation, please follow below steps. 

Step 1. Unzip source code
        tar xzf cmaudio-041.tar.gz

Step 2. Turn on sound support (soundcore module)

Step 3. Complied source code
	make
	make install

Step 4. Edit your /etc/modules.conf or conf.modules depending on the Distribution
        alias sound-slot-0 cmaudio    
        post-install sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -L >/dev/null 2>&1 || :
        pre-remove sound-slot-0 /bin/aumix-minimal -f /etc/.aumixrc -S >/dev/null 2>&1 || :

Step 5. reboot your machine



Phone Jacks Configuration:
We provide a console mode program, cmconfig.c, in order to let you change jacks' configuration.
please follow below steps.

Step 1. Compiled source code, the source code is also in cmaudio-041.tar.gz.
        cc -o cmconfig cmconfig.c

Step 2. Execute and change the settings
        ./cmconfig
[/SIZE][/COLOR][/B]

---

### Post by cronos01101x5 on 2005-03-01
uh.... sorry about the size of the text on the previous post..... having some font issues here :P

---

