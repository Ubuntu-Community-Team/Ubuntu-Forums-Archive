---
title: "thinkpad 600 sound for the n00b!"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by thefamousnomo on 2006-01-20
hello people

thanx to the generosity of the forum users, i have overcome most of the probs i have encountered, detailed in [http://ubuntuforums.org/showthread.php?t=116155](http://ubuntuforums.org/showthread.php?t=116155).

for what its worth, fixes as follows -

 - video / resolution: ran "sudo dpkg-reconfigure xserver-xorg" and changed default depth to "16". i believe that if you change to

Section "Screen"
Identifier "Default Screen"
Device "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
Monitor "Generic Monitor"
DefaultDepth 16

in the /etc/X11/xorg.conf file, you are happy too!

 - wireless config hanging: when trying to configure the sound i added "acpi=off pnpbios=off" to the /boot/grub/menu.lst file, and disabled "quick boot" in the bios. i was then able to configure my wireless card and must say it works a treat! it is a "belkin wireless g notebook network card" and works out the box!

 - sound: after following the above steps and adding "cs4232 io=0x530 irq=5 dma=1 dma2=3 mpuirq=10" to /etc/modules file i have made some progress i believe! i no longer have a cross on the sound icon in the top right hand corner or suffer the "no sound device detected" error messages,

**but**

i still have no sound, and there is no soundcard in the drop down menu in "preferences>sound". bearing in mind im still very much a n00b with regard to linux in general (linux handbook in post!), how can i get this sound configured?

thanx again for all previous help and i claim no credit for any of the fixes above, just detailing what worked for me!

thanx

---

### Post by thefamousnomo on 2006-01-30
well, despite trying to drive some very helpful people from the #ubuntu irc to this thread i have had no more help as you can see!

i hope that the resolution and wireless points may help out someone, even though they are available elsewhere in the forum.

:cry:

---

### Post by mips on 2006-01-30
[http://www.ubuntuforums.org/showthread.php?t=31290](http://www.ubuntuforums.org/showthread.php?t=31290) & [http://panopticon.csustan.edu/thood/tp600lnx.htm](http://panopticon.csustan.edu/thood/tp600lnx.htm) 
To make things a bit clearer read the part about RESOURCES !!!

[http://www.thinkwiki.org/wiki/ThinkWiki](http://www.thinkwiki.org/wiki/ThinkWiki)   [http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_ThinkPad_600](http://www.thinkwiki.org/wiki/Problem_with_broken_sound_on_ThinkPad_600)

---

### Post by davinci on 2006-01-31
I can't provide any further assistance, than I have  already given in [this thread]("http://ubuntuforums.org/showthread.php?t=96240"), but i will repeat the iportant points.

1) Enter the bios at startup and turn off fast boot
2) edit /boot/grub/menu.lst
my boot parameters are: pci=noacpi pci=usepirqmask vga=790 ro quiet

3) edit /etc/modules 
add line: snd-cs4236

4) edit /etc/modprob.d
add line: options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0

I had no success with the snd_4232 module too!

My thinkpad 600 has sound, wireless network and eth0 network. Acpi works and it is quite fast (after I turned off lots off unneeded services and compiled a custom kernel). So it can be done. Don't give up. And give us info, so we can provide further help.

---

### Post by thefamousnomo on 2006-01-31
[QUOTE=davinci]I can't provide any further assistance, than I have  already given in [this thread]("http://ubuntuforums.org/showthread.php?t=96240"), but i will repeat the iportant points.

1) Enter the bios at startup and turn off fast boot
2) edit /boot/grub/menu.lst
my boot parameters are: pci=noacpi pci=usepirqmask vga=790 ro quiet

3) edit /etc/modules 
add line: snd-cs4236

4) edit /etc/modprob.d
add line: options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0

I had no success with the snd_4232 module too!

My thinkpad 600 has sound, wireless network and eth0 network. Acpi works and it is quite fast (after I turned off lots off unneeded services and compiled a custom kernel). So it can be done. Don't give up. And give us info, so we can provide further help.[/QUOTE]

1. done
2. my boot parameters are '/boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash pnpbios=off acpi=off'. this allowed me to use wifi card, but will change to yours and note (if) any issues.
3. my modules line is 'cs4232 io=0x530 irq=5 dma=1 dma2=3 mpuirq=10'. this is the only advice that i have been offered that has bore any fruit at all! anything else displays red cross on volume icon (top right). although i can adjust volume there is no default sound card in *preferences>sound*. i will change to yours and note (if) any issues.
4. i dont have an 'etc/modprob.d' file! i have a 'modprobe.d' dir... should i create one?!?!?

