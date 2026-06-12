---
title: "Thinkpad 600E Sound - Why do no posts solve my problem?"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by becatlibra on 2006-03-08
It seems this is a common issue - However none of the solutions have worked for me.

I'll start out by saying I'm not new to linux. I have been a user for around 8 years and manage a few linux servers at my office. I have used many distros and currently am using debian, slackware and rh9. I wanted to give my wife my old thinkpad 600e (which I had slackware on) and thought I'd put ubuntu on it. I liked the look and thought it might be easier for her to use.

I have been trying for 2 days to get the sound going (and I thought the pain would be the wireless PCMCIA card.) I have made it work before in RH9 and slackware. I can't seem to get it going here.

I tried the blacklist/alsa-base mod without any real results. The volume icon in the 'systray' does not have an x through it but the sound does not function (testing with an audio cd.) The System>Pref>Multimedia Sys Select tells me "Failed to construct test pipeline for '<insert soundsystem name here>'" I have tried ESD,OSS and Alsa. Currently I have the setup suggested where I have blacklisted and then modified alsa-base. I have pnpbios=no acpi=off and pci=noacpi in my menu.lst The acpi was set to force due to someone elses suggestion.

This post was the most helpful. 

===>

Known problem with the TP600E. The soundcard is incorrectly identified as CS462x.

There are plenty of web pages out there describing solutions to this. But here is the Reader's Digest version:

1. Blacklist the incorrect sound card in /etc/hotplug/blacklist. Add lines for

snd-cs46xx
cs46xx

as written above - with the xx's

2. Add the following lines into /etc/modprobe.d/alsa-base

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

NOTE: When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'.

3. Add the line

snd-cs4236

to the file /etc/modules

Reboot.

Also important: During power up, if you press F2 (I think), you get into change the config. In this you need to make sure that the Fastboot option is *disabled*.

If you are still having no success: try adding 'acpi=off pnpbois=off' at the end of the kernel boot params. Press 'esc' during Grub countdown and select 'e' to edit the boot command and add these to the end. I need these to allow my Xircom PCMCIA ether card to work.

Regards

Warren

===>

I replied to it but then realized it was really in the wrong area so I started a new thread here

I can't afford to spend any more work hours on this and I can't surprise her if I work on it at home.

SOMEONE PLEASE help. I can post ANY info requested.

Regards,

Benjamin

---

### Post by grumpymole on 2006-03-09
Benjamin,

Can you post the output of > lsmod | grep snd here?

Also, the default volume setting is zero until you adjust it.  I know it sounds silly, but check whether you can adjust your sound volume at all.  Also, check the system sound volume using the blue Fn key and PgUp.  Hit that a few times and see if you get any beeps.

Regards

Warren

---

### Post by becatlibra on 2006-03-09
Thank you for your response Warren.  I was hoping you'd get back with me :]

Okay - I am not at the laptop now.  I will have to check later on the lsmod.  As for the volume, using alsamixer the sound is up.  I hear what you are saying about the system volume but I forgot to put in the ibm key module so those keys don't currently work.

The thing is that the card isn't able to be used by the system currently.  When I try to "test" it in the Ubuntu config it tells me it is unable to make a pipe (as I stated in my previous post.)  Also the cdplayer won't even PLAY the cd.  It see's it and gets the cd info from CDDB but then, when play is pressed, it is unable to actually start.  It just sits there and does nothing.

I found an interesting article about these machines while trying to help someone with a T40 ethernet/wireless problem.  I am going to try this solution and see if I can make it work: 

[http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode](http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode)

I will post here later to let everyone know and if it doesn't work I'll post the lsmod info.  

Thanks again for your help

Regards

Benjamin

---

### Post by becatlibra on 2006-03-09
Okay so that didn't fix it either.

here is the output of lsmod | grep snd:

snd_opl3_lib           10624  0
snd_hwdep               8896  1 snd_opl3_lib
snd_cs4236_lib         15840  0
snd_mpu401_uart         7296  0
snd_rawmidi            24704  1 snd_mpu401_uart
snd_seq_device          8460  2 snd_opl3_lib,snd_rawmidi
snd_cs4231_lib         25312  1 snd_cs4236_lib
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_cs4236_lib,snd_cs4231_lib,snd_pcm_oss
snd_timer              24164  3 snd_opl3_lib,snd_cs4231_lib,snd_pcm
snd                    54884  11 snd_opl3_lib,snd_hwdep,snd_cs4236_lib,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_cs4231_lib,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_cs4231_lib,snd_pcm

now - after changing things back to the way you suggested initially - the volume icon has an X through it.

