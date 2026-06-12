---
title: "Ubuntu 16.04 - AMDGPU-Pro - AMD R9 m395x - Nothing Works"
date: 2016-07-26
forum: Hardware
---

### Post by skinner345 on 2016-07-26
Hey first time poster here.

I'm running an: Alienware 15 r2 with AMD Radeon R9 M395X - Intel® Core™ i7-4720HQ CPU @ 2.60GHz and 16GB of RAM
I'm far from an ubuntu expert but im currently running Ubuntu 14.04 using the propitiatory AMD FGLRX drivers... there are some minor performance issues but other wise things work perfectly.

Now my problem comes when I try to install ubuntu 16.04. I boot from USB (without nomodeset) and the boot loader stalls after throwing text at me and hangs, never reaching the liveCD part of the boot.
This is fixed by my using nomodeset, which allows me to install, but throw this error as i boot into the liveCD:  [drm:amdgpu_init [amdgpu]]*ERROR* VGACON disables amdgou kernel modesetting. No im assuming this issues is because im forcing the nomodeset at boot.

Once the install has finished I cant boot into ubuntu 16.04 without forcing nomodeset, when i do this I can boot to gui and log in.
I then tried to install the AMDGPU-Pro drivers, which install without any issues. I reboot, and nothing changes, except this time when i force nomodeset i can loging but unity doesnt load and im left with a black screen.

Everything I have read so far tells me my hardware is supported...

Any insight or help is appreciated.

---

### Post by skinner345 on 2016-07-27
UPDATE!!!: Still no luck sadly. I can only assume that my hardware is not supported after all. I would still really appreciate anyone else's opinion on this.

---

### Post by QIII on 2016-07-27
The AMD GPU is surely supported.  I suspect the issue is the hybrid graphics:  your i7 also sports Intel HD 4600 graphics.

How old is this machine?  If it is recent, the troubles would have been ironed out with the fglrx driver but I'm not sure with AMDGPU.

---

### Post by skinner345 on 2016-07-29
Hey,

5-6 months old

cant get anything to work.

I upgraded to kernel 4.6 which allowed me to boot without nomodeset, but i still couldn't install the AMDGPU, there were also no radeon/ati/AMDGPU config files or drivers being loaded.


thanks for the response.

---

### Post by skinner345 on 2016-07-29
UPDATE: updated the the new Kernel (4.7) same results as 4.6... I tried installing an updated version of the AMDGPU-PRO drivers and i get the black screen with the curses blinking after the install and reboot
I'm also being warned about possible missing firmware modules for Intel i915 both at startup and anytime i -upgrade etc.

thanks.

---

### Post by yoshii on 2016-07-30
this might be somewhat related:  you have to set nomodeset in grub, so that it remains beyond reboots.  
i think it's in /etc/default/grub ...I forget.  Please search the forums for this.  Anyways, after you edit that, you must do a "sudo update-grub" and let it complete, then reboot.

---

### Post by skinner345 on 2016-07-30
I thought the same but no modest after the amdgpu install creates a login loop and x can't start.  the good news with the 4.7 kernel is that the updates for the kernel and the messa 12.01 updates means I'm now some what stable on the open source drivers with dri3 enabled. 

the amdgpu-pro drivers would bring support for opengl 3.3 and higher I hope :) I'll keep you all posted with my progress... I will post on the amd forums and see if there is an issue with my card etc and link back an info here.

any other opinions are welcome. 

thanks all.

---

### Post by skinner345 on 2016-08-02
Edit: I have posted this question on the AMD forums. no answers as yet.

I have read that kernel 4.8 will contain added support for hybrid GPUs so maybe a solution will present itself in time. 

Would still appreciate input if anyone has any ideas.

thanks

---

### Post by mastablasta on 2016-08-04
> **skinner345 said:**
> 

I have read that kernel 4.8 will contain added support for hybrid GPUs so maybe a solution will present itself in time. 



use what works best for you. if 14.04 works well there is no need to upgrade to 16.04. at leats not yet and at leats not until the driver issues are resolved. AMDGPU is very new (many features are still misisng, full support for chips is missing) so until they stabilize it, use 14.04 if it works well for you.

or suffer through, report as much bugs as you can, so they (devs) know what is wrong, so they can know what to fix.

---

