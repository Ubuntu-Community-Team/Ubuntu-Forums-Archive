---
title: "GeForce GT 520 graphics card not found"
date: 2017-11-21
forum: Hardware
---

### Post by psyclone on 2017-11-21
Hi,
I have installed (hardware) a GV-N520D3-1GI (gigabyte) graphics card. When installing Nvidia Driver, the installation program can't locate hardware. I understand it could be a conflict with an open source Nouveau driver. 

When looking at Ubuntu software centre I've found libdrm-nouveau2 is currently installed, but I'm unable to remove due to many dependencies. I can copy & paste in the list of dependencies for libdrm-nouveau2 if this is related to the graphics driver not working.

I desperately need to have this graphics card running to gain accelerated graphics. Can you please help.

---

### Post by Autodave on 2017-11-21
What driver did you install and where did you get it from?

---

### Post by Autodave on 2017-11-21
According to Nvidia's site, you need the 340.104 driver.

---

### Post by psyclone on 2017-11-21
I've also tried blocking the Nouveau Driver from working, to attempt to install the equivalent  Nvidia Driver. I've read several posts but my efforts so far have failed. The graphics card is working-I'm running my monitor through now. But I believe I need to replace the software running graphics card currently or at least update it with a Nvidia Driver to see If I can get the accelerated graphics working.

Have I presented this post correctly to ask for assistance?

Hi Autodave,
I haven't manually installed any graphics driver since installing Ubuntu OS. But I'll try installing the 304.104 al let you know

Thanks to Autodave for his response.

---

### Post by psyclone on 2017-11-21
Can you please attach a link to that driver?

---

### Post by psyclone on 2017-11-21
I'm getting the same thing following thing as before, when attempting to install the 304.104 driver.

ERROR: The Nouveau kernel driver is currently in use by your system.  This   
         driver is incompatible with the NVIDIA driver, and must be disabled   
         before proceeding.  Please consult the NVIDIA driver README and your  
         Linux distribution's documentation for details on how to correctly    
         disable the Nouveau kernel driver.

---

### Post by QIII on 2017-11-21
Hello!

Which release of Ubuntu are you running?

---

### Post by Bashing-om on 2017-11-21
psyclone; OK;

I too will wade in here, we get this sorted out !
Post back the outputs - Between code tags - of termional commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

lsb_release -a
lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display
sudo find / -name "NVIDIA-Linux-*"

```
See what it is going to take to clean up, verify what is ... and what is to then be done.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2017-11-21
It sounds like you downloaded a driver from Nvidia site and are trying to install it. That's not a good idea. This is not Windows.
It's better to use a properly packaged version that takes care of details for you (like blacklisting nouveau). Why can't you use the nvidia driver from the standard repository? Or, if you insist on absolute latest version, see: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

> When looking at Ubuntu software centre I've found libdrm-nouveau2 is currently installed, but I'm unable to remove due to many dependencies.

You don't need to remove it.

> **Autodave said:**
> According to Nvidia's site, you need the 340.104 driver.

False. The 384.xx and 387.xx driver support Kepler (GT400 series) and newer.

---

### Post by Autodave on 2017-11-21
I was waiting for him to respond as to where he got the driver from. Since Nvidia called for the 304, I figured that would at least be safe if he said that he got it from the repositories. If he didn't get it there, he would have to purge whatever one he tried to install from the Nvidia site, if that is what he tried.

We still need to hear where he got the driver and which one.

---

### Post by Yellow Pasque on 2017-11-21
> I was waiting for him to respond as to where he got the driver from.

Since the OP said "the installer" and referenced the "nouveau is loaded" error message, I assumed it was an Nvidia installer rather than a proper package. If that was wrong, OP should link to where s/he got the driver.

> Since Nvidia called for the 304

Where are you getting this information? First, you said the 340.xx was needed, and now Nvidia "calls for" the 304 (which is a different driver series). I'm not sure if you typo'd 340/304?
Either way, the 304 and 340 series are legacy drivers, which do support the GT520, but there's no reason to use them unless one has issues with latest stable driver for that card.
I find this summary helpful: [http://nvidia.custhelp.com/app/answers/detail/a_id/3142](http://nvidia.custhelp.com/app/answers/detail/a_id/3142)

---

### Post by Autodave on 2017-11-22
I apologize: I obviously plugged false info into Nvidia's site last night since I now get the same info as you posted. The second mistake was a typo: just as bad as the first mistake.  Sorry for the bad info.

---

