---
title: "N2N DMX6Fire 24/96 Ubuntu Karmic 9.10 AMD64 Pulseaudio and Alsa InDaComputa"
date: 2010-01-29
forum: Hardware
---

### Post by UbuAli on 2010-01-29
[COLOR=DarkRed]**N2N**[/COLOR] =** N**ewbie **2 N**ewbie so now you know. 

It contains the essence of all i found/tried to get my DMX6Fire 24/96 with Pulseaudio and Alsa in Ubuntu Karmic 9.10 AMD64 finally to work.

**so lets start**

Fresh Installation and no DMX6Fire 24/96 Sound ...mhh...
I wanted to get sound just to the Headphones on Frontpanel of DMX6Fire 24/96 but nothing

This is the 9.10 setup sofar

- Ubuntu Karmic 9.10 AMD64

    - Network Connection eth1 (8029(AS)) onboard lan doesn't work
    - IP.V.4  - Manually[INDENT]         :: IP = 192.168.0.69
[/INDENT][INDENT]         :: Submask = 255.255.255.0
[/INDENT][INDENT]         :: Gateway = 192.168.0.1
[/INDENT][INDENT]     - DNS-Server :: 192.168.0.1
[/INDENT]- Update Language Pack
- Update Ubuntu Patches/pakets 213 kernel 2.6.31-17 


So looks my DMX6Fire 24/96 at the moment
[COLOR=SeaGreen]SYSTEM -> PREFERENCES -> SOUND
System -> Einstellungen -> Klang[/COLOR]


default audio
Internes Audio
1 Ausgabe / 1 Eingabe (IEC958) something 2 stereo


Here i wondered normally i would have been expected ICE1712.

__________________________________________________________________________
**STARTUP**
-----------------------------------------------------------------------------------------------------------------------
TEST A SOUNDFILE

Open Terminal / Console Shell

Terminal / Console Shell ::[COLOR=SeaGreen] APPLICATION -> ACCESSORIES -> TERMINAL / CONSOLE SHELL[/COLOR][INDENT][INDENT][INDENT]              ::[COLOR=SeaGreen] Anwendungen -> Zubehör -> Terminal[/COLOR]
[/INDENT][/INDENT][/INDENT]**YOU NEED TO OPEN TERMINAL / CONSOLE SHELL JUST ONCE !!!**

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]aplay /usr/share/sounds/alsa/Front_Center.wav[/COLOR]

RUNS/PLAYS BUT NO SOUND ON FRONTPANEL - Headphone
-----------------------------------------------------------------------------------------------------------------------
**1 CHANGE** :: AS USER :: root for .asoundrc file
Path :: /home/useraccount/.asoundrc 
__________________________________________________________________________

in Terminal / Console Shell

[COLOR=DarkOrchid]type [/COLOR]

[COLOR=DarkRed]dir -a[/COLOR] (shows hidden .xxxx files/folders)

just to be sure there is no .asoundrc hidden file - yes no .asoundrc file


[COLOR=DarkOrchid]type [/COLOR]

[COLOR=DarkRed]sudo -s[/COLOR]   (makes you root user of ubuntu Terminal example:: root@youruser-desktop) good to know


create file .asoundrc

Path :: /home/ubuali/.asoundrc    (ubuali = your ubuntu user account)
should be default by opening Terminal/ Console Shell

[COLOR=DarkOrchid]type[/COLOR]

[COLOR=DarkRed]gedit .asoundrc[/COLOR]


copy + paste beneath to .asoundrc

[COLOR=Blue]pcm.!default {
    type pulse
    }

    ctl.!default {
    type pulse
    }

    pcm.pulse {
    type pulse
    }

    ctl.pulse {
    type pulse
    }

    # &#8220;Sensaura&#8221; like effect
    pcm.ice1712 {
    type hw
    card 0
    device 0
    }

    pcm.sensaura { #!default
    type plug
    ttable.0.0 1
    ttable.1.1 1
    ttable.0.2 1
    ttable.1.3 1
    ttable.0.4 0.5
    ttable.1.4 0.5
    ttable.0.5 0.5
    ttable.1.5 0.5
    slave.pcm ice1712
    }[/COLOR]     

save file + close gedit

-----------------------------------------------------------------------------------------------------------------------
**2 CHANGE** default.pa from PulseAudio 0.9.19
PATH :: /etc/pulse/default.pa
__________________________________________________________________________


open file
PATH :: /etc/pulse/default.pa

[COLOR=DarkOrchid]type [/COLOR]
[COLOR=DarkRed]cd /[/COLOR]
[COLOR=DarkRed]cd etc
cd pulse[/COLOR] 
[COLOR=DarkRed]gedit default.pa[/COLOR]

insert line

[COLOR=Blue]load-module module-alsa-sink device=sensaura[/COLOR]

search filecontent looks like follows and insert like that

### Load audio drivers statically (it's probably better to not load
### these drivers manually, but instead use module-hal-detect --
### see below -- for doing this automatically)
[COLOR=Blue]load-module module-alsa-sink device=sensaura[/COLOR]
#load-module module-alsa-sink
#load-module module-alsa-source device=hw:1,0
#load-module module-oss device="/dev/dsp" sink_name=output source_name=input
#load-module module-oss-mmap device="/dev/dsp" sink_name=output source_name=input
#load-module module-null-sink
#load-module module-pipe-sink


save file + close gedit

-----------------------------------------------------------------------------------------------------------------------
**TEST SOUND ON FRONTPANEL** - Headphone
Terminal / Console Shell

[COLOR=DarkOrchid]type[/COLOR]

(if Terminal / Console Shell is:: root@youruser-desktop firstly) [COLOR=DarkRed]exit[/COLOR]

than[COLOR=DarkOrchid] type[/COLOR] 