let me know about 4 man and ill give it a try!

thanx again people!

---

### Post by davinci on 2006-01-31
sorry about 4. 

add the line to /etc/modprobe.d/alsa-base.

or just type in your terminal:

modprobe snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0

if the module loads then things get interesting, if not ... well. 
Check with:

lsmod

---

### Post by gotaserena on 2006-02-01
Unless someone was playing with your irqs and dmas using the PS2.EXE utility, your settings for the sound card should be as davinci posted. You should also remember that changes may not be noticed immediately by gnome's volume control. You should try alsamix from the control line first to unmute the channels.

---

### Post by thefamousnomo on 2006-02-01
thanx for all your help people, think im close!

modules all loaded no prob on startup, no red cross ( :D ), default sound card is c4237b, sounds on event now play, but still no sound!!!!

cant seem to find alsamix either!!!

one last time d00ds, feel it in my bones!

thanx

---

### Post by davinci on 2006-02-01
as gotaserena stated use:

alsamixer

unmute and turn up the volume on all channels


Just to make sure also check the BIOS volume control:
Press Fn + Page up     and repeat until the desired volume level is reached

---

### Post by thefamousnomo on 2006-02-02
[QUOTE=davinci]as gotaserena stated use:

alsamixer

unmute and turn up the volume on all channels


Just to make sure also check the BIOS volume control:
Press Fn + Page up     and repeat until the desired volume level is reached[/QUOTE]

:cry: 

now when the module loads at startup all i get is a very high pitched screeching sound, very similar to feedback! im thinking hardware fault but it worked fine with win98se...

any ideas?

thanx

---

### Post by davinci on 2006-02-02
Did you turn up the Mic Volume too? This way I am able to get a very nice feedback sound too ....

---

### Post by Jackal82 on 2006-02-02
Yeah!
Thanks!
Now sound works, I just did everything you told.

However, first I wrote "esd" on terminal. Sound might have worked already though.

---

### Post by thefamousnomo on 2006-02-03
[QUOTE=gotaserena]alsamix[/QUOTE]

although i really appreciate the help, please understand that being new to ubuntu and linux in general this is frustrating! thanks for the correction davinci. no offence gotaserena!

[QUOTE=davinci]
unmute and turn up the volume on all channels[/QUOTE]

this was what you said, this was what i did! tried remuting the mic channels but didnt realise that it would take a restart to apply changes. didnt realise that there was an onboard mic, or that the speakers would be react in this way.

[QUOTE=jackal82]Yeah!
Thanks!
Now sound works, I just did everything you told.

However, first I wrote "esd" on terminal. Sound might have worked already though.[/QUOTE]

1. check the title of the thread, im a *n00b*
2. these are help forums, these comments dont help
3. esd? hope your wrong or my hair is missing for nothing
4. go and 'help' someone else

everyone has been really helpful this far (not jackal82) and i really do appreciate it. davinci, it must be as much a test of your patience as a learning curve for me. thanx again.

status: feedback stopped, no sound. in preferences>multimedia systems selector when i try to test alsa driver it shows error 'unable to construct a test pipeline'!

any ideas or sarcastic comments? remember (jackal82) you were not born with your knowledge, someone somewhere had to help you once. i would like to meet you and try to 'help' you be more patient.

thanx

---

### Post by Jackal82 on 2006-02-03
[QUOTE=thefamousnomo]
1. check the title of the thread, im a *n00b*
2. these are help forums, these comments dont help
3. esd? hope your wrong or my hair is missing for nothing
4. go and 'help' someone else

everyone has been really helpful this far (not jackal82) and i really do appreciate it. davinci, it must be as much a test of your patience as a learning curve for me. thanx again.

any ideas or sarcastic comments? remember (jackal82) you were not born with your knowledge, someone somewhere had to help you once. i would like to meet you and try to 'help' you be more patient.

thanx[/QUOTE]

Sorry. I was just happy to get my ibm TP600 sound working. No hard feelings.

ok, this is all what I did:
I have kernel: 2.6.12-10.26 Have you updated it?

1. Bios fast boot off
2. /boot/grub/menu.lst "acpi=off pnpbios=off"
3. /etc/modules "snd-cs4236"
4. /etc/modprobe.d/alsa-base 
"options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0"

5. alsamixer
unmute and turn up the volume on all channels

6. restart

7. command "esd" activates the sound card

...and then I put a audio cd in and.. listen to music. :)

---

### Post by thefamousnomo on 2006-02-03
[QUOTE=Jackal82]Sorry. I was just happy to get my ibm TP600 sound working. No hard feelings.

ok, this is all what I did:
I have kernel: 2.6.12-10.26 Have you updated it?

