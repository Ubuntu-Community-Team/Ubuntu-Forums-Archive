---
title: "[Ubuntu] Lenovo Ideapad 100s 11ibr"
date: 2018-07-07
forum: Hardware
---

### Post by libtiff on 2018-07-07
Hello i've been struggling to get the sound working on my laptop though speakers/headphones but unfortunately all of the things i've tried have failed.
I tried all the things listed with flavors like Ubuntu/Xubuntu/Lubuntu without any improvement. Back on windows10 sound is working properly so it must be a driver issue?

[COLOR=#1A1A1A][FONT=&amp]This laptop supports 32bit EFI so first thing first , ive disabled  _secure boot_ , set my bios to _*[FONT=inherit]setup mode[/FONT]*_, downloaded ubuntu's latest distro version and included in the EFI/Boot folder the bootia32bit.efi file. 
Booted to live desktop , and launched the installation from there which was successful. The only issue im having is that im not getting any audio from speakers nor analogue output. With Xubuntu and Ubuntu on the Output Audio Devices the list was completely empty , with Lubuntu it was showing analogue output but again with no sound.[/FONT][/COLOR]
[COLOR=#1A1A1A][FONT=&amp]Tried all the following on all 3 flavors without any improvement:
[/FONT][/COLOR]
**[COLOR=#1A1A1A][FONT=&amp][FONT=inherit]Attempt #1:[/FONT][/FONT][/COLOR]**
> sudo alsa force-reload

Restart -> No Improvement.

**[COLOR=#1A1A1A][FONT=&amp][FONT=inherit]Attempt #2:[/FONT][/FONT][/COLOR]**
> sudo apt-get remove --purge alsa-base pulseaudio
[COLOR=#1A1A1A][FONT=&amp]sudo apt-get install alsa-base pulseaudio sudo alsa force-reload

[/FONT][/COLOR]Restart -> No Improvement.

[COLOR=#1A1A1A][FONT=&amp][FONT=inherit]
**Attempt #3:**
[/FONT][/FONT][/COLOR]
> sudo gedit /etc/default/speech-dispatcher
and set RUN=No

Again without any success. 

[B][COLOR=#1A1A1A][FONT=&amp][FONT=inherit]Attempt #4:
[/FONT][/FONT][/COLOR][/B]> 
killall pulseaudio 
rm -r ~/.config/pulse/* 
rm -r ~/.pulse* 

pulseaudio -k

Restart -> No Success.

[COLOR=#1A1A1A][FONT=&amp][FONT=inherit]**Attempt #5**
[/FONT][/FONT][/COLOR]
> sudo apt-get remove --purge alsa   
sudo apt-get install pavucontrol 
sudo pavucontrol  

Which resulted in:
Pulse Server in the Environment/X11 Root Window Properties or default-server in client.conf is misconfigured.

[COLOR=#1A1A1A][FONT=&amp]**[FONT=inherit]With Alsamixer i got the following:[/FONT] **
[https://postimg.cc/image/q9auqvba3/](https://postimg.cc/image/q9auqvba3/)

**Laptop Specs:**

Lenovo IdeaPad 100s 11ibr 

Processor Intel® Atom&#8482; Z3735F Processor Baytrail
Graphics Intel® HD Graphics
Memory 2GB DDR3L 1333 MHz
Storage 32GB eMMC
AudioStereo Speakers with Dolby® Advanced Audio&#8482; Certification

[/FONT][/COLOR][INDENT]Long story short couldn't get the sound speakers to work or any sound at all , any help or tips are welcome.
[/INDENT]

---

