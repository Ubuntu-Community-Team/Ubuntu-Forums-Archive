---
title: "Bad colors when using &quot;nvidia&quot; driver"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by andrewski on 2008-03-29
Everything has taken on a greenish tint since I upgraded my video card to an NVidia GeForce 4 Ti 4600. In so doing, I switched my monitor (22" Acer AL2216W) to using its DVI cable.

This behavior happens only in X and only with the "nvidia" driver; testing on the console or with the "nv" driver works just fine.

Here's a screenshot:
[_[IMG]http://img134.imageshack.us/img134/1282/n30202314306198305151gu8.th.jpg[/IMG]_]("http://img134.imageshack.us/my.php?image=n30202314306198305151gu8.jpg")

So far I have:[LIST=1]
[*]Reset my xorg.conf: 'sudo dpkg-reconfigure --default-priority xserver-xorg'
[*]Upgraded to Hardy (been meaning to do that anyway).
[*]Reset my monitor.
[*]Switched video card's DVI outputs.
[*]Reduced the color depth from 24 to 16.[/LIST]Nothing has worked. Does anyone have any ideas as to what might be causing it (or if it seems like a bug)? I really like the speed of my card, but I'm going to have to go back to "nv" because these colors are maddening! :p

---

### Post by xenon2000 on 2008-04-15
I have this same issue with 8.04 beta on 2 different systems. One system is a much newer card, can't remember the models off the top of my head. And the other is an old 64MB Geforce2 something.

Both systems output from DVI connection. I am wondering if that is the issue.

Anyways, I get the exact same greenish low color video when using the Restricted Nvidia drivers.

Can't find any help yet.

---

### Post by andrewski on 2008-04-16
> **xenon2000 said:**
> Both systems output from DVI connection. I am wondering if that is the issue.
I just got a DVI/VGA adapter and I'm going to try that with my LCD and CRT monitors. Seems like I've tried just about everything else....

---

### Post by steveneddy on 2008-04-16
Is that an older video card?

If so, you may need to run the legacy nvidia driver.

---

### Post by andrewski on 2008-04-16
> **steveneddy said:**
> Is that an older video card? If so, you may need to run the legacy nvidia driver.
In my experience, Ubuntu at this point is good at picking the right driver package, and this is no exception: nvidia-glx-legacy did not work at all.

---

### Post by andrewski on 2008-04-16
> **andrewski said:**
> Everything has taken on a greenish tint since I upgraded my video card to an NVidia GeForce 4 Ti 4600. In so doing, I switched my monitor (22" Acer AL2216W) to using its DVI cable.
And it seems this was all it took. On a whim, I tried using a DVI->VGA adapter from the suggestion of a coworker and that seemed to do the trick.

This seems to explain it: > [http://www.datapro.net/techinfo/dvi_info.html#Page02:](http://www.datapro.net/techinfo/dvi_info.html#Page02:)
There are three types of DVI connections: DVI-Digital, DVI-Analog, and DVI-Integrated (Digital & Analog). High-Res Analog         [DVI-A cables]("http://www.datapro.net/catalog/DVIA.html") are used to carry a DVI signal to an analog display, such as a CRT monitor or budget LCD.Mine is definitely a budget LCD, so this makes sense. Stupid Acer. :rolleyes:

xenon2000, any luck for you?

---

### Post by xenon2000 on 2008-04-21
Sorry for the long delay. DVI->DVI LCD was giving greenish tint with 8.04 and Geforce2 MX200 64MB AGP card. And like you, if I shutdown and do DVI->VGA with adapter, then colors are fine.

Odd that this even affects new Geforce7 cards that use the glx-new drivers via DVI->DVI/HDMI oh well.

---

### Post by andrewski on 2008-04-21
> **xenon2000 said:**
> Odd that this even affects new Geforce7 cards that use the glx-new drivers via DVI->DVI/HDMI oh well.
Did you see the link I shared ([http://www.datapro.net/techinfo/dvi_info.html#Page02)?](http://www.datapro.net/techinfo/dvi_info.html#Page02)?) It appears this has to do with the various DVI standards that exist. I expect that if we had the correct DVI cable all would be fine, and we wouldn't have to revert to VGA.

---

### Post by xenon2000 on 2008-04-22
> **andrewski said:**
> Did you see the link I shared ([http://www.datapro.net/techinfo/dvi_info.html#Page02)?](http://www.datapro.net/techinfo/dvi_info.html#Page02)?) It appears this has to do with the various DVI standards that exist. I expect that if we had the correct DVI cable all would be fine, and we wouldn't have to revert to VGA.

I did. And I have a DVI-I and I have tried a DVI-D. But they both use the same path for digital to digital. The only difference with DVI-I is that it has analog-to-analog as an option. But that means that your DVI display has to support analog as an input signal.

So the issue is that Digital-to-digital with even newer Nvidia cards does not work with glx-new unrestricted drivers. This is unfortunate as my HTPC projector setup is DVI->HDMI and so I would need to use the VGA port on my projector instead. Which is ok, but odd that digital-to-digital gives this green tint issue.

At least we know what is going on and others can find this thread and just switch to analog.

---

### Post by xenon2000 on 2008-04-22
I forgot to mention that when I did switch to a DVI->VGA connection, that while the colors are normal, the bottom of the image is cut off. The odd thing is that my monitor is set to resize the image so that even if the res was too high for my LCD or too low, it would still show the whole image but distorted. But the bottom part of the image isn't showing as if the signal is actually that way.

Edit: Sorry, ALSO, it does work fine after changing the res manually again in the GUI. All is good.

---

