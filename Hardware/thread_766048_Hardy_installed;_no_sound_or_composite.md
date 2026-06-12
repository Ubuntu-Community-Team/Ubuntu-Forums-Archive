---
title: "Hardy installed; no sound or composite"
date: 2008-04-25
forum: Hardware
---

### Post by gutterballk7 on 2008-04-25
Hi,

I just installed Hardy today, and it would appear I no longer have audio support or ATI graphics support, although these worked when I installed the beta a few weeks ago. I've never really had a problem with this before...

I used the alternate installer, and no funky errors were given, as far as I can tell.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400

They show up in lspci, but the graphics card is definitely not in the restricted drivers manager. :confused:

I wonder if I should just go
```
apt-get install xorg-driver-fglrx
```

Don't have any idea about the audio though.

Sorry if a solution is posted elsewhere.

---

### Post by prshah on 2008-04-25
> **gutterballk7 said:**
> Hi,
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Don't have any idea about the audio though.


Please post the output of ```
lsmod | grep snd
``` that will tell us the current sound position.

---

### Post by gutterballk7 on 2008-04-25
No output whatsoever.

---

### Post by gutterballk7 on 2008-04-25
It would also appear that my wireless was not installed because it did not show up in the restricted manager. Ugh, this feels like Windows! lol

---

### Post by ndstate on 2008-04-25
edit: I now have sound

---

### Post by gutterballk7 on 2008-04-25
Perhaps there is something wrong with my alternate install cd. I went and torrented the desktop CD and now that works fine. Sound, wireless, and graphics. Hoorah. So, my problem is "solved."

---

### Post by TrusigheR on 2008-04-25
I also have no sound, doing a 'lspci' gives me
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

doing 'lsmod | grep snd' gives me

```
snd_rtctimer            4640  0 
snd_hda_intel         344728  7 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  4 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  22 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  2 snd

```

I haven't really played around with ubuntu lately, but I know when I had 7.10 installed it worked correctly, and it worked when I put the live cd of 8.04 in.

---

### Post by TrusigheR on 2008-04-25
Nevermind I just figured it out, in the sound preferences, I changed my 'Default Mixer Tracks' to Analog Devices AD1981 (OSS Mixer), when I had that setting on HDA Intel (alsa mixer) nothing would play back.

I also changed everything above that to the ALSA mixer and it worked just fine.

---

### Post by thestonefox on 2008-04-25
I also have no sound on my Sony Vaio TR2MP

My driver is Intel 82801DB-ICH4 (Alsa Mixer)

The sound just doesnt come out, there doesnt seem to be any missing driver or anything though.

---

### Post by slack---line on 2008-06-12
There seems to be a solution [here]("http://ubuntuforums.org/showthread.php?p=5169880"), but its using some KDE application settings.

Would be keen to resolve this under Xubuntu (Xfce4) or via the command line.

---

### Post by slack---line on 2008-06-12
> **slack---line said:**
> There seems to be a solution [here]("http://ubuntuforums.org/showthread.php?p=5169880"), but its using some KDE application settings.

Would be keen to resolve this under Xubuntu (Xfce4) or via the command line.

Okay, found the answer [here](http://ubuntuforums.org/showthread.php?p=5169942).

Basically just turn off the channel "External Amplifier" under alsamixer, then save the configuration (alsactl store 0).

---

### Post by dipteshc on 2008-07-29
I am also having the same problem , i.e., no sound . I have a compaq presario V3035TU laptop . 


this is what i did:

```
diptesh@diptesh-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


```

i also did the following:

```
diptesh@diptesh-laptop:~$ lsmod | grep snd
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
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
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

Can someone help me fix this problem?? I am rally new to linux and havnt done much tinkering around. 

```

---

### Post by slack---line on 2008-07-29
> **dipteshc said:**
> I am also having the same problem , i.e., no sound . I have a compaq presario V3035TU laptop . 


this is what i did:

```
diptesh@diptesh-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


```

i also did the following:

```
diptesh@diptesh-laptop:~$ lsmod | grep snd
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
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
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

 

```Can someone help me fix this problem?? I am rally new to linux and havnt done much tinkering around.

Have you tried turning off the channel "External Amplifier" under alsamixer and then saving the settings as suggested in the above post?

slack

---

### Post by katakaio on 2008-08-02
I too had this problem getting sound to work in Hardy. I tried all the external amplifier tricks, but none seemed to work. What did it for me was installing the GNOME ALSA Mixer, and my sound suddenly worked. I didn't even have to tweak any settings in this mixer - the sound was just there. One thing I noticed after getting it to work was that enabling certain sense modules (like headphone jack sense) would kill the sound. Although this didn't make a difference before I installed GNOME ALSA Mixer, it did have an effect afterward.

Hope this helps!

---

### Post by dkuhlman on 2008-08-09
> **slack---line said:**
> Have you tried turning off the channel "External Amplifier" under alsamixer and then saving the settings as suggested in the above post?


How do I "turning off the channel 'External Amplifier' under alsamixer"?

When I run:

```
$ alsamixer
```

or:

```
$ gnome-alsamixer
```

I do not see anything about "External Amplifier".

I lost all sound one day after logging in to a KDE session.  I normally use Gnome.  I don't know if that is related.

I'm on Ubuntu 8.04.

- Dave

---

### Post by Yellow Pasque on 2008-08-09
Perhaps this will help:
[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

