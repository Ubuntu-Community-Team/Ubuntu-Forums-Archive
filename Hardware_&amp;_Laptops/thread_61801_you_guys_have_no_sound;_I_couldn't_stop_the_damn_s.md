---
title: "you guys have no sound; I couldn't stop the damn sound!"
date: 2005-09-02
forum: Hardware &amp; Laptops
---

### Post by agro1986 on 2005-09-02
When the gnome login screen appears, my Ubuntu makes a repeated sound of "thud" (drum beat). So it goes like

thud... thud... thud... thud...

Argh!

It's an onboard sound. Device manager says that the sound device is CM8338A. Old PC-CHIPS mobo for Pentium II (dunno the model).

Tried "system"-"preferences"-"sound" and turned the tick off for "enable sound server startup" but the THUD goes on...

Tried "system"-"preferences"-"multimedia systems selector" to test out all default audio sink but what I get is the error message "Failed to construct test pipeline".

totem gives "Could not open resource for writing." error when I try to open an mp3.

Well, the sound card has proven itself capable of sending output (the almighty thugs) into the speaker. The problem is, how do I make it behave sanely?

Can someone point me in the right direction?

Thanks a lot,

Agro

---

### Post by agro1986 on 2005-09-02
OK guys, here's what I have tried...

1) sudo apt-get install linux-headers-2.6.10-5-386 (I guess it's needed to compile alsa driver)
2) Installed alsa-driver-1.0.9b (on ./configure I added --with-cards=cmipci --with-sequencer=yes)
3) Installed alsa-lib-1.0.9
4) Installed alsa-utils-1.0.9a
5) opened /etc/modules, added snd-cmipci, snd-pcm-oss, snd-mixer-oss, snd-seq-oss

After reboot, the result is........

It THUDS faster...

thud.thud.thud.thud.thud (faster tempo then the previous one)

Yea, let's dance baby!!!

I'm eagerly wating for alsa 1.1 to make it thud even faster... :)

Seriously, anyone know a solution...??

Thanks,

Agro

---

### Post by pakux on 2005-12-03
hey, finally someone with my same issue !!!!

at least we're two now for "thuding"....

i've been googgling around for a couple of weekends and it seems everybody with this d@mn chipset has some troubles, but as you mentioned they all didn't get sound whereas we're becoming mad with the drums.

i've managed to stop the noise with a sudo killall aplay; however something goes really bad because if i try to reproduce some other sound or even to change the multimedia system and test the pipeline it starts again to repeat the first second continuously.

did you solve it? does anybody else know to explain this bizarre issue?

---

### Post by kosako on 2005-12-17
[QUOTE=pakux]hey, finally someone with my same issue !!!!

at least we're two now for "thuding"....
[...]
did you solve it? does anybody else know to explain this bizarre issue?[/QUOTE]

At least we're three :(

I did solve partially that by compiling my kernel. The results: Ubuntu did not recognize the card, BUT... excepting system sounds, the sound worked fine (using oss). The trouble: I had to reinstall Ubuntu from scratch (damn Duffy, sorry, Dappy or whatever) and I was trying to fix the problem in the right way, with terrible results :). Using alsa the drums are faster, using esd and oss slower... Just now, the solution is #killall aplay at startup, and #killall esd when gaim is doing the thing.

Using the multimedia sound howtos I read, the trouble is similar, but with particularities: I can have now multiple instances of the thud issue, I mean, i.e., I get the crash with multiple sounds at the same time.

My guess: the card's having trouble with the IRQ. In my case, Ubuntu discard the card IRQ at start up; I will try tomorrow loading the module giving the right parametes... (I saw that this's possible through modprobe). If works I'll post here, if don't... too :). If you guys find a solution, just whistle :).

---

### Post by rj_jedi on 2006-01-11
well, there are atleast 4 of us now..
i really could do without my own personal non-stop drum solo.
any progress?

---

### Post by XiX on 2006-01-20
Hi there

I have the same problem :(
I have also a soundcard which is onboard and did the steps described in:
[http://www.ubuntuforums.org/showthread.php?t=78618&page=2](http://www.ubuntuforums.org/showthread.php?t=78618&page=2) to get any sound... but now I have the neverending "THUD" problem :(

Any solution??

Today I will get a new soundcard, maybe this will change the things... hopefully!?

TiA XiX

---

### Post by samden on 2007-02-07
That drum beat sound is intended to alert you to the fact that the screen is ready for you to log in I believe. It should run for a second then stop - if it is not stopping that is strange.

I believe if you go into System>Login Window and play with the settings in there you may be able to turn it off.

---

