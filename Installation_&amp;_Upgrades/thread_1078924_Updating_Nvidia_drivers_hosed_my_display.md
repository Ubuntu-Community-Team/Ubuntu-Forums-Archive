---
title: "Updating Nvidia drivers hosed my display"
date: 2009-02-23
forum: Installation &amp; Upgrades
---

### Post by RockDawg on 2009-02-23
I just installed Ubuntu 8.10 for the purpose of running XBMC.  I am a total Linux newb, but the Ubuntu install went like a breeze.  Next I needed to update the Nvidia display drivers.  Here's where everything went downhill.  I downloaded the file (NVIDIA-Linux-x86-180.29-pkg1.run) and tried to run it with "sudo sh" and it complained that i needed to shut down X server, so I read that "/etc/init.d/gdm stop" would do it but it still complained it was running.  So I ran it again and then followed it with Ctrl+Alt+F1 and then the Nvidia file would run.  During installation it said something about not being able to find the right kernel and asked if I wanted it to compile a new one.  I said yes, and everything seemed good until it rebooted.  Now Ubuntu will only boot intt low graphics mode and neither of the default propietary version (1.73 and 1.77) fix it either.

So how do I get things back to normal?  And then how do I correctly update to the latest Nvidia drivers?

---

### Post by hansdown on 2009-02-23
Hi RockDawg.

That version is still in beta testing.

Try going to synaptic package manager, and installing the nvidia-glx 

version.

---

### Post by RockDawg on 2009-02-23
I didn't see just nvidia-glx, but there was a nvidia-glx-180 and I selected it.  It seemed to install and said it was removing 1.73, but when I go to Hardware Drivers, it says it's not using a propietary driver and the only options are 1.73 or 1.77.

---

### Post by hansdown on 2009-02-23
If you click system> administation>hardware drivers, enter password. Does it say anything about these drivers?

Sorry. The 1.77 drivers seem to be stable. You should use those.

---

### Post by RockDawg on 2009-02-23
> **hansdown said:**
> If you click system> administation>hardware drivers, enter password. Does it say anything about these drivers?

Sorry. The 1.77 drivers seem to be stable. You should use those.

...but when I go to Hardware Drivers, it says it's not using a propietary driver and the only options are 1.73 or 1.77.

The 180 drivers are the ones I really need as they have the functioning VDPAU support which is the whole reason I'm trying Ubuntu.  I know others are using them without issue.

---

### Post by hansdown on 2009-02-23
I apologise RockDawg.

I thought your problem was easily fixed. I'll keep checking back until someone who can help comes along.

---

### Post by soltanis on 2009-02-24
IMO you should never use the Nvidia installers (unless you really know what you're doing). I've read somewhere that the .sh installers overwrite and break crap left and write; rather, you should use .deb packages.

As to what you should do now;
I recommend you regenerate your xorg.conf file, since that is probably what is screwing you over. You do this by running

```

Xorg -configure

```

I believe, at the command line. The output of that will tell you it wrote a new configuration file; replace your old one with that, then try restarting X.

Once you do that, try uninstalling all the nvidia drivers you have, then reinstalling 177.

---

### Post by RockDawg on 2009-02-24
OK, I got my desktop showing normal again, but how do I get the Nvidia 180 drivers installed?

---

### Post by hansdown on 2009-02-24
RockDawg, I caution you about using something that is still in beta testing,

as it may not work the way you wish it to.

It will be released soon, so you will be able to get it in synaptic, 

which is the safest place.

If you so wish, you can check this thread.

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by MCMcButtah on 2009-03-12
> **RockDawg said:**
> OK, I got my desktop showing normal again, but how do I get the Nvidia 180 drivers installed?

I am thinking what happened is you said yes to the question the installer gives you about configuring your display. This usually hoses up your xorg.conf. That is what has happened to me in the past anyway. If you do the install, but leave your
xorg.conf as was, then you should be ok. *should*. But since you were already able to recover from your last attempt, might as well give it another go.

You should probably backup your xorg.conf first though

---

