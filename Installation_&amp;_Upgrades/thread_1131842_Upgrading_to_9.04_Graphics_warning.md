---
title: "Upgrading to 9.04 Graphics warning"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by Ur_Cat on 2009-04-21
Hey,

I am relatively new to ubuntu and have been learning the ropes with the help of a friend.

just tried to upgrade to 9.04 and I get this error :

[IMG]http://img237.imageshack.us/img237/6329/13428723.png[/IMG]

these are my graphic card details

[IMG]http://img513.imageshack.us/img513/7356/screenshotcatqueenbitch.png[/IMG]

any ideas ? lol

---

### Post by pastalavista on 2009-04-21
You might have better luck with [this junk]("http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html") than I did. Borked my whole system. I had to reinstall everything. Next time I'll wait for Ubuntu to do it.


edit: I was curious so I went looking

I found this [here]("http://www.ubuntu.com/testing/jaunty/beta")

"Upgrading a desktop system using an ATI video chipset with the fglrx binary-only driver may result in a warning that the driver needs to be replaced. There is a bug in the driver replacement logic, so if you see this prompt, please cancel the upgrade until this is fixed, which will happen immediately after the beta release."

---

### Post by peakshysteria on 2009-04-21
I got the same prompt. I was tempted by living on the burning edge. Answered yes. Running pretty smooth now actually. From the beginning, now issues with the graphics. All worked out of the box.

> **pastalavista said:**
> You might have better luck with [this junk]("http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html") than I did. Borked my whole system. I had to reinstall everything. Next time I'll wait for Ubuntu to do it.


edit: I was curious so I went looking

I found this [here]("http://www.ubuntu.com/testing/jaunty/beta")

"Upgrading a desktop system using an ATI video chipset with the fglrx binary-only driver may result in a warning that the driver needs to be replaced. There is a bug in the driver replacement logic, so if you see this prompt, please cancel the upgrade until this is fixed, which will happen immediately after the beta release."

pastalavista, I read this beforehand as you, as you guys can see the message you refer to and the prompt are different. That's also why I went for it.

---

### Post by vivedekananda on 2009-04-23
I only had a quick look, so I am not completely sure about this,
but it seems ubuntu 9.04 uses fglrx driver version 8.600 which doesn't
support some "older" ati cards anymore. If you want to use the proprietary fglrx driver use catalyst 9.3 or lower.
The open source driver xorg-driver-ati still support the older cards (and should get better as ati released the docs for the concerned hardware).
Try searching the web if you need more info on this.

I also have one of those ati card that aren't compatible with the new fglrx drivers anymore, I think I will wait with my ubuntu upgrade for a while to see how the open source drivers are doing(using kubuntu 8.04 atm).

---

### Post by dagfinn on 2009-04-23
I just got this warning. I'm wary of this, since I've been totally dependent on the AMD fglrx driver to even get my extra screen to work. But I suspect that may not be the case any more. I'm downloading and burning a CD to see how it works when booting from the CD.

---

### Post by wwomack on 2009-04-23
> **dagfinn said:**
> I just got this warning. I'm wary of this, since I've been totally dependent on the AMD fglrx driver to even get my extra screen to work. But I suspect that may not be the case any more. I'm downloading and burning a CD to see how it works when booting from the CD.

Great idea.   I'm downloading the cd iso now so I can try the same thing.    I guess if I'm not happy with the results of that I'll just stick with Intrepid for a while.

---

### Post by sanjit on 2009-04-23
I got the same message. As much as I'm tempted, I think I'll wait a bit, and stick with Kubuntu 8.10.

---

### Post by volchara on 2009-04-23
So how long do we wait? Just try upgrading every day, see if the warning is displayed, and post the results here?

---

### Post by dagfinn on 2009-04-23
> **volchara said:**
> So how long do we wait? Just try upgrading every day, see if the warning is displayed, and post the results here?
The ATI driver is updated each month. There was a release on April 17, so you might wonder whether the warning message is obsolete. If not, perhaps you would have to wait until next month. I'm just speculating.

---

### Post by volchara on 2009-04-23
> **dagfinn said:**
> The ATI driver is updated each month. There was a release on April 17, so you might wonder whether the warning message is obsolete. If not, perhaps you would have to wait until next month. I'm just speculating.

I wonder how long does it usually take for the binary driver to get from "released by AMD" to "available in Ubuntu repos".

---

### Post by dagfinn on 2009-04-24
I tried booting from a CD. Actually two different ones, Ubunutu and Kubuntu.

In Gnome, I can use the GUI for display setup to get a dual monitor setup working. In KDE (which is what I use), I can't. I tried searching and fiddling a bit, without success.

I'm not looking desktop effects. They've never worked on this machine. Just dual monitors. I've only been able to do it with the proprietary ATI drivers before.

I've spent as much time as I'm willing to waste on this right now. Unless someone more knowledgable has some tips.

---

### Post by dagfinn on 2009-04-24
This looks like an explanation of why I can't do it from KDE:

[http://forum.kde.org/ati-radeon-9550-dual-monitor-setup-not-working-kde-4-2-2-t-47263.html](http://forum.kde.org/ati-radeon-9550-dual-monitor-setup-not-working-kde-4-2-2-t-47263.html)

Apparently there are two unfortunate circumstances that together prevent this from working for me. One related to ATI, one to KDE/Kubuntu.

---

