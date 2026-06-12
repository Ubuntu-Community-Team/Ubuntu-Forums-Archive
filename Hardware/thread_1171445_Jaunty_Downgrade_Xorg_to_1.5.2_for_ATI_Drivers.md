---
title: "Jaunty: Downgrade Xorg to 1.5.2 for ATI Drivers"
date: 2009-05-27
forum: Hardware
---

### Post by xaviermerino on 2009-05-27
Hi!.. As my title states I am trying to downgrade Xorg in Jaunty in order to use the ATI Drivers. However, I found problems. 

Umm.. this site: [http://www.kdedevelopers.org/node/3942?destination=node%2F3942]("http://www.kdedevelopers.org/node/3942?destination=node%2F3942") 

This says it is possible. And many people have confirmed this. So I wanted to the do same. I checked the packages that the website above is using, but they seem to be in amd64 and right now i am using i386. 

So I download all those same packages for i386 and tried, I also downloaded the ATI Propietary Drivers from ati. I installed everything, and when I rebooted my screen showed nothing.. nothing.. not even the terminal. So I used the recovery-mode to fix it. I did it.. Now I am working with Xorg 1.6, but can someone help me downgrading it to Xorg 1.5.2?

:(

---

### Post by |Blu@Sky| on 2009-06-14
1) apt-get remove 'xserver-*'

2) apt-get remove libdrm2 libdrm-intel1 libgl1-mesa-dri

3) copy /etc/apt/sources.list /etc/apt/sources.list.jaunty

4) substitute 'jaunty' with 'intrepid' everywhere in /etc/apt/sources.list

5) apt-get update

6) apt-get install xserver-xorg-core

7) apt-get install libdrm2 libdrm-intel1 libgl1-mesa-dri

8) mv /etc/apt/sources.list.jaunty /etc/apt/sources.list

9) apt-get update

10) apt-get install <non_xserver_packages_eliminated_in_step_1>

---

### Post by eternal404 on 2009-06-15
Hey,

BlueSky, I followed your instructions to downgrade xorg. Everything semt to work fine. Now, should I lock the versions of the packages I downgraded, so they won't be upgraded in the future ? How can I do that ?

Thanks in advance.

---

### Post by semidark on 2009-07-05
Hi eternal404,

I also wanted to downgrade the xorg version in Jaunty to 1.5.2 to re-enable my Laptop's ATI X300 Card.

I think i could follow the steps mentioned, but previously i would like to know how your
result are with your downgraded xserver.

Could you give me a brief overview of your results?

Many Thanks in advance.

---

### Post by semidark on 2009-07-13
OK. I gave it a try.

The Downgrade Process explained by blu@sky worked without a problem.

So I downloaded the ATI Catalyst Drivers version 9.3. This are the last ones that support the old Cards.

I installed them using this Tutorial.
[http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation](http://wiki.ubuntuusers.de/Grafikkarten/ATI/fglrx/Manuelle_Treiberinstallation) [GER]

And YES. 3D acceleration and Compiz is working \\:D/**... BUT...**


[LIST]
[*]XVideo is not supported with this Driver and my Card. So the Video Player only plays extremly choppy. I Tried a few xorg.conf settings but nothing helped.
As workaround I tried MPlayer with openGL output device wich seems to play fine.
[*]xOrg uses around 30% of the CPU and it also seams a bit choppy.
[*]The CPU Clock is not dynamicly set anymore. The CPU always runs at the Highest speed. Not very good on an Notebook Computer.
[*]The MonitorSettings manager does not work anymore. So you have to use the one bundled with the drivers.
[/LIST]
This Result was not acceptable for me. [-( So I upgraded back to version Xorg 1.6.2.

A solid System is more important to me than playfull 3D Effects in Gnome.

If anywone got better results I would love to hear...

---

### Post by achilleas.k on 2009-09-01
I found this guide on a blog and followed it and it worked, but I wanted to ask something about it. I'm using Kubuntu so I don't have the ability to lock the Xorg version through Synaptic. I installed wajig instead which seems to be doing a great job. I was just wondering what packages I should lock to be sure I don't get something that'll "break" my system.

```

The following packages are on hold:                                                
fglrx-amdcccle                                                                     
fglrx-kernel-source                                                                
libdrm-intel1                                                                      
libdrm2                                                                            
xorg-driver-fglrx                                                                  
xserver-xorg-core                                                                  
xserver-xorg-input-all                                                             
xserver-xorg-video-all
```

I'm pretty sure these are more than enough. I was wondering if all these were overkill and if I should let some upgrade anyway.

Thanks

---

### Post by Tuxoid on 2009-09-06
> **|Blu@Sky| said:**
> 1) apt-get remove 'xserver-*'

2) apt-get remove libdrm2 libdrm-intel1 libgl1-mesa-dri

3) copy /etc/apt/sources.list /etc/apt/sources.list.jaunty

4) substitute 'jaunty' with 'intrepid' everywhere in /etc/apt/sources.list

5) apt-get update

6) apt-get install xserver-xorg-core

7) apt-get install libdrm2 libdrm-intel1 libgl1-mesa-dri

8) mv /etc/apt/sources.list.jaunty /etc/apt/sources.list

9) apt-get update

10) apt-get install <non_xserver_packages_eliminated_in_step_1>

Step 4... Would that not switch every package down to intrepid, including ones of which have nothing to do with X? Isn't just a method of downgrading Ubuntu?

I need some way of downgrading the video drivers on my dad's desktop, and I'd like to try this method, but I just would like to know how much this will actually do; downgrade X11 components only, or downgrade Ubuntu completely?

---

### Post by ssri on 2009-09-08
this guide worked for me:

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

---

### Post by s.l.i.m on 2009-09-09
> **ssri said:**
> this guide worked for me:

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

thanks **ssri** it works for me too.

I have  Toshiba Satellite A100-788 - **Core Duo T2250 1.73 GHz** with an **ATI X1400** but i have the "HIGH CPU" problem. And i don't know how to change the brightness level.

Slim.

---

### Post by ssri on 2009-09-09
> **s.l.i.m said:**
> thanks **ssri** it works for me too.

I have  Toshiba Satellite A100-788 - **Core Duo T2250 1.73 GHz** with an **ATI X1400** but i have the "HIGH CPU" problem. And i don't know how to change the brightness level.

Slim.

Did you downgrade your gnome session package?

'Flávio: "I found the solution for the high CPU problem!
Downgrade the package gnome-session. Use the intrepid package."'

I'm using KDE, so do not have this problem.  Hope this downgrade solves yours though.

---

### Post by fwoncn on 2011-02-03
> **Tuxoid said:**
> Step 4... Would that not switch every package down to intrepid, including ones of which have nothing to do with X? Isn't just a method of downgrading Ubuntu?

I need some way of downgrading the video drivers on my dad's desktop, and I'd like to try this method, but I just would like to know how much this will actually do; downgrade X11 components only, or downgrade Ubuntu completely?

I think all X stuff are located in "main"component

---

