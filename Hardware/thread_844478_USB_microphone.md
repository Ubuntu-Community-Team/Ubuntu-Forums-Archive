---
title: "USB microphone"
date: 2008-06-29
forum: Hardware
---

### Post by catonano on 2008-06-29
Hello people,

I have a Dell Vostro 1700 and the sound card is not supported, so the microphone does not work and so Skype cannot be used on that machine. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=750407")

I'd love to know about a USB microphone that "just works".

The person that will have to plug it in is a secretary, she won't be able to try around with the drivers.

A mike like [this]("http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=us,en") would be good but anyone could do. The important thing is that it _just works_.

Thanks for any hint
Bye
Cato

---

### Post by kessaris on 2008-06-30
I've successfully gotten the logitech to work under linux before!

[http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=us,en](http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=us,en)

I actually got it working with Skype too, version 1.5.  Version 2 of skype is even better in that it lets you choose your audio device settings.

another option might be a USB soundblaster external sound card, but I'm not sure if those work under linux.. I would suspect that they do..

Oh, I just noticed you were linking to the same page.  It doesn't list linux compatibility, but if they are still using the AK5370 hardware, it worked reasonably well when I used it.

---

### Post by ukripper on 2008-06-30
> **catonano said:**
> Hello people,

I have a Dell Vostro 1700 and the sound card is not supported, so the microphone does not work and so Skype cannot be used on that machine. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=750407")

I'd love to know about a USB microphone that "just works".

The person that will have to plug it in is a secretary, she won't be able to try around with the drivers.

A mike like [this]("http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=us,en") would be good but anyone could do. The important thing is that it _just works_.

Thanks for any hint
Bye
Cato

Your internal mic can work using this guide [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)

And there is whole wiki devoted to your laptop here
[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700)

---

### Post by catonano on 2008-06-30
> **kessaris said:**
> I've successfully gotten the logitech to work under linux before!

[http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=us,en](http://www.logitech.com/index.cfm/webcam_communications/microphones/devices/221&cl=us,en)

I actually got it working with Skype too, version 1.5.  Version 2 of skype is even better in that it lets you choose your audio device settings.

another option might be a USB soundblaster external sound card, but I'm not sure if those work under linux.. I would suspect that they do..

Oh, I just noticed you were linking to the same page.  It doesn't list linux compatibility, but if they are still using the AK5370 hardware, it worked reasonably well when I used it.

Thank you, that's helpful ! 

In the meantime, I found [this]("http://www.amazon.com/review/product/B0007ZFM38/ref=cm_cr_pr_link_3?_encoding=UTF8&pageNumber=3&sortBy=bySubmissionDateDescending") and there's a guy reportin it worked under Feisty Fawn (7.x).

Now, I wonder, since it worked in Feisty, is it reasonable to assume that it's going to work under Hardy Heron too ?

I already found that item on ebay and I was going to buy it...

Thanks so much anyhow
Bye
Cato

---

### Post by catonano on 2008-06-30
> **ukripper said:**
> Your internal mic can work using this guide [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work)

And there is whole wiki devoted to your laptop here
[https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700](https://wiki.ubuntu.com/InstallingUbuntuOnADellVostro1700)

Ukripper,

thank you, but:


this guide [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Built_In_Digital_Mic_Does_Not_Work) refers to a .deb package that requires kernel 2.6.22.14 to be there and I suppose it was the Gutsy kernel. On m hardy Heron I see the 2.6.24.16 and 2.6.24.19 only. So The backports from Dell won't work because of a dependancy not satisfiable.

Also, most of the issues in the wiki refer to Gutsy !

Thanks for your help, though; I didn't know about the Dell support sites

Bye
Cato

---

### Post by sunnyabc on 2008-08-06
I Post reply thinking this might be helpful.
I have struggled with buil-in microphone on my Vosotro 1500 laptop,
but, mic is now working fine with Ubuntu 8.04 (2.6.24-19-server).

My /etc/modprobe.d/alsa-base includes the follwing:
options snd-hda-intel model=dell-m44

dell-m42, dell-m43, dell-m44, ref can be tried.
Find out appropriate device name from [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

In alsamixer, increase volume for two *Capture*, turn off *Analog Loopback*, set *Digital Input Source* to Digital Mic 1, increase volume for two *Mux*.

I tested mic using gnome-sound-recorder which is easily found in Application tab on gnome desktop. When recording, set *Record from input* to *Capture* or *Capture1*.

Just in case, I installed alsa-driver, alsa-lib, and alsa-utils (1.0.17) from sources as advised in [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
Have a look at section entitled *Update to the Latest Version of ALSA*

---

