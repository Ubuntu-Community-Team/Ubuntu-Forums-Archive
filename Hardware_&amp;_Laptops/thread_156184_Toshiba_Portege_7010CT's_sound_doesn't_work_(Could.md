---
title: "Toshiba Portege 7010CT's sound doesn't work (Could be ESS Maestro chip)"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by FSO on 2006-04-06
The sound has worked such a well in Debian with kernel 2.4.*. I got tired to Debian's old packages, and I installed ubuntu, but sound didn't work. In /etc/modules there is snd_cs8427, but it looks like it is not the right one. How ever it's could be ISA-chip because lspci doesn't find it. I know I should have written up the correct modules and settings in Debian, but i didn't :(

---

### Post by FarEast on 2006-04-07
Hi;) ,
Can you detect the sound chip by executing 'lspnp' ?

---

### Post by Emmanuel_uk on 2006-04-18
Hi, same problem with mandriva 2006. (kernel 2.6.12 something)
No listing with lspci
I believe the card is compliant with Standards Sound Blaster 16/Pro, Microsoft WSS 1.0/2.0

What are your settings in the BIOS for the card?

I believe it is a maestro chip but (on a 7020CT) it is funny there is also
a Yamaha 3D OPL3-SA3  around (for a 7010CT)
[http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAP701](http://linux.toshiba-dme.co.jp/linux/eng/spec.php3?model=PAP701)

Also see
[http://linux.toshiba-dme.co.jp/linux/eng/qa/others/02874.htm](http://linux.toshiba-dme.co.jp/linux/eng/qa/others/02874.htm)
where
soundcore
sound [opl3sa2 mpu401 ad1848]

Here are the sound settings in the BIOS:
WSS I/O 530H
SB I/O 220H
Synth I/O 388H
IRQ 5
Play DMA 1
Rec DMA 0
Ctrl I/O 370H
MIDI 330H

Here is what I put in my /etc/modules.conf file
# ALSA
alias snd-card-0 opl3sa2
options opl3sa2 wss_port=0x530 sb_port=0x220 irq=5 dma1=1 dma2=0 port=0x370
midi_port=0x330
# OSS - from samples on the page about Yamaha options
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

and user was told to try ymfpci driver

Another post
<<I was never able to get opl3sa2 to work using ALSA, so I used the kernel
sound drivers and now have sound working. On my Protege 3020CT I needed
to add 'append="opl3sa2=0x370,5,1,0,0x530,0x330"' in lilo.conf to make it
work.>>

Nothing leading me to the full answer yet but see as well
[http://groups.yahoo.com/group/linux-on-portege/](http://groups.yahoo.com/group/linux-on-portege/)

I do not have the laptop with me to try anything, but was going to
recompile kernel and add whatever is needed (to also try to optimise laptop)

---

### Post by Sef on 2006-04-18
This is what I did to get sound.

[http://ubuntuforums.org/showthread.php?t=160576]("http://ubuntuforums.org/showthread.php?t=160576")

---

### Post by Emmanuel_uk on 2006-04-18
[QUOTE=Sef]This is what I did to get sound.
[/QUOTE]
Thanks for the post.
However I believe we are dealing with an OSS driver not alsa.
So I am not sure how your thread is going to help us.

A bit more search confirmed it should be a yamaha chipset
not a maestro. For example
[http://www.nylaptops.com/specials/7010.pdf](http://www.nylaptops.com/specials/7010.pdf)

Another piece of info 
Toshiba default control IO is 538H (one of their website) for a 7010CT.
Some user quote using 370H. They might both work.

My plan
use lspnp
disable alsa and enable OSS instead
locate opl3sa2
append option to grub
recompile a kernel with the had-hoc modules

One can also try what is in
[http://72.14.207.104/search?q=cache:HmMi4wXcNDcJ:home.icequake.net/~nemesis/linuxlaptops/portege7010ct/7010/7010ct-sound.html+opl3sa2+7010+linux&hl=en&gl=uk&ct=clnk&cd=3](http://72.14.207.104/search?q=cache:HmMi4wXcNDcJ:home.icequake.net/~nemesis/linuxlaptops/portege7010ct/7010/7010ct-sound.html+opl3sa2+7010+linux&hl=en&gl=uk&ct=clnk&cd=3)

--------- quote -----------
Toshiba Portege 7010CT Sound with docking-station attached 

Yamaha OPL3-SA3 16 bit sound ship 
Tested with Linux Redhat 5.2 

Check BIOS Setup (default): 
    WSS I/O:                    0x530 
    SBPro I/O:                  0x220 
    Synt. I/O:                  0x388 
    WSS & SBPro & MPU401 Irq.:  5 
    WSS (Play) DMA:             1 
    WSS (Rec) & SBPro DMA:      0 
    Control I/O:                0x538 
    MPU 401 (MIDI I/F):         0x330 


By hand: needed Linux drivers: 
    insmod soundcore 
    insmod soundlow 
    insmod sound 
    insmod mpu401 
    insmod ad1848 
    insmod opl3 io=0x388 
    insmod opl3sa2 io=0x538 mss_io=0x530 irq=5 dma=0 dma2=1 mpu_io=0x330 


Update the following files to automatically load the above modules 
during startup: 
    /etc/conf.modules: 
        alias sound opl3sa2 
        alias midi opl3 
        options opl3 io=0x388 
        options opl3sa2 io=0x370 mss_io=0x530 irq=5 dma=0,1 mpu_io=0x330 


    /etc/sysconfig/soundcard 
        CARDTYPE=OPL3_SAX 


Tested applications: 
    cdplay 
    xmixer 
    xplaycd 


--------- unquote ---------

---

### Post by Emmanuel_uk on 2006-04-19
Ok, here goes the easy solution
(this is under mandriva 2006 but you can / have probably do it / download
sndconfig)

check aumix settings + speaker volume wheel side of laptop next to floppy
start a terminal
su / sudo
run sndconfig
choose the yamaha opl3sa2

and that is it
sound works

(tried under icewm, not sure under KDE or gnome, and
how this will go with artsd, alsa etc)

sndconfig is for old cards (similar in principle to alsaconfig)


PS: Can you change display contrast etc?
Does any of the Fn key works?
I can toggle the display to external
Not sure about energy saving or reading battery level

---

### Post by FSO on 2006-04-22
w00t! I got the sound working with that Yamaha-module. Huge thanks to Emmanuel_uk! I am going to build a mile tall golden statue for you!

Fn-key does the usual things, it can change contrast and pc speaker volume. I have not tried the external monitor yet.

---

### Post by Emmanuel_uk on 2006-04-22
Am going to blush...
Tell you what, am happy to help.
What you can do now is fill a hardware compatibility thingy for Ubuntu.

Also if you do not mind, in [www.linuxquestions.org](www.linuxquestions.org)  (HCL tab)
in a few weeks time there will be an entry for the 7010CT
can you input in there your use of ubuntu?

Found sound skips in icewm but not in windowsmaker BTW
(for some people it is a pcmcia issue, not here)

It is the start of a 7010CT club  ;)

You know there is no driver (only a project) for the mpgeg II decoder
of the PC

---

### Post by Emmanuel_uk on 2006-04-24
FSO, if you ever manage to get dvd playing the onboard mpeg II decoder can you please let me know?

wine + [http://home.icequake.net/~nemesis/linuxlaptops/toshiba_dvd/](http://home.icequake.net/~nemesis/linuxlaptops/toshiba_dvd/)
(I suppose)

or
[http://home.icequake.net/~nemesis/linuxlaptops/toshiba_dvd/cinemaster/](http://home.icequake.net/~nemesis/linuxlaptops/toshiba_dvd/cinemaster/)
points to
[http://www.cifelli.com/support/cifePEG/c3.x/98-ME-2K-XP/30Installer.zip](http://www.cifelli.com/support/cifePEG/c3.x/98-ME-2K-XP/30Installer.zip)
aka DVD Player 1.9 and updated drivers 
I suppose this might work under wine

I will not have time to test for a while

The best I could do was
single mode (boot)
then
mplayer dvd://1 -framedrop -vc sound=30 -cache 8192 -vo vesa
(disable zoom option in /etc/mplayer.conf or sthg like that helps)

---

### Post by FSO on 2006-04-29
The hard disk got broken, and it is not clever to buy a new one to such a old laptop. I think I must now search for a new (=used) laptop. Maybe I should thought when I bought the Toshiba that getting reliable laptop for 50e is not so easy.

I don't have a dvd drive in my laptop, so the I didn't have possibility to use the decoder, but how ever I just noticed that it exists.

---

### Post by Emmanuel_uk on 2006-04-29
I am sorry to hear that. I am afraid the advice is yes get a new old pc.
Saying that, it is a such a nice looking good machine so you could hold to it until
you find a 5-10 £ HD

---

### Post by fparri on 2006-07-04
[QUOTE=FSO]w00t! I got the sound working with that Yamaha-module. Huge thanks to Emmanuel_uk! I am going to build a mile tall golden statue for you![/QUOTE]
You mean you used sndconfig? Strange, I couldn't find in in my Ubuntu Dapper... :(

---

