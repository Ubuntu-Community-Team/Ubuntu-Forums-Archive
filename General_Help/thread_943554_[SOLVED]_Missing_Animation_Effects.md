---
title: "[SOLVED] Missing Animation Effects"
date: 2008-10-10
forum: General Help
---

### Post by ellalan on 2008-10-10
Hi
I have installed compiz-git, everything works except the Burn effect(see the attachment),could someone please tell me how to get that effect. I have searched in this forum but no luck.
I have installed using the link
[http://ubuntuforums.org/showthread.php?t=781218](http://ubuntuforums.org/showthread.php?t=781218)
I am not sure about the version(probably 7.6). TIA.

---

### Post by ellalan on 2008-10-10
The screen shot

---

### Post by Therion on 2008-10-10
Not sure what to tell you other than that you're missing a LOT of animations; probably two-thirds of them are missing by comparison to my install based on your screenshot.

Maybe I'm missing something here (still on my first cup of coffee) but Compiz-Fusion comes pre-installed on a default Hardy install...  Why did you re/install from git?

---

### Post by ellalan on 2008-10-10
Hi
I have installed the compiz-fusion in synaptics(version 7.4), it has many effects as you mentioned but Cube Atlantis couldn't be enabled. Then I tried this, now Atlantis working but the Animations missing.
Is there a way to upgrade the version 7.4 to 7.6?

---

### Post by Therion on 2008-10-10
What version of Ubuntu are you using?

---

### Post by ellalan on 2008-10-10
Hi
Its Hardy Heron 8.04. Thanks for the help.

---

### Post by Therion on 2008-10-10
Okay so there was no need to INSTALL Compiz-Fusion... It's already installed by default.

At this point I'm not sure WHAT you have installed.  I think you might want to simply use Synaptic to uninstall everything Compiz-related and reinstall it again from the Repo.  

Further, do you know what kind of graphics chipset or graphics card your PC has installed?  Not every graphics solution is capable of running Compiz-Fusion.

---

### Post by ellalan on 2008-10-10
Hi
I have done what you told me to do but the compiz settings remain same as when I had compiz-git. How can I remove any trace of compiz-git? If I could do that I can live without the Atlantis and more merrier with Burn and Airplane effects.
My graphics chipset: Mobile Intel(R)945 chipset family
                     Available Graphics memory-251MB
                     Dedicated system memory-64MB
                     Shared system memory-187MB.

---

### Post by armageddon08 on 2008-10-10
> **ellalan said:**
> Hi
I have done what you told me to do but the compiz settings remain same as when I had compiz-git. How can I remove any trace of compiz-git? If I could do that I can live without the Atlantis and more merrier with Burn and Airplane effects.
My graphics chipset: Mobile Intel(R)945 chipset family
                     Available Graphics memory-251MB
                     Dedicated system memory-64MB
                     Shared system memory-187MB.

Try uninstalling compiz-git by:
```
cd compiz-git
./compiz-git uninstall
cd ..
rm -r compiz-git
```

Then remove Compiz-Fusion of the repos from Synaptic and then try reinstalling compiz-git using this method:
[http://ubuntuforums.org/showthread.php?t=643485&highlight=makefusion]("http://ubuntuforums.org/showthread.php?t=643485&highlight=makefusion")
I've the same graphics chipset as yours and have my CF installed by this method works perfectly.

Also, in future whenever you are installing compiz-fusion from git make sure it is safe to compile compiz-fusion from git from [here]("http://status.compiz-fusion.org/").

---

### Post by ellalan on 2008-10-11
Hi
I have removed compiz-git and installed compiz through synsptics, I have got all my effects except the Atlantis. Thank you all for helping me.

---

### Post by armageddon08 on 2008-10-11
> **ellalan said:**
> Hi
I have removed compiz-git and installed compiz through synsptics, I have got all my effects except the Atlantis. Thank you all for helping me.

You're welcome....glad, I could help you.

---

