---
title: "Help with fixing FGLRX Warnings in Ubuntu 12.04"
date: 2012-04-28
forum: Hardware
---

### Post by Lamukra on 2012-04-28
Hello Guys!
Could you please give me a suggestion on these lines from my Xorg.0.log. How to fix 'em and shold I fix them at all?
Installed driver is Catalys 12.4 from AMD web page. I don't know why but installing through Jockey made compiz not working (Setting Manager) maybe something different and could You please give me a note what should be added to xorg.conf with fglrx driver. I was always using open-source driver, but in 12.04 proprietary give a better control over heat levels and fan speed by itseld. With Open-Source Heat was crazy and fan was insane working. Here it is

```
[    17.620] (WW) Falling back to old probe method for fglrx
[    17.769] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    17.924] (WW) fglrx(0): board is an unknown third party board, chipset is supported
```

My Xorg.conf

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by Lamukra on 2012-04-28
Forgot to mention that I am using Radeon HD 5650 with 1GB dedicated on a laptop

---

### Post by Lamukra on 2012-04-30
Is there anyone, Please!?

---

### Post by sffvba[e0rt on 2012-04-30
Hi,

I am not going to be much help analyzing the error (and I am struggling with Google as it keeps saying I am sending automated queries?!) ... Have tried using the drivers that you can install from "Additional Drivers" as opposed to the latest ones from AMD/ATI?

AFAIK they are still proprietary...


404

edit: Congrats on the avatar :)

---

### Post by Lamukra on 2012-04-30
Lates driver is installed using AMD's installation file, through Jockey things did not go very well and 3D did not come to work and compiz was not working, now I have these WW - Warnings in log file that don't seem very good

---

### Post by Lamukra on 2012-04-30
Seems that I am not only one who is affected with this. For now we are two already :) after installing Proprietary driver. User "galerie" from this thread has the same Warning messages :)

