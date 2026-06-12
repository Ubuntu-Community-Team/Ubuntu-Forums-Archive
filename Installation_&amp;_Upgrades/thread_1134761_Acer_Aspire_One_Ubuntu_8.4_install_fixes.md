---
title: "Acer Aspire One Ubuntu 8.4 install fixes"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by rachelgoodpeople on 2009-04-23
Hi, my friend just installed ubuntu 8.4 on my acer aspire one, but now as I use it I am noticing things not working and was wondering if anyone could help me.  I am new to ubuntu, but familiar with windows, so I know a little about computers. The problems I am encountering so far is my webcam is not working. It works with Skype but not on it's own.  I wanted to download the Cheese app, but it is not listed in the program choices. Also, the photo card reader does not work at all.  Nothing happens when I put the card in, and it is not listed in places>computer. If anyone can help me with these things, it would be awesome, and remeber I'm an ubuntu newbie!  Thanks!

---

### Post by wightman.p on 2009-04-24
Try

sudo modprobe tifm_core
sudo modprobe tirm_sd

---

### Post by imagia on 2009-04-24
You might be better off trying a distro that has already been modified for the Aspire One. It will save you time getting the hardware all working.

Have a look at [Linux4One]("http://www.linux4one.it") - I have it on my Aspire One and everything works out of the box - no fixing required. It's based on Ubuntu Hardy. This has Cheese included.

The new [Ubuntu Netbook Remix]("http://www.ubuntu.com/getubuntu/download-netbook") released yesterday is supposed to work without problems. Well worth a look.

---

### Post by ddrichardson on 2009-04-24
Like the above said, Ubuntu 9.04 Netbook Remix supports the Acer Aspire One, I'm using it now and have been since the first USB image was released.

---

### Post by akoblentz on 2009-04-24
Any idea if that Linux4One supports suspend/resume on lid close/open?

That and the hardware wifi button are the only things that don't work 100% on my Aspire One D150 with jaunty.

---

### Post by ddrichardson on 2009-04-24
> **akoblentz said:**
> Any idea if that Linux4One supports suspend/resume on lid close/open?

That and the hardware wifi button are the only things that don't work 100% on my Aspire One D150 with jaunty.
I've got the switch working on mine but it took a lot of messing around and frankly I haven't written down what I did, the only problem I have is the WiFi LED the kernel patch for which doesn't seem to be applicable in Jaunty.

Haven't tried Linux4One since an earlier release but UNR supports suspend/resume on lid close/open, certainly on the A110.

---

### Post by rachelgoodpeople on 2009-04-24
I think I would just like to keep this version of ubuntu 8.4 do you know how to get the webcam or photo card reader working? Thanks RAchel

---

### Post by ddrichardson on 2009-04-24
I really can't offer any advice, I'm using UNR which has focussed on the 9.04 release. Up until the release of UNR I was using Arch on my Aspire One.

---

### Post by akoblentz on 2009-04-24
> **rachelgoodpeople said:**
> I think I would just like to keep this version of ubuntu 8.4 do you know how to get the webcam or photo card reader working? Thanks RAchel


Is there any reason you cannot upgrade to jaunty? 9.04?
Realistically, everything that you want works out of the box there.
It seems like the kernel in hardy doesn't fully support everything you want.

---

### Post by akoblentz on 2009-04-24
> **ddrichardson said:**
> Haven't tried Linux4One since an earlier release but UNR supports suspend/resume on lid close/open, certainly on the A110.

On mine, when I close the lid, nothing happens... At all.  I can suspend/resume manually no problem. Everything works after resume too which is great.  I checked my power preferences and it is set to suspend on lid close.  I'm not sure what's going on.  I didn't see anything of particular interest in dmesg.

---

### Post by ddrichardson on 2009-04-24
If you can suspend/resume manually then the ACPI events are probably wrong. There's a guide on my [wiki]("http://wiki.lynxworks.eu/aspireone/arch#power_management"), its for Arch but its the same.

If not then the lid closing event mightn't be recognised, I couldn't say why though - it is on mine.

---

### Post by rachelgoodpeople on 2009-04-24
Well I guess I could. Do I have to do a clean reinstall or can I just upgrade?

---

### Post by akoblentz on 2009-04-24
> **ddrichardson said:**
> If you can suspend/resume manually then the ACPI events are probably wrong. There's a guide on my [wiki]("http://wiki.lynxworks.eu/aspireone/arch#power_management"), its for Arch but its the same.

If not then the lid closing event mightn't be recognised, I couldn't say why though - it is on mine.



Weird.  I didn't have a lid event... I had a lidbtn event.  I added the lid event, restarted acpid, and my machine went into a suspend loop...  Removed it, restarted acpid, everything's back to normal now.

---

### Post by ddrichardson on 2009-04-24
Bizarre.

---

### Post by akoblentz on 2009-04-24
> **rachelgoodpeople said:**
> Well I guess I could. Do I have to do a clean reinstall or can I just upgrade?


You can upgrade, clean install would be best, but you can upgrade...

either do ```
sudo apt-get dist-upgrade
``` or use the GUI update manager.  I think you need to do ```
update-manager -d
``` to get it to show you the jaunty update.  Not sure.

---

### Post by akoblentz on 2009-04-24
> **ddrichardson said:**
> Bizarre.

I agree.  I read somewhere that acpi or the kernel need to be updated/patched.  Something about acpi thinking the lid is sending multiple close events and only 1 open event, so even if it does auto-suspend, it will never wake up... unbalanced open/close events. ((((()  is still an "open" state.

---

### Post by imagia on 2009-04-24
> **akoblentz said:**
> Any idea if that Linux4One supports suspend/resume on lid close/open?

That and the hardware wifi button are the only things that don't work 100% on my Aspire One D150 with jaunty.

Yes, they have got the suspend/resume working and the hardware button too.

---

### Post by akoblentz on 2009-04-24
> **imagia said:**
> Yes, they have got the suspend/resume working and the hardware button too.


You're sure it works on the D150?  Do you know if it was a kernel patch or an acpi patch?  I'd like to avoid using a different distro if possible.

---

### Post by rachelgoodpeople on 2009-04-24
I started the upgrade, is it all going to fit on there???

---

### Post by imagia on 2009-04-24
> **akoblentz said:**
> You're sure it works on the D150?  Do you know if it was a kernel patch or an acpi patch?  I'd like to avoid using a different distro if possible.

I have the light version (LXDE) on my A110 and the suspend/resume is working fine. It even reconnects the wifi. I had the full version before and it was working for me on that too. I don't know how it's been achieved though, best to ask in their forum.

I would try the new Jaunty Netbook Remix, but I found that GNOME is a bit much for the Atom and the 512mb ram, and I don't fancy installing all that bloat I don't need...

---

### Post by ddrichardson on 2009-04-24
> **imagia said:**
> I have the light version (LXDE) on my A110 and the suspend/resume is working fine. It even reconnects the wifi. I had the full version before and it was working for me on that too. I don't know how it's been achieved though, best to ask in their forum.

I would try the new Jaunty Netbook Remix, but I found that GNOME is a bit much for the Atom and the 512mb ram, and I don't fancy installing all that bloat I don't need...
UME isn't too bad as it goes. Not as snappy as XFCE on Arch was but then I compiled a kernel for that and optimised a lot of the build.

---

