---
title: "Problem with recording device..."
date: 2008-11-26
forum: General Help
---

### Post by t4ggs on 2008-11-26
For most of the time since I start using ubuntu (with version 6.06) till today using hardy, I've been having problems with my microphone, specially with skype..sometimes it works and sometimes it doesn't...and the microphone is perfect, the same happens with the sound recorder...

My chip is the ALC880 from Realtek

I think I don't completely understand the sound driver in linux...whats the difference between ALSA, OSS and PULSE???

Please if someone could help me...I'm really loosing my mind with this thing, I don't know why but each time I use skype I find myself changing the capture device in the skype options and playing around..

---

### Post by kidcharles on 2008-11-26
I have the same chipset and have had no luck getting the mic to work with skype. The mic is working to where I can actually hear what the mic records on the speakers, but the skype test call does not work.

---

### Post by kidcharles on 2008-11-26
Okay, I actually fixed it. My problem was that the mic recording was muted, and it was the input called "front mic" not "mic." I was able to add the recording channels to the volume control by double clicking on the speaker icon, choosing "Preferences" and checking all the boxes for the various channels to appear in Volume Control. Then I clicked on the "recording" tab and unmuted the capture channel. I also chose "HDA Nvidia" for the Skype audio capture device.

---

### Post by nzadLithium on 2008-11-26
Go to system << preferences << sound

In sound capture try each of the different options, hit test, see which ones work then pick one of the working ones. That should get your sound recording going :D

If none work you might want to take a look at what support your soundcard has on linux.

---

### Post by t4ggs on 2008-11-27
Tried changing the settings in skype and in >System>Preferences>Sound
Also tried connecting the mic to other jack in the pc...has no luck

Another strange issue is that in the front panel I have two jacks one for a mic and one for the headphones, when in windows, the green one works with the headphones, but im ubuntu I have to use the pink one... (and its connected as it should in the mobo)

I dont know what to do... I guess that I can't just uninstall windows yet.

---

### Post by nzadLithium on 2008-11-27
post output of lspci and lsmod. We'll check its loading right drivers.

---

### Post by t4ggs on 2008-11-28
lspci

00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 0e)
00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 0e)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
02:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)


lsmod



Module                  Size  Used by
vmnet                  40256  13 
vmmon                1830700  0 
af_packet              25728  2 
binfmt_misc            16904  1 
ipv6                  263972  14 
vboxdrv                71576  0 
ppdev                  15620  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
video                  25104  0 
output                 11008  1 video
sbs                    19464  0 
sbshc                  13440  1 sbs
pci_slot               12552  0 
container              11520  0 
wmi                    14504  0 
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
sbp2                   29324  0 
lp                     17156  0 
snd_hda_intel         381488  2 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
evdev                  17696  6 
nvidia               6900560  36 
agpgart                42184  1 nvidia
i2c_core               31892  1 nvidia
snd_seq_oss            38528  0 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcspkr                 10624  0 
snd                    63268  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               18596  0 
iTCO_vendor_support    11652  1 iTCO_wdt
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133384  2 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42264  8 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
ata_generic            12932  0 
ahci                   37132  0 
ata_piix               24580  6 
libata                177312  4 pata_acpi,ata_generic,ahci,ata_piix
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ohci1394               37936  0 
ieee1394               96324  2 sbp2,ohci1394
r8169                  35972  0 
ehci_hcd               43276  0 
uhci_hcd               30736  0 
usbcore               148848  4 usbhid,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  9

---

### Post by nzadLithium on 2008-11-28
Well it seems its loading the right drivers, so basically I have absolutely no idea whats going on XD

