---
title: "MSI Wind L2100 - ATI x1250"
date: 2010-01-14
forum: Hardware
---

### Post by Shibblet on 2010-01-14
START OF RANT

When are companies like Intel and ATI going to get it.  Nvidia understands.

You can't drop support of a product that is still being sold!  I just bought this notebook, it's not even 2 months old.  And it came equipped with a graphics processor that ATI dropped Linux support for!  The new Xorg server, which has been universally picked up and used by all the major distributions... IS NOT COMPATIBLE WITH THE CURRENT DRIVER.

I feel like ATI takes [this]("http://www.youtube.com/watch?v=JcJkhSUSnek") approach to my new computer.

What?  Did I hear that correctly?  Why even make a frickin' driver then?   [Here's the driver...]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.2&product=2.4.2.3.8&lang=English") but it doesn't work.

This reminds me of when I was in high-school, and asked that girl out, and she told me she'd rather be friends.

Me:  I need a Linux driver for my ATI x1250.
ATI:  Here you go.
Me:  Thanks!  Wait... It's not compatible with the new Xorg.
ATI:  We know.
Me:  Every distribution uses the new Xorg.
ATI:  We know that too.
Me:  What the heck is that driver for then?
ATI:  Legacy support.
Me:  I just bought it in a new notebook.
ATI:  It's still legacy.

END OF RANT

Anyway, I've been searching and searching for days trying to figure out how to get Kubuntu Karmic on this notebook, and the only answers I can come up with are... No.

Without this driver, my video playback blows the south side of a north bound bovine.

Is there anything that can be done to get this driver working correctly, or did my rant cover it all?  The only other option I have is to run Windows 7 on this computer, and I just don't want to.

---

### Post by Shibblet on 2010-01-15
Bump-diddle.

---

### Post by Shibblet on 2010-01-21
Bump Again.  Hoping someone has some news on a functional ATI Legacy Support Driver.

Or maybe a way to dial back the X Server to allow use of the current drivers.

---

### Post by Shibblet on 2010-01-21
Could I build Arch to work on this notebook, with the correct X server and drivers?

---

### Post by speedkreature on 2010-02-15
At the risk of sounding like an idiot, exactly what is your indication that ATI has dropped support?

What kernel are you using (uname -r)?

My L2100 has an x1200 and is running 9.10, but I can't even really start the installation process.
I have another system, a desktop, with the same card, but a previous version of Ubuntu (9.04 64-bit) and the driver installed fine just now.

---

### Post by Shibblet on 2010-02-16
> **speedkreature said:**
> At the risk of sounding like an idiot, exactly what is your indication that ATI has dropped support?

What kernel are you using (uname -r)?

My L2100 has an x1200 and is running 9.10, but I can't even really start the installation process.
I have another system, a desktop, with the same card, but a previous version of Ubuntu (9.04 64-bit) and the driver installed fine just now.

Nope, you don't sound like an idiot.  I am trying to run 9.10, and I do have functional drivers, but they are open-source.

Check out the [xorg-edgers PPA at Launchpad.net]("https://launchpad.net/~xorg-edgers/+archive/ppa")

---

### Post by speedkreature on 2010-04-01
I'm not really a fan of raising the dead, but I wanted to offer closure to this thread.
AMD does support the chipset (because it is a mobile version), but not as implemented in any given note/netbook.  They leave that up to the vendor.

[http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx](http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx)

I have tried installing support for my X12xx chip using the standard desktop installer and it fails.

The only reason I would say this is a problem is because output via HDMI is not clean.  My test with two different monitors and two different cables (all known good) produced output with horizontal lines and/or snow mixed with the output image.

I would expect that we (Linux powered L2100 owners) are a very small demographic.  Still, we might throw pebbles at them and see if they respond.  I'll post a link for that as soon as I find one...unless someone else beats me to the punch...you know, out of all 2 of us. ;)

---

### Post by Shibblet on 2010-04-01
> **speedkreature said:**
> I'm not really a fan of raising the dead, but I wanted to offer closure to this thread.
Have you never seen Michael Jackson's Thriller?  ;)

> **speedkreature said:**
> AMD does support the chipset (because it is a mobile version), but not as implemented in any given note/netbook.  They leave that up to the vendor.

[http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx](http://support.amd.com/us/kbarticles/Pages/737-28041SupportforATIMobility.aspx)
Yep.  They support the windows version with a legacy driver.

> **speedkreature said:**
> I have tried installing support for my X12xx chip using the standard desktop installer and it fails.

The only reason I would say this is a problem is because output via HDMI is not clean.  My test with two different monitors and two different cables (all known good) produced output with horizontal lines and/or snow mixed with the output image.
I found this same problem.  In Windows 7, HDMI would only support 1280x720.

> **speedkreature said:**
> I would expect that we (Linux powered L2100 owners) are a very small demographic.  Still, we might throw pebbles at them and see if they respond.  I'll post a link for that as soon as I find one...unless someone else beats me to the punch...you know, out of all 2 of us. ;)
Ah!  Now you can join me on the dark side...

Check out my walkthrough for the L2100 and the X-Org Edger drivers.

[http://ubuntuforums.org/showthread.php?t=1443132]("http://ubuntuforums.org/showthread.php?t=1443132")

---