[COLOR=DarkRed]pulseaudio -k[/COLOR]
[COLOR=DarkRed]pulseaudio --start[/COLOR]
[COLOR=DarkRed]aplay /usr/share/sounds/alsa/Front_Center.wav[/COLOR]

SOUND PLAYS AND A FEMALE VOICE SAYS :: Front,Center


Restart Computer - Systems Sound Works as well (You could skip restart and procced to MP3 TEST)

-----------------------------------------------------------------------------------------------------------------------
**TEST MP3 ON FRONTPANEL** - Headphone

default Player for .mp3 files is :: Totem Video-Player 2.28.2
double click your .mp3 file

now will popup a messagebox click on button search and install those 3 plugins for decoding .mp3 files

close Totem Video-Player and double click once again your .mp3 file

MP3 ON FRONTPANEL - Headphone works 

-----------------------------------------------------------------------------------------------------------------------
**TEST GAME ON FRONTPANEL** - Headphone (You could skip here )
[COLOR=SeaGreen]APPLICATION -> SOFTWARE CENTER -> GAMES ->[/COLOR] Beneath a Steel Sky (Point & Click Adventure)
[COLOR=SeaGreen]Anwendungen -> Software Center -> Spiele ->[/COLOR] Beneath a Steel Sky
Install
[COLOR=SeaGreen]APPLICATION -> GAMES ->[/COLOR] Beneath a Steel Sky : click
[COLOR=SeaGreen]Andwendungen -> Spiele ->[/COLOR] Beneath a Steel Sky : click

GAME ON FRONTPANEL - Headphone works
-----------------------------------------------------------------------------------------------------------------------


__________________________________________________________________________

**What else you could do**
__________________________________________________________________________
-----------------------------------------------------------------------------------------------------------------------
No Sound (on Headphones) check alsamixer
Open Terminal / Console Shell

[COLOR=DarkOrchid]type[/COLOR] 
[COLOR=DarkRed]alsamixer[/COLOR]

currently installed should be alsamixer:: 1.0.20
card should be : PulseAudio
everything should be pulled to 100

on alsamixer:: 1.0.21 you could choose your dmx6fire soundcard by pressing F6 or F5 key
than check if DAC0 and DAC1 is muted or pull it up :: default should be 102
--------------------------------------------------------------------------------------------------------------------

**INSTALL Envy24 Control**
--------------------------------------------------------------------------------------------------------------------
A GUI Control like Alsamixer for Desktop (Gnome and KDE i guess)

Open

[COLOR=SeaGreen]SYSTEM -> SYSTEM ADMINISTRATION -> SYNAPTIC PAKETADMINSTRATION[/COLOR]
[COLOR=SeaGreen]System -> Systemverwaltung -> Synaptic Paketverwaltung[/COLOR]

Enlarge Synaptic and search for 

alsa-tools-gui

and install it

Envy24 Control is at

[COLOR=SeaGreen]APPLICATION -> ENTERTAINMENT -> Envy24 Control[/COLOR]
[COLOR=SeaGreen]Anwendungen -> Unterhaltungsmedien -> Envy24 Control[/COLOR]

Switch to Analog Volume
check if DAC0 and DAC1 both pulled to 102 should be by default
_______________________________________________________________________________

**LATEST PULSEAUDIO 0.9.21 + ALSA 1.0.21  (KARMIC ONLY | UNSTABLE | 32- BIT)**
-----------------------------------------------------------------------------------------------------------------------

Here you get latest PULSEAUDIO 0.9.21 for 32Bit runs also on 64Bit (Karmic only)

[http://www.webupd8.org/2009/11/upgrade-pulseaudio-to-version-0921-in.html](http://www.webupd8.org/2009/11/upgrade-pulseaudio-to-version-0921-in.html)



Here you get latest ALSA 1.0.21 for 32Bit runs also on 64Bit (Karmic only)

[http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html](http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html)


----------------------------------------------------------------------------------------------------------------------
_______________________________________________________________________________

**Where you could read too, more useful or less useful Website Collection links i discovered**
-----------------------------------------------------------------------------------------------------------------------
[http://owened.net/2009/11/03/mythbuntu-9-10-pulseaudio-iec958-spdif](http://owened.net/2009/11/03/mythbuntu-9-10-pulseaudio-iec958-spdif)
[http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712](http://www.alsa-project.org/main/index.php/Matrix:Module-ice1712)
[http://wiki.archlinux.org/index.php/PulseAudio](http://wiki.archlinux.org/index.php/PulseAudio)
[http://pulseaudio.org/ticket/624](http://pulseaudio.org/ticket/624)
[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1810844.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1810844.html)
[http://ubuntuforums.org/showthread.php?t=1282745](http://ubuntuforums.org/showthread.php?t=1282745)
[http://forums.debian.net/viewtopic.php?t=12497](http://forums.debian.net/viewtopic.php?t=12497)
[http://koroshiyaitchy.wordpress.com/2009/04/25/ubuntu-904-jaunty-jackalope-customised-for-performance-on-a-nexoc-osiris-e705iii-clevo-m57ru-laptop/](http://koroshiyaitchy.wordpress.com/2009/04/25/ubuntu-904-jaunty-jackalope-customised-for-performance-on-a-nexoc-osiris-e705iii-clevo-m57ru-laptop/)

-----------------------------------------------------------------------------------------------------------------------
**UbuAli other Beans**
-----------------------------------------------------------------------------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1395997](http://ubuntuforums.org/showthread.php?t=1395997) Nvidia
[http://ubuntuforums.org/showthread.php?t=1403260](http://ubuntuforums.org/showthread.php?t=1403260) Games

---

### Post by Lepto on 2010-02-27
Thank you so much !! Hearing a sound, at last... it's a second birth !

---

