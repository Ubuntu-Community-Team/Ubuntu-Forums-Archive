---
title: "Asus A6Q00VC won't boot"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by ertai on 2005-11-11
I have tried to install Ubuntu 5.10 on my laptop (a Asus A6Q00VC). It installed correctly but didn't boot. When it came to starting the hotplug system it stopped. I could only turn the laptop off by holding the powerbutton. When I tried to boot in recovery-mode it stopped with the message "missing kernel or user mode driver hw_random"

I also tried the 4.10 livecd (which i still had) and that started.

Does anyone know why?

---

### Post by zonk on 2005-11-11
Hi ertai!

When your system boots, had it comes to hotplug press "Ctl-c" then hotplug won't be started, and probably your system will boot.
I think this has to do with the sound. It is known that breezy doesn't like the intel hda sound chipset(codec?).
If you do have the intel HDA sound chipset you need to put the modules  snd-hda-intel on the  /etc/hotplug/blacklist .

Then your system will boot(hopefully).
And there is a Howto to get your sound working again. I'll sent you the url as soon as i find it.
Hope I could help.


cheers

zonk

---

### Post by zonk on 2005-11-11
By the way:
Take a look at:
[www.linux-on-laptops.com](www.linux-on-laptops.com)

or on [www.tuxmobil.org](www.tuxmobil.org)

there you will find a lot of information about linux-on-laptops.;) 

cheers


zonk

---

### Post by ertai on 2005-11-13
thnx.. It works now..

pressing "Ct-C" during the boot didn't work. But when I rebooted with the 4.10 Live-cd and adjusted the /etc/hotplug/blacklist by adding the snd-hda-intel module. Then it worked and I am now posting this from my laptop.

Many thanks. Now I can work fine with ubuntu

---

### Post by zonk on 2005-11-13
Hi ertai.

If you want to try you can still have sound. What I did to get sound working was easy. Just try this:
First get alsa-sources eg. with synaptic.
the go to /usr/src/

untar  with:  tar xfj alsa-driver.tar.bz

then:

cd linux-headers-`uname -r`  (uname -r stands for your kernel, you are using.)
sudo make-kpkg --rootcmd=fakeroot --append-to-version=-9-386 modules-image (just replace -9-386 with your own kernel header.)

After that go back to 
cd..
and do a 
sudo dpkg -i alsa-modules-`uname -r`_1.0.9b-4+10.00.Custom_i386.deb
Your name can of course be different!

After that you should remove the modules from the blacklist, boot and sound should be working! At least it does with the Chipset: ALC880 

If not try:
sudo gedit  /etc/modprobe.d/sound

and add:

options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

I hope it works. 


cheers 

zonk

---

### Post by ertai on 2005-11-19
Hi zonk,

I tried your explenation. But I can't download the right package I think.
When i download the sources of the alsa-driver I don't have the linux-headers.

But when I just ignore that rule and make the package it begins and then gives a bit of C-code as output and stops.

I'm sorry I can't give you the error here because my laptop died. The harddisk is broken and the laptop is back to the shop to be fixed. I can try again in a week or 2.

Hopefully you'll help me then if I can paste the output I've had.

Thnx

---

### Post by zonk on 2005-11-19
Hi, ertai.

I'm sorry i forgot to tell you that you need to download the kernelheaders as well. And of course the right ones for your kernel. try typing "uname -r" in a shell an you'll see what kernel you are currently using. Then download the right linux-headers with synaptic. And you will then find them in /usr/src/linux-headers-....
Then you can do what i wrote you before. 

If it doesn't work you can of course send me a message.
Hope you'll get your laptop back soon.


zonk.

---

### Post by filos on 2005-11-26
[QUOTE=zonk]untar  with:  tar xfj alsa-driver.tar.bz

then:

cd linux-headers-`uname -r`  (uname -r stands for your kernel, you are using.)
sudo make-kpkg --rootcmd=fakeroot --append-to-version=-9-386 modules-image (just replace -9-386 with your own kernel header.)

After that go back to 
cd..
and do a 
sudo dpkg -i alsa-modules-`uname -r`_1.0.9b-4+10.00.Custom_i386.deb
Your name can of course be different!

[/QUOTE]

I have the same computer, same problem. 
I've tried to do what I've just quoted:
sudo make-kpkg --rootcmd=fakeroot --append-to-version=-9-386 modules-image [COLOR="Lime"]oks it does[/COLOR]
cd..

[COLOR="Red"]sudo dpkg -i alsa-modules-`uname -r`_1.0.9b-4+10.00.Custom_i386.deb   here it stops and says alsa-modules-...  can't' be find[/COLOR]
maybe I've wrong something with the Synaptic packages and forgot something (I'm noob :( ) , I don't' know.