[http://ubuntuforums.org/showthread.php?p=11892962#post11892962](http://ubuntuforums.org/showthread.php?p=11892962#post11892962)

NOTE: Installing through Jockey gave the same exact message but in my case 3D was not working and compiz had trouble as well...

---

### Post by galerie on 2012-04-30
Ola all... :D
as mentioned by Lamukra
I experienced thes same WW message :D
with addition :
- If I directly used unity 3D when first logon than I will get hang the only way I can do is to reboot.
- If First I logon to unity 2D then I relog to Unity 3D, it will work like normal. I can Use unity 3D

this the result when I type :
```

/usr/lib/nux/unity_support_test -p

OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4650 
OpenGL version string:  3.3.11631 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```
Lamukra : are you experiece this too?

---

### Post by Lamukra on 2012-04-30
> **galerie said:**
> Ola all... :D
as mentioned by Lamukra
I experienced thes same WW message :D
with addition :
- If I directly used unity 3D when first logon than I will get hang the only way I can do is to reboot.
- If First I logon to unity 2D then I relog to Unity 3D, it will work like normal. I can Use unity 3D

Lamukra : are you experiece this too?

Nope, I did not have this trouble, but unity automatically dropped to 2D with first logon and after installing Proprietary driver and instantiating it things got better... My output of

```
/usr/lib/nux/unity_support_test -p
```

```
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6500M/5600/5700 Series
OpenGL version string:  4.2.11631 Compatibility Profile Context

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by QIII on 2012-04-30
I have a partition set aside on an AMD/ATI machine for Ubuntu, but haven't installed it yet.  (I use Kubuntu and Xubuntu)

I'll see if I have time to install it tonight and see what I come up with.

I know that Gnome has problems with ATI.  The Gnome developers are working on it.  Unity may be problematic, too.  The driver works fine with KDE, Xfce and E17.

---

### Post by ratcheer on 2012-04-30
FWIW, I have had tons of problems in 12.04 with the drivers downloaded from AMD, but the one from jockey loads and functions just fine. It is a little older, though.

```
[    13.603] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    13.604]    compiled for 1.4.99.906, module version = 8.96.4
```

Tim

---

### Post by galerie on 2012-05-01
> **QIII said:**
> I have a partition set aside on an AMD/ATI machine for Ubuntu, but haven't installed it yet.  (I use Kubuntu and Xubuntu)

I'll see if I have time to install it tonight and see what I come up with.

I know that Gnome has problems with ATI.  The Gnome developers are working on it.  Unity may be problematic, too.  The driver works fine with KDE, Xfce and E17.
I used gnome shell before, everything ok but the titlebar, sometimes it look like a mess, when open more than one windows. :D, but everything else is fine.except now I always have computer hang if I logon to Gnome or unity 3D. but it'll be fine if first I logon to unity2D then relog to unity3D.
I'll be waiting to any advice you will come thank you QIII

> **ratcheer said:**
> FWIW, I have had tons of problems in 12.04 with the drivers downloaded from AMD, but the one from jockey loads and functions just fine. It is a little older, though.

```
[    13.603] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[    13.604]    compiled for 1.4.99.906, module version = 8.96.4
```Tim
First thing I did before after installing fresh precise. try to install from jockey. but not work on my machine.
I got crash report with apport comes out.
now I am using fglrx from amd/ati site. but have problem like I mentioned before. 
I cannot directly logon to unity 3D after booting. :D.
well but now my machine is cooler than before.
any suggest for me ratcheer?
thank you.

---

### Post by ratcheer on 2012-05-01
> **galerie said:**
> 
any suggest for me ratcheer?
thank you.

Since we seem to have different problems, I really don't have any ideas for you.

I did a fresh install of 12.04, Saturday. My first attempt was to install the fglrx 12.4 driver downloaded from AMD, especially since it said it had specific support for 12.04. I followed all the instructions at the cchtml Wiki. The .debs were created but, when I tried to install them, it failed.

Since so much crap had been installed by that preinstallation step of installing ia32libs, I did another fresh install of Ubuntu. Then I ran jockey and installed the AMD proprietary driver. It installed without a hitch and has worked ever since (wow - that is a whole three days).

However, I do run the downloaded-from-AMD driver on my Oneiric installation. It works just fine, there.

Tim

---

### Post by galerie on 2012-05-01
ok I got it. thank you.
I tried to search this matter that happened to me.
but still don't get any answer.
one of indonesian ubuntu forum community member suggest me to update my kernel to v.3.3
he said that it will solve my problem and Lamukra
but I'am just a new linux user and still afraid to update my kernel manually
especially when I found a post in askubuntu said that it is not for novice.
however I will not stop to try anything possible to make it work normally like before on oneiric.
now all of my data backed up to a safe place, I will try any suggestion from anyone :D
thank before for any respond to this thread.
for Lamukra : do you have any progress bout' this matter?
I would love to hear as soon as you solved it :D

---

### Post by Lamukra on 2012-05-01
> **galerie said:**
> ok I got it. thank you.
I tried to search this matter that happened to me.
but still don't get any answer.
one of indonesian ubuntu forum community member suggest me to update my kernel to v.3.3
he said that it will solve my problem and Lamukra
but I'am just a new linux user and still afraid to update my kernel manually
especially when I found a post in askubuntu said that it is not for novice.
however I will not stop to try anything possible to make it work normally like before on oneiric.
now all of my data backed up to a safe place, I will try any suggestion from anyone :D
thank before for any respond to this thread.
for Lamukra : do you have any progress bout' this matter?
I would love to hear as soon as you solved it :D

Nah... not yet, internet does not have answer yet for this issue... dunno... will keep searching, will keep you posted :)

---

### Post by Lamukra on 2012-05-01
I will try to investigate a question about updating kernel to 3.3... might give it a try.... we'll see :)

---

### Post by galerie on 2012-05-01
> **Lamukra said:**
> I will try to investigate a question about updating kernel to 3.3... might give it a try.... we'll see :)
as usual you do a quick response that amaze me
don't you ever sleep? :D kidding'
I want to update my problem status.
I have dual boot precise and windows 7.
just now I rebooted to my win 7 cause my sister need to do something within.
and now I rebooted to precise and try a direct logon to unity 3D and my freezing problem magically disappeared.
but the VESA message in details still happen :D
a friend from ubuntu indonesia forum updated kernel to 3.3 now. I waited about his review but he haven't report any till now.

please let me know if updating kernel solve your problem :D

---

### Post by Lamukra on 2012-05-01
> **galerie said:**
> as usual you do a quick response that amaze me
don't you ever sleep? :D kidding'
I want to update my problem status.
I have dual boot precise and windows 7.
just now I rebooted to my win 7 cause my sister need to do something within.
and now I rebooted to precise and try a direct logon to unity 3D and my freezing problem magically disappeared.
but the VESA message in details still happen :D
a friend from ubuntu indonesia forum updated kernel to 3.3 now. I waited about his review but he haven't report any till now.

please let me know if updating kernel solve your problem :D

It is just because this thread is instant message alert about new response to my email, and I get alert straight away into my phone mail client, on phone I always have internet connection, so... :):):)

Really weird about the dual boot problem solution :D... I also have dual boot with windows 7 but did not have anything like this... but it is good this one is gone now! Less with one trouble :)

---

### Post by Lamukra on 2012-05-14
Some update on a topic about a problem...

I decided to re-install my ubuntu, because made some things pretty messed up, but it came out with positive outcome.

When I was done with installing and updating the system I went to check into 
System Setting --> Details and surprise. In the Graphic there was written **Gallium 0.4 on REDWOOD** and then I decided to go and install proprietary driver through Jockey, because in terminal after running

```
cat /var/log/Xorg.0.log | grep EE
```

there was standing that fglrx module is missing and falling back to old probe method vesa and fb

then I installed proprietary driver and after restart on the same place in system setting there was under graphics written **VESA:MADISON**

What is that suppose to mean?
Anyone?

---

### Post by Yellow Pasque on 2012-05-15
Those warnings are standard. They're nothing to worry about.

As for your new install, it means fglrx didn't install correctly, Purge it and try again.

---

