---
title: "Satellite R10, Tablet fails upon waking from hibernate"
date: 2007-11-01
forum: Hardware &amp; Laptops
---

### Post by JarrettBillingsley on 2007-11-01
I've got a Toshiba Satellite R10 tablet PC with Kubuntu Gutsy.  The tablet works fine, but if I put it into hibernate and bring it back up, the tablet fails to re-initialize.  I found the following lines in the KSystemLog regarding the Wacom driver:

> 	information	Wacom xf86WcmWrite error : Input/output error

There are about 20 of those lines, identical.  

The only way I've been able to get it to work is to shut down and restart.  Needless to say this is a bit of a pain.

Has anyone else experienced this, or knows how to make it work?

---

### Post by oofnik on 2007-11-01
I've heard of the following line of code being appended to the acpi resume script to fix problems:
```
/bin/setserial /dev/ttyS0 port 0x0200 irq 5 autoconfig
```
That's from an IBM ThinkPad wiki page, so the numbers may be different for your particular hardware. It's worth a shot though. Good luck.

---

### Post by JarrettBillingsley on 2007-11-02
Thanks for the tip, but as you expected it doesn't work with mine.. the tablet is ttyS0, though, so it's at least in the ballpark.

---

### Post by JarrettBillingsley on 2007-11-02
Meh, I ended up downgrading to Feisty, and it works fine with this.  I think I'm gonna give Gutsy a few more months to get the kinks worked out (this was not the only problem I was having, by far).

---

### Post by JGSD on 2007-11-03
> **JarrettBillingsley said:**
> Meh, I ended up downgrading to Feisty, and it works fine with this.  I think I'm gonna give Gutsy a few more months to get the kinks worked out (this was not the only problem I was having, by far).

I'm using the exact same tablet and have experienced the same problem with hibernating. I am also unable to do a clean shut-down, either. When I do, the screen goes black and the hard drive light practically stays on non-stop. I left it like this for an hour and it didn't stop. At first, I thought it was doing a memory dump, but I only have 1GB of RAM, so I can't see why it would take so long. Besides, there's no reason I can think of for it to do a dump before shutdown!

JarretBillingsley: You mentioned that you'd experienced other problems on your R10, too? I must say that everything else seems to be working fine for me (even WiFi, Compbiz etc etc). It's only the Hibernate and Shutdown commands giving me problems. What else did you have problems with?

Is anyone else using the Toshiba Satellite R10 Tablet and having problems with Shutdown and Hibernate?

---

### Post by froghopper on 2007-11-03
I have got a R10 and the wacom pen inoperative after resuming from suspend happens to me. It seems to be something to do with the serial port ttyS0, which the wacom driver is attached to, going away and this is the meaning of the "ttyS0: LSR safety check engaged!" which appears in my /var/log/messages. 

This has been reported several places but it sounds to me that it may be something deep and messy to do with the 2.6.22 kernel.

[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/137563](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/137563)
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/108961](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/108961)
[http://www.nabble.com/linuxwacom-discuss-f3779.html](http://www.nabble.com/linuxwacom-discuss-f3779.html)

The problem with the tablet hanging on shutdown and the fan racing was solved in feisty by unloading the wifi driver ipw2200 before shutdown but I do not seem to need to do that in gusty for some reason and it shuts down fine for me.

---

### Post by JarrettBillingsley on 2007-11-04
> I'm using the exact same tablet and have experienced the same problem with hibernating. I am also unable to do a clean shut-down, either. When I do, the screen goes black and the hard drive light practically stays on non-stop. I left it like this for an hour and it didn't stop. At first, I thought it was doing a memory dump, but I only have 1GB of RAM, so I can't see why it would take so long. Besides, there's no reason I can think of for it to do a dump before shutdown!

Holy crap, you just described perfectly what happened to me too!  It would also turn the CPU fan on crazy fast.  But yeah, it very rarely shut down correctly.

Other than that, odd touchpad issues (not respecting my "no tapping" option, not remembering other random settings -- using ksynaptics), random crashes here and there, and all this nonsense compounded with the fact that I couldn't really tell that Gutsy was any different from Feisty in terms of features.. meh.

---

