---
title: "SOUND PROBLEM, PLease HELP, ITS VERY IMPORTANT To me."
date: 2008-03-28
forum: Hardware &amp; Laptops
---

### Post by the_analyzer on 2008-03-28
I cannot neither youtube videos, nor system log in/out sound.
I had alsa mixer, and my laptop speakers worked fine with that, but when I plugged my headphones, nothing changed (so I did not listen anything on my headphones, and the speakers were no muted)
NOW i removed alsa mixer and I installed another alternative sound card, sry I dont remember the name but you people should know. anyway. NOW

1. I cannot listen from flash, 
2. I cannot listen from some games (for example from Xmoto)
3. When I plug my external speakers (or headphones) they work but the sound is low, and the lap-top speakers arent muted. (BIG PROBLEM)
4. Im going crazy from these problems. 

Can anyone help me? 

REGARDS

---

### Post by Yellow Pasque on 2008-03-28
- Do you have everything in System -> Preferences -> Sounds set to ALSA?
- When you start firefox in a terminal and go to a site with Flash/sound, what error messages does it output?
- What sound card do you have? Please type *sudo update-pciids; lspci* in the terminal and gives us the audio device line. If it's some type of Intel/Azalia/'High-Def' compliant chip, check out this post: [http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

EDIT: feel free to AIM/YIM me

---

### Post by projectgonewrong on 2008-03-28
I have this same problem on Hardy Heron.  I found it to be that when a YouTube video starts the volume is automatically turned to off and when I raise it, it doesn't do anything.  But there is a way to get around it, it isn't a fix but it is a way to get around it.  

I just do this:

See the link for example, [http://youtube.com/watch?v=_1ADlw8IuQ4](http://youtube.com/watch?v=_1ADlw8IuQ4) just change that link to [http://youtube.com/v/_1ADlw8IuQ4](http://youtube.com/v/_1ADlw8IuQ4)     NOTE VIDEO ISN'T AVAILABLE ANYMORE IT'S not something wrong with your computer

So just delete the "watch?" and change the "=" to a "/".   Then to play click on the small play button not the large Play Arrow on the video.

So as I said it isn't a fix but you can watch videos with sound.  I think its cause the /v/ version is the embedded version and you have to open a mini menu to change sound.  Also this proves there isn't anything wrong with your sound card, I just think it's the way Flash opens youtube on youtube.com standard video player vs offsite embedded player.  But sometimes Firefox just closes when you do this for some reason.

---

### Post by the_analyzer on 2008-03-28
I wroted that, and thats what I saw.
And Im a beginner, I dont know to open the firefox with the terminal. anyway. hoping for solution.

myuser@ENP070120:~$ sudo update-pciids; lspci
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  129k  100  129k    0     0  27675      0  0:00:04  0:00:04 --:--:-- 30665
Done.
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
0a:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0a:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0a:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

---

### Post by the_analyzer on 2008-03-28
> **projectgonewrong said:**
> I have this same problem on Hardy Heron.  I found it to be that when a YouTube video starts the volume is automatically turned to off and when I raise it, it doesn't do anything.  But there is a way to get around it, it isn't a fix but it is a way to get around it.  

I just do this:

See the link for example, [http://youtube.com/watch?v=_1ADlw8IuQ4](http://youtube.com/watch?v=_1ADlw8IuQ4) just change that link to [http://youtube.com/v/_1ADlw8IuQ4](http://youtube.com/v/_1ADlw8IuQ4)     NOTE VIDEO ISN'T AVAILABLE ANYMORE IT'S not something wrong with your computer

So just delete the "watch?" and change the "=" to a "/".   Then to play click on the small play button not the large Play Arrow on the video.

So as I said it isn't a fix but you can watch videos with sound.  I think its cause the /v/ version is the embedded version and you have to open a mini menu to change sound.  Also this proves there isn't anything wrong with your sound card, I just think it's the way Flash opens youtube on youtube.com standard video player vs offsite embedded player.  But sometimes Firefox just closes when you do this for some reason.



I tried that, I mean changing the URL of the video. and it doesnt work. 
Why there are so many bugs in ubuntu? Its awful.

---

### Post by projectgonewrong on 2008-03-28
Well you have supplied little information for us to help you.  What Ubuntu are you using?

Also to run Firefox in the Terminal just type "firefox"

---

### Post by the_analyzer on 2008-03-29
> **projectgonewrong said:**
> Well you have supplied little information for us to help you.  What Ubuntu are you using?

Also to run Firefox in the Terminal just type "firefox"

I use ubuntu 7.10, gutsy. 
And when I run the firefox in terminal, it just opens firefox, Not any error messages when I opened youtube, anyway, I dont think that its only the problem of the flash.

---

### Post by fourthofjuly on 2008-03-29
> **the_analyzer said:**
> I cannot neither youtube videos, nor system log in/out sound.
I had alsa mixer, and my laptop speakers worked fine with that, but when I plugged my headphones, nothing changed (so I did not listen anything on my headphones, and the speakers were no muted)
NOW i removed alsa mixer and I installed another alternative sound card, sry I dont remember the name but you people should know. anyway. NOW

1. I cannot listen from flash, 
2. I cannot listen from some games (for example from Xmoto)
3. When I plug my external speakers (or headphones) they work but the sound is low, and the lap-top speakers arent muted. (BIG PROBLEM)
4. Im going crazy from these problems. 

Can anyone help me? 

REGARDS
i have intel 945G/GZ chipset & sound did not work out of the box in any distros - Ubuntu, openSuSE, Fedora etc. no sound at all...

struggled for 6 months until i found this soln:

i added following line at the end in my /etc/modprobe.d/alsa-base file:

options snd-hda-intel model=ref

using following command from terminal:

sudo gedit /etc/modprobe.d/alsa-base

let me know if it works...

regards,

devang.

---

### Post by fourthofjuly on 2008-03-29
> **fourthofjuly said:**
> i have intel 945G/GZ chipset & sound did not work out of the box in any distros - Ubuntu, openSuSE, Fedora etc. no sound at all...

struggled for 6 months until i found this soln:

i added following line at the end in my /etc/modprobe.d/alsa-base file:

options snd-hda-intel model=ref

using following command from terminal:

sudo gedit /etc/modprobe.d/alsa-base

let me know if it works...

regards,

devang.
for your information

output of my lspci command:

devang@edubuntu:/etc/modprobe.d$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)

---

### Post by the_analyzer on 2008-03-30
> **fourthofjuly said:**
> i have intel 945G/GZ chipset & sound did not work out of the box in any distros - Ubuntu, openSuSE, Fedora etc. no sound at all...

struggled for 6 months until i found this soln:

i added following line at the end in my /etc/modprobe.d/alsa-base file:

options snd-hda-intel model=ref

using following command from terminal:

sudo gedit /etc/modprobe.d/alsa-base

let me know if it works...

regards,

devang.

it didn't worked, 
I dont know what to say but Im starting to hate ubuntu, and not only the sound, but also it get stuck a lot, and I lose a lot of data. 
anyway,

---

### Post by fourthofjuly on 2008-03-31
> **the_analyzer said:**
> it didn't worked, 
I dont know what to say but Im starting to hate ubuntu, and not only the sound, but also it get stuck a lot, and I lose a lot of data. 
anyway,
could you please see this thread? maybe you can get a clue...

[http://ubuntuforums.org/showthread.php?t=685532]("http://ubuntuforums.org/showthread.php?t=685532")

regards,

devang.

---

### Post by the_analyzer on 2008-04-02
that is excatly my problem,

You mean to add that line to alsa-base (model=ref i think, right?) Actually some days before i did that, but I forget that I have unistalled alsa and I have installes OSS. Now Im a beginner so can you tell me how to uninstall OSS and Install again Alsa. 
regards.

---

### Post by fourthofjuly on 2008-04-02
> **the_analyzer said:**
> that is excatly my problem,

You mean to add that line to alsa-base (model=ref i think, right?) Actually some days before i did that, but I forget that I have unistalled alsa and I have installes OSS. Now Im a beginner so can you tell me how to uninstall OSS and Install again Alsa. 
regards.
reinstalling alsa... see the section on "Gettting the alsa drivers from a fresh kernel" in the following link:

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

before you reboot... as indicated in the link, do not forget to run:

sudo apt-get install gdm ubuntu-desktop


after reboot, add the line to the end of the alsa-base file and again reboot...

regards,

devang.

---