here is my /etc/modprobe.d/alsa-base file just in case things should be arranged differently in there:

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7
# Load optional modules above their base modules
install snd modprobe --ignore-install snd && { modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 && { /lib/alsa/modprobe-post-install snd-emu10k1 ; modprobe --quiet snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx && { /lib/alsa/modprobe-post-install snd-via82xx ; modprobe --quiet snd-seq ; }
# Cause a script to be run after *-synth module initialization
install snd-emu8000-synth modprobe --ignore-install snd-emu8000-synth && /lib/alsa/modprobe-post-install snd-emu8000-synth
install snd-emu10k1-synth modprobe --ignore-install snd-emu10k1-synth && /lib/alsa/modprobe-post-install snd-emu10k1-synth
# Cause a script to be run after card driver module initialization
install snd-ad1816a modprobe --ignore-install snd-ad1816a && /lib/alsa/modprobe-post-install snd-ad1816a
install snd-ad1848 modprobe --ignore-install snd-ad1848 && /lib/alsa/modprobe-post-install snd-ad1848
install snd-ali5451 modprobe --ignore-install snd-ali5451 && /lib/alsa/modprobe-post-install snd-ali5451
install snd-als100 modprobe --ignore-install snd-als100 && /lib/alsa/modprobe-post-install snd-als100
install snd-als4000 modprobe --ignore-install snd-als4000 && /lib/alsa/modprobe-post-install snd-als4000
install snd-armaaci modprobe --ignore-install snd-armaaci && /lib/alsa/modprobe-post-install snd-armaaci
install snd-asihpi modprobe --ignore-install snd-asihpi && /lib/alsa/modprobe-post-install snd-asihpi
install snd-atiixp modprobe --ignore-install snd-atiixp && /lib/alsa/modprobe-post-install snd-atiixp
install snd-au1x00 modprobe --ignore-install snd-au1x00 && /lib/alsa/modprobe-post-install snd-au1x00
install snd-au8810 modprobe --ignore-install snd-au8810 && /lib/alsa/modprobe-post-install snd-au8810
install snd-au8820 modprobe --ignore-install snd-au8820 && /lib/alsa/modprobe-post-install snd-au8820
install snd-au8830 modprobe --ignore-install snd-au8830 && /lib/alsa/modprobe-post-install snd-au8830
install snd-azt2320 modprobe --ignore-install snd-azt2320 && /lib/alsa/modprobe-post-install snd-azt2320
install snd-azt3328 modprobe --ignore-install snd-azt3328 && /lib/alsa/modprobe-post-install snd-azt3328
install snd-ca0106 modprobe --ignore-install snd-ca0106 && /lib/alsa/modprobe-post-install snd-ca0106
install snd-cmi8330 modprobe --ignore-install snd-cmi8330 && /lib/alsa/modprobe-post-install snd-cmi8330
install snd-cmipci modprobe --ignore-install snd-cmipci && /lib/alsa/modprobe-post-install snd-cmipci
install snd-cs4231 modprobe --ignore-install snd-cs4231 && /lib/alsa/modprobe-post-install snd-cs4231
install snd-cs4232 modprobe --ignore-install snd-cs4232 && /lib/alsa/modprobe-post-install snd-cs4232
install snd-cs4236 modprobe --ignore-install snd-cs4236 && /lib/alsa/modprobe-post-install snd-cs4236
install snd-cs4281 modprobe --ignore-install snd-cs4281 && /lib/alsa/modprobe-post-install snd-cs4281
install snd-cs46xx modprobe --ignore-install snd-cs46xx && /lib/alsa/modprobe-post-install snd-cs46xx
install snd-darla20 modprobe --ignore-install snd-darla20 && /lib/alsa/modprobe-post-install snd-darla20
install snd-darla24 modprobe --ignore-install snd-darla24 && /lib/alsa/modprobe-post-install snd-darla24
install snd-dt019x modprobe --ignore-install snd-dt019x && /lib/alsa/modprobe-post-install snd-dt019x
install snd-echo3g modprobe --ignore-install snd-echo3g && /lib/alsa/modprobe-post-install snd-echo3g
install snd-emu10k1x modprobe --ignore-install snd-emu10k1x && /lib/alsa/modprobe-post-install snd-emu10k1x
install snd-ens1370 modprobe --ignore-install snd-ens1370 && /lib/alsa/modprobe-post-install snd-ens1370
install snd-ens1371 modprobe --ignore-install snd-ens1371 && /lib/alsa/modprobe-post-install snd-ens1371
install snd-es1688 modprobe --ignore-install snd-es1688 && /lib/alsa/modprobe-post-install snd-es1688
install snd-es18xx modprobe --ignore-install snd-es18xx && /lib/alsa/modprobe-post-install snd-es18xx
install snd-es1938 modprobe --ignore-install snd-es1938 && /lib/alsa/modprobe-post-install snd-es1938
install snd-es1968 modprobe --ignore-install snd-es1968 && /lib/alsa/modprobe-post-install snd-es1968
install snd-es968 modprobe --ignore-install snd-es968 && /lib/alsa/modprobe-post-install snd-es968
install snd-fm801 modprobe --ignore-install snd-fm801 && /lib/alsa/modprobe-post-install snd-fm801
install snd-fm801-tea575x modprobe --ignore-install snd-fm801-tea575x && /lib/alsa/modprobe-post-install snd-fm801-tea575x
install snd-gina20 modprobe --ignore-install snd-gina20 && /lib/alsa/modprobe-post-install snd-gina20
install snd-gina24 modprobe --ignore-install snd-gina24 && /lib/alsa/modprobe-post-install snd-gina24
install snd-gusclassic modprobe --ignore-install snd-gusclassic && /lib/alsa/modprobe-post-install snd-gusclassic
install snd-gusextreme modprobe --ignore-install snd-gusextreme && /lib/alsa/modprobe-post-install snd-gusextreme
install snd-gusmax modprobe --ignore-install snd-gusmax && /lib/alsa/modprobe-post-install snd-gusmax
install snd-harmony modprobe --ignore-install snd-harmony && /lib/alsa/modprobe-post-install snd-harmony
install snd-hda-intel modprobe --ignore-install snd-hda-intel && /lib/alsa/modprobe-post-install snd-hda-intel
install snd-hdsp modprobe --ignore-install snd-hdsp && /lib/alsa/modprobe-post-install snd-hdsp
install snd-hdspm modprobe --ignore-install snd-hdspm && /lib/alsa/modprobe-post-install snd-hdspm
install snd-ice1712 modprobe --ignore-install snd-ice1712 && /lib/alsa/modprobe-post-install snd-ice1712
install snd-ice1724 modprobe --ignore-install snd-ice1724 && /lib/alsa/modprobe-post-install snd-ice1724
install snd-indigo modprobe --ignore-install snd-indigo && /lib/alsa/modprobe-post-install snd-indigo
install snd-indigodj modprobe --ignore-install snd-indigodj && /lib/alsa/modprobe-post-install snd-indigodj
install snd-indigoio modprobe --ignore-install snd-indigoio && /lib/alsa/modprobe-post-install snd-indigoio
install snd-intel8x0 modprobe --ignore-install snd-intel8x0 && /lib/alsa/modprobe-post-install snd-intel8x0
install snd-interwave modprobe --ignore-install snd-interwave && /lib/alsa/modprobe-post-install snd-interwave
install snd-interwave-stb modprobe --ignore-install snd-interwave-stb && /lib/alsa/modprobe-post-install snd-interwave-stb
install snd-korg1212 modprobe --ignore-install snd-korg1212 && /lib/alsa/modprobe-post-install snd-korg1212
install snd-layla20 modprobe --ignore-install snd-layla20 && /lib/alsa/modprobe-post-install snd-layla20
install snd-layla24 modprobe --ignore-install snd-layla24 && /lib/alsa/modprobe-post-install snd-layla24
install snd-maestro3 modprobe --ignore-install snd-maestro3 && /lib/alsa/modprobe-post-install snd-maestro3
install snd-mia modprobe --ignore-install snd-mia && /lib/alsa/modprobe-post-install snd-mia
install snd-miro modprobe --ignore-install snd-miro && /lib/alsa/modprobe-post-install snd-miro
install snd-mixart modprobe --ignore-install snd-mixart && /lib/alsa/modprobe-post-install snd-mixart
install snd-mona modprobe --ignore-install snd-mona && /lib/alsa/modprobe-post-install snd-mona
install snd-mpu401 modprobe --ignore-install snd-mpu401 && /lib/alsa/modprobe-post-install snd-mpu401
install snd-msnd-pinnacle modprobe --ignore-install snd-msnd-pinnacle && /lib/alsa/modprobe-post-install snd-msnd-pinnacle
install snd-mtpav modprobe --ignore-install snd-mtpav && /lib/alsa/modprobe-post-install snd-mtpav
install snd-nm256 modprobe --ignore-install snd-nm256 && /lib/alsa/modprobe-post-install snd-nm256
install snd-opl3sa2 modprobe --ignore-install snd-opl3sa2 && /lib/alsa/modprobe-post-install snd-opl3sa2
install snd-opti92x-ad1848 modprobe --ignore-install snd-opti92x-ad1848 && /lib/alsa/modprobe-post-install snd-opti92x-ad1848
install snd-opti92x-cs4231 modprobe --ignore-install snd-opti92x-cs4231 && /lib/alsa/modprobe-post-install snd-opti92x-cs4231
install snd-opti93x modprobe --ignore-install snd-opti93x && /lib/alsa/modprobe-post-install snd-opti93x
install snd-pc98-cs4232 modprobe --ignore-install snd-pc98-cs4232 && /lib/alsa/modprobe-post-install snd-pc98-cs4232
install snd-pcsp modprobe --ignore-install snd-pcsp && /lib/alsa/modprobe-post-install snd-pcsp
install snd-pcxhr modprobe --ignore-install snd-pcxhr && /lib/alsa/modprobe-post-install snd-pcxhr
install snd-pdaudiocf modprobe --ignore-install snd-pdaudiocf && /lib/alsa/modprobe-post-install snd-pdaudiocf
install snd-pdplus modprobe --ignore-install snd-pdplus && /lib/alsa/modprobe-post-install snd-pdplus
install snd-portman2x4 modprobe --ignore-install snd-portman2x4 && /lib/alsa/modprobe-post-install snd-portman2x4
install snd-powermac modprobe --ignore-install snd-powermac && /lib/alsa/modprobe-post-install snd-powermac
install snd-pxa2xx-ac97 modprobe --ignore-install snd-pxa2xx-ac97 && /lib/alsa/modprobe-post-install snd-pxa2xx-ac97
install snd-rme32 modprobe --ignore-install snd-rme32 && /lib/alsa/modprobe-post-install snd-rme32
install snd-rme96 modprobe --ignore-install snd-rme96 && /lib/alsa/modprobe-post-install snd-rme96
install snd-rme9652 modprobe --ignore-install snd-rme9652 && /lib/alsa/modprobe-post-install snd-rme9652
install snd-s3c2410 modprobe --ignore-install snd-s3c2410 && /lib/alsa/modprobe-post-install snd-s3c2410
install snd-sa11xx-uda1341 modprobe --ignore-install snd-sa11xx-uda1341 && /lib/alsa/modprobe-post-install snd-sa11xx-uda1341
install snd-sb16 modprobe --ignore-install snd-sb16 && /lib/alsa/modprobe-post-install snd-sb16
install snd-sb8 modprobe --ignore-install snd-sb8 && /lib/alsa/modprobe-post-install snd-sb8
install snd-sbawe modprobe --ignore-install snd-sbawe && /lib/alsa/modprobe-post-install snd-sbawe
install snd-serialmidi modprobe --ignore-install snd-serialmidi && /lib/alsa/modprobe-post-install snd-serialmidi
install snd-serial-u16550 modprobe --ignore-install snd-serial-u16550 && /lib/alsa/modprobe-post-install snd-serial-u16550
install snd-sgalaxy modprobe --ignore-install snd-sgalaxy && /lib/alsa/modprobe-post-install snd-sgalaxy
install snd-sonicvibes modprobe --ignore-install snd-sonicvibes && /lib/alsa/modprobe-post-install snd-sonicvibes
install snd-sscape modprobe --ignore-install snd-sscape && /lib/alsa/modprobe-post-install snd-sscape
install snd-sun-amd7930 modprobe --ignore-install snd-sun-amd7930 && /lib/alsa/modprobe-post-install snd-sun-amd7930
install snd-sun-cs4231 modprobe --ignore-install snd-sun-cs4231 && /lib/alsa/modprobe-post-install snd-sun-cs4231
install snd-sun-dbri modprobe --ignore-install snd-sun-dbri && /lib/alsa/modprobe-post-install snd-sun-dbri
install snd-trident modprobe --ignore-install snd-trident && /lib/alsa/modprobe-post-install snd-trident
install snd-usb-audio modprobe --ignore-install snd-usb-audio && /lib/alsa/modprobe-post-install snd-usb-audio
install snd-usb-usx2y modprobe --ignore-install snd-usb-usx2y && /lib/alsa/modprobe-post-install snd-usb-usx2y
install snd-vx222 modprobe --ignore-install snd-vx222 && /lib/alsa/modprobe-post-install snd-vx222
install snd-vxp440 modprobe --ignore-install snd-vxp440 && /lib/alsa/modprobe-post-install snd-vxp440
install snd-vxpocket modprobe --ignore-install snd-vxpocket && /lib/alsa/modprobe-post-install snd-vxpocket
install snd-wavefront modprobe --ignore-install snd-wavefront && /lib/alsa/modprobe-post-install snd-wavefront
install snd-ymfpci modprobe --ignore-install snd-ymfpci && /lib/alsa/modprobe-post-install snd-ymfpci
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
# Added from [http://www.ubuntuforums.org/showthread.php?t=94414](http://www.ubuntuforums.org/showthread.php?t=94414)
alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1


Thanks again for all your help

Regards,

Benjamin

---

### Post by grumpymole on 2006-03-09
Benjamin,

Just to be sure: You have definitely turned off the FastBoot option in the BIOS?  

Regards

Warren

---

### Post by becatlibra on 2006-03-10
Warren,

Yep - I used to repair ALL models of thinkpads - all day.  I am very familiar with the BIOS in the 600 series - it is definately off.  Unless my wife or son changed it back - which I don't even think they know HOW to do.

-B

---

### Post by andycrofts on 2006-03-10
Hi. I just installed "Breezy badger" on a 600E for the first time. Sound and internet working fine.
Here's exactly what I did (Remember - the first Law of Engineering - if it's not written down, it never happened!!!)

1) start 600E with Ubuntu CD installed. a the boot prompt added info. so it looks like:
boot: linux pci=noacpi apm=noapm
2) go through whole install. Network picked up (didn't till I added the "apm=noapm" bit).
3) try CD. No sound.
4) Add to /etc/module a line :
        snd-cs4236
