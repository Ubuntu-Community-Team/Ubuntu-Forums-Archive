---
title: "System Restore Utility?"
date: 2008-09-28
forum: General Help
---

### Post by ShinHadoken on 2008-09-28
One thing that I enjoyed about Windows was the System Restore tool. I've had a little PC trouble lately, and I was wondering if there's such a thing for Ubuntu. I know there's Keep for Kubuntu, but is there something for Ubuntu?

Thanks,

SH

---

### Post by hansdown on 2008-09-28
Hi ShinHadoken.

Have you tried sysres?  [http://linux.softpedia.com/get/System/System-Administration/Sysres-41254.shtml](http://linux.softpedia.com/get/System/System-Administration/Sysres-41254.shtml)

---

### Post by TeXtonyx on 2008-09-28
If you don't want to register at softpedia then use,
[http://downloads.sourceforge.net/sysres/sysres0.8.tar.gz?modtime=1219615538&big_mirror=0](http://downloads.sourceforge.net/sysres/sysres0.8.tar.gz?modtime=1219615538&big_mirror=0)

---

### Post by LaRoza on 2008-09-28
Please don't use 1.0.2, use 1.0.3, at [https://launchpad.net/sysres/trunk/1.0](https://launchpad.net/sysres/trunk/1.0)

Download the .deb and double click.

Hope you like it!

---

### Post by ShinHadoken on 2008-09-28
Looks nice, but is it available in the repos? I'd like to stay with software that's in the repos if I can. Also, how well does Keep work in Gnome? If Keeps works with Gnome, and sysres is in the repos, then I'll have a little to choose from. =)

---

### Post by Comhra on 2008-09-28
I didn't know that this was available. How do I use it?  Just point and click in Create, give the restore point a name and click Ok?  Is it really that simple or am I missing something?  I thought Linux was supposed to be hard.

Anyhow, the program tells me that it's gone ahead and created a restore point and the details show in the panel, so I guess I'm good to go.

Looks like I can add a bunch of stuff to the default files to save.

What are the next most important items that I might add?

This is great...mind you, I hope I never have to use it.

---

### Post by LaRoza on 2008-10-03
> **ShinHadoken said:**
> Looks nice, but is it available in the repos? I'd like to stay with software that's in the repos if I can.

No, it is not in the repos. It is open source (and written by me, with other people from the forum).

> **Comhra said:**
> I didn't know that this was available. How do I use it?  Just point and click in Create, give the restore point a name and click Ok?  Is it really that simple or am I missing something?  I thought Linux was supposed to be hard.

Yes, there is more to it if you want, but if you knew (or cared) about that, you wouldn't be using this. (One of the problems with development was that none of use used it and had trouble testing it)

> 
Anyhow, the program tells me that it's gone ahead and created a restore point and the details show in the panel, so I guess I'm good to go.

That is good.

> 
Looks like I can add a bunch of stuff to the default files to save.

What are the next most important items that I might add?

I don't know. Right now, it does video settings, fstab, repository settings and grub. Those are the default because they are the ones I noticed that caused the most problems on the forum when people altered them (and asked for System Restore).

Basically, for system settings, don't change them unless you know what you are changing. I can think of settings that could be changed that might benefit from this, but know of them are system settings like those. 

> 
This is great...mind you, I hope I never have to use it.

If you don't change settings, you probably won't. Most people don't need to change those settings if everything works until you add new hardware or try experimenting.

---

### Post by TeXtonyx on 2008-10-03
I had occasion to use sysres recently. I have a high resolution nvidia video card which I
configured and thought I saved it to xorg.conf. When I rebooted I'd be back to 800 x 600
resolution and a message that my nvidia driver was missing. So I decided to put sysres to
the test and create a restore point so the next time I could just click on the restore point
and not go through the config process again.  Well, it didn't work. But maybe because
the nvidia-settings utility doesn't actually write to and change xorg.conf . Anyway, I 
posted because I think backing up xorg.conf for sysres is at least as important as fstab.
I could manually back xorg.conf and reboot with the live cd and mv a trusted backup 
file of xorg.conf, but I was hoping sysres was going to make that more automatic. When
this X settings problem happened I thought this is a perfect time to install and use sysres.

---

### Post by LaRoza on 2008-10-05
> **TeXtonyx said:**
> I had occasion to use sysres recently. I have a high resolution nvidia video card which I
configured and thought I saved it to xorg.conf. When I rebooted I'd be back to 800 x 600
resolution and a message that my nvidia driver was missing. So I decided to put sysres to
the test and create a restore point so the next time I could just click on the restore point
and not go through the config process again.  Well, it didn't work. But maybe because
the nvidia-settings utility doesn't actually write to and change xorg.conf . Anyway, I 
posted because I think backing up xorg.conf for sysres is at least as important as fstab.

That is a driver issue. I think. 

> 
I could manually back xorg.conf and reboot with the live cd and mv a trusted backup 
file of xorg.conf, but I was hoping sysres was going to make that more automatic. When
this X settings problem happened I thought this is a perfect time to install and use sysres.

sysres does do that, it just backs up xorg.conf and writes it back. 

If manually moving the file did work, then could you give more information about what happened with sysres?

---

### Post by TeXtonyx on 2008-10-11
I think you were right about the driver. At first I downloaded the driver from Nvidia and 
it seemed like it recompiled or rebuilt the kernel? so that the driver was incorporated.
I tried again with I think envyNG and it took longer about 30 seconds in the rebuild
process and afterward the driver stuck. It used the xorg.conf that I had created with
the Nvidia driver installation process. So I think sysres did not fail and is quite a 
good idea! Thanks for your observation about the driver.
EDIT: Actually I see build-essential is for building packages not the kernel.

---

