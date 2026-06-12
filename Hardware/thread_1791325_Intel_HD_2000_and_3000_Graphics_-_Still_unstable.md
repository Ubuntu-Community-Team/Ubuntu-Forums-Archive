---
title: "Intel HD 2000 and 3000 Graphics - Still unstable"
date: 2011-06-26
forum: Hardware
---

### Post by Signal64 on 2011-06-26
I'm still looking for the magic bullet to cure basic Sandybridge desktop stability with 11.04 x64 and Intel HD 2000 or 3000 graphics.

I have 2 desktop systems with an i5 2400 (HD 2000) and i7 2600K (HD 3000) that I have tried with various P67 and z68 motherboards over the past few months. Stability in Windows 7 is fine and no OC'ing is being done.

With a default 11.04 x64 install + updates I eventually end up with random desktop restarts and/or white artifacts (rectangles or full horizontal lines).

The suggestions I've found were to update the kernel and mesa.
I've just tried kernel to 2.6.39.2 and mesa to 7.11.0 110624 and end up in a worse state.
The desktop will end up crashing with a endless loop of blanking the screen and then repainting the background and any open windows. 

This happens with either Unity or Classic mode.
I thought that it was screensaver or power management related but have disabled both.

Ideas?  (other than giving up and throwing a nvidia or ati card in).

---

