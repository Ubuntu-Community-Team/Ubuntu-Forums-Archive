---
title: "No earphone sound output for ASUS K42JR-VX050"
date: 2010-06-15
forum: Hardware
---

### Post by zzzliperzzz on 2010-06-15
Hello guys. I bought a new laptop, ASUS K42JR-VX050 and I installed Windows 7 and Ubuntu 10.04 LTS. Ubuntu works fine for me except for the headphone sound. There is no sound coming out from the headphone but when I use the internal speakers it works fine. I've already tested my headphone to my other OS and it works fine. I've already browsed other threads to search for solutions and all the solutions I found are only for dell, toshiba and lenovo laptops only. I can't find any solution for the ASUS K42Jr-VX050.

Any help will be appreciated.
Thanks.

---

### Post by pignic on 2010-06-15
+1 on Asus K42F ! I've already tried the main solutions proposed on others forums, but nothing helped !

---

### Post by sleepitoff on 2010-06-15
Conexant audio? I have a k52jr and this fixed it: 

[http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)

---

### Post by lidex on 2010-06-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by zzzliperzzz on 2010-06-17
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

uname -a: 
```
Linux ********-laptop 2.6.32-22-generic #36-Ubuntu SMP i686 GNU/Linux
```


aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


dpkg -l | grep "alsa":
```
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA

```



head -n 1 /proc/asound/card*/codec#*:
```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI

```

---

### Post by lidex on 2010-06-17
Try this. Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot

---

### Post by zzzliperzzz on 2010-06-18
> **lidex said:**
> Try this. Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot

It doesn't work for me. :(
I still don't hear any sound from my  earphones.

---

### Post by regiestry on 2010-06-18
[http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)

This post solved my trouble with the speaker and headphones also... kudos to saiganeshb...

---

### Post by lidex on 2010-06-18
> **regiestry said:**
> [http://ubuntuforums.org/showpost.php?p=9459478&postcount=38](http://ubuntuforums.org/showpost.php?p=9459478&postcount=38)

This post solved my trouble with the speaker and headphones also... kudos to saiganeshb...

That won't work here as OP's codec is not conexant.

---

### Post by lidex on 2010-06-18
OK. Uninstall the alsa-backports and try this. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.
Then
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

---

### Post by mekh on 2010-06-19
The same problem with Asus K42F (K42F-350MSCEDAW).
Sound works only through the internal speakers, but it doesn't through the headphones.

**uname -r**
```
Linux mech 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux

```

**aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice &#8470;0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice &#8470;0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice &#8470;0: subdevice #0

```

**dpkg -l | grep "alsa"**
```
ii  alsa-base                                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                           1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-utils                                         1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                         4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                    0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                                 0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-22-generic     2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.

```


**head -n 1 /proc/asound/card*/codec#***
```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC269

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX

```

I did try to change /etc/modprobe.d/alsa-base with different options, such as "options snd-hda-intel model=base"
, or "options snd-hda-intel model=fujitsu". But nothing helps.



2**[SIZE="3"]lidex[/SIZE]**,
```
sudo rm /etc/asound.conf
```
No such file or directory.

---

### Post by zzzliperzzz on 2010-06-19
> **lidex said:**
> OK. Uninstall the alsa-backports and try this. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```Logout/in.
Then
```
sudo apt-get update
sudo apt-get upgrade
``````
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```**Reboot.**


```
rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```doesn't exist. I tried to do the update and upgrade plus the reinstall but still my headphone is not working
with Ubuntu Lucid Lynx. Thanks for the help, anyway.

---

### Post by lidex on 2010-06-19
Well guys, the backports don't seem to be working. At this point I would uninstall alsa backports and upgrade fully to 1.0.23 via the alsa-upgrade link in my sig.

---

### Post by mekh on 2010-06-21
> **lidex said:**
> Well guys, the backports don't seem to be working. At this point I would uninstall alsa backports and upgrade fully to 1.0.23 via the alsa-upgrade link in my sig.
Yearrrrr =D>
It realy works!
Great thank for your help ;-)

P.S. I don't know was it really needed, but at first I've removed pulseaudio, and only after that run alsa-upgrade script.

---

### Post by pignic on 2010-06-21
> **mekh said:**
> Yearrrrr =D>
It realy works!
Great thank for your help ;-)

P.S. I don't know was it really needed, but at first I've removed pulseaudio, and only after that run alsa-upgrade script.

Is it possible to know which model did you choose in your alsa-base.conf file ? Because, I also tried to run the alsa-upgrade script, but there is still no sound from the headphone ! I didn't remove pulseaudio before, I don't know if it really change something !

Thanks !

---

### Post by mekh on 2010-06-21
**pignic**,
Not in alsa-base.conf, but in aslsa-base :)

```
$ cat /etc/modprobe.d/alsa-base
options snd-hda-intel model=lifebook

```

If it won't work, the last chanse to get it work is to remove pulseaudio, IMHO.

---

### Post by pignic on 2010-06-21
Oh Yeah, it works, good job !

Thanks a lot

---

### Post by pryzah on 2010-06-22
Worked for me too(asus k42Jr Ubuntu 10.04):
1. Updated alsa as **lidex** suggested: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810]("http://ubuntuforums.org/showthread.php?p=6589810#post6589810").

(Brief instructions (but i recommend to read everything in link above):
1. download the script and save it somewhere(it is in attachments)
2. cd <your-download-dir>
3. tar xvf AlsaUpgrade-1.0.23-2.tar
4. sudo ./AlsaUpgrade-1.0.23-2.sh -d
5. sudo ./AlsaUpgrade-1.0.23-2.sh -c
6. sudo ./AlsaUpgrade-1.0.23-2.sh -i
7. sudo shutdown -r 0)

