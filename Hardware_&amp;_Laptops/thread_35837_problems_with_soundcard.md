---
title: "problems with soundcard"
date: 2005-05-20
forum: Hardware &amp; Laptops
---

### Post by kes on 2005-05-20
I've installed Ubuntu hoary on the Toshibe A60-124 and there were no problem with initialization of sound card (wav- and flac-files were played w/o any problem)
but after I tried to install gstreamer0.8_etc  and mplayer there's no more sound at all...
System-Parameters-Multimedia-Audio-Out (ESD) -> "check" -> error

I'm not very experienced with Linux, so I have no idea what to do... :| 
thanks for any help

---

### Post by f.prisson on 2005-05-20
Do you have no sound in mplayer or no sound in any application? What do you mean with "System-Parameters-Multimedia-Audio-Out (ESD) -> "check" -> error". Doesn't your esound daemon start?

---

### Post by kes on 2005-05-21
I have no sound at all (not even start-up sound)
With "System-Parameters-Multimedia-Audio-Out (ESD) -> "check" -> error" I mean when I'm trying to check the output of the sound card there's nothig but error message: "Error while creating the testing chain (?) for  ESD"
(I'm using russian interface, so I'm not sure if I translate it correctly)

---

### Post by andlinux21 on 2005-05-23
[FONT=Comic Sans MS]I don't have any sound either using my Micron Transport XKe laptop it works fine under winblows me ESS1879[/FONT] ](*,)

---

### Post by webmost on 2005-05-23
Likewise my Micron Transport LT

---

### Post by der_kaiser on 2005-05-23
I also have a Toshiba A60, and I had the same problem with the sound.
You have to follow the instructions on this page : [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly)

And after add these lines to:

/etc/hotplug/blacklist  : snd-atiixp-modem 
                                     snd-atiixp

 /etc/modules : snd-atiixp

You also have to type "chmod 777 /dev/dsp"

Good luck!

---

### Post by kes on 2005-05-27
2 der_kaiser: thanks for suggestion
Actually, I should be more precise: in my case the sound appears and disappears in absolutely random way each time I turn on the computer [well, I made quite a nice statistics during this week..=) ]. I mean IF there is a "welcome" wav than the sound card works, if there's nothing - "Error message"
Did you have the same situation?

---

### Post by der_kaiser on 2005-05-27
I had the same situation before, but when I've done all what I've wrote you, I disappeared. I don't know what have been exactly the thing that made it working,  because I've done all this at the same time!!
Je me demande si tu as fais tout ca..parce que normalement ca devrait marcher sur ton PC, vu qu'on a des modèles assez similaires...
Dans tous les cas, fais moi part du résultat des tes manipulations..
Bonne chance!

---

### Post by kes on 2005-05-29
2 der_kaiser: I've followed your instruction, but it seems of no help...=(
there's still no sound
moreover after adding the lines mentioned above to the /etc/hotplug/ blacklist and /etc/modules I've recieved th following messages:
- using device defult
ALSA lib pcm_dmix.c:868: (snd_pcm_dmix_open) unable to open slave

---

### Post by der_kaiser on 2005-05-29
I'm sorry kes, I really have no idea..
It seems that we have the same hardware but not the same problems..

---

### Post by ::DoGG:: on 2005-05-29
in system-preferences-multimedia system chooser- check the esound output driver and the push test.

---

### Post by kes on 2005-05-30
2 :: DoGG:: 
Already done
That's how I've figured out that I have a problems with the soundcard (it is written in my very first post)... :-? 

2der_kaiser: s'est pas grave
dans tout cas merci beaucoup pour votre aide

---

### Post by ::DoGG:: on 2005-05-31
Did you try to pick another driveer ? Are all the drivers tests ending with error ?

---

### Post by kes on 2005-05-31
yes, all of them, regardless whether I try input or output
sound appears and disappears on its own from one session to another.
I am sure it is not the problem of the hardware, because under live CD with PCLinuxOS and Knoppix I don't have any problems with that

---

### Post by andlinux21 on 2005-05-31
[FONT=Comic Sans MS][SIZE=3][COLOR=Blue]When my laptop boots it shows ALSA is ok but I dont have any sound either.  I tried the instructions to get my video fixed but the audio instructions didnt work for me. :-x [/COLOR][/SIZE][/FONT]

---

### Post by consecratus on 2005-06-01
Good day mate


Have you tried adjusting your settings in MULTIMEDIA SYSTEMS SELECTOR?

System > Preference > Multimedia Systems selector?

My current settings are

**Default Sink**
Output ESD - Enlightenment Sound Daemon

**Default Source**
Input - OSS - Open Sound System

You also said that after you have made gstreamer(s) your sound isn't working.
I suppose you are doing this because of MP3 stuff..Well.. Try the below address in Synaptics repo: [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/)
Also enable ALL(I know it sounds bit dumb..) Repos, RELOAD Synaptic(as in RELOAD BUTTON) Go to search and type in gstreamer as name and description.
See if any audio gstreamers are missing.

I suspect you might have bloody broken packages in gstreamer.

What I would do is to remove gstremer(s) completely, download gstreamer(s) via the above address and ubuntu repos including universe(ALL) 

See how you go.

---

### Post by andlinux21 on 2005-06-02
i did lsmod but other than my pc speakers i dont see my sound card

lsmod
Module                  Size  Used by
nls_cp437               5888  0
isofs                  33720  0
udf                    77060  0
proc_intf               4100  0
freq_table              4100  0
cpufreq_userspace       4572  0
cpufreq_ondemand        6172  0
cpufreq_powersave       1920  0
pcmcia                 21380  4
apm                    19948  2
ipv6                  229504  9
af_packet              20744  2
arc4                    2048  1
adm8211                52224  0
yenta_socket           19584  1
pcmcia_core            53568  2 pcmcia,yenta_socket
i2c_piix4               8592  0
i2c_core               21264  1 i2c_piix4
uhci_hcd               30224  0
usbcore               107384  2 uhci_hcd
floppy                 54864  0
analog                 10784  0
ns558                   5632  0
gameport                4608  2 analog,ns558
pcspkr                  3816  0
rtc                    12216  0
md                     43856  0
dm_mod                 53116  1
capability              5000  0
commoncap               7808  1 capability
tsdev                   7488  0
evdev                   9088  0
psmouse                19336  0
mousedev               11160  1
parport_pc             34372  1
lp                     10792  0
parport                33480  2 parport_pc,lp
ide_cd                 38532  0
cdrom                  36508  1 ide_cd
ext3                  120968  1
jbd                    54168  1 ext3
ide_generic             1664  0
piix                    9988  1
ide_disk               18176  3
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk
unix                   26164  727
processor              22708  0
fbcon                  34048  0
font                    8448  1 fbcon
bitblit                 5120  1 fbcon
vesafb                  6948  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3072  1 vesafb
cfbfillrect             3584  1 vesafb

This is a Micron Transport Xke Laptop

---

