---
title: "Shuttle XPC SB95P"
date: 2005-05-23
forum: Hardware &amp; Laptops
---

### Post by fbn on 2005-05-23
Hi,

is anybody using Ubuntu Linux on a Shuttle XPC SB95P or knows somebody who does?

I hope that I'm not the only one with this type of hardware because it would be nice to share some experiences ...

Regards,
  Frank

---

### Post by rdjurovich on 2005-07-04
Hi Frank,

I have been running Hoary on my SB95P (v2) for a couple of weeks now and everything appears to be working fine, except for my soundcard isn't found.
Are there any problems you are having? I am a full time Ubuntu user and would love to be able to hear things :)

---

### Post by fbn on 2005-07-05
[QUOTE=rdjurovich]Hi Frank,

I have been running Hoary on my SB95P (v2) for a couple of weeks now and everything appears to be working fine, except for my soundcard isn't found.
Are there any problems you are having? I am a full time Ubuntu user and would love to be able to hear things :)[/QUOTE]
 My soundcard is working fine as I can hear sound. But it's only possible to activate the back output of the soundcard, SB95P also has nice front audio ports which can be used with headsets for example - they don't work.

Do you have SATA harddisks in your system? I've experienced some issues with Ubuntu installation on these disks also.

---

### Post by rdjurovich on 2005-07-05
Yes I do have SATA but no problems for me.
This is odd, that you have no problems with sound but with SATA, and I have problems with sound and not SATA.
Do you have the SB95P or SB95Pv2?
Also, what version of the bios are you running? (I am running the latest, which is "n").

P.S. Did you have to do anything special for the soundcard to work? Also, what colour port did you use on the back?

---

### Post by fbn on 2005-07-05
Ryan,

I don't remember exactly but I think that I had to disable SATA in BIOS and use the harddisks as normal ATA for Ubuntu installation. First thing I did was building my own kernel from sources after that I was able to enable SATA again.

I will do a fresh install with the new Ubuntu release in October, would be nice to use the Ubuntu default kernel then :)

There are drivers for Linux available from Realtek for the audio device on the SB95P mainboard which I have, not sure if the same audio device is in SB95Pv2.
I'll have a look at lspci at home, can't do this now because I'm at work.

Do you have a Jabber/XMPP account?

Frank

---

### Post by rdjurovich on 2005-07-05
Now it makes sense that your soundcard works and mine doesn't - you have the original SB95P with a realtek chipset - the SB95Pv2 has the brand new Intel HD Audio chipset, which my Ubuntu doesn't seem to like. I think I have to compile alsa from source or something, so I will look into that a little later.

About Jabber - I have just been reading more into it (I heard about it a while ago, but never really was interested), and have now signed up with jabber.org.au - my account is [email]rad@jabber.org.au[/email]  :)

---

### Post by sunscape on 2005-07-05
I don't have an XPC but I have just ordered a motherboard with Intel HD sound and I would love to get it working :-P.

---

### Post by fbn on 2005-07-06
Jabber is nice I like it :)

Are the other components working on your system?

I experienced an issue while unmounting USB devices (USB stick for example): complete system freeze ... 

Is the card reader working for you?

---

### Post by rdjurovich on 2005-07-06
I have just tested the card reader with a CF card and everything works fine!

Something else interesting... I GOT MY SOUND WORKING!!! :) 
Wanna know how? I simply followed the steps found here:
[http://wiki.ubuntu.com//HdaIntelSoundHowto](http://wiki.ubuntu.com//HdaIntelSoundHowto)
(I used the first method, not the second - it was really easy though - I simply downloaded 4 files, extracted them, and did what the intructions said - very easy!)
This is why I love Ubuntu - the HOWTO's are awesome! :) 

Hopefully that link above helps you, sunscape ;-)

Well, as for now, I know everything on my system works - except sometimes shutting down doesn't quite work (it ends with loud fan, no vga output, and doesn't ever power down). Not to worry though, as the shutdown problem is just a little annoying, and doesn't seem too be a serious problem (I will just have to keep my machine on).

 :)

---

### Post by fbn on 2005-07-06
[QUOTE=rdjurovich]I have just tested the card reader with a CF card and everything works fine!

Something else interesting... I GOT MY SOUND WORKING!!! :) 
Wanna know how? I simply followed the steps found here:
[http://wiki.ubuntu.com//HdaIntelSoundHowto](http://wiki.ubuntu.com//HdaIntelSoundHowto)
(I used the first method, not the second - it was really easy though - I simply downloaded 4 files, extracted them, and did what the intructions said - very easy!)
This is why I love Ubuntu - the HOWTO's are awesome! :) 

Hopefully that link above helps you, sunscape ;-)

Well, as for now, I know everything on my system works - except sometimes shutting down doesn't quite work (it ends with loud fan, no vga output, and doesn't ever power down). Not to worry though, as the shutdown problem is just a little annoying, and doesn't seem too be a serious problem (I will just have to keep my machine on).

 :)[/QUOTE]
 Good to hear that you've got your sound working :)

What about the front and back outputs (I think you have them too with your SB95Pv2) - are they both working? With the Windows driver I have the possibility to select what device is on which output/input port (microphone, headspeakers, desktop speakers, ...) but on Ubuntu I can only choose one input and one output on the back, the ones on front are ignored.

And have  you ever tried to unmount an USB stick? :)

Shutting down is also sometimes an issue with my system, but a bit different than you've described.

Are you satisfied with the hardware performance on your Ubuntu system? We could do some performance benchmarks and compare them ... :)

---

### Post by sunscape on 2005-07-06
Thanks for the help! Here goes :-D

---

### Post by rdjurovich on 2005-07-07
Something very interesting... when you asked about the front panel audio connections, i decided to open up the mixer and noticed when clicking "File>Change Device" it had to devices - one of which was the "HD Intel" device.
I then noticed when clicking "Edit>Preferences" it had a whole heap of options such as "Front","Front Mic","Centre","Surround", etc.
However, I turned the volume up on "Front" and plugged my speakers in the front, and no noise came out, so I am guessing I am missing something else. At least I know they have built in previon for this to work in future (or now, if I could work it out).

USB sticks - yes unmounting seems to work fine.

Benchmarks - I dont really care that much about performance as I dont have much time to learn how to run benchmarks (new territory for me), but I am always willing to learn if you think it would be that interesting.

I am happy with SB95Pv2 as is at the moment - as long as things stay this way! :smile:

---

### Post by rdjurovich on 2005-07-07
I just noticed that muting "Front" when my speakers are plugged in the back stops sound - so I am guessing maybe it is a bug or something I dont understand.

---