5) added to /etc/modules.d/sound (new file)
        options snd-cs4236 isapnp=0 port=0x530 cport=0x538 irq=5 fm_port=0x388 sb_port=0x220 dma1=1 dma2=0

** Note - all on one line. nano has nasty habit of messing up new lines, so use the  -w option, i.e., 
nano -w  /etc/modules.d/sound

6) sudo shutdown -h now  -- shut the thing off
7) Power off, then on, holding the F1 key.
8 ) select initialise from the bios menu that comes up, OK that. then select fastboot off. OK that. Then use the bios menu to restart.
Play a CD. Should have sound (use the "Fn" key with "PgUp" key to max).
Sound there, but quiet. Click on the loudspeaker sign at top right (on the menu bar).
Better, but not perfect.
Go Applications-->sound and Video--> volume control.
Wind the PCM up.
Almost there....
I found I also got a bit more thrutch out of it by selecting (in aforementioned Volume Control) Edit -> Preferences and tick "playback". Then wind that up till it distorts!

[ADDENDUM!!! Just found I can only play CD's in Sound Juicer - NOT CD player...Odd.....More work needed]

Hope that helps. I've been messing about with getting sound (to no avail) in SuSE 10 for ages (I got SuSE 9.3 working easily enough) and in desperation tried Ubuntu.

Floats my boat!!!!

-Cheers
-Andy

---

### Post by grumpymole on 2006-03-13
Benjamin,

Any luck yet?

From the lsmod output, it seems that the right module is being loaded.  The only other thing that I can think of is to check that when the machine boots, that acpi=off pnpbios=off are definitely being added to boot parameters.  I.e. you can see them in the kernel line after the GRUB countdown.  I re-installed my 600e with Flight 5 - the latest dapper - and I had a similar problem in that I was sure that they were there, but I couldn't get the sound going.  

BTW, Dapper is a lot faster than Breezy and if you are not going to be using the machine to edit your PhD due next week, then it is reasonably safe to install.

Cheers

Warren

---

### Post by SnowSparrow on 2006-03-31
The model number on my thinkpad says simply 600
:KS 
Here is how I got the sound to work
this worked both on Ubuntu Badger and on what i'm running now- Debian Testing Etch

Kernel is 2.6.15-1-486. 
I followed the instructions posted by Waikato LUG 
[http://www.wlug.org.nz/ThinkpadNotes](http://www.wlug.org.nz/ThinkpadNotes)

----Begin Waikato LUG wiki instructions --------
If you are running a Debian or Ubuntu-based system, add "snd-cs4236" to the /etc/modules file (create it if it doesn't exist) so that this module is automatically loaded on boot.

I have the following snippet in /etc/modprobe.d/sound:

options snd-cs4236 isapnp=0 port=0x530 cport=0x538 irq=5 \
 fm_port=0x388 sb_port=0x220 dma1=1 dma2=0

(should all be on one line).

Those are the default settings, but it's possible that your card is using different settings. If you have a windows partition on the laptop, you can boot into windows to run a utility to configure the soundcard (the ps2.exe file was in c:\windows\options\utility)

> rem the cs4232 0x530, irq 5, dma 0 1
> ps2 audio address 530
> ps2 audio irq 5
> ps2 audio sbaddress 220
> ps2 audio dma 0 1
> ps2 audio enable
> ps2 audioctrl address 538
> ps2 audioctrl enable

After rebooting into linux, my sound worked. (This was a 600E Thinkpad)

You should also go into the BIOS menu (hold down F1 on power-on), and disable "fast boot". Fast boot means that you are using a PNP? OperatingSystem, so the BIOS won't configure the hardware, assuming that the OS will. You should disable this so that the hardware is correctly initialised. Interestingly, my sound card worked even with "fast boot" on, until I re-installed Ubuntu on the laptop, when my sound stopped working. Changing this setting fixed it again.
---------End Waikato LUG instructions--------------------------------
I had a problem finding this solution on the web, so I'm going to add some keywords at the end of my post to help people find this soltion that works.
Hope no one minds
[B]Thinkpad 600 sound debian
thinkpad 600 sound ubuntu
thinkpad 600 sound linux[/B]

---

### Post by burnttrees on 2006-04-28
ok i have read the posts in this thread and followed them and after 45 minutes realized something i forgot from useing my own 600e when you start the system hold down the F1 key to get into the bios utility and then goto config and then click on Initialize this resets the system from experience the different distros have different ways of finding the info for the sound card and the different ways at times can scramble the sound card setting in the bios meening that it is not sb_port=0x220 (just as an example) any more but something different this is the only piece of hardware i have seen this problem with on the thinkpads 

i hope this helps i have looked at alot of forums about the sound card and i do not remember ever seeing anyone mention the initialize in the bios

---

### Post by Valhalla on 2006-04-28
I'm also trying to get the s ound working on my roommates thikpad 600.  I was trying to folow the directions to turrn off what I have heard described as both quick boot and fast boot in the bios, however, when I go into the menu, the initialise button is greyed out, and I can't select it.  Does anyone know a way around this?](*,)

---

### Post by fluxion on 2006-05-01
I've recently got sound working on my Thinkpad 600E, it required a slightly altered script from from ThinkWiki ([http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode](http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode)) and an addition to the pci blacklist. I'm running Xubuntu dapper, it works great on the 600E with 128Mb of ram. Steps taken to get sound working were:
(1) Add the following to '/etc/modprobe.d/blacklist'.
```
# snd_cs46xx doesn't work on thinkpad 600e
blacklist snd_cs46xx

```
(2) Change '/etc/rc.local' so it includes the sound chip enable and module parameter load as shown below.
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# enable sound chipset and load module

# Sound-via-pnp-script for Thinkpad 600E and possibly other computers with onboard
# CS4239/CS4610 that do not work with the PCI driver and are not recognized by the
# PnP code of snd-cs4236

# search sound card pnp device

for dev in /sys/bus/pnp/devices/*
do
  grep CSC0100 $dev/id > /dev/null && WSSDEV=$dev
  grep CSC0110 $dev/id > /dev/null && CTLDEV=$dev
done

# activate devices (Thinkpad boots with devices disabled unless "fast boot" is turned off)

echo activate > $WSSDEV/resources
echo activate > $CTLDEV/resources

# parse resource settings

{ read
 read bla port1
 read bla port2
 read bla port3
 read bla irq
 read bla dma1
 read bla dma2
 # Hack: with PnPBIOS: ports are: port1: WSS, port2: OPL, port3: sb (unneeded)
 #       with ACPI-PnP:ports are: port1: OPL, port2: sb, port3: WSS
 # (ACPI bios seems to be wrong here, the PnP-card-code in snd-cs4236.c uses the
 #  PnPBIOS port order)
 # Detect port order using the fixed OPL port as reference
 if [ ${port2%%-*} = 0x388 ]
 then
   # PnPBIOS: usual order
   port=${port1%%-*}
   oplport=${port2%%-*}
 else
   # ACPI: mixed-up order
   port=${port3%%-*}
   oplport=${port1%%-*}
 fi
 } < $WSSDEV/resources

{ read
 read bla port1
 cport=${port1%%-*}
} < $CTLDEV/resources

# load the module

echo "options snd-cs4236 port=$port cport=$cport fm_port=$oplport irq=$irq dma1=$dma1 dma2=$dma2 isapnp=0 index=0" > /etc/modprobe.d/snd-cs4236

modprobe snd-cs4236

# end of sound module load

exit 0

```

After the above script is run you should find a new file in '/etc/modprobe.d/' called 'snd-cs4236', with the detected sound card settings. I've found that it needs the script to run to enable the sound chip, using the modprobe options on their own does not work. This may not be the recommended method i.e. dynamically writing module parameters, but it works for me ;) 

PS If the above still doesn't work make sure you have set up appropriate bios settings using the DOS 'ps2.exe' utility and 'fast boot' is turned off.

---

### Post by sb73542 on 2006-05-02
Why does Ubuntu refuse to add support for alsaconf and ISA cards?  This is all that is really needed.  Even the 60MB Puppy Linux 1.0.8 runs alsaconf automatically, and BANG, configures my card.  That's it.  Modifies /etc/modules so that it works at boot.  Mandriva also includes alsaconf, and it JUST WORKS.  I once asked the developers to add it, and they said it would be too hard to support alsaconf, so they just eliminated it.

---

### Post by Razi on 2006-08-29
I would like to **_CONFIRM_** for one that the post #12 method **_WORKED._**  I tried some of the others and none worked. Nice!! No recompiling the world!!  

I did find an updated driver elsewhere, but lost the link during a reboot.  This works so there is no point tracking it down...for me anyway ;)  I was worried I would need to install the DEV libraries to get it to compile and spend all night recompiling everything... this is much easier indeed.  THANK YOU!! :)

I have one question though.  What do you mean by "DOS ps2.exe" utility.  I'm not using dual boot, and it worked... just a curious what that is.

---

### Post by subijmt on 2006-09-04
> (1) Add the following to '/etc/modprobe.d/blacklist'.
Code:

# snd_cs46xx doesn't work on thinkpad 600e blacklist snd_cs46xx



I am trying to add this code but it will not let me save the changes. How do I override the "read only"?

---

### Post by grumpymole on 2006-09-04
It depends how you are editing the file.

If you are using a cli editor, like vi or nano, then make sure you start it with ```
sudo vi ...
``` or ```
sudo nano ...
```

On the other hand, if you editing with a gui editor, open it from the command line using ```
gksudo gedit ....
```

In these examples, "..." is the filename you want to enter and you will need to enter your user password to open the file and edit as root.

Regards

Warren

---

### Post by subijmt on 2006-09-06
Thanks for the help!!! I have sound now!!! 

Just another confirmation that post 12 does work. You just have to be smart enough to know how to edit the code, which apparantly I was not until help arrived. 
Thanks again all!

---

### Post by butchd on 2006-09-12
SnowSparrow, let me get this straight---you followed ALL of the instructions from Waikato LUG? Or just the "snd-cs4236" and then editing /etc/modprobe.d/sound, etc? I've been working on this sound problem on my 600E for two weeks and already blew GRUB up once, so I want to be sure. If so, do you edit menu.lst like this: "kopt=root=/dev/hda1 ro pnpbios=off"? Thanks.

---

### Post by butchd on 2006-09-12
Whoops, didn't see the second page...fluxion's #12 looks promising. After editing "blacklist" how do I get the script to run? Sorry for the confusion.

---

### Post by ingo on 2006-10-06
> **becatlibra said:**
> It seems this is a common issue - However none of the solutions have worked for me.


1. Blacklist the incorrect sound card in /etc/hotplug/blacklist. Add lines for

snd-cs46xx
cs46xx



Hi, 

maybe a little too late now, but the instructions in your original post worked perfectly for my tp600e apart from one mistake above. Instead of /etc/hotplug/blacklist it should read /etc/modprobe.d/blacklist. 

HTH

ingo

---

### Post by grumpymole on 2006-10-06
ingo,

Yes, I think that is a difference between Hoary, Dapper, and Edgy.  Some of the directories or filenames have changed slightly.  But the principles should be the same.

I think that there is an updated list in the [bug filed]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-cirrus/+bug/40116") for this.

Glad you got it working.

Cheers

Warren

---

### Post by ame on 2006-10-25
Hi, I just joined this forum so I could reply to message #12.  I am using Mepis 6.0 on an IBM ThinkPad 600e.  Mepis 6.0 uses the Ubuntu repositories as its base.  This means that I had the same problem getting sound to work as someone using Ubuntu.  I followed the instructions in message #12 and it worked.  I see there are some other suggestions in a couple of other threads, but I didn't try them.

Anyway, thanks for posting the solution, and thanks to the others who verified it worked, meaning that I felt confident I was not wasting my time.

---

### Post by clembone on 2006-10-25
I too have had this issue with my 600e. I did not hit the forum to resolve the issue though. I looked at notes from two separate websites I found on Google. I combined them to correct the problem. I have documented what it took to get this working for 6.06. I have also had another person validate that this resolved his issue with sound. Give them a try.

Regards

** Fix **
[http://www.ubuntuforums.org/showthread.php?t=282624&highlight=600e]("http://www.ubuntuforums.org/showthread.php?t=282624&highlight=600e")

** Validation **
[http://www.ubuntuforums.org/showthread.php?t=267549&page=2&highlight=600e]("http://www.ubuntuforums.org/showthread.php?t=267549&page=2&highlight=600e")

---

### Post by clembone on 2006-10-26
This is for post #11. This is what I did to initialize the bios. Pop out all of your PCMCIA cards and remove the floppy if you have it connected. Enter the bios, Initialize 1st, then make your setting changes, then save and reboot.

Regards,

---

### Post by ingo on 2006-10-27
since we are all 600e users here how about exchanging some other info, too?

have you all got your modem working? if not, ask!
how's your suspend to disk? if it isn't, don't ask, cos mine worked out of the box...
anybody tried to get freemind or other java software? if you don't know how, ask...
anybody else got any clever hacks? i've managed to get wpa working, but that has nothing to do with the box, rather the card you are using :(

cheers

ingo

---

### Post by grumpymole on 2006-10-27
ingo,

There is a wiki page to try and list all of the things that do and don't work [here.]("https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600E")  Some of the things you have mentioned are listed, but some need some input.

Regards

Warren

---

### Post by BrendaEM on 2006-11-21
After over 20 hours of experimentaion, I still have no sound. The fixes posted in this thread do not work for me.

I have quickboot disabled in the bios.

For those people who have no floppy there is a ps2.exe .iso here:
[http://www.enderak.com/linux/thinkpad600/](http://www.enderak.com/linux/thinkpad600/)

I believe that the "Sound Works" status should be changed on:
[https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600E](https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600E)

...as many people cannot get sound working with any known fix.

---

### Post by deanlinkous on 2006-11-21
You have to be very systematic about fixes to get it working. Sometimes it still depends on the thinkpad initializing everything properly I think. Sometimes passing grub acpi options help like these acpi=off pnpbois=off Sometimes going into the bios and choosing to re-initialize will work.

It is a battle but usually it is winnable. ;)

Oh and last but not least go into the sound mixer and crank up all the sound controls.

Which version of ubuntu are you using? I think I still have my 600e around here somewhere.

But I agree "sound works" is a bit of a optimistic statement!

---

### Post by ingo on 2006-11-22
@ BrendaEM

bit of a pain, but could you post your

/etc/modprobe.d/blacklist
/etc/modprobe.d/alsa-base
/etc/modules

files? 

as deanlinkous said it is a bit of a dodgy process and I have always found that  (twenty) four eyes see more than two :)

ingo

ps.: for more info re ubuntu on the ibm600e you might want to check [www.toad.110mb.com](www.toad.110mb.com)

---

### Post by BrendaEM on 2006-11-30
I have done a hundred experiments so far. Regrettably, I trashed the beginning of my alsa-base; now it only has the remainder, which has everyone changes-dejour.

I think that the problem that the sound chip misidentified should be fixed.

Until then, I think it would be very helpful if someone who has full alsa-sound working on their 600e, could do a fresh clean Ubuntu 6.1 installation, and then document how it was achived.

[Once, when I had working sound, I noticed that the most popular mod worked, but I had already done another mod. The everpopular blacklist, modules, and alsa-base mod may not work alone.

BTW, I tried the ps2.exe .iso. It works great. You don't need a floppy to set up the hardware. The think boot into MSDOS. You type (PS2 ?) for a list of commands. You can check IRQs. I tried enabling the midi port, disabling IR, and the odvious things like enabling the sound chip and ctrl. Of course, it still didn't work, but it was fun. I've also pulled the CMOS battery cable, reset the time, and yes, disabled FASTBOOT in CMOS so many time I am seeing those little cursor birds in my sleep.]

---

### Post by deanlinkous on 2006-11-30
yea I thought the bird was cute as a button the first five times I seen it, now I loathe it with a vengenance! :)
Make sure to initialize the hardware also, sometimes that makes things work.

If I get around to downloading the latest and I get some time I will goof with it.

---

### Post by ingo on 2006-12-01
> Until then, I think it would be very helpful if someone who has full alsa-sound working on their 600e, could do a fresh clean Ubuntu 6.1 installation, and then document how it was achived.

Your are welcome to my installation notes:

[http://www.german-connection.org/public/](http://www.german-connection.org/public/)

---

### Post by nabfa1 on 2006-12-03
Hello,
I had wished to add hope by saying that soound is now working due to the very very awesome help of post # 12. I had wished to add some personal experience however. 
Kindly note that the method in post #12 should not be mixed or added to previous threads ( regarding sound and thinkpad 600e ). By this I mean to note that in previous threads changes were to made to the "etc/modules" file. These changes have to be reversed. No addition is needed to this file with the steps noted in post #12. 
Also, although I had canceled "Quick Boot" option, once the changes were made to these files ( as noted in post # 12 )  for some funny ( or not ) reason the bios had taken it upon itself to change back to quick boot! Kindly, for those having problems do re-check it.
For those who note that in the process of re-initialization some choices are  "grayed out " , this appears more common on a restart vs. a complete shutdown and restart and entry into BIOS.
Thank you again for all the help in these forums and a big thanks to Ubuntu.
Thank you.

---

### Post by moptop on 2006-12-14
[QUOTE=fluxion;974031]I've recently got sound working on my Thinkpad 600E, it required a slightly altered script from from ThinkWiki ([http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode](http://www.thinkwiki.org/wiki/Script_for_configuring_the_CS4239_sound_chip_in_PnP_mode)) and an addition to the pci blacklist. I'm running Xubuntu dapper, it works great on the 600E with 128Mb of ram. Steps taken to get sound working were:
(1) Add the following to '/etc/modprobe.d/blacklist'.
```
# snd_cs46xx doesn't work on thinkpad 600e
blacklist snd_cs46xx

```
(2) Change '/etc/rc.local' so it includes the sound chip enable and module parameter load as shown below.
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

# enable sound chipset and load module

# Sound-via-pnp-script for Thinkpad 600E and possibly other computers with onboard
# CS4239/CS4610 that do not work with the PCI driver and are not recognized by the
# PnP code of snd-cs4236

# search sound card pnp device

for dev in /sys/bus/pnp/devices/*
do
  grep CSC0100 $dev/id > /dev/null && WSSDEV=$dev
  grep CSC0110 $dev/id > /dev/null && CTLDEV=$dev
done

# activate devices (Thinkpad boots with devices disabled unless "fast boot" is turned off)

echo activate > $WSSDEV/resources
echo activate > $CTLDEV/resources

# parse resource settings

{ read
 read bla port1
 read bla port2
 read bla port3
 read bla irq
 read bla dma1
 read bla dma2
 # Hack: with PnPBIOS: ports are: port1: WSS, port2: OPL, port3: sb (unneeded)
 #       with ACPI-PnP:ports are: port1: OPL, port2: sb, port3: WSS
 # (ACPI bios seems to be wrong here, the PnP-card-code in snd-cs4236.c uses the
 #  PnPBIOS port order)
 # Detect port order using the fixed OPL port as reference
 if [ ${port2%%-*} = 0x388 ]
 then
   # PnPBIOS: usual order
   port=${port1%%-*}
   oplport=${port2%%-*}
 else
   # ACPI: mixed-up order
   port=${port3%%-*}
   oplport=${port1%%-*}
 fi
 } < $WSSDEV/resources

{ read
 read bla port1
 cport=${port1%%-*}
} < $CTLDEV/resources

# load the module

echo "options snd-cs4236 port=$port cport=$cport fm_port=$oplport irq=$irq dma1=$dma1 dma2=$dma2 isapnp=0 index=0" > /etc/modprobe.d/snd-cs4236

modprobe snd-cs4236

# end of sound module load

exit 0

```

After the above script is run you should find a new file in '/etc/modprobe.d/' called 'snd-cs4236', with the detected sound card settings. I've found that it needs the script to run to enable the sound chip, using the modprobe options on their own does not work. This may not be the recommended method i.e. dynamically writing module parameters, but it works for me ;) 

everytime I try to run this script I get an error:  
read: 57: arg count

any idea what I can do to fix that?  Seems like there's a syntax error but I don't know enough about bash to diagnose it.  can you help?  this is running a 1.6.29 kernel that I'm trying out.  don't have a working earlier kernel anymore I'm afraid.  thanks!!

matt

---

### Post by BrendaEM on 2006-12-14
I got the same error.

Oddly, I've been reading that many people disable the PNP bios in: boot/grub/menu.lst  ,which has issues, and it would seem that disabling the pnpbios would prevent the script from returning accurate information. Just guessing.

I think that just enough people having the sound working on the 600e to prevent it from ever being fixed the proper way. The underlying problem is: the sound chip is misidentified. 

The time I spent messing around with it, at minimum wage, I could have put toward a newer computer, but is that what we are supposed to do, throw out working computers because of software problems?

Sigh.

---

