---
title: "&quot;Best&quot; ultralight laptop for Ubuntu?"
date: 2010-12-11
forum: Hardware
---

### Post by RBLevin on 2010-12-11
By "best" I mean, ideal collection of hardware for Ubuntu native open source drivers.

I presently have an old but good Alienware Area 51 laptop, a classic MSI Wind U-123 netbook, and a Lenovo S-12 netbook.

Ubuntu likes the MSI. Everything worked after install, no fiddling required. But the MSI only has 2G RAM and, for a main PC, doesn't have a fast architecture.

The Lenovo has audio and video playback problems that, despite tweaking, I have been unable to resolve, and which got worse after upgrading to 10.10. CPU utilization hits 100% when I play videos. The videos stutter. If I switch to the proprietary Nvidia driver, video playback degrades further and, amazingly, the videos get corrupted (bizarre and, you would think, impossible). Oddly, if I am on the open source Nouveau driver and open the volume control applet before playing audio or video, everything works. So, it's more of an annoyance than a critical failure. There's something in the sound config that I and others here and elsewhere have not been able to resolve.

Since upgrading to 10.10 from 10.4, the Alienware hangs when embedded videos are played back in Chrome (not in Firefox). Disabling the proprietary Nvidia driver solves the problem, but 2D acceleration seems less effective, and I believe 3D acceleration is not available yet on Nouveau. The Alienware also required tweaking to get the sound I/O ports to operate properly (basically I had to tell Ubuntu that it running on a certain Lenovo laptop).

As an aside, I am tired of Nvidia's drivers. Nvidia does not provide an easy way (i.e., not time consuming) to upgrade; and they never seem to update via the Software Center or Update Manager, yet there are more recent versions on Nvidia's site.

No deal-breakers here, and I am not posting to ask for support on the above annoyances. They are for background only. 

But I am in the market for a new, fast ultralight; I want to put Ubuntu 10.10 on it; and I don't want to waste time futzing with drivers. So my question is, are there any known *ULTRALITE* models from major vendors (Lenovo, Sony, Dell, etc.) that are perfectly aligned with Ubuntu's preferred hardware out of the box? Is there a killer Ubuntu laptop?

An alternate version of this question would be: which audio, video, and wireless chipsets should I look for (or look out for)?

Thanks much for your advice.

RBL

---

### Post by sanderd17 on 2010-12-11
Don't go for Toshiba, Toshiba laptops have quite a few problems with ubuntu.

