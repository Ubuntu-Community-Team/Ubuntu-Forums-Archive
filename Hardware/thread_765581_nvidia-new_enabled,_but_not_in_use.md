---
title: "nvidia-new enabled, but not in use???"
date: 2008-04-24
forum: Hardware
---

### Post by jimmy the saint on 2008-04-24
In the hardware drivers window it shows that nvidia_new is enabled, but next to that it says it is not in use.  How do I make ubuntu use it?  If it is enabled shouldn't it use it by default?

---

### Post by ew16301 on 2008-04-24
Im having the same problem

---

### Post by TechboyUK on 2008-04-24
Me too.

---

### Post by KevLeviathan on 2008-04-24
I have the same problem.

---

### Post by jimmy the saint on 2008-04-24
I came accross another thread where the "solution" was to download the free86 drivers.  Thats great, but last time I checked they don't enable 3d on most cards.  I was checking out xorg.conf and everything listed is generic or "enabled device."  there is no entry for the nvidia driver.  I will have to do a little research on this one.

---

### Post by hvacr on 2008-04-24
Same here, I went with envy. Seems to be ok with that.

---

### Post by masticate on 2008-04-24
Hi I had the same problem. 

I resolved it by:
[LIST=1]
[*]unchecking the enabled box
[*]reboot
[*]checking the enabled box (which downloads and installs the driver)
[*]reboot
[/LIST]

---

### Post by bclintbe on 2008-04-24
I have the same problem with the ATI card on my laptop. I've been using 8.04 BETA with all the updates for the past few weeks, and it let me use my ATI drivers without any problems (I was using 3D Desktop). Today I install the final release of 8.04 and now I have a driver that is enabled but not in use... ???

---

### Post by jimmy the saint on 2008-04-24
masticate's solution works.  A slightly faster way that I just found is to open synaptic, and go to settings>repositories and where it asks Download From, select other.  Click on the button that says use the best server (or whatever it says) at the upper right.  This will test the servers available and pick the fastest one.  Then go to the hardware drivers section and enable the driver (it should now be disabled for some reason).  
This way only requires one restart rather than two.

Hopefully all Hardy bugs are this easy to fix!!

Good luck all!

Marking as solved

---

### Post by cogadh on 2008-04-24
> **jimmy the saint said:**
> masticate's solution works.  A slightly faster way that I just found is to open synaptic, and go to settings>repositories and where it asks Download From, select other.  Click on the button that says use the best server (or whatever it says) at the upper right.  This will test the servers available and pick the fastest one.  Then go to the hardware drivers section and enable the driver (it should now be disabled for some reason).  
This way only requires one restart rather than two.

Hopefully all Hardy bugs are this easy to fix!!

Good luck all!

Marking as solved
Its not really a bug with Hardy. Since this is Ubuntu release day, the official repo servers are being absolutely hammered by traffic, which is causing some people (myself included) to have some problems downloading the restricted drivers. If you switch to a different server as you described, you are guaranteed a better connection and will be able to easily download and install the driver.

---

### Post by doriard on 2008-04-26
How do I get the "Hardware Drivers" window to become available in Kubuntu?  The Add/Remove Programs shows that it's installed, but it's not showing up.  I'm having problems with both video and wireless drivers and I need to access the Hardware Drivers settings.

---

### Post by prock on 2008-04-26
In Ubuntu 8.04 64 bit. When I enable the Nvidia-new driver I boot to a bright white screen with a 1 and a half inch gray vertical line.  My notebook screen resolution is 1280 X 800 in System > Preferences > Screen Resolution as it should be.  It lists refresh rates of 60 or -2147483. Is this a bug?

---

### Post by ludicrous on 2008-06-17
I just reinstalled Ubuntu, and I'm having this problem.  I've tried all of the suggestions above, and nothing has ever come up to download the driver. Any other ideas? Can I find it in Synaptic and download it manually?

---

### Post by ludicrous on 2008-06-17
Never mind- it just worked.

If your situation matches mine half an hour ago... just keep trying, maybe fiddle around with the repositories in Synaptic.

---

### Post by Odrodzona-Sarmacja on 2008-06-18
I had once something like that. Unchecking and checking in restricted hardware menu didn't work. So...

I removed the nvidia-glx-new package in synaptic. Then I rebooted in recovery mode and let Ubuntu fix my x display server. Then I went to restricted drives and checked for it, to install it anew. After reboot everything was back to normal.

;)

---