### Post by exobuzz on 2011-06-28
please see [https://bugzilla.kernel.org/show_bug.cgi?id=38492](https://bugzilla.kernel.org/show_bug.cgi?id=38492)

---

### Post by Hyper01 on 2011-07-02
The solution I found (which seems to work so far) was:
* Upgrade 11.04 to use kernel 3.0.0-rc5 (or later when available)
* Upgrade intel drivers, X, etc via Xorg edgers ppa
* adding i915.i915_enable_rc6=0 as a kernel boot parameter

The last one is what finally got it working on my Asrock Z68 Pro3-M motherboard (using onboard/intel graphics over DisplayPort @ 2560x1600) after much hair pulling.

EDIT: Using an i5 2500K processor.

Thanks to exobuzz for pointing me in the right direction.

BTW, a related (current) kernel bug appears to be: [https://bugzilla.kernel.org/show_bug.cgi?id=38332](https://bugzilla.kernel.org/show_bug.cgi?id=38332)

---

### Post by asrock-z68 on 2011-07-11
I'm having similar issues with an asrock z68 pro-3 m motherboard and an i7 2600k with ubuntu 11.04 desktop. 11.04 server is more stable, but it occasionally hangs during boot as well. I have windows 7 installed with no problems. I was only able to get 11.04 desktop installed by installing 10.10 then upgrading. After upgrading to 11.04 the system would hang during boot. Occasionally I can get the system up and running by booting recovery mode and selecting failsafeX graphics mode.

I'm a newbie with ubuntu and linux in general. I tried updating the xorg-edgers intel drivers and adding the i915 kernel boot parameter as suggested by Hyper01 but had more problems then before. I didn't install the 3.0.0-rc5 kernel as I'm not sure how to do that.

I was wondering if someone would be willing to provide me step-by-step instructions to implement the fix as described in exobuzz's link.

[https://bugzilla.kernel.org/show_bug.cgi?id=38492](https://bugzilla.kernel.org/show_bug.cgi?id=38492)

That seems to be the cleanest solution but I'm not sure how to make the intel_display.c changes.

Thanks for your help.

---

### Post by Signal64 on 2011-07-16
Just tried a a couple of fresh 11.04 x64 installs on a gigabyte GA-Z68MX-UD2H-B3, i7 2600K, 8GB DDR3 1600.
It starts failing for me almost immediately after login.

Steps I followed:

1. Installed 11.04 x64 and online updated.

2. Followed this guide to update the kernel to 3.0rc7 (tried both deb and compile methods after each install try)
[http://www.explodingpenguin.tv/2011/06/07/installcompile-linux-kernel-3-0-in-ubuntu/](http://www.explodingpenguin.tv/2011/06/07/installcompile-linux-kernel-3-0-in-ubuntu/)

3. Updated to today's xorg-edgers

4. Added kernel parameter i915.i915_enable_rc6=0

At each step along the way I tried logging in and use the system until artifacts or other issues appeared. For instance, after edgers update the desktop background goes black and moving the mouse around would re-paint the background again.

I've just switched to classic + no effects to see how that goes.

To confirm, I'm not overclocking and windows 7 x64 "works" fine.

---

### Post by exobuzz on 2011-07-16
> **asrock-z68 said:**
> 
[https://bugzilla.kernel.org/show_bug.cgi?id=38492](https://bugzilla.kernel.org/show_bug.cgi?id=38492)

That seems to be the cleanest solution but I'm not sure how to make the intel_display.c changes.

Thanks for your help.

did you try the boot parameter mentioned a few posts up ?

i noticed asrock released a new firmware that changes the default gpu voltage. perhaps with that it may work better without changes anyway - as i had found before increasing the gpu temp stabalised things somewhat,

---

### Post by Signal64 on 2011-07-16
I tried the i915.i915_enable_rc6=0 kernel parameter mentioned without luck.

As far as applying the patch to the intel code, with xorg-edgers branch I don't know the correct process yet.

---

### Post by exobuzz on 2011-07-16
you could try my kernel then from [http://malus.exotica.org.uk/~buzz/ubuntu/kernel/z68/](http://malus.exotica.org.uk/~buzz/ubuntu/kernel/z68/)

---

### Post by Signal64 on 2011-07-16
Ah.. duh.. for some reason I wasn't thinking it was in the kernel.

Tried it with rc7 and no improvement.
Will give rc5 and your kernel a shot.

---

### Post by asrock-z68 on 2011-07-17
> **exobuzz said:**
> did you try the boot parameter mentioned a few posts up ?

i noticed asrock released a new firmware that changes the default gpu voltage. perhaps with that it may work better without changes anyway - as i had found before increasing the gpu temp stabalised things somewhat,

Hi exobuzz. Thanks for the response. I was able to recompile the kernel with the intel_display.c changes and that allowed me to boot with Unity on a DVI monitor. Adding the i915.i915_enable_rc6=0 kernel parameter alone didn't work for me.

I did upgrade to the 1.40 firmware after that but didn't think to retest a vanilla 11.04. I just tested booting 11.04 liveCD (USB stick) and it appears that works now too! So I think you are correct the firmware upgrade to 1.40 has fixed the problem.

I still can't boot with my 24" Apple LED Cinema Display (DisplayPort) alone although it works just fine on the same hardware with Windows 7 64-bit. It looks like Intel Xserve driver can't figure out a proper configuration. The system still runs (I can ssh into it) but there is no display. Here is an excerpt from the Xorg.0.log file.

[    15.336] (II) intel(0): EDID for output DP2
[    15.336] (II) intel(0): Manufacturer: APP  Model: 9236  Serial#: 34318216
[    15.336] (II) intel(0): Year: 2009  Week: 28
[    15.336] (II) intel(0): EDID Version: 1.4
[    15.336] (II) intel(0): Digital Display Input
[    15.336] (II) intel(0): 8 bits per channel
[    15.336] (II) intel(0): Digital interface is DisplayPort
[    15.336] (II) intel(0): Max Image Size [cm]: horiz.: 52  vert.: 32
[    15.336] (II) intel(0): Gamma: 2.20
[    15.336] (II) intel(0): DPMS capabilities: Off
[    15.336] (II) intel(0): Supported color encodings: RGB 4:4:4 
[    15.336] (II) intel(0): Default color space is primary color space
[    15.336] (II) intel(0): First detailed timing is preferred mode
[    15.336] (II) intel(0): Preferred mode is native pixel format and refresh rate
[    15.336] (II) intel(0): redX: 0.653 redY: 0.334   greenX: 0.300 greenY: 0.615
[    15.336] (II) intel(0): blueX: 0.146 blueY: 0.057   whiteX: 0.312 whiteY: 0.329
[    15.336] (II) intel(0): Manufacturer's mask: 0
[    15.336] (II) intel(0): Supported standard timings:
[    15.336] (II) intel(0): #0: hsize: 1920  vsize 1200  refresh: 60  vid: 209
[    15.336] (II) intel(0): Supported detailed timing:
[    15.336] (II) intel(0): clock: 154.0 MHz   Image Size:  518 x 324 mm
[    15.336] (II) intel(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    15.336] (II) intel(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
[    15.336] (II) intel(0): Serial No: 2A9281BV0K0
[    15.336] (II) intel(0): Monitor name: LED Cinema
[    15.336] (II) intel(0): Number of EDID sections to follow: 1
[    15.336] (II) intel(0): EDID (in hex):
[    15.336] (II) intel(0): 	00ffffffffffff000610369288a70b02
[    15.336] (II) intel(0): 	1c130104a5342078266ea1a7554c9d25
[    15.336] (II) intel(0): 	0e5054000000d1000101010101010101
[    15.336] (II) intel(0): 	010101010101283c80a070b023403020
[    15.336] (II) intel(0): 	360006442100001a000000ff00324139
[    15.336] (II) intel(0): 	3238314256304b300a20000000fc004c
[    15.336] (II) intel(0): 	45442043696e656d610a202000000000
[    15.336] (II) intel(0): 	00000000000000000000000000000129
[    15.336] (II) intel(0): 	400102000000007e2401a500ffff031a
[    15.336] (II) intel(0): 	1aa80100000000004000000000000000
[    15.336] (II) intel(0): 	00000000000000000000000000000000
[    15.336] (II) intel(0): 	00000000000000000000000000000000
[    15.336] (II) intel(0): 	00000000000000000000000000000000
[    15.336] (II) intel(0): 	00000000000000000000000000000000
[    15.336] (II) intel(0): 	00000000000000000000000000000000
[    15.336] (II) intel(0): 	00000000000000000000000000000057
[    15.336] (II) intel(0): No remaining probed modes for output DP2
[    15.338] (II) intel(0): EDID for output DP3
[    15.338] (II) intel(0): Output VGA1 disconnected
[    15.338] (II) intel(0): Output HDMI1 disconnected
[    15.338] (II) intel(0): Output DP1 disconnected
[    15.338] (II) intel(0): Output HDMI2 disconnected
[    15.338] (II) intel(0): Output HDMI3 disconnected
[    15.338] (II) intel(0): Output DP2 connected
[    15.338] (II) intel(0): Output DP3 disconnected
[    15.338] (WW) intel(0): Unable to find initial modes
[    15.338] (EE) intel(0): Output DP2 enabled but has no modes
[    15.338] (II) intel(0): Kernel page flipping support detected, enabling
[    15.338] (EE) intel(0): No modes.
[    15.338] (II) UnloadModule: "intel"
[    15.338] (II) Unloading intel
[    15.338] (EE) Screen(s) found, but none have a usable configuration.
[    15.338] 
Fatal server error:
[    15.338] no screens found
[    15.338] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    15.338] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    15.338] 
[    15.339]  ddxSigGiveUp: Closing log

Thanks again for your help.

---