2. Added "options snd-hda-intel model=lifebook" into file /etc/modprobe.d/alsa-base.conf

Thanks everybody!! At last i have sound in my headphones!!! :p

---

### Post by felyn on 2010-06-23
Also works for K42JK-VX026 using Lucid. 

1. Removed pulseaudio: [URL="http://art.ubuntuforums.org/showthread.php?t=1313253"]http://art.ubuntuforums.org/showthread.php?t=1313253
[/URL] I only did the following lines though
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
```2. Ran lidex's script:  [URL="http://ubuntuforums.org/showthread.php?p=6589810#post6589810"]http://ubuntuforums.org/showthread.php?p=6589810#post6589810
[/URL] 
3. Added the following to  /etc/modprobe.d/alsa-base.conf as mekh had suggested
```
options snd-hda-intel model=lifebook
```I don't know if removing pulseaudio made any difference though. I am an absolute linux noob. Thank you so much everyone!!!

---

### Post by zzzliperzzz on 2010-06-26
> **felyn said:**
> Also works for K42JK-VX026 using Lucid. 

1. Removed pulseaudio: [URL="http://art.ubuntuforums.org/showthread.php?t=1313253"]http://art.ubuntuforums.org/showthread.php?t=1313253
[/URL] I only did the following lines though
```
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio
sudo apt-get autoremove
```2. Ran lidex's script:  [URL="http://ubuntuforums.org/showthread.php?p=6589810#post6589810"]http://ubuntuforums.org/showthread.php?p=6589810#post6589810
[/URL] 
3. Added the following to  /etc/modprobe.d/alsa-base.conf as mekh had suggested
```
options snd-hda-intel model=lifebook
```I don't know if removing pulseaudio made any difference though. I am an absolute linux noob. Thank you so much everyone!!!

Thanks. this solve my problem.
Thanks for all the help guys.
More power for all of you.
Don't stop helping Ubuntu Users. :D

---

### Post by felyn on 2010-06-27
After doing the steps above, I realized that rhythmbox wouldn't play any sound if I opened videos in youtube. I searched around and found this fix:[ http://ubuntuforums.org/showthread.php?t=1455816]("http://ubuntuforums.org/showthread.php?t=1455816")

/etc/asound.conf didn't exist for me, so I just made the file, pasted the code in, rebooted and it worked. Everything looks good so far.

Hopefully this helps someone else too.

---

### Post by lidex on 2010-06-27
Has anyone tried this fix without removing pulseaudio? And did it work?

---

### Post by felyn on 2010-07-01
So I was playing with some of the configuration files on my system and I broke something. I thought I'd just reinstall ubuntu since it was a new PC anyway and I didn't really have anything on it yet.

This time I didn't remove pulseaudio while upgrading to ALSA since I read somewhere that ubuntu was going with pulseaudio for future versions of ubuntu. So I upgraded ALSA and edited asound.conf, and everything worked. So yes, the ALSA upgrade does seem to work with pulseaudio. At least on my system anyway :p

---

### Post by amirkabir on 2010-07-17
Thanks everyone, all my researches last 2hr, and come to an end with this useful  _thread._
I've just add this line 
```
options snd-hda-intel model=lifebook
```into file /etc/modprobe.d/alsa-base.conf

No i don't remove **pulseaudio** [lidex.]("http://www.uluga.ubuntuforums.org/member.php?u=577099")

---

### Post by lidex on 2010-07-17
Awesome, guys, thanks for the feedback!

---

### Post by midnightcarousel on 2010-08-03
> **lidex said:**
> Try this. Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot

This worked for me, thanks!

---

### Post by papermeh on 2010-08-21
> **zzzliperzzz said:**
> Thanks. this solve my problem.
Thanks for all the help guys.
More power for all of you.
Don't stop helping Ubuntu Users. :D
i have ASUS A42JV, this solution is not working for me...
any other solution?? or i just miss out something??

---

### Post by lolivivi on 2010-08-21
I'm from this problem, please help us to answer.

---

### Post by lidex on 2010-08-22
> **papermeh said:**
> i have ASUS A42JV, this solution is not working for me...
any other solution?? or i just miss out something??

Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by alxmichael on 2010-09-14
i have k42jk-vx026, a complete linux noob.i can't seem to edit the alsa-base.conf file (something to do with the file permission). please help, i can't add the options snd-hda-intel model=lifebook line.

---

### Post by zzzliperzzz on 2010-09-14
> **alxmichael said:**
> i have k42jk-vx026, a complete linux noob.i can't seem to edit the alsa-base.conf file (something to do with the file permission). please help, i can't add the options snd-hda-intel model=lifebook line.

Use sudo.
[CODE]
$ sudo gedit /etc/modprobe.d/alsa-base.conf
[CODE]

(I'm not sure if that is the correct path.)
Enter your password when prompted. :)
Good luck. :)

---

### Post by lidex on 2010-09-15
> **zzzliperzzz said:**
> Use sudo.
[CODE]
$ sudo gedit /etc/modprobe.d/alsa-base.conf
[CODE]

(I'm not sure if that is the correct path.)
Enter your password when prompted. :)
Good luck. :)

Make sure to use either gksudo or gksu rather than plain sudo as this is a graphical app.

---

### Post by zzzliperzzz on 2010-09-15
> **lidex said:**
> Make sure to use either gksudo or gksu rather than plain sudo as this is a graphical app.

Thanks for the info.:D

---

