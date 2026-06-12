---
title: "Canon IP90 &amp; TurboPrint"
date: 2011-06-06
forum: Hardware
---

### Post by WoollyW on 2011-06-06
I'm running Ubuntu 10.04, it recognises my IP90 but it won't print above 600x600, which isn't good enough for high res images & documents.

Is there any way to get the resolution that the printer is capable of (4,800) without buying TurboPrint, and if TurboPrint is the only way to go, which version would have the full res capabalities? i.e. (Pro vs Studio - and I'm guessing that the higher priced package probably has all resolutions...)

We've tried the IP90 with Windows 7 and it saturates magenta - if we can't get it to work with Ubuntu, anyone know any good tricks beyond manual balance editing? Everything we've tried there has failed, although it does at least print at the highest resolution.

I'm not against buying TurboPrint but want to know it's going to work fully before I do - enough time & ink has been wasted so far!

TIA :)

---

### Post by Plexor on 2011-06-15
Support is not yet available for this printer in the linux printer driver projects (looks like work is being done to add support to gutenprint)...  So it seems there is just the Canon v2.7 linux driver (appears to be broken on current distros) and Turboprint.

I noticed on the turboprint site that you can try it free for 30 days ([http://www.turboprint.info](http://www.turboprint.info)).  I suspect you would be able to find out whether or not it meets your needs with the trial.

Currently, I have been using VirtualBox with Windows XP.  I have VBox set up to pass the Canon USB connection to Windows XP.  I installed the official Canon drivers.  When I want to print something, I simply load VBox and print from windows.

Its just a workaround, but it works great and prevents me from having to 'dual boot.'

Would be nice if Canon either updated their drivers, made them opensource or at least released the documentation necessary to support the linux community (or all of the above.)  For now, I will probably just keep using the VBox method.

---