try these two commands and post the output from them here
sudo fuser -v /dev/dsp*
sudo fuser -v /dev/snd/*

---

### Post by t4ggs on 2008-11-29
sudo fuser -v /dev/dsp*

doesn't return anything

but sudo fuser -v /dev/snd/* gives me:

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  ytaggs     5116 F.... pulseaudio

---

### Post by t4ggs on 2008-11-29
sudo fuser -v /dev/dsp*

doesn't return anything

but sudo fuser -v /dev/snd/* gives me:

                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  ytaggs     5116 F.... pulseaudio

---

### Post by nzadLithium on 2008-11-29
Pulseaudio seems to kill my sound recording as well, it seems when you start it, it takes control of some devices, and then other apps decide they can't access them so then they don't get any sound. 

I would suggest you try killall pulseaudio
That will stop pulseaudio, then try your sound recording again, you may have to play with the volume controls again to get it going.

---

### Post by luppie on 2008-11-30
I would suggest that you verify whether Ubuntu has the correct sound and microphone drivers running for your PC before killing off running processes.  

A simple way to verify this is to use the built-in application such as "Sound Recorder." Go to [Application]->[Sound & Video]->[Sound Recorder] and try to record a short message, then play back.  If you can hear your recording, then you have the right sound and microphone drivers installed and the application [Sound Recorder] started these drivers correctly.  

At this point, I think it's a Skype's issue.  My guess is that Skype was not able to start the right sound and microphone drivers for your PC while the Ubuntu's built-in application [Sound Recorder] was able to.

I tried to reconfigure /etc/esound/esd.conf to set auto_spawn=1 and restart with no success.  So what's next?  

If I can determine which drivers/(linux) processes are the correct one to use with my sound devices then I can start the same one when running Skype.  Unless anyone else a better idea, I think I will take a snap shot of the system processes, then another while running [sound recorder] and do a "diff" to see what else sound-related started. Then I would "diff" them with the system running Skype (but not [sound recorder]) to see whether or not Skype started the correct drivers.  My guess is that it does not!  If this is so, I have to find which (*.conf) file Skype uses to start the sound/microphone drivers and include the correct drivers.  I think this should work.

Does anyone knows which file Skype uses to starts the sound drivers?

---

### Post by luppie on 2008-11-30
OK, scratch everything I said in my previous post.  I think I was delirious from the lack of sleep.  Since my Ubuntu's built-in application [sound recorder] works, I went into Skype and re-configure BOTH the "Sound in" and "Sound out" option to "pulse" and Skype starts to work.

Based on the outputs from your lspci, lsmod and /dev/snd/* and if you can get your Ubuntu's built-in application [sound recorder] to work, I think re-configure your Skype as I did, it should work.

---

### Post by t4ggs on 2008-11-30
killed pulseaudio....still didn't help i cant record with the audio recorder and yes i've been swithching between audio input...

---

### Post by nzadLithium on 2008-12-01
If your talking about gnome recorder, I wouldn't bother, I've never managed to get it work in a way that it doesn't throw up some error at some point during recording.

Try this,
sudo apt-get install sound-recorder
sound-recorder -c 2 -s 48000 -b 16 -f wav -s 00:10 test.wav

Start talking into your microphone (with it plugged in). See if your getting anything back in a file called test.wav in your home directory. This sound recorder uses oss for recording.

---

### Post by nzadLithium on 2008-12-01
> I would suggest that you verify whether Ubuntu has the correct sound and microphone drivers running  We already did.

> A simple way to verify this is to use the built-in application such as "Sound Recorder."  As I said, sound recorder is painful, its never worked for me, even though sound in ts and running vent through wine works perfectly.

> At this point, I think it's a Skype's issue. My guess is that Skype was not able to start the right sound and microphone drivers for your PC. ... Does anyone knows which file Skype uses to starts the sound drivers? Why/what driver is skype loading drivers exactly? I don't see any reason for it to be loading any drivers? *confused*

---

### Post by t4ggs on 2008-12-01
> **nzadLithium said:**
> 
Try this,
sudo apt-get install sound-recorder
sound-recorder -c 2 -s 48000 -b 16 -f wav -s 00:10 test.wav


when doing sound-recorder -c 2 -s 48000 -b 16 -f wav -s 00:10 test.wav, i get:
Illegal samplingrate 0 defaulting to 44100.

so tried sound-recorder -c 2 -s 44100 -b 16 -f wav -s 00:10 test.wav
but still get the same message

dont know why??

---

### Post by nzadLithium on 2008-12-01
post the output of aplay -l here plz :D

---

### Post by t4ggs on 2008-12-02
> **nzadLithium said:**
> post the output of aplay -l here plz :D

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Does it tells u something?

---

### Post by nzadLithium on 2008-12-02
yes, that tells me you have no recording devices, so your problem is that your driver for some reason is not working properly for your card. Post the output of dmesg | grep snd-hda-intel

---

### Post by t4ggs on 2008-12-02
It gives me nothing...

---

### Post by nzadLithium on 2008-12-04
Your driver seems to have quite a few problems judging by the bugtracker XD
I found some docs on this driver. What's the model and manufacturer of your pc? If it's custom built can you post all the specifications up for your motherboard? I'm assuming your soundcard is onboard?

---

### Post by t4ggs on 2008-12-04
yes is custom made, my mobo is an abit aa8xe and the onboar sound chip is alc880

more about my motherboard
[http://www.neoseeker.com/Articles/Hardware/Reviews/abitaa8xe/](http://www.neoseeker.com/Articles/Hardware/Reviews/abitaa8xe/)

---

### Post by nzadLithium on 2008-12-05
ur mobo has two sound plugs at the front as well aye? so u have 6 rear then a mic and headphone at front?

```
Your card has these models: ALC880
	  3stack	3-jack in back and a headphone out
	  3stack-digout	3-jack in back, a HP out and a SPDIF out
	  5stack	5-jack in back, 2-jack in front
	  5stack-digout	5-jack in back, 2-jack in front, a SPDIF out
	  6stack	6-jack in back, 2-jack in front
	  6stack-digout	6-jack with a SPDIF out
	  w810		3-jack
	  z71v		3-jack (HP shared SPDIF)
	  asus		3-jack (ASUS Mobo)
	  asus-w1v	ASUS W1V
	  asus-dig	ASUS with SPDIF out
	  asus-dig2	ASUS with SPDIF out (using GPIO2)
	  uniwill	3-jack
	  fujitsu	Fujitsu Laptops (Pi1536)
	  F1734		2-jack
	  lg		LG laptop (m1 express dual)
	  lg-lw		LG LW20/LW25 laptop
	  tcl		TCL S700
	  clevo		Clevo laptops (m520G, m665n)
	  medion	Medion Rim 2150
	  test		for testing/debugging purpose, almost all controls can be
			adjusted.  Appearing only when compiled with
			$CONFIG_SND_DEBUG=y
	  auto		auto-config reading BIOS (default)
```

I reckon the most likely one is 6stack-digout so try this, 
sudo rmmod snd-hda-intel 
sudo modprobe snd-hda-intel model=6stack-digout

If that doesn't work try
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel auto

I don't think any of the others are likely to work, maybe the asus ones? I duno.

---

### Post by t4ggs on 2008-12-05
yeah, i have 6 jack in the rear and 2 in the front, one for mic and one for headphones...but i always connect the mic in the rear..btw one funny thing is that i thougth that i cant use the headphones in ubuntu, because i couldn hear anything and i do in windows...the funny thing is that one day i connected them by mistake to the mic front jack and it worked...i dont know why, but in windows its work with the green jack and in ubuntu with the pink one..strange.

ytaggs@ytaggs-station:~$ sudo rmmod snd-hda-intel 
[sudo] password for ytaggs: 
ERROR: Module snd_hda_intel is in use

and why does it says asus?? my motherboard is from abit??

---

### Post by nzadLithium on 2008-12-06
Thats a list of all motherboards that implement the same audio as you. As you can see, your motherboard isn't listed, so if these generic ones don't work, your probably going to have to get a new soundcard :S

You could try the asus ones as well, your manufacturer might implement it similarly to asus? I don't know, but I would suggest you try all of them until you find one that works when you plug ur speakers and mic into the right jacks XD

It wont remove it coz other modules are using it.

Post output of 
lsmod | grep snd-hda-intel

---

### Post by t4ggs on 2008-12-07
I don't get it, u r suggesting me to try connecting the mic to very jack just for try?

lsmod | grep snd-hda-intel returns anything...

---

