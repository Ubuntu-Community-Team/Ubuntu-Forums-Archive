---
title: "Ubuntu 8.04 Beta fixes laptop earphone problem"
date: 2008-03-25
forum: Georgia Team - US
---

### Post by siafulinux on 2008-03-25
Alrighty, so I had bought a Toshiba laptop a few months back and was dissapointed when I plugged in my earphones and sound came from both the earphones and the regular speakers.

I was using Feisty with Kubuntu. I knew it wasn't the jack as it worked under Windows just fine!

 Since the 8.04 Beta upgrade, using Gnome I might add, it works without a hitch. Haven't tried with KDE just yet, but I am extremely happy as this was a near deal breaker for me and I almost returned the laptop!

I'm wondering if this has to do with Pulse Audio?

Thought I'd share the good news. Now if only I can get Compiz Fusion running on it's ATI card...

---

### Post by siafulinux on 2008-03-25
uh, that's meant to be Gutsy, not Feisty! :-)

---

### Post by JReagan1990 on 2008-03-26
I know that on the 8.04 beta, the ATI driver on Ubuntu works with Compiz Fusion if you use the fgrlx driver provided via the Hardware Manager.

---

### Post by siafulinux on 2008-03-27
> **JReagan1990 said:**
> I know that on the 8.04 beta, the ATI driver on Ubuntu works with Compiz Fusion if you use the fgrlx driver provided via the Hardware Manager.

After I posted I decided to dig a little deeper on that; found that I also had to install xserver-xgl. This worked, but there was a crash at every login - gnome-settings-manager or something along those lines. 

Now this was an upgrade, so I wiped everything and did a fresh install but have not, as of yet, experimented any further with it. One of my children broke the USB network card! Just snapped it... yup, he snapped it! So I cannot download anything until I get that sorted out.

Still, 8.04 is noticing the internal Atheros card in the "Restricted Devices", but I haven't seen it actually show up anywhere usable? *scratches head a little*.

JC

---

### Post by siafulinux on 2008-03-28
Okay, so I decided to go ahead and do a fresh install. 

I attempted to get the Atheros wireless to work using a [madwifi guide]("http://ubuntuforums.org/showthread.php?t=662877") that seemed to work for most people. I opted for ndiswrapper when that failed. I had to disable the HAL and Atheros support from the Hardware Drivers utility. 

Needless to say, it now works beautifully! In fact, it seems to be faster and gets better connections than the external USB Belkin I had.

After getting that to work, I enabled the restricted ATI driver and rebooted to find that Compiz was working without doing anything. Only slight nag I have is that it did not include the compizconfig-settings-manager automatically, but a quick install from Synaptic solved that.

I will post the URL for the Atheros driver when I get home tonight for those who may find this useful or having a similar problem.

---

### Post by siafulinux on 2008-03-30
[[Click Me]]("http://ubuntuforums.org/showthread.php?t=512828") for the forum entry where I was able to find a usable driver for the internal Atheros card. 

Now an update on the compiz. I discovered with Compiz enabled, I get a flicker when attempting to play games like "lincity-ng" and on screen savers. I attempted to install xserver-xgl, which seems to get rid of the flicker, but then causes a crash upon login.

Removing it gets rid of the crash. I read somewhere that it was a problem with the ATI driver (or is it?), so I'm hoping for a fix soon.

Anyway, glad to have everything working, even with a slight hitch. At least I can shut it off without having to restart to play a game or two. Still the screen saver would be nice if it didn't flicker all the time.

---

