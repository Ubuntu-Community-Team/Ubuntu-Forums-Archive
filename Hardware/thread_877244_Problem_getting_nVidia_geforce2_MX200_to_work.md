---
title: "Problem getting nVidia geforce2 MX200 to work"
date: 2008-08-01
forum: Hardware
---

### Post by Sharpiedeluxe on 2008-08-01
Ok, so basically I'm having trouble getting the card stated above working at least semi-normally. I can run it with vesa drivers, but even though I have nvidia drivers, they don't seem to be working. However, xorg lists the driver as nvidia, and under the restricted drivers tab, it says the driver exists and is in use. 

lspci states: VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)

dpkg states: ii nvidia-glx
               NVIDIA binary XFree86 4.x/X.Org driver
            
             ii nvidia-kernel-common
               NVIDIA binary kernel module common files

If you guys need anything else let me know, thanks.

---

### Post by phidia on 2008-08-01
I believe there is a nvidia-glx-legacy package for your card. 
What exactly are you noticing-symptoms that tell you the driver isn't working?
(The card is working-it just may not be driven correctly)
You can also edit your xorg.conf and use the opensource "nv" driver, but you probably want more than that.

---

### Post by Sharpiedeluxe on 2008-08-01
Well, I just installed the legacy package. Mainly the symptoms are that my resolution stays at 800x600 and Im still using vesa drivers. xorg says that it's using nvidia under the device, so I really don't understand what I would need to do in regards to changing anything in xorg to get this working.

[edit] yes, I believe the card IS working, just I dont know whats going on with the drivers. Just when I boot, it states that I'm running in low graphics mode.

---

### Post by abyssius on 2008-08-08
I've been struggling to get my nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2) card to work for months. I had no problem using the basic 'nv' driver, which doesn't support 3d operation, special effects, etc. Every time I tried to invoke the nvidia restricted driver [nvidia-glx-legacy] via synaptic manager or the [system/hardware drivers] menu, I got the same low resolution problem you describe.

Each time I invoked the restricted driver, I had to manually edit xorg.conf to select driver 'nv' to get back to high resolution (1280X1024) screen. After much google-based research, I've finally fixed the problem. I now have full 3-d and all the special effects Ubuntu has to offer. I accomplished it in two stages:

(a) Following the advice of member dpatel, [http://ubuntuforums.org/showthread.php?t=582818]("http://ubuntuforums.org/showthread.php?t=582818") I edited the compiz file [/usr/bin/compiz] and commented out the line: NVIDIA_MEMORY="65536" # 64MB (put a hash in front of it). This made sense, since my MX200 only had 32MB of memory. However, this did not by itself solve the problem.

(b) I next used synaptic to remove the nvidia-glx-legacy driver, and then I installed the regular nvidia-glx driver, even though it is not supposed to support the MX200. I rebooted my computer - voila - 1280X1024 and full 3-d special effects functionality.

I'm pretty sure both these steps are needed, since I had tried the nvidia-glx driver before, and the low resolution problem occured. Anyway, I hope this solution works for you.

---

