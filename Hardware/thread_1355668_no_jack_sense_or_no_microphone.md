---
title: "no jack sense or no microphone"
date: 2009-12-15
forum: Hardware
---

### Post by joris1977 on 2009-12-15
My girlfriend is the happy owner of a medion sim 2070 laptop, which has been working with ubuntu since dapper drake. 

Recently I did a fresh install of Karmic. For some reason she couldn't get her microphone working. 

I checked all the channels in alsamixer and no microphone is muted. In the gnome sound preferences it stated under the input tab Unamplified. Weird...

So looking around on google I found the advice to try different options in /etc/modprobe.d/alsa-base.conf

When I add the line
options snd-hda-intel  model=6stack-dig

and reboot. Her microphone started working! Great!.... but then not so great, because her speakers don't mute anymore when she plugs in her headset. That is weird because that was working before, without the extra line in alsa-base.conf.

So I tried almost every option I could find and related to her audio chip, but it all was no jack sense or no microphone.

Since this is a laptop she is using for traveling both options are unacceptable. She  wants to listen to music without everybody in the train hearing it and for skype you really need a microphone...

The weird thing is it was working in all earlier versions of Ubuntu and out of the box...

Any help would be really appreciated. I hope it is not necessary to install an earlier version of ubuntu, because of this. I would make a bug report if I knew what was failing here...

some more technical info...

~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC883
Codec: LSI Si3054

 ~$ cat /proc/asound/version Advanced Linux Sound Architecture Driver Version 1.0.21.
Compiled on Dec 11 2009 for kernel 2.6.31-17-generic (SMP).

# lshw -class sound
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:29 memory:feb38000-feb3bfff

 
?

---

### Post by wwuster on 2009-12-15
I'm trying to run skype on 9.10. It was working about a week ago. There has been an update, I think since then. Now the microphone is not recognized. I can hear calls but can't transmit sound to the other end. I have a desktop core 2 duo with a Intel 82801H sound device.

How can I get this working again?

thanks,
William

---

### Post by joris1977 on 2010-11-18
Since my girlfriend is traveling a lot this issue became more annoying.  I even posted a bug report about it: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/585401](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/585401) 

... after googling for a few hours looking for a clue to get this fixed. I went out for a walk and suddenly I thought; why not just buy a usb headset. Bought a logitech usb headset H330 and guess what? It works perfect. 

Fresh air can be so good for you!


:cool:

---

