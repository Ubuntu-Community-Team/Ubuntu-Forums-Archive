---
title: "Flash playing too fast"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by chris-at on 2009-04-28
I'm running Kubuntu 9.04 with Firefox and flashplugin-installer 10.0.22.87ubuntu2/Flash 10,0,22,87 in a VMware machine (vmtools installed).

For some reason all Adobe Flash animations (videos and even [http://www.adobe.com/software/flash/about](http://www.adobe.com/software/flash/about)) play at about twice the speed of normal.

I also can't hear any sound (sound in other apps works).

Any ideas on how to fix this? thanks!

---

### Post by chris-at on 2009-04-28
I was able to fix it by reinstalling with "-purge".

---

### Post by hasadwasas on 2009-06-26
I just installed Xubuntu 9.04 into a VMware machine and have the exact same problem with no sound and all flash videos playing twice as fast as they should.  I used the synaptic package manager to uninstall the adobe-flashplugin version 10. Restarted the system. Reinstalled-- but to no effect. The fast play/stream continues. 

Could a more detailed solution be posted or the full command line used with the -purge option to clarify what fixed the problem? Thanks.

---

### Post by chris-at on 2009-07-07
It worked for me after I switched everything to PulseAudio. VMware has a bug (or PulseAudio?) and will disconnect the sound after booting - wait until you are logged in then reconnect it.

---

### Post by zfoobar1234 on 2009-09-21
> **chris-at said:**
> I'm running Kubuntu 9.04 with Firefox and flashplugin-installer 10.0.22.87ubuntu2/Flash 10,0,22,87 in a VMware machine (vmtools installed).

For some reason all Adobe Flash animations (videos and even [http://www.adobe.com/software/flash/about](http://www.adobe.com/software/flash/about)) play at about twice the speed of normal.

I also can't hear any sound (sound in other apps works).

Any ideas on how to fix this? thanks!


I had issue with Flash videos playing too fast on ubuntu with vmware. This fixed it.

This issue fixes the problem in w98 aswell according to another thread but none of these linux threads mentioned this so I'm replying here.


Add these to the virtual machine settings:

pciSound.DAC1InterruptsPerSec = 0
pciSound.DAC2InterruptsPerSec = 0

No idea what they do, but sound works fine after those are in.

---

