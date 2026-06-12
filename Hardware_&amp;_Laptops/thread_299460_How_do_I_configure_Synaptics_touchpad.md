---
title: "How do I configure Synaptics touchpad?"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by finite9 on 2006-11-14
In Breezy Badger, my touchpad worked fine, but since Dapper, the touchpad is overly sensitive with regards to using the pad to left-click.  Very light touches of the pad to move the pointer result in a left click, and adversly, if i tap the touch pad to left-click select something, it doesn't register until I left-click touch a second time.

At some point after a daily Dapper upgrade, it started working great again (about 2 months ago), then another upgrade broke it again.

My question is: Can the sensitivity be configured somewhere?  Did the Dapper upgrades simply change the sensitivity or is it more a a driver issue?

---

### Post by ThrobbingBrain66 on 2006-11-14
if you are using Ubuntu:
sudo aptitude install gsynaptics

if you are using Kubuntu:
sudo aptitude install ksynaptics

these packages allow for configuring things like sensitivity on the touchpad

---

### Post by finite9 on 2006-11-15
I found qsynaptics and ksynaptics for KDE but no gsynaptics for Ubuntu (Iuse Ubuntu).

Is this package in the main/universe/multiverse or other?  I have the first three enabled.

---

### Post by ThrobbingBrain66 on 2006-11-15
its located in the utilities section of universe.

strange that you couldn't find it...when i search for 'synaptics' in Synaptic, gsynaptics shows right above ksynaptics

---

### Post by finite9 on 2006-11-15
I see from your profile that you're using Edgy Eft.  Maybe this package is in Edgys repository, but it's not in Dappers repository.

---

### Post by ThrobbingBrain66 on 2006-11-16
> **finite9 said:**
> I see from your profile that you're using Edgy Eft.  Maybe this package is in Edgys repository, but it's not in Dappers repository.

this is entirely possible...qsynaptics should work for you too.  It's built with QT so it won't look pretty in gnome, but it should still work.

---

### Post by finite9 on 2006-11-16
dont want to install that as it will drag in all the Qt libs as well, but im planning on upgrading to edgy quite soon anyway so I can leave this until then.  Thanks for the tip anyway, im sure it will work fine when I upgrade.

---