take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1620640](http://ubuntuforums.org/showthread.php?t=1620640)

---

### Post by ajgreeny on 2010-12-11
In spite of your comments about nvidia, most users would probably say that they have the best choice of proprietary drivers available for graphics cards, thouugh ATI/AMD are getting better.

Intel chips for all things are also generally very well supported, though that does not mean there are never problems, as you may remember with the lack of Poulsbo drivers a while back on some netbooks, in particular.

Linux in general and Ubuntu in particular is getting better and better, I think, in terms of hardware support and compatibility.  Just avoid the very newest hardware, and it is likely that most hardware will be supported, either out of the box, or with very little work to get it going.

---

### Post by cascade9 on 2010-12-12
> **RBLevin said:**
> As an aside, I am tired of Nvidia's drivers. Nvidia does not provide an easy way (i.e., not time consuming) to upgrade; and they never seem to update via the Software Center or Update Manager, yet there are more recent versions on Nvidia's site.

No deal-breakers here, and I am not posting to ask for support on the above annoyances. They are for background only. 

The 'no easy way to upgrade' is more of a distro problem than nvidias problem. 

I dont know why people have this drive to always have the 'newest' drivers. If you are gaming, there might be some point, but for desktop use, its worring over nothing. 

If you really want the newest nvidia drivers you can add a PPA, but I wouldnt. Its been known to cause problems.

---

### Post by linuxforartists on 2010-12-12
If by "best" you mean cheap and pre-installed with Ubuntu, this qualifies:
[URL="http://www.omgubuntu.co.uk/2010/11/dells-new-vostro-v130-ultra-thin-ubuntu-laptop/"]
Dell's new Vostro V130 ultra-thin laptop with Ubuntu 10.04[/URL]

System76 and ZaReason's machines are probably better, but it'd be hard to beat the Dell price (US$429).

---

### Post by RBLevin on 2010-12-14
Thanks.

---

### Post by RBLevin on 2010-12-14
Thanks. BTW, I'm not driven to be on the latest and greatest. Only reason I'm asking about that is because I am experiencing issues with the proprietary driver, and would like to try a more recent version to see if it resolves same. Right now I'm on the open source driver, and it works great -- but it can be slow when rendering 2D, and it won't do 3D yet.

---

### Post by RBLevin on 2010-12-14
> **linuxforartists said:**
> If by "best" you mean cheap and pre-installed with Ubuntu, this qualifies:
[URL="http://www.omgubuntu.co.uk/2010/11/dells-new-vostro-v130-ultra-thin-ubuntu-laptop/"]
Dell's new Vostro V130 ultra-thin laptop with Ubuntu 10.04[/URL]

System76 and ZaReason's machines are probably better, but it'd be hard to beat the Dell price (US$429).
Thanks.

---

### Post by linuxforartists on 2010-12-15
You're welcome.  Another computer I was considering was this [Toshiba computer with Ubuntu]("http://www.linucity.com/scripts/prodView.asp?idproduct=48").  Good compromise between the size of a netbook and the power of a laptop.

The only thing holding me back is the horrid design of that LinuxCity website.  Doesn't exactly inspire trust.  Or maybe that's where they're saving money, so they can sell cheaper Linux machines?

Good luck with your decision.

---

### Post by RBLevin on 2010-12-16
> **linuxforartists said:**
> You're welcome.  Another computer I was considering was this [Toshiba computer with Ubuntu]("http://www.linucity.com/scripts/prodView.asp?idproduct=48").  Good compromise between the size of a netbook and the power of a laptop.

The only thing holding me back is the horrid design of that LinuxCity website.  Doesn't exactly inspire trust.  Or maybe that's where they're saving money, so they can sell cheaper Linux machines?

Good luck with your decision.

Thanks. Looks like a great deal. I'll check it out. I'll report back here after I buy something and go through the install.

I might have bought myself some time on my Lenovo. The light bulb went off when I realized I could simply add USB audio. I popped an old Turtle Beach dongle into the Lenovo. Has a C-Media chipset, which every version of Ubuntu I have used since perhaps 6 or 7 has liked. Viola. Good, non-crackling sound. You can buy these on Amazon for $6 to $10! They'll show up under "linux usb audio."

Re: their web site, I looked them up but only found one blog post about them: [http://www.oblurb.com/anyone-bought-a-computer-from-linuxcity.html](http://www.oblurb.com/anyone-bought-a-computer-from-linuxcity.html)

---

### Post by linuxforartists on 2010-12-18
Nice to hear you're getting some extra mileage out of your machine.  If it makes you feel better, I'm running a 3-year-old laptop that only has a single-core AMD processor.  Although that fulfills most of my needs, except viewing 1080p HD videos at full-screen.

> **RBLevin said:**
> Re: their web site, I looked them up but only found one blog post about them: [http://www.oblurb.com/anyone-bought-a-computer-from-linuxcity.html](http://www.oblurb.com/anyone-bought-a-computer-from-linuxcity.html)

I laughed when I read that page.  If you click on "view original thread with replies," you'll find it was actually written by *me*!  That was the first thing I ever posted on Ubuntu Forums.  I can't for the life of me figure out how my thread ended up on that blog!

I've been looking at Linux laptops, and LinuxCity is the only one that has prices that can compete with Dell's Ubuntu machines.

---

### Post by Alver on 2010-12-18
> **sanderd17 said:**
> Don't go for Toshiba, Toshiba laptops have quite a few problems with ubuntu.

take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1620640](http://ubuntuforums.org/showthread.php?t=1620640)
I have a Toshiba L505-10M with a dual boot W7/U10.04.1 64b. U works fine with few hiccups (some Fn keys do not work but since I do not use them, this is not a problem). I had an issue with 64b Flash but after I installed the Lovinglinux patch all is working now. No issues with temperature or fans either.

Alver

---

### Post by RBLevin on 2010-12-18
> **linuxforartists said:**
> Nice to hear you're getting some extra mileage out of your machine.  If it makes you feel better, I'm running a 3-year-old laptop that only has a single-core AMD processor.  Although that fulfills most of my needs, except viewing 1080p HD videos at full-screen.



I laughed when I read that page.  If you click on "view original thread with replies," you'll find it was actually written by *me*!  That was the first thing I ever posted on Ubuntu Forums.  I can't for the life of me figure out how my thread ended up on that blog!

I've been looking at Linux laptops, and LinuxCity is the only one that has prices that can compete with Dell's Ubuntu machines.

Wow. That's nuts! Small world theory proven once again.

I love my Lenovo S-12. It's a shame they stopped making it. Light, great keyboard, 12" screen, and 3G RAM -- which is hard to find in a true netbook. CPU and video performance could be a little better, but for what I need it to do -- biz apps in the cloud -- it's ideal.

One thing I love about Ubuntu and Linux in general is that it shatters the myth of new hardware. I have some very old machines with ridiculously limited resources by today's standards that run great using Ubuntu.

I have a very old Acer Mini (I think that's what it was called) that was a Mac Mini knock-off. Came with Linspire. I moved it to Ubuntu. Has 256M of RAM. I connected it to my TV, put Boxee and Chrome on it, and the family has a nice Internet TV rig. Runs great. Never have to touch it.

---

### Post by RBLevin on 2010-12-18
> **Alver said:**
> I have a Toshiba L505-10M with a dual boot W7/U10.04.1 64b. U works fine with few hiccups (some Fn keys do not work but since I do not use them, this is not a problem). I had an issue with 64b Flash but after I installed the Lovinglinux patch all is working now. No issues with temperature or fans either.

Alver

Thanks, Alver.

---

### Post by RBLevin on 2010-12-18
> **linuxforartists said:**
> I've been looking at Linux laptops, and LinuxCity is the only one that has prices that can compete with Dell's Ubuntu machines.

See also here:
[http://www.linuxcertified.com/linux_laptops.html](http://www.linuxcertified.com/linux_laptops.html)

---

### Post by linuxforartists on 2010-12-21
Cool, thanks for the tip on Linux Certified.

---

### Post by TNT1 on 2010-12-21
ultralight and best? Macbook Air:popcorn:

---