Is there also an howto for resolving problem wih audio intel chipset? Maybe I just need that ;)

---

### Post by mengqing on 2005-11-26
[QUOTE=zonk]Hi ertai.

If you want to try you can still have sound. What I did to get sound working was easy. Just try this:
First get alsa-sources eg. with synaptic.
the go to /usr/src/

untar  with:  tar xfj alsa-driver.tar.bz

then:

cd linux-headers-`uname -r`  (uname -r stands for your kernel, you are using.)
sudo make-kpkg --rootcmd=fakeroot --append-to-version=-9-386 modules-image (just replace -9-386 with your own kernel header.)

After that go back to 
cd..
and do a 
sudo dpkg -i alsa-modules-`uname -r`_1.0.9b-4+10.00.Custom_i386.deb
Your name can of course be different!

After that you should remove the modules from the blacklist, boot and sound should be working! At least it does with the Chipset: ALC880 

If not try:
sudo gedit  /etc/modprobe.d/sound

and add:

options snd-hda-intel model=z71v position_fix=1
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel
alias sound-slot-0 snd-card-0
alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

I hope it works. 


cheers 

zonk[/QUOTE]

Hi, I followed your step until where you have to enter

sudo make-kpkg --rootcmd=fakeroot --append-to-version=-9-386 modules-image (just replace -9-386 with your own kernel header.)

and i got the following error

make[1]: Entering directory `/usr/src/modules/alsa-driver'
fakeroot /usr/bin/make -f debian/rules binary-modules
make[1]: fakeroot&#65306;command not found
make[1]: *** [kdist_image] error 127
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
Module /usr/src/modules/alsa-driver failed.
Perhaps /usr/src/modules/alsa-driver does not understand --rootcmd?
If you see messages that indicate that it is not
in fact being built as root, please file a bug
against /usr/src/modules/alsa-driver.
Hit return to Continue


What should I do?? thankyou

---

### Post by zonk on 2005-11-26
Hi mengqing. 

The error message does already tell you what is wrong/what you probably need to do. 
You see:

make[1]: fakeroot&#65306;command not found

That means you don't have installed fakeroot. Open synaptic and install fakeroot. Then it should work

zonk.



> **mengqing]Hi, I followed your step until where you have to enter

sudo make-kpkg --rootcmd=fakeroot --append-to-version=-9-386 modules-image (just replace -9-386 with your own kernel header.)

and i got the following error

make[1]: Entering directory `/usr/src/modules/alsa-driver'
fakeroot /usr/bin/make -f debian/rules binary-modules
make[1]: fakeroot&#65306 said:**
> : *** [kdist_image] error 127
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
Module /usr/src/modules/alsa-driver failed.
Perhaps /usr/src/modules/alsa-driver does not understand --rootcmd?
If you see messages that indicate that it is not
in fact being built as root, please file a bug
against /usr/src/modules/alsa-driver.
Hit return to Continue


What should I do?? thankyou

---

### Post by zonk on 2005-11-26
Hi filos.

[COLOR="Red"]sudo dpkg -i alsa-modules-`uname -r`_1.0.9b-4+10.00.Custom_i386.deb   here it stops and says alsa-modules-...  can't' be find[/COLOR]

Did you change the 'uname -r ' against your actuall kernel version?
take a look at the module name!

Write in the shell as root:  dpkg -i alsa-modules- and press "TAB" and it should complete the correct name. 


zonk :)

[QUOTE=filos]I have the same computer, same problem. 
I've tried to do what I've just quoted:
sudo make-kpkg --rootcmd=fakeroot --append-to-version=-9-386 modules-image [COLOR="Lime"]oks it does[/COLOR]
cd..

[COLOR="Red"]sudo dpkg -i alsa-modules-`uname -r`_1.0.9b-4+10.00.Custom_i386.deb   here it stops and says alsa-modules-...  can't' be find[/COLOR]
maybe I've wrong something with the Synaptic packages and forgot something (I'm noob :( ) , I don't' know.

Is there also an howto for resolving problem wih audio intel chipset? Maybe I just need that ;)[/QUOTE]

---

### Post by ertai on 2005-11-27
Hi Zonk,

I got my laptop back. And now I tried what you suggested. But I got these errors.

The changelog says we are creating 2.6.1210-686, but I thought the version is 2.6.12-10-686
make: *** [modules-image] Fout 1

I have done some things extra. I installed the 686-kernel. And the linux-source, linux-tree and libc6-dev. Then I came to this fault.

Greetings
ertai

---

### Post by ertai on 2005-12-05
is there nobody who can help me??

---

