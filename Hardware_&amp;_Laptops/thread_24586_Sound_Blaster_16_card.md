---
title: "Sound Blaster 16 card"
date: 2005-04-07
forum: Hardware &amp; Laptops
---

### Post by BeZet on 2005-04-07
Hi,
I've recently installed Ubuntu 5.04. Everything works fine, but it seems that my soundcard (Sound Blaster 16) hasn't been detected. Does Ubuntu 5.04 support Sound Blaster 16? Is there a way to make it work?

---

### Post by Klin'Targ on 2005-04-08
Yes, one of my machines also has this card, and no linux distro I have used has correctly autodetected it. Add "snd-sb16" to /etc/modules to load it at boot.

---

### Post by BeZet on 2005-04-08
[QUOTE=Klin'Targ]Yes, one of my machines also has this card, and no linux distro I have used has correctly autodetected it. Add "snd-sb16" to /etc/modules to load it at boot.[/QUOTE]
 Okay, the sound seems to work (I am able to hear a sound on the login screen), but now Gnome hangs-up on start up (I can hear a sound played, but it stops unexpectidely; You can only see the cursor, nothing happends next). Is there a problem with the sound server? Any clue what should be done?
EDIT:
I've changed 'snd-sb16' to 'sb' and now it works perfectly.

---

### Post by moopere on 2005-04-10
[QUOTE=BeZet]Okay, the sound seems to work (I am able to hear a sound on the login screen), but now Gnome hangs-up on start up (I can hear a sound played, but it stops unexpectidely; You can only see the cursor, nothing happends next). Is there a problem with the sound server? Any clue what should be done?
EDIT:
I've changed 'snd-sb16' to 'sb' and now it works perfectly.[/QUOTE]
 Hmm.  Interesting.  I'm having this problem as well...were gnome just stops loading up at the brown wallpaper and the 'startup sound' cuts short.

I've just tried your solution, removing the snd-sb16 module....yep, now gnome starts up...

Continued as you suggest, loaded the sb module instead (I don't have the pnp version of the card though and had to use insmod sb io=0x220 irq=5 dma=1,5 mpu_io=0x330 pnp=0).

Fire up GDM, now login...everything is ok!

So, what does this mean?  The sb module is an OSS driver, would this suggest that the snd-sb16 module, which is an ALSA driver has a bug?  Or is something funky going on as esd is fired up after login?  

This last seems likely to me, something going 'foo' when GDM lets go and gnome starts up (and starts ESD) anyone care to hazzard a guess as to where/how gnome starts up ESD?  I reckon something is happening during the startup sound only.  If I kill ESD from a VT then gnome starts, then if I start ESD again from an VT everything seems normal.

Cheers,
Craig

---

### Post by Klin'Targ on 2005-04-10
I can confirm that it is a gnome-related bug. I suggested snd-sb16 because it works as expected in kubuntu. I tried installing ubuntu-desktop and had the same problem with the snd-sb16 module as you guys did. Using sb is not an ideal solution since OSS has been deprecated, and seems to be giving me skipping issues.

---

### Post by Ozitraveller on 2005-04-16
[QUOTE=BeZet]Okay, the sound seems to work (I am able to hear a sound on the login screen), but now Gnome hangs-up on start up (I can hear a sound played, but it stops unexpectidely; You can only see the cursor, nothing happends next). Is there a problem with the sound server? Any clue what should be done?
EDIT:
I've changed 'snd-sb16' to 'sb' and now it works perfectly.[/QUOTE]


Changing 'snd-sb16' to 'sb' in /etc/modules has work me me also!

Thanks guys!

---

### Post by StarkD on 2005-04-25
It doesn't work for me. I have got a non plug-n-play Sound Blaster 16 card. When I use snd-sb16 or snd_sbawe I get the "no such device" when booting. When I use sb I don't get any errors but it doesn't work. Any suggestions how to proceed?

---

### Post by moopere on 2005-04-25
[QUOTE=StarkD]It doesn't work for me. I have got a non plug-n-play Sound Blaster 16 card. When I use snd-sb16 or snd_sbawe I get the "no such device" when booting. When I use sb I don't get any errors but it doesn't work. Any suggestions how to proceed?[/QUOTE]

If your card is set to 'standard' io, irq settings then you just need to do an insmod snd-sb16 isapnp=0.  Set this up for boot time application by adding snd-sb16 to /etc/modules and making a file called snd-sb16 in /etc/modprobe.d with the following in it:

options snd-sb16 isapnp=0

If your card is not set to standard then things get longer, put this into your /etc/modprobe.d/snd-sb16 file:

options snd-sb16 index=0 id="SB-16" port=0x220 mpu_port=0x330 irq=5 dma8=1 dma16=5 isapnp=0

obviously you need to change the values I've plonked in above to suit your card.

Hope that helps.  Remember, gnome won't boot past the gdm screen if you use the alsa driver (snd-sb16).

Cheers,
Craig

---

### Post by StarkD on 2005-04-25
[QUOTE=moopere]If your card is set to 'standard' io, irq settings then you just need to do an insmod snd-sb16 isapnp=0.  Set this up for boot time application by adding snd-sb16 to /etc/modules and making a file called snd-sb16 in /etc/modprobe.d with the following in it:

options snd-sb16 isapnp=0[/QUOTE]

This solved the problem. I installed XFCE (GNOME crashes) and now everything is working perfectly. Thank you very much Craig!

---

### Post by Nasky on 2005-07-13
Hi

 I NEED you.

 I have the same problem. I have done what you said but it still doesn't work!!!
Actually, when I add "snd-sb16" to /etc/modules but nothing changed.
Then, I tried to do as **moopere** suggested. Now I get a message at the boot. Indeed, I can read : * ** Sound Blaster 16 not found or device busy ** * !!

So what should I do ??

Moreover - and the weirdest - I have a problem with the sound on Windows 98. This problem came just after I had tried moopere's solutions.
The sound is not clear... It seems I have a problem with IRQ and not my sound card,
because I don't know how a problem on Linux could affect Windows partition...
So it's probably a device problem...

I really want to have sound on UBUNTU. I wasn't able to make the sound work on Mandriva (which I was using before installing Ubuntu). I hope I will on Ubuntu...
Thanks guys.

Nas'

---

