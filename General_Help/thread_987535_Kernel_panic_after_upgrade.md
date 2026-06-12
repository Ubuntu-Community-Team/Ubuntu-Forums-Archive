---
title: "Kernel panic after upgrade"
date: 2008-11-19
forum: General Help
---

### Post by mikelygee on 2008-11-19
I upgraded my laptop to Ubuntu 8.10  still using my old, custom-built kernel, and all was fine.

 

Then I decided to try the new ‘official’ Ubuntu kernel.

 

Now I can’t boot, using either the old or new kernel. The tail end of the boot messages looks like this:

 

    […] Using IPI No-Shortcut mode

    […]   Magic number: 0:28:905

    […]   hash matches device ptyzl

    […] Freeing unused kernel memory: 372k freed

    mount: you must specify the filesystem type

    […] Kernel panic – not synching: Attempted to kill init!

 

I’ve booted from a live CD, mounted the root file system from the harddisk, used ‘chroot’ to re-install both the old and new kernel versions, and even ran ‘update-initramfs’, all with no change in the symptoms.

 

Any suggestions would be greatly appreciated!

 

--Mike

---

### Post by omycron on 2010-01-18
Hey!

I've got a similar problem ...

I decided to upgrade my Ubuntu 8.10 to 9.10.
So first I had to upgrade to 9.04.
This worked fine, so far. I got no errors, rebooted the system and so I got Ubuntu 9.04.

Then I wanted to upgrade to 9.10.
So first I made an update and installed the latest software (apt-get update && apt-get upgrade).

Then I did the same thing like before, when I did the upgrade to 9.04. But after downloading the files there occured several errors while installing. Then after about 15 errors or so, the upgrade-process stopped and told me, that there were several serious errors and this upgrade will be undone via 'dpkg --configure -a' or so. And I should pack all log files from this upgrade and report this error.

So it tried to undo this upgrade, but it didn't seem to work. After ending of this upgrading-process I tried 'apt-get update' and 'apt-get upgrade' and I got told, that there were not fulfilled dependencies. But installing these missing ones didn't work either.

So I decided to restart my system. But this seemed to be the wrong way.
So now it doesn't boot anymore, only a few seconds. Then my front-LEDs start flashing. If I try the recovery, the last lines are
'Kernel panic - not syncing: Attempted to kill init!'
'Dumping ftrace buffer:'
'  (ftrace buffer empty)'

I also took a picture of this final screen, so If there is interest in this pic, I could upload it somewhere ...

But the worst thing is, that I cannot start any of my older kernels, cause they encounter the same problem!

My system is a:
Samsung X22 - Notebook
2GB RAM
2 x 2GHz Intel Core 2 Duo T7300
ATI Radeon Mobility HD 2400

What else is needed?

I hope someone can help me ...
& thx in advance

---