1. Bios fast boot off
2. /boot/grub/menu.lst "acpi=off pnpbios=off"
3. /etc/modules "snd-cs4236"
4. /etc/modprobe.d/alsa-base 
"options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0"

5. alsamixer
unmute and turn up the volume on all channels

6. restart

7. command "esd" activates the sound card

...and then I put a audio cd in and.. listen to music. :)[/QUOTE]

jackal82, i am sorry for that, i took you totally the wrong way! i didnt realise you were working through the same issues, i thought you were mimicking / ripping me! i apologise unreservedly! :-# 

command esd does nothing!!! :neutral:  sudo esd anyway, put in a cd and get message to check permissions. cannot open default alsa. sorry, at work the now, this is from memory.

again jackal82, i was out of line, past flame-forum syndrome! i hate to ask a question, i know! not sure about updated kernel, how do i do this? the word kernel frightens me! bad experiences with this early in my ubuntu career!

thanx all!

---

### Post by Jackal82 on 2006-02-03
[QUOTE=thefamousnomo]
again jackal82, i was out of line, past flame-forum syndrome! i hate to ask a question, i know! not sure about updated kernel, how do i do this? the word kernel frightens me! bad experiences with this early in my ubuntu career!
thanx all![/QUOTE]

No problem, dude. The word Ubuntu mens "humanity to others". :) 

Updating the kernel.

I assume you have the default kernel 2.6.12-9-386. to check that, just write "dmesg" in terminal. And read the first line: Linux version...

Then download [http://fi.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb](http://fi.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb)

Place it to your desktop. If you have no network then use USB flash memory or something..

Then open terminal and command: **sudo dpkg -i linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb**

after the installation, restart and do everything (1. Bios fast boot off
2. /boot/grub/menu.lst "acpi=off pnpbios=off"..... etc) again to get the sound working.

---

### Post by thefamousnomo on 2006-02-04
[QUOTE=Jackal82]No problem, dude. The word Ubuntu mens "humanity to others". :) 

Updating the kernel.

I assume you have the default kernel 2.6.12-9-386. to check that, just write "dmesg" in terminal. And read the first line: Linux version...

Then download [http://fi.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb](http://fi.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb)

Place it to your desktop. If you have no network then use USB flash memory or something..

Then open terminal and command: **sudo dpkg -i linux-image-2.6.12-10-386_2.6.12-10.26_i386.deb**

after the installation, restart and do everything (1. Bios fast boot off
2. /boot/grub/menu.lst "acpi=off pnpbios=off"..... etc) again to get the sound working.[/QUOTE]

shes alive..... ALIVE!

**but**

after installing the upated kernel and restarting i found i was booting into xubuntu. startup hung on 'configuring network'. tried this half a dozen times, including adding the to the boot line acpi=off pnpbios=off. still wouldnt start up.

entered grub on boot and tabbed to my original kernel version, added the acpi=off pnpbios=off and started up with sound!

any ideas why this is the case? the new kernel doesnt seem to like my network device or want to start up, but my old kernel (which was the same as it was before installing the new kernel) booted, now with sound.

do certain base components get updated throughout all installed kernel versions? if so, could i have just updated this component instead of installing a whole new kernel, which i cant boot into anyway?

think ill have to edit the menu.lst to default my old kernel with added items.

what do you guys think?

thanx jackal82 and the rest of you guys for getting me this far!

---

### Post by thefamousnomo on 2006-02-09
hello people

cmon guys, getting it working is only half the fun, why did this work the way it did?

any ideas? thanx again guys!

---

### Post by Jackal82 on 2006-02-09
[QUOTE=thefamousnomo]hello people

cmon guys, getting it working is only half the fun, why did this work the way it did?

any ideas? thanx again guys![/QUOTE]

Hi!

I had exactly same problems with my Ubuntu. Startup hung on 'configuring network' for about a minute or two, but I was able to start though. 

I had huge problems with my pcmcia wlan-card and I took a risk installing Ubuntu Dapper (6.04) which is still a beta version. Now everything works; I have kernel 2.6.15-14, startup does not hung on anymore and sound works too. And installing RaConfig 2500 + compiling drivers my wlan worked too, but it had nothing to with version 6.04 I believe.

---

### Post by thefamousnomo on 2006-02-10
hello people

well it works anyway (just made the old kernel the default in grub/menu.lst and added the magical acpi=off pnpbios=off) thanx to all your help, and kudos to jackal82 who gave me the last piece of this puzzle.

would still like to know if there is just a component or two i could have updated instead of a whole kernel but for the meantime, im more than happy!

thanx again!

---

