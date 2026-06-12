---
title: "Toshiba A70 acpi alternate (apm not available)"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by FishRCynic on 2007-04-22
i have toshiba a70 laptob which presently works fine with Feisty when i use acpi=ht on the boot line
which in my case basically acpi off. (which i tried acpi=off and i get a software lockup)
i can even run beryl without fgrlx drivers

blacklisting the snd-atiixp-modem does not help with sound with or without acpi enabled

I have attempted various means and ways to enable acpi - 
using combinations of various kernel options
noapic nolapic irqpoll pci=......  
however when i do that, i create sound issues.

i have looked up the various kernel codes, alsa pages etc 

is there another way to load acpi (i tried apm but it doesn't seem to be supported on this machine)

thanks 

p.s.
oh yes wireless works i am outside now enjoying the sun and fresh air for a change

---

### Post by FishRCynic on 2007-04-22
I have reached a compromise with the laptop

Toshiba Satellite A70 model psa70c-ts10e 

I have acpi
no kernel boot options required

no modifications to /etc/modules
no blacklisted devices

I installed pulse audio sound server and set it for default in the multimedia center.

I have no system sounds (why i have not quite figured out)
i can play rhythmbox, totem etc. with apparently no issues

i am going to reload the system sounds and see where that leads me

---

### Post by FishRCynic on 2007-04-25
it appears there is a bug 
whether it is gnome, esd or pulseaudio i am not qualified to judge

i do know that if i make a.gnomerc file in my home directory and add the line

ln -s /tmp/.esd /tmp/.esd-1000

i now have logon sound and system sounds.

this is slightly modified solution from a bug report

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/108577](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/108577)

i am now waiting for some goody two shoes to fix the gnome esd pulseaudio issue
and then nothing will work for me :) 

but at present i am happy - feisty appears to be 99% operational on this Toshiba A70
i haven't tried suspend or hibernate yet but that will be another day

:popcorn:

---

### Post by dcg001 on 2007-04-29
Thanks for the tip, adding "acpi=ht" to the end of:

kernel		/boot/vmlinuz-2.6.20-15-generic......... acpi=ht
in /boot/grub/menu.lst

has worked for me. It sopped my Toshiba A70 from locking up every 10 minutes and as an added benefit, the Desktop Effect now work. The only down side is the battery monitor isn't working but that is the next challenge but otherwise I'm extremely happy, Feisty works well on this A70.

---

### Post by bonzini on 2007-04-30
Hi fellow A70 users;

Interesting to read about your acpi problems.  I had a problem with lockups that you can read at [https://bugs.launchpad.net/bugs/98999](https://bugs.launchpad.net/bugs/98999)

In my case, "noapic" was the silver bullet.

I'm also interested to note that you have audio problems.  The only time I've ever had an audio problem is when Skype somehow switched my audio device to the modem...

By the way, mine is a PSA70C-RX100E.

---

### Post by FishRCynic on 2007-05-06
i did not have freezing problems per se such as yours.  

However esound does not seem to work correctly for me but using pulse audio as a replacement and loading sl-modem fixes my issues (sound, microphone, graphics all work and it appears the modem is operable though i haven't tried it.)  I have left the dual boot option so far but i have been feisty solely for the last week or so. 
This laptop had more issues with feisty that i originally anticipated, but in my opinion it was worth it as the machine now is more useable that with the xp home it came with.

---

### Post by FishRCynic on 2007-05-13
i am working on a how to for this - see link below
(ah the blind leading the blind)

[http://ubuntuforums.org/showthread.php?t=417819&page=2](http://ubuntuforums.org/showthread.php?t=417819&page=2)

---

