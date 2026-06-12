---
title: "ASUS M51Sn Laptop Experience"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by Neovos on 2008-04-13
Wanted to make a post about this amazing laptop. First off, what you get hardware-wise for the money is outstanding. Just got it off Newegg.com. 

Anyway, I wiped Vista from it and put in Hardy beta. Everything is working AMAZINGLY out of the box:

-Function key works, but not all the functions work. Sleep, wireless, mail, internet, contrast up, contrast down, lcd backlight shutoff, sound mute, sound up, sound down, play, pause, next song, previous song all work. Switch from lcd to external display, touch pad on/off( *edit*:now works for some reason), and some others that are vista only functions don't work but are detected by running xev. *edit* I forgot to say that the function keys next to the power button also do not work or show up on xev.

-Webcam and built in mic work

-Touchpad works

-all the usb, video (dvi and the...other one...) and LAN ports work. Haven't tried the modem. Don't think I ever will. But it's detected anyway.

-Card reader works

-Haven't tried the fingerprint scanner but I don't think it's standard kernel material so a kernel recompile might be in order to get that working.(*edit*: It does work and is supported. But doesn't work to well enough to be a password replacement, at least for me. Check out: [http://legacy.madman2k.net/comments/105](http://legacy.madman2k.net/comments/105) and [http://www.geekplanet.fr/content/view/37/1/](http://www.geekplanet.fr/content/view/37/1/) )

(*edit*:Audio is solved, see below)
Now the only thing that has prevented me from total bliss is...........AUDIO. I've tried all sorts of combinations of muting and unmuting from the sound control and switching between auto detect and something specific on the "sound" menu. There isn't even the presence of white noise from the built in speakers OR the headphones no matter how high I turn it up. So I think there just isn't a driver in use for it. I think it's a hardware thing because of this little discovery too: 

my lspci output is 

```
:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0405 (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

"Intel Corporation 82801H (ICH8 Family) HD Audio Controller"

I look at that initially and think sweet, cutting edge hardware. Then I look here:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)
and realize it's too new. 

Is this the correct conclusion to draw? Should I just wait? Or is there some other source for sound card drivers that I don't know about? Also is there a way to "propose" a new sound card for development over at ALSA? Some official channel? Any ideas? It's hilarious having such a badass laptop in every except for when I go to listen to something......I just hear the sound of the hard drive working....

---

### Post by Gen2ly on 2008-04-13
new.

At least, more than likely.  The project site found is the best place to look and I have seen that this is kept up to date pretty well.  The good news is, that alsa does procuce drivers pretty quickly.

---

### Post by tonyb486 on 2008-04-14
With the hda-intel driver, my ICH9 (I'd think newer than ICH8 ) card works fine on.. fedora rawhide (and fedora 8 too).

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
```

```
[tonyb@tonybox ~]$ /sbin/lsmod | grep hda
snd_hda_intel         447540  0 
snd_pcm                86024  3 snd_usb_audio,snd_hda_intel,snd_pcm_oss
snd_page_alloc         16912  2 snd_hda_intel,snd_pcm
snd_hwdep              16520  2 snd_usb_audio,snd_hda_intel
snd                    66808  13 snd_usb_audio,snd_usb_lib,snd_rawmidi,snd_hda_intel,snd_seq_dummy,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
```

Alsa changelog for 1.0.14rc1 shows ICH9 support
[http://www.alsa-project.org/main/index.php/Changes_v1.0.13_v1.0.14rc1](http://www.alsa-project.org/main/index.php/Changes_v1.0.13_v1.0.14rc1)
>    - hda-intel - patch for Intel ICH9

Alsa changelog for 1.0.11 shows ICH8 support added
[http://www.alsa-project.org/main/index.php/Changes_v1.0.10_v1.0.11](http://www.alsa-project.org/main/index.php/Changes_v1.0.10_v1.0.11)
>    - hda-intel - patch for Intel ICH8

---

### Post by Neovos on 2008-04-14
NOW I'm getting somewhere...

The interesting thing is that I have conflicting data now, digging around the source file for "alsa-driver-1.0.16" from the ftp site, in a file called "CARDS-STATUS" it tells me that

>  - snd-intel8x0
Intel 82801AA:jk
Intel 82901AB
Intel MX440 

which makes it seems like my card is a work in progress. 

Also in a file called "SOUNDCARDS" under /doc in the same file it says these cards are supported:

> ID: Intel i810/i820/i830/i840/MX440
IF: MIXER,PCM,MIDI

which agrees with the supported soundcard page here: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

But if it works for you, Tony, on supposedly newer hardware, and the change log says such, what should be the next step? The fact that my lspci detects it and names it correctly means it's detected by the kernel right? Any ideas? In the meantime I'll try recompiling from source and reinstalling.

---

### Post by Neovos on 2008-04-22
So after that reinstall of ALSA drivers and lots more research, I've made progress but still no sound.

I wanted to look into Pulseaudio a bit. Being that it's a new addition to the Ubuntu lineup and all. I figured the next best thing would be a bug or some type of misconfiguration of Pulseaudio, but it really seems to be working correctly. I attached a screen shot (Audio1) that has a lot of info on it. If I understand correctly, pulseaudio can only be broadcasting audio if 

1) ALSA works correctly and
2) Pulsaudio works correctly

If you check out the shot, it shows that from the software perspective, everything is sending out audio with no problem. It's making it to the channels through ALSA and Pulseaudio.

So I guess from this I can say that not only is everything detected correctly (as per my earlier posts) but it's working from the os perspective and sending things to where they need to. But it's almost as if its not making it to the built in speakers or the headphone jack.

Is this looking to be a hardware thing? Perhaps the sound card is installed correctly but there is some sort of a driver I'm missing that gets the speakers/headphone jack to work? There's another screen shot (Audio2) of my hardware setup that shows possible evidence of this being the case. 

Here's the output of some audio related things in case it helps.

```
brian@Apollo:~$ aplay --list-devices
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
brian@Apollo:~$ sudo ./aadebug
[sudo] password for brian: 
ALSA Audio Debug v0.1.0 - Tue Apr 22 22:21:46 EDT 2008
http://alsa.opensrc.org/aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux Apollo 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel         344728  5 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Modprobe Conf ---------------------------------------------

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Apr 21 2008 for kernel 2.6.24-16-generic (SMP).
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebf8000 irq 23
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer
00-01: HDA Codec 1
00-00: HDA Codec 0
00-06: Si3054 Modem : Si3054 Modem : playback 1 : capture 1
00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 1
Client info
  cur  clients : 3
  peak clients : 3
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
    Connecting To: 15:0
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
Client  15 : "OSS sequencer" [Kernel]
  Port   0 : "Receiver" (-we-)
    Connected From: 0:1

Dev Snd ---------------------------------------------------
controlC0  hwC0D0  hwC0D1  pcmC0D0c  pcmC0D0p  pcmC0D6c  pcmC0D6p  seq	timer

CPU -------------------------------------------------------
model name	: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
cpu MHz		: 2401.000
model name	: Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
cpu MHz		: 2401.000

RAM -------------------------------------------------------
MemTotal:      3107564 kB
SwapTotal:     6000236 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

brian@Apollo:~$ 

```

Other then that, I'm stumped at this point.

---

### Post by Neovos on 2008-04-23
Found something that muddies the water even more today. If ctrl + alt and f1-6 are the tty terminals, f7 is your x11 session, f8 shows you what seems to be the tail end of the boot sequence? Well the very last line of that says:

```
*** PULSEAUDIO: unable to connect: connection refused   [fail]
```

which doesn't make any sense at all because it works as per the the screen shots above (well, works minus the sound anyway). So now what does THIS mean? Could this be some sort of refusal to connect with the hardware, that is, my speakers? Because it doesn't seem to be any sort of permission problem or setup issue with the software side. Any ideas?

Edit: I do want to add, since I'm thinking about the hardware, the computer DID make sound successfully when I got it out of the box and booted into .... ahem...vista. So I know the speakers do in fact work.

---

### Post by embe83 on 2008-04-24
Try adding two lines to /etc/modprobe.d/alsa-base
```
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
```

It works for me.

---

### Post by Neovos on 2008-04-24
IT WORKED!!! I don't really know how though, here's what I had before:

```
options snd-hda-intel model=3stack-660
options snd-hda-intel index=0
```

which is what I put in because that was exactly what my model is. I tried model=asus, model=auto, and some others but never thought to try lenovo. Don't know why thats the case for an asus laptop. But thank you so much for that. I was worried no one would know the fix because it's a pretty new laptop.

Anyway, now I can fully recommend this laptop for Ubuntu Hardy! (which was the original reason for this post)

---

### Post by drhank on 2008-05-03
Thanks this helped a lot.

---

### Post by tidytibs on 2008-05-07
With the new Ubuntu 8.04 Live CD, the changes to the alsa-base file is all I needed to get the M51SN working. However, the video is only 800x600. I'm currently working to find the driver fix for the nVidia 9500.

-T

---

### Post by futuromc on 2008-05-14
sorry im really noob at linux 
but i have a brand new m51sn and no sound as well 
im on live cd because i suspected tha i might have problems whit drivers 
and it did nt workde for me 
were do i add the two lines in alsa-base ??
any were ?? 
i did had the two lines in various places 
but no sound for me 

see it ---


options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
# autoloader aliases
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel


if some one coul please put it right for me 
i whould be gratefull 
thankz any way 
 oo and im portuguese and my english is a litle bit rusty lol 

i hate the missing drivers 
just vista just vista 
monopoly

---

### Post by Neovos on 2008-05-16
I'm not quite sure if the location in the file matters. But I'm pretty confident that you should only put it in there once. The "#" are comments meaning the machine doesn't read the contents of that line, not a type of "section" or anything. So it's not working on your machine because the computer is reading multiple definitions for those properties (even though it's the same definition) I attached mine, I put my lines at the bottom. I'm thinking that it's only after stuff "loads" at the top, that you can then start to define "defaults" and other parameters at the bottom.

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

#Additional options
#options snd-hda-intel model=3stack-660
#options snd-hda-intel index=0
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
```

The last two comments are what the parameters SHOULD be as far as I know (maybe it really is a Lenovo sound card that just calls itself intel or whatever) But in any case, just copy and paste this whole thing and put it in your alsa-base file. I didn't compare yours to mine EXACTLY to see if they are the same, but it's a pretty safe assumption if they're the same model.

---

### Post by jet200 on 2008-05-31
Thanks that last two line solved everything :D even though my laptop is a different model asus f3sg to be exact.

---

### Post by JeroenHoek on 2008-06-04
Thanks to the people in this thread I too have my M51sn up and running.

Issues remaining for me:

[COLOR="Purple"]I still have to change two keys on the keyboard with xmodmap. I have the Japanese model, and although the existing keymap for Japanese is largely correct (all the special keys work, and most of the keys are correct), two keys don't give me the proper keysims. One of them is the Yen key, which gives the backslash. This is standard behaviour for a Japanese keyboard because Japanese fonts use the Yen sign in place of the \, but I'd rather use the Unicode Yen sign, there already is a normal backslash key, so it's just silly legacy behaviour. The other is the ] key, which now also gives me a backslash (I have 3 keys for backslashes now, lovely).

How did you get the mousepad on/off switch to work? Any hints on that?

Also, the wireless buttons don't seem to work properly, although the FN + wireless key does light up the led (and wireless works).

The 5 launch keys next to the power key don't work yet.

For the NVidia 9500m GS GPU I am using the drivers from the NVidia website. I can't shake the impression that performance isn't optimal yet when I put the Compiz visual effects on the "extra" setting in "Appearance". Is there anything I can change in the configuration to make full use of the card, or am I just imagining a lower performance?[/COLOR]

Issues aside, all in all, this is a great laptop.

The Japanese keyboard (photo):
[http://picasaweb.google.com/jeroenhoek.nl/JapanJuni2008/photo#5207945475259005314](http://picasaweb.google.com/jeroenhoek.nl/JapanJuni2008/photo#5207945475259005314)

The laptop itself:
[http://picasaweb.google.com/jeroenhoek.nl/JapanJuni2008/photo#5207945479553972626](http://picasaweb.google.com/jeroenhoek.nl/JapanJuni2008/photo#5207945479553972626)

---

### Post by JeroenHoek on 2008-06-05
For me this laptop replaces my ageing Medion MD9783 laptop (six years old I think). In every aspect the Asus M51SN is bests the old laptop, but there is one thing that it can't beat. The speakers on this laptop are much, much worse than the ones on the Medion. Perhaps I should through LADSPA into the PulseAudio mix and do some equalising? Any thoughts from fellow M51 owners?

(For serious music listening and such I have headphones of course.)

---

### Post by Neovos on 2008-06-06
> **JeroenHoek said:**
> I have the Japanese model...I have 3 keys for backslashes now
Good luck with that one. I apologize if this insults your intelligence, but did you try changing your "layout options" in the "keyboard preferences" window under the "layout" tab? I remember seeing Japanese layout alternates listed in there.

> How did you get the mousepad on/off switch to work? Any hints on that?
To be honest, I don't. All I remember is that it didn't work when I first checked it out. A month and a lot of updates/customizations later, it did. One thing I did do as a fix for having it NOT work in the beginning, was adding some stuff to have it disable for a time when I started typing, here:
[http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing](http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing)

I'm to lazy to uninstall that and see if my touchpad button no longer works but that would be my first place to look. Maybe installing that added the ability to manually disable it.

> Also, the wireless buttons don't seem to work properly, although the FN + wireless key does light up the led (and wireless works).
Are you talking about the hard switch or the fn+wireless button? My fn+wireless button only works if the hard switch is on. But if the hard switch is off, the fn+wireless does nothing. I prefer the hard switch anyway just because it's less total keystrokes. And my LED does correctly represent the status of my wireless taking into account the above.

> The 5 launch keys next to the power key don't work yet.
Me as well. Their default actions seem redundant but I would love to be able to customize those guys.

> Is there anything I can change in the configuration to make full use of the card, or am I just imagining a lower performance?
Did you try to let it download the drivers itself? I remember that as soon as I booted, the "hardware drivers" window told me that it wanted to download the proprietary drivers (the "latest cards one"), I let it, and everything has worked fine. Did you compile the drivers from the site and install them yourself? I remember when I did that on one my other computers (gutsy) even though all was lean and mean from the nvidia-settings side, Ubuntu didn't want to recognize it (through that same "Hardware Drivers" and my compiz never worked. It didn't even install let alone run. So my hunch is that it might be better to sacrifice some cutting edge version goodness and run the proprietary driver in the repository. I haven't tested it with the open source driver but figured I didn't need to once the proprietary one worked just fine. 

> Issues aside, all in all, this is a great laptop.
M51sn=crazydelicious

---

### Post by Neovos on 2008-06-06
> **JeroenHoek said:**
> For me this laptop replaces my ageing Medion MD9783 laptop (six years old I think). In every aspect the Asus M51SN is bests the old laptop, but there is one thing that it can't beat. The speakers on this laptop are much, much worse than the ones on the Medion. Perhaps I should through LADSPA into the PulseAudio mix and do some equalising? Any thoughts from fellow M51 owners?

(For serious music listening and such I have headphones of course.)
I agree. They actually seem like just the tweeters from the Altec Lansing 3 piece job that everyone knows and loves. If anything, I seem to not get enough volume out of the system in general. I always have everything up almost full for the speaker usage and a hair under that for the headphone jack. I also have to mute the CD column to get rid of an annoying hissing. This happens on almost every computer I've ever owned. Its from, I believe, the direct connection from the CD drive to the sound card for bypassing the OS. It creates more problems the solutions in my opinion. When the drive is turned on (always) it sends the hiss to the speakers.

I almost never actually use the real speakers. When I'm home, I plug in my 3 piece Altec Lansing's into the headphone jack, and when I'm mobile, It's all headphones, so I kinda avoid the speaker issue. But for the record, out of the box, they instantly seemed not up to par with the rest of the system.

---

### Post by JeroenHoek on 2008-06-06
> **Neovos said:**
> Good luck with that one. I apologize if this insults your intelligence, but did you try changing your "layout options" in the "keyboard preferences" window under the "layout" tab? I remember seeing Japanese layout alternates listed in there.

No offence taken, any suggestion is welcome. I did look, but these layouts all seem to completely lack the ] key for some reason. The keycode is a bit odd as well, usually keys like [ and ] are assigned consecutive keycodes, but in this case it is a completely different code.

I used Xmodmap to fix the issue.

I'll look into the touchpad activation, thanks.

> **Neovos said:**
> Are you talking about the hard switch or the fn+wireless button? My fn+wireless button only works if the hard switch is on. But if the hard switch is off, the fn+wireless does nothing. I prefer the hard switch anyway just because it's less total keystrokes. And my LED does correctly represent the status of my wireless taking into account the above.
On reflection, they do seem to work properly. Odd, I could have sworn I had wireless up with the LED off.

> **Neovos said:**
> 
Me as well. Their default actions seem redundant but I would love to be able to customize those guys.
I can't find them in the inputdev devices either. It doesn't seem to be connected to a USB device, but I couldn't spot them in lspci either.

I use the nvidia driver from the NVidia website. It works perfectly in terms of acceleration and such, I was just wondering if there are xorg.conf or driver parameters that can make it perform even better. I can't shake the feeling that Compiz should perform better when I compare it to the performance of this machine in games on Vista.

---

### Post by Neovos on 2008-06-06
> **JeroenHoek said:**
> I use the nvidia driver from the NVidia website. It works perfectly in terms of acceleration and such, I was just wondering if there are xorg.conf or driver parameters that can make it perform even better.

sudo apt-get install nvidia-settings ?

also upon more mindless button pressing, I found that the touchpad toggle button next to the power button does work. I assume it gained functionality once the other one started working too. But still, nothing else up there works or is recognized (it still isn't picked up via xev, but does work, weirdish)

---

### Post by cayhorstmann on 2008-06-07
> **embe83 said:**
> Try adding two lines to /etc/modprobe.d/alsa-base
```
options snd-hda-intel enable=1 index=0 model=lenovo
alias snd-card-0 snd-hda-intel
```

It works for me.

I stumbled upon this with my own private PulseAudio grief on a Thinkpad X60, and the same magic incantation worked for me. It turned out I had to add position_fix=1 so that recordmydesktop would work--https://sourceforge.net/forum/forum.php?thread_id=1804915&forum_id=590957

---

### Post by JeroenHoek on 2008-06-10
Did anyone test the S/PDIF out on the front yet? I'm considering buying a set of speakers for music listening purposes, but it would be rather pointless if it doesn't work yet.

---

### Post by stevenyu on 2008-06-15
I have recently bought the M51SN serie notebook, has anyone manage to get the internal tv tuner working under linux?  I am having the sound problem, but looking at some of the early post I think I can solve it.

---

### Post by FruitieX on 2008-06-29
Hey, I created this page on the Ubuntu Wiki after owning this laptop for about 2 weeks :):

[https://wiki.ubuntu.com/LaptopTestingTeam/AsusM51Sn](https://wiki.ubuntu.com/LaptopTestingTeam/AsusM51Sn)


Oh and by the way, to get the most fps out of Compiz you should configure it right and create a simple script to activate/deactivate it.

First install compizconfig-settings-manager with:

sudo apt-get install compizconfig-settings-manager

Then, go to System -> Preferences -> Advanced Desktop Effects Settings. Go to General options, display settings, untick "Detect refresh rate", tick "Sync to VBlank", set refresh rate to 61 and configure compiz as you wish by clicking back :).

I've found out that you have to unselect the Sync to VBlank setting in nvidia-settings BEFORE starting compiz to get max fps. That is a little cumbersome, so we create an easy script like this:

Run:

gedit ~/compiz.sh

Paste the following into the text editor and save:
```

#!/bin/bash
nvidia-settings -a SyncToVBlank=0
nvidia-settings -a FSAA=0
sleep 0.5
compiz --replace

```
Then run:

gedit ~/compizoff.sh

and paste this into the text editor and save:
```

#!/bin/bash
nvidia-settings -a SyncToVBlank=1
nvidia-settings -a FSAA=1
metacity --replace &
killall -s SIGKILL compiz
killall -s SIGKILL compiz.real

```

Fire up the compiz settings manager again and go to General options, commands, expand the Commands section and type in:
```

/home/*username*/compiz.sh

```
into the first box and
```

/home/*username*/compizoff.sh

```
into the second box. Replace *username* with your username, duh.

Expand the Key bindings section and create a bind for Run command 0 and 1. 0 turns compiz on and 1 turns compiz off. I used Super+C for on, and Super+X for off - easy to remember! :D

Don't forget to make the scripts executable with

chmod -x ~/compiz.sh

and

chmop -x ~/compizoff.sh

Also, don't forget to install nvidia-settings with sudo apt-get install nvidia-settings

Then try pressing the keybind for turning compiz on, and hope for the best! :D

---

### Post by FruitieX on 2008-06-29
By the way, is there any way to get the 5 hotkeys and non-functional Fn key-combinations to work? :)

---

### Post by JeroenHoek on 2008-06-29
Thank you for the Compiz suggestions. I'll give it a try!

No luck yet with the Fn and hotkeys, although I don't miss them really. I have mailed Asus about this, although such a direct approach is probably futile. I did get past the first-line helpdesk, and apparently my request for some details of the technical implementation of the hotkeys has been forwarded to the relevant department at Asus. I will be pleasantly surprised if I receive a reply.

---

### Post by beejay82 on 2008-07-03
Ok, so I finally installed Ubuntu on my ASUS M51sn after my frustrating time with Vista Home Premium. 

I saw in a few threads that they were not getting very loud sound from the built in speakers and that they just use headphones or external speakers.

I was getting the same problem but when I started messing with the volume control (right click speaker icon>volume control), then raised the PCM and Front speakers to maximum, then the sound became way better on the laptop. I think by default, the PCM was set to 50%. and when you press the volume buttons on the laptop, it just raises the master.

Hope this helps somebody.

---

### Post by Neovos on 2008-07-03
> **beejay82 said:**
> 
I was getting the same problem but when I started messing with the volume control (right click speaker icon>volume control), then raised the PCM and Front speakers to maximum, then the sound became way better on the laptop. I think by default, the PCM was set to 50%. and when you press the volume buttons on the laptop, it just raises the master.

Right, I was actually commenting on how even after this is done and the master, the PCM, and AND the "Front" channel are turned up, it's still significantly lower in volume then other laptops I've come across. 

I also got quite annoyed with having to constantly turn those up every time I booted. I wanted the PCM and the "Front" channel up 100% all the time so that I can get the final say with the master channel and have full use of the sound range. So to edit those to percentages of your choice upon bootup, just ```
sudo gedit /etc/rc6.d/K50alsa-utils 
``` and go to about line 140 where it says "sanify_levels_on_card()" and edit those percentages. I changed mine so that PCM and "Front" are up 100% so that when I put the "master" at max, I know it's at maximum.

---

### Post by stevenyu on 2008-07-04
Still trying to get the internal TV tuner to work, here are the detail from Windows Vista:

DIB7700 DTV Tuner

Hardware Ids - 
USB\VID_1164&PID_1F08&REV_0100
USB\VID_1164&PID_1F08

Manufacturer - Dibcom
Physical Device Object Name - \Device\USBPDO-9

---

### Post by JeroenHoek on 2008-07-04
> **Neovos said:**
> I also got quite annoyed with having to constantly turn those up every time I booted. I wanted the PCM and the "Front" channel up 100% all the time so that I can get the final say with the master channel and have full use of the sound range. So to edit those to percentages of your choice upon bootup, just ```
sudo gedit /etc/rc6.d/K50alsa-utils 
``` and go to about line 140 where it says "sanify_levels_on_card()" and edit those percentages. I changed mine so that PCM and "Front" are up 100% so that when I put the "master" at max, I know it's at maximum.

Odd. Mine are always at 100% on bootup, without the edit. Perhaps PulseAudio sets the hardware levels as well with the restore sound levels module? I use PulseAudio to set the masters for the onboard sound and a headset to 50% on bootup.

---

