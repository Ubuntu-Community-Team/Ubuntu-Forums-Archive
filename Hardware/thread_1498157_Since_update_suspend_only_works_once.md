---
title: "Since update suspend only works once"
date: 2010-05-31
forum: Hardware
---

### Post by timosha on 2010-05-31
Since a regular Ubuntu 10.04 update last week suspend only works once on my Thinkpad R51 - 2887. The updates are the "recommended updates".

The first suspend and resume works fine. The next suspend results in a blinking moon led with a hanging system. Only a power recycle can cure this.

When I remove all updates everything works fine again, as before.

Is there anybody out there experiencing this problem after a Lucid update?

---

### Post by timosha on 2010-06-01
Am I really the only one with this suspend problem after a recommended Lucid update?

I removed all updates and everything is working fine again. But yet, I am a bit surprised that a recommended update can break such an important function on a laptop.

---

### Post by timosha on 2010-06-01
Sorry for this monologue :confused:

An update to gnome-screensaver 2.30.0-0ubuntu2 caused the problem. Downgrading to gnome-screensaver2.30.0-0ubuntu1 solved it.

---

### Post by Soul-Sing on 2010-06-01
timosha thx sharing this with us.

---

### Post by Cavsfan on 2010-06-01
Glad to see you solved your own problem! 
I have not had that same problem and I have gnome-screensaver 2.30.0-0ubuntu2
The newest update. That is peculiar though!

---

### Post by timosha on 2010-06-01
Suspend is very tricky on an IBM Thinkpad R51. In the past pm-utils was always the cause of a broken suspend, but not this time.

I did some troubleshooting on (almost) every recommended update I have and isolated gnome-screensaver. I filed a bug report.

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/588406](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/588406)

---

### Post by pwaugh on 2010-06-01
> **timosha said:**
> Sorry for this monologue :confused:

An update to gnome-screensaver 2.30.0-0ubuntu2 caused the problem. Downgrading to gnome-screensaver2.30.0-0ubuntu1 solved it.

How do you downgrade?  I also experience this problem.  My system also locks to the point I have to remove the battery to reboot, or when it attempts to reboot it says ATA3 and ATA4 fail and then locks.

I'm on an HP Touchsmart with an updated 10.04 LTS

patrick

---

### Post by timosha on 2010-06-01
> **pwaugh said:**
> How do you downgrade?  I also experience this problem.  My system also locks to the point I have to remove the battery to reboot, or when it attempts to reboot it says ATA3 and ATA4 fail and then locks.

I'm on an HP Touchsmart with an updated 10.04 LTS

patrick

In Synaptic search for the package and highlight it. Then in the taskbar select "Package" and then select "Force Version". Now you get a dropdown list. Select the previous version.

Then select "Lock Version" to avoid that an upgrade will overwrite your selected version.

---

### Post by pwaugh on 2010-06-01
> **timosha said:**
> In Synaptic search for the package and highlight it. Then in the taskbar select "Package" and then select "Force Version". Now you get a dropdown list. Select the previous version.

Then select "Lock Version" to avoid that an upgrade will overwrite your selected version.

Thank you.  After doing this do I need to reboot or restart the x-server?

patrick

---

### Post by timosha on 2010-06-01
> **pwaugh said:**
> Thank you.  After doing this do I need to reboot or restart the x-server?

patrick

Reboot please.

---

### Post by pwaugh on 2010-06-01
> **timosha said:**
> Reboot please.

As soon as I downgraded, I had to run gconf-editor again to turn my touchpad back on, as something again mysteriously turned it off!

I have now rebooted and will post here is it gets turned off again after this downgrade.

patrick

---

### Post by seul on 2010-11-19
Thanks for posting mate, that bothered me on my t60 for quite a while now. Will let you know whether it worked or not.

Edit: Worked twice now, so looking good. Thanks again.

---

