---
title: "Not booting when ACPI enabled (Samsung QX412-S01AU)"
date: 2011-07-29
forum: Hardware
---

### Post by jaon on 2011-07-29
Hi everyone

I've just received a new notebook - Samsung NP-QX412-S01AU.  I'm trying to install Kubuntu 11.04 (or Ubuntu, I don't mind) and while the live CD works fine, I had difficulty getting it to boot after installation.

Eventually I realised it would boot if I turn ACPI off in the grub config, but then I lose all of my power management features.  

Can anyone point me in the right direction for how I might go about resolving this?

Thanks
Jason

p.s. For anyone wondering, other than this issue Ubuntu seems to have detected most of the hardware fairly well.  
p.p.s If anyone wants to see the specs of the laptop to aid in helping point me in the right direction, see here: [http://www.samsung.com/au/consumer/pc-peripherals/notebook-pc/thin-light/NP-QX412-S01AU/index.idx?pagetype=prd_detail&tab=specification](http://www.samsung.com/au/consumer/pc-peripherals/notebook-pc/thin-light/NP-QX412-S01AU/index.idx?pagetype=prd_detail&tab=specification)

---

### Post by jaon on 2011-07-31
*bump*

---

### Post by Larry64 on 2011-08-18
I have my QX412 boot Ubuntu 11.04 fine.

I had to change the windows install to use a single partition before I could get grub to "stick"

Basically I did a restore from the recovery media into a single partition leaving space for ubuntu.  Then did a recovery using the HDD recovery parttion to get back the trial office version.  Then when I installed ubuntu from CD boot it was able to install grub in the boot sector and not disappear after a reboot.

Not directly related to your problem, but I hope it helps.

I have come here to try and find a way to enable/disable the radios.  A large number of the function keys don't work, but very usable for the most part. (I haven't installed native nvidia drivers yet, just using intel I get about 4hrs battery life)

---

### Post by jaon on 2011-08-18
Hi Larry

Thanks for the reply.  I agree the laptop is "very usable for the most part", but the biggest thing for me is that the "noacpi" thing that linux has none of the power management things.

Can you confirm that you have basic power functionality - it shows you how much battery is left, sleep and resume work, etc?

Just so I know whether to keep trying or whether to wait for the next version of Ubuntu to come out...

Thanks!
Jason

---

### Post by Larry64 on 2011-08-21
Yes, it has battery indicator and time remaining charging/discharging etc.  Hibernate and suspend work.  powerbutton and lid both work. I have a /proc/acpi directory

$ ls /proc/acpi
ac_adapter  battery  button  event  wakeup 

I didn't change anything special during the install, but if there are any config files/settings you think might help let me know.

---

### Post by Larry64 on 2011-08-21
What is the trouble with booting?  As said, after my first install of Ubuntu it booted directly to windows7 still.  

There seems to be some very funky boot sequence settings with the bios/recoverer/win7


Also the brightness up/down keys set the brightness to max.  This appears to be caused by the fact "xbacklight get" always returns 100% and SETS it to 100%!  In fact anything that seems to read the currant state of the back-light seems to change it to 100%.  I am making a fudge around script to store a last state value and just use xbacklight set <val> on key presses.

Also rfkill un/block all seems to work, but isn't activated by fn+f9

---

### Post by murray.sum on 2011-09-05
I thought I would share my experiences and fixes. It appears most versions of Ubuntu 64bit do not boot correctly from the live cd without messing around with grub boot options. Instead I settled for Natty 32bit which boots and installs without issue. I can report that most things work straight out of the box but there are a few issues.[B]

Multi-touch Trackpad [/B]

Support for the multi-touch trackpad is not great. Natty appears to only have basic multitouch functionality. like edge scroll, two/three finger tab to right click and middle click  respectively. However right button click, middle click and two finger scrolling is still missing. This is a problem with synaptic and can be partially resolved by following these instructions:  [http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/](http://bigbrovar.aoizora.org/index.php/2011/05/24/better-clickpad-support-for-ubuntu-11-04/)

**Brightness & Backlight**
As others have reported brightness cannot be controlled with the function keys and sometimes it flickers. Assuming people are using the integrated Intel graphics this issue is to do with Intel i915 driver ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611)). This can be resolved by patching the kernel using this ppa: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-i915bri]("https://launchpad.net/%7Ekamalmostafa/+archive/linux-kamal-i915bri")

Full instructions can be found here: [http://www.absolutelytech.com/2011/08/01/solved-unadjustable-brightness-on-laptops-having-i915-kernel-module/](http://www.absolutelytech.com/2011/08/01/solved-unadjustable-brightness-on-laptops-having-i915-kernel-module/)

Also Ubuntu Oneiric (11.10) systems already include all of these patches. They have also been submitted to be included in the official Maverick and Natty kernels .

**[COLOR=Red]IMPORTANT:[/COLOR] **Check that you are using the i915 driver using:
```
lsmod | grep i915
```[B]

Function Keys[/B]
Only some of the function keys work such as volume control and trackpad on/off. I have not investigated getting all of the function keys working but I have looked into getting the wireless on/off key working. It appears that the key press is logged in kern.log:

```
Sep  4 23:29:52 Steve kernel: [ 3935.098742] atkbd serio0: Unknown key pressed (translated set 2, code 0xd5 on isa0060/serio0).
Sep  4 23:29:52 Steve kernel: [ 3935.098752] atkbd serio0: Use 'setkeycodes e055 <keycode>' to make it known.

```As a result, I suspect this should be easy to fix. Once I have figured it out I will post a solution.

I am planning on trying out dual graphics card support with Bumblebee so I will report if I am successful.

---

