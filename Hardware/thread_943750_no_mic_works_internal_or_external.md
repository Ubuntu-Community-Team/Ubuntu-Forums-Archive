---
title: "no mic works internal or external"
date: 2008-10-10
forum: Hardware
---

### Post by shane2peru on 2008-10-10
Ok, this is a serious issue.  I have a Toshiba Satellite laptop.  I found out my mic doesn't work.  Sound works great, just no mic.  I'm running 64 bit (for the record).  Here is the output of a line I found searching the forums:
```

head -n 1 /proc/asound/card0/codec*
Codec: Conexant CX20561 (Hermosa)

```
That is my hardware.  It has an internal mic, and web cam, neither work.  I plugged in my external mic, and it doesn't work either.  Please don't tell me I have to start dual booting.  I have been using Linux exclusively for several years now.  Any help would be greatly appreciated.

Shane

---

### Post by markbuntu on 2008-10-10
What model Toshiba laptop?
What does aplay -l tell you?

---

### Post by shane2peru on 2008-10-10
> **markbuntu said:**
> What model Toshiba laptop?
What does aplay -l tell you?

Hey markbuntu, I have read several of your posts on this issue.  Any rate here is the aplay -l output:
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

My toshiba Satellite model is:  M305D-S4830

Thanks for taking a crack at this.

Shane

---

### Post by markbuntu on 2008-10-10
These threads cover most HDA devices, including the HDA ATI SB series. have a look at them.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

You can also look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by shane2peru on 2008-10-14
> **markbuntu said:**
> These threads cover most HDA devices, including the HDA ATI SB series. have a look at them.

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

You can also look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

OK, it has taken me three days, but I have worked through these threads all to no avail. :(  At one point I had no sound. I have Alsa x.18-rc3 version installed using the scripts from one of those posted.  I tried the x.17 stable version too to no avail.  It seems as though my chipset (Conexant cx20561) is not specifically mentioned anywhere.  I think it is just very new, and not supported yet by alsa.  I do have sound, and it does work, I just am really disappointed by not having a mic.  I looked at going to OSS for my sound, but doesn't look like it is supported there either.  Any specific help would really be appreciated.  I'm really at a loss here as to how to fix this.  And it looks bad for me (and Linux) because of the amount of people I have told about the greatness of Linux, now I cannot Skype with those same people because I don't have a mic.  Ahh.  Not good.  We are taking a serious hit here.  (Most of these people only use Skype because I use it because it was all I could get to work with Linux)

Shane

---

### Post by markbuntu on 2008-10-14
If that is the case, a usb headset would probably be your best bet. Since it is an entirely separate device and they seem to work out of the box ( I have seen no complaints of a usb headset not working), you should have no problem with using it for skype. Plus you can get one pretty cheap these days.

---

### Post by shane2peru on 2008-10-14
> **markbuntu said:**
> If that is the case, a usb headset would probably be your best bet. Since it is an entirely separate device and they seem to work out of the box ( I have seen no complaints of a usb headset not working), you should have no problem with using it for skype. Plus you can get one pretty cheap these days.

Thank you and just in the nick of time!  Got a Skype call just a few minutes after testing and setting up the microphone through my usb camera that I know works with Linux. :)  Soo, I guess I will be shopping for a usb type headset.  Any recommendations???  I want to get something that works. 

Shane

---

### Post by shane2peru on 2008-10-14
AHHHHH I'm pulling my hair out!  This is crazy.  Ok, I now have a mic that records in Audacity, but not in Sound Recorder, and it doesn't work in Skype!!!  It is through the OSS sound not alsa.  I didn't change anything other than what I had changed before.  The plug-in mic doesn't work either and the built in mic (it is a laptop) works but sounds tinnny on the recording.  The usb camera mic works fine with Skype. The problem is that we have about 100 different sound options, and someone (me) that doesn't know what they are doing trying to set it up.  I'm open for ideas and suggestions here.  Also my internal web cam works for a little bit with skype and then seems to crash and quit sending pictures.  I did no configuration with that.

Shane

---

### Post by markbuntu on 2008-10-14
I was hoping we could avoid this because it can be very long and involved for you, but you can look through my 10,000 page guide to sound in Ubuntu and that may help you fix most of your problems:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by shane2peru on 2008-10-14
yes, I was trying to avoid the 10,000 page guide as well, I saw it in another post. :D  that is what spurred this new post.  :lol:  well, I guess if there is no other way, I will have to start reading through the 10,000 pages.  Thanks for the info.  Perhaps I will become a sound setup expert on this when all is said and done! lol.  At least I got enough to work with for now, and can work on getting it better.  Thanks for all the help!


Shane

---

### Post by shane2peru on 2008-11-07
Ok, I'm getting mixed things here, and I'm not sure what my sound card is.  Here is a series of commands that I have plugged in:

