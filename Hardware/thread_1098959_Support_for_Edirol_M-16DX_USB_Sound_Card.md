---
title: "Support for Edirol M-16DX USB Sound Card?"
date: 2009-03-17
forum: Hardware
---

### Post by renauddenis on 2009-03-17
Hi everyone,

I recently acquired a Edirol M-16DX Mixer, which is also a DAW Controller as well as an external USB Sound Card.

Using it as an external USB Sound Card is a must have for me...

Unfortunately, it looks like it's not recognized by alsa's usb driver as it should.

I stumbled upon a wiki page on ALSA, showing how to recompile the usb driver in order to make this work, but this seems to be outdated :/

What could I do to activate this topic at Ubuntu/Alsa? Should I open an issue on launchpad / alsa bugtrack? Is there any chance to see this hardware supported in the future?

Renaud

---

Official M-16DX web page:
[http://www.rolandus.com/products/productdetails.aspx?ObjectId=860](http://www.rolandus.com/products/productdetails.aspx?ObjectId=860)

Alsa wiki about M-16DX:
[http://alsa.opensrc.org/index.php/Edirol_M-16DX](http://alsa.opensrc.org/index.php/Edirol_M-16DX)

---

### Post by markbuntu on 2009-03-18
You should at least bug roland about adding linux support. But anyway that alsa link was last updated a month ago so someone is paying attention to it and the info is probably still good.

You could also ask at the alsa mailing list etc. there are links at alsa.org

---

### Post by renauddenis on 2009-03-18
> **markbuntu said:**
> But anyway that alsa link was last updated a month ago so someone is paying attention to it and the info is probably still good.

Indeed, you're right. It's weird I can't find this usbquirks.h then, even tough I installed linux-source and alsa-source. I'll get a look deeper at that.

Thanks a lot anyway, I'll take you informed
Renaud

---

### Post by renauddenis on 2009-03-30
Related issue at alsa: [http://bugtrack.alsa-project.org/alsa-bug/view.php?id=4473](http://bugtrack.alsa-project.org/alsa-bug/view.php?id=4473)

---

### Post by renauddenis on 2009-03-31
Answer from Roland (in french):

[INDENT]Bonjour,
A l'heure actuelle - et à ma connaissance - il n'y a pas de support officiel de la part de Roland pour Linux. Je poserai cependant la question aux développeurs lors du prochain salon de la musique à Francfort.
[/INDENT]

Globally says that no linux support is provided by Roland, but that he will ask around soon :)

---

### Post by markbuntu on 2009-03-31
Taling points for conversations with Roland.

They sell hardware. They need to be able to market to as wide a user base as possible and many many professionals are moving to linux for studio and performance work. Some of the leading software companies in the music production business are also porting their software to linux.

Many of their competitors already support linux either with their own proprietary drivers or by publishing detailed programming specs so the open source community can write the drivers. 

If they wish to even just hold on to their current market share they need to support linux.

---

### Post by rrob on 2009-03-31
I have it too and i want use it in Ubuntu too .(

---

### Post by IMnotelmo on 2009-07-11
i've heard that there is not yet a driver for Linux
that supports multiple audio channels on USB 2.0
(all the multi-channel audio is done via firewire)

Since the M-16DX uses USB 2.0 exclusively that
is probably the problem.

If you put the M-16DX in the mode where it just
sends the Mains Out down the USB does it work then?

---

### Post by IMnotelmo on 2009-07-21
looks like a driver may be coming
[http://lkml.indiana.edu/hypermail/linux/kernel/0906.1/01425.html](http://lkml.indiana.edu/hypermail/linux/kernel/0906.1/01425.html)

about 2/3 of the way through takashi iwai's ALSA patches one reads:
ALSA: usb-audio - Add quirk for Roland/Edirol M-16DX

---

### Post by schlangen on 2009-08-30
Hi,

I'd need to get it running with Ubuntu too.
We will buy a new computer and would like to install Ubuntu(studio), 
but if it does not support the hardware, 
we have to run it with Windows (and nobody wants that).

So, any news since the last post?

Regards,
schlangen

---

### Post by renauddenis on 2009-08-30
Hi,

I've been able to enable the M-16DX by following the instructions at [http://alsa.opensrc.org/index.php/Edirol_M-16DX](http://alsa.opensrc.org/index.php/Edirol_M-16DX).

But there's still the problem of a periodic "crackling" sound like described in there.

According to IMnotelmo's link, support for the card should come in the next 2.6.32 kernel revision.

Let's hope it will be included in Ubuntu 9.10, coming by october 2009. But as far as I know, the latest alpha version only includes 2.6.30.

I add to re-enable a windows partition to properly work with the M-16DX, cause it wasn't working good in a virtual box either.

---

### Post by renauddenis on 2009-11-02
Supported in Ubuntu 9.10 Karmic.
The crackling sound issue's still here though

---

### Post by nightfly68 on 2009-11-30
Hi everyone.. I'm new to ubuntu and trying to set my system with an edirol M16DX
 
Reading this part of the instruction linked
 
 EDIROL M-16DX at usb-0000:00:1d.7-7, high speed : USB AudioPlayback: Status: Stop Interface 0   Altset 1   Format: 0xa   Channels: 2   Endpoint: 2 OUT (ASYNC)   Rates: 44100Capture: Status: Stop Interface 1   Altset 1   Format: 0xa   Channels: 18   Endpoint: 1 IN (ASYNC)   Rates: 44100I see the rates set to 44100, but this soundcard works at 48000 it's possible the cracklings are for this reason?

---

### Post by superpapcpac on 2010-05-24
> **renauddenis said:**
> Supported in Ubuntu 9.10 Karmic.
The crackling sound issue's still here though
How about crackling sound in 10.04. Still an issue?

---

### Post by ceverett on 2010-06-05
Foo.  They need to add support for the Edirol M-10DX as well.  Should be trivial, they're supposed to be the same.

---

### Post by bruhja on 2013-02-04
the m16dx can have the sample frequency set interally to 96000,48000,or 44100.

That may help.

This is a link i found for the clock synch issue workaround havent tried it yet but may help. 

[http://en.usenet.digipedia.org/thread/17996/23177/](http://en.usenet.digipedia.org/thread/17996/23177/)

---

