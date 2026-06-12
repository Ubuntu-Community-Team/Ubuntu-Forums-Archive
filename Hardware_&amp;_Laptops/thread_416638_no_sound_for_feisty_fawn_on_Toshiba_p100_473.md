---
title: "no sound for feisty fawn on Toshiba p100 473"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by ben_jammin on 2007-04-21
Hello,

I've just installed feisty fawn on Toshiba p100 473 laptop, and have no sound. The sound card is recognized, I have the choice between
HDA Intel (Alsa mixer)
Conexant CX20549 (Venice)(OSS Mixer)

and Alsa seems to be working.

I tried turning acpi=off at boot, as indicated in some threads, but still no sound.

Any help, anyone ? It would be greatly appreciated :)

---

### Post by wastedtime on 2007-04-21
I am not sure if this will work.. try typing alsamixer in the terminal. on the screen that comes up check if the master and pcm are set to something more than 00 .

or maybe this will help

[http://ubuntuforums.org/showthread.php?t=416207](http://ubuntuforums.org/showthread.php?t=416207)

---

### Post by ben_jammin on 2007-04-21
no, none of these solutions worked ...

---

### Post by cptcrunch on 2007-04-25
I have the exact same problem. I have a Toshiba Satellite Pro P100 laptop. I installed Kubuntu 7.04 Feisty. I managed to get the display working properly with this site

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

>lspci -v | grep -i audio

Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I tried installing the drivers libraries and utils (I think they need to be built using a compiler) using the instructions from

[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-inte](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-inte)
l

but was not successful yet. I'm a newbie to Linux. I'll keep trying.

turning ACPI off is a bad fix, after all, what good is a laptop without it??

---

### Post by **Jas** on 2007-04-25
Same for me, After a lot of stuffing around got the nvidia drivers working and the "cube effect looks great".

However no sound. :( 
Toshiba P100

Please post up any solutions if you have managed to get this to work.

Cheers
Jas

---

### Post by ben_jammin on 2007-04-26
Mmm, I''ve tried again, and the problem seems to be coming from the alsa drivers. I can't compile them, I guess we need to wait for alsa to update ??

---

### Post by cptcrunch on 2007-04-26
I found this HowTo

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I'll give it a go and see what happens.

---

### Post by cptcrunch on 2007-04-27
:(  Still no luck with sound issues. Yes, I guess we need to wait for a driver update from ALSA.

---

### Post by ben_jammin on 2007-04-27
Argh, hard luck :(  Yeah, I guess we need to wait for an ALSA update, after all, this laptop is pretty new, so I wouldn't be surprised if we have to wait a few weeks...

---

### Post by chriswyatt on 2007-05-02
[http://ubuntuforums.org/showthread.php?t=415363]("http://ubuntuforums.org/showthread.php?t=415363")

The solution here didn't work for me.  I managed to get a sound when I tried Test Sound in Sound Preferences but didn't get sound from anywhere else.  Test Sound stopped working when I plugged and unplugged my USB soundcard :( .  This is a popular chipset which really needs better support, hopefully it'll get fixed soon :) .

---

### Post by **Jas** on 2007-05-04
I went through a lot of the methods tried above as well as a few others and the alsa help page without success.  I was prepared to wait for a solution and cope without sound until I released last night I have another major problem.  The fan for the laptop would only idle and the bottom of the laptop was cooking!!  I rebooted and whilst the POST screen was one the fan went straight to full speed but as soon as ubuntu loaded the fan went back to idle.  

A lack of sound whilst annoying, I could live with but the fan not working correctly is not an option.  Hence fixmbr.exe and partition magic have restored my laptop back to XP-Pro.  :( 

Maybe next release .....

---

### Post by cptcrunch on 2007-05-07
Did you turn ACPI off?

---

### Post by EndPerform on 2007-05-07
I had the same issue with my Toshiba laptop (model P105-S6227).  Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

It's an ACPI issue.  Be aware it might not work, but it's worth a shot.  It worked fine for me.  Turning off ACPI will mean your fans will probably stay on constantly.

---

### Post by cptcrunch on 2007-05-24
Update: I now managed to obtain audio with the help of this thread

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

this may be of help to others with Toshiba laptops.

Cheers :)

---

### Post by cookies on 2007-05-24
Oo, glad I found this thread. Hope it'll work for me when I get Feisty onto my P105- S9772.

---

### Post by Jad on 2007-05-24
I'm not fan of turning of ACPI on laptops.

---

### Post by cptcrunch on 2007-05-24
> **Jad said:**
> I'm not fan of turning of ACPI on laptops.

I have sound with ACPI on

---