```

 cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf0000000 irq 17

```
```

 head -n 1 /proc/asound/card0/codec*
Codec: Conexant CX20561 (Hermosa)

```
```

 lspci -v | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

```
```

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
OOOOk, all that being said, I'm working on a laptop with an internal Microphone and Webcam.  I did a fresh install of Ubuntu Intrepid 64bit Final RC.  I then did all the updates except the kernel update.  I was using the RC intrepid before it was released and my sound seemed to work better, after the kernel update it broke everything, and left me with a mess, that is why I re-installed.  My sound now works, but is touchy, if I mess with volumes, or mute it, It goes bersurck, and I have to really fiddle with things before I can get my sound back.  This is a very highly annoying problem and I really need someone help me figure out what device I need to work on, should I use Alsa, Pulse, or OSS4.1?  Any help would greatly be appreciated.

Shane

---

### Post by amdg on 2008-11-30
I have gotten my internal microphone working using OSS 4.1. My laptop is a Toshiba Satellite M305D-S4829.

I have written instructions [here]("http://blog.tagabunot.com/2008/11/30/toshiba-satellite-m305d-working-microphone/") but since I'm running Gentoo Linux, you'll have to figure out how to do it in Ubuntu.  Hopefully that can point you in the right direction though.

---

### Post by shane2peru on 2008-11-30
Thanks for bringing this thread back up, I had forgotten about it.  I also got my internal mic working via OSS 4.1.  I followed this thread:  

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

It works very well for me.  Even did a kernel upgrade (I think it just an upgrade of the same kernel number), and it didn't mess up my sound!!! Perhaps lucky this time around.  At any rate OSS4.1 is great!

Shane

---

### Post by maolin on 2008-12-03
Hi Shane2peru:

In this moment, is your internal mic working?
If the answer is "yes", please help me!!!
I already have a problem with sound like you did. I have the next config in my laptop:

```

mauro@mauro-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0500000 irq 22
mauro@mauro-laptop:~$ head -n 1 /proc/asound/card0/codec*
Codec: Conexant CX20561 (Hermosa)
mauro@mauro-laptop:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
mauro@mauro-laptop:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: Conexant Digital [Conexant Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```
 
and I have spend too much time trying to fix my internal mic!!!... I followed your thread... but the problem already exists!!!!....  My sound with ALSA works well, but my mic doesn't work yet... was OSS your exit for succesfull???... 

Thanks for reply!!!

---

### Post by shane2peru on 2008-12-03
> **maolin said:**
> Hi Shane2peru:

In this moment, is your internal mic working?
If the answer is "yes", please help me!!!
I already have a problem with sound like you did. I have the next config in my laptop:

```

mauro@mauro-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf0500000 irq 22
mauro@mauro-laptop:~$ head -n 1 /proc/asound/card0/codec*
Codec: Conexant CX20561 (Hermosa)
mauro@mauro-laptop:~$ lspci -v | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
mauro@mauro-laptop:~$ aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: Intel [HDA Intel], dispositivo 1: Conexant Digital [Conexant Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```
 
and I have spend too much time trying to fix my internal mic!!!... I followed your thread... but the problem already exists!!!!....  My sound with ALSA works well, but my mic doesn't work yet... was OSS your exit for succesfull???... 

Thanks for reply!!!

It seems that OSS is your only answer.  I couldn't get it working with Alsa.  I'm no expert, but OSS provided a relatively quick fix for me, and after all was said and done, seems to work very well.  

See my post just above yours for the guide to install OSS.

Shane

---

### Post by RussellHill on 2009-01-26
> **shane2peru said:**
> AHHHHH I'm pulling my hair out!  This is crazy.  Ok, I now have a mic that records in Audacity, but not in Sound Recorder, and it doesn't work in Skype!!!  It is through the OSS sound not alsa.  I didn't change anything other than what I had changed before.  The plug-in mic doesn't work either and the built in mic (it is a laptop) works but sounds tinnny on the recording.  The usb camera mic works fine with Skype. The problem is that we have about 100 different sound options, and someone (me) that doesn't know what they are doing trying to set it up.  I'm open for ideas and suggestions here.  Also my internal web cam works for a little bit with skype and then seems to crash and quit sending pictures.  I did no configuration with that.

Shane

 About Skype... well I do not know why they prefer to support ALSA over OSS, but they provide a special version of Skype with OSS support. This is currently the best solution to get Skype working with OSS. Download Skype with OSS support here: [http://www.skype.com/go/getskype-linux-oss](http://www.skype.com/go/getskype-linux-oss)

---

### Post by shane2peru on 2009-02-07
> **RussellHill said:**
> About Skype... well I do not know why they prefer to support ALSA over OSS, but they provide a special version of Skype with OSS support. This is currently the best solution to get Skype working with OSS. Download Skype with OSS support here: [http://www.skype.com/go/getskype-linux-oss](http://www.skype.com/go/getskype-linux-oss)

Yep, I have that one, forgot I had posted about that.  Thanks!

Shane

---

