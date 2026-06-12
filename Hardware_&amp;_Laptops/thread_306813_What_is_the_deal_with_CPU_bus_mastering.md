---
title: "What is the deal with CPU bus mastering?"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2006-11-25
okey, i have been doing some reading, various web sites, what is the deal with bus mastering?  and why does my notebook not have it?  Its only about 1 year old, seems like something it should have, but does not seem to be available.  Is the notebook just a POS, is the manuf. using some funny windows drivers to enable it? is there a switch i can throw somewhere to enable it? seems odd when this seems to enable by default with older Asus notebooks?

I have an Asus z70va, P-M based machine running edgy.
I had to use the maxcstate patch to get the "generic" kernel to have a reasonable cpu usage; might this have disabled the bus mastering?

anyway... 

cat /proc/acpi/processor/CPU1/*

processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        yes
throttling control:      yes
limit interface:         yes
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0
active state:            C1
max_cstate:              C1
bus master activity:     00000000
states:
   *C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[06763447] duration[00000000000000000000]
    C2:                  type[C2] promotion[--] demotion[C1] latency[001] usage[00023049] duration[00000000000232385370]
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%

---

### Post by zgornel on 2006-11-25
Bus mastering if a feature that all modern chipsets support (everything after 1997-98 ). If I understand right, without the maxcstate patch your cpu usage is very high ... ? There is no hardware way to enable bus mastering or disable it. I suggest recompiling your kernel, it is probably a bug of the kernel with your specific configuration.

---

### Post by hardyn on 2006-11-25
thanks for the help...

my switch i actully meant software switch, but i will try the recompile...

last time a tired to build a kernel, even using all the ubuntu stuff, i managed to kill the wireless, do you know how ubuntu is doing it so there generic kernel makes my wireless work, but the ones a build dont?

i have the oh-so-common intel 2915 wireless card.

---

### Post by ShinjiLeery on 2006-11-25
> **zgornel said:**
> Bus mastering if a feature that all modern chipsets support (everything after 1997-98 ). If I understand right, without the maxcstate patch your cpu usage is very high ... ? There is no hardware way to enable bus mastering or disable it. I suggest recompiling your kernel, it is probably a bug of the kernel with your specific configuration.

i have the same problem with a Asus M6800 (Centrino 1.6GHz).
Can you tell me where i found a good guide to compile a kernel for a laptop? 

Tnx,
Luca.

---

### Post by zgornel on 2006-11-25
hardyn, the i2915 will work if you recompile the kernel as long as you copy the firmware in a new dir with the name given by 'uname -r' in the /lib/firmware dir.
Kernel compilation howtos :
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu), search the forum for other compilation guides, they're good.

---

### Post by hardyn on 2006-11-25
thanks for the link... why do the commands differ so much from the this set of instructions:

[https://wiki.ubuntu.com/KernelCustomBuild](https://wiki.ubuntu.com/KernelCustomBuild)

would it be wise to use a combitnation of the two, the above package import commands but, make changes to the configuraton using your link (make menuconfig)?  or am i best staying with the vanilla kernel?

could you please explain the i2915 thing a little further... does the new directory and copy have to happen before or after the compile? uname -r is the name of my NEW kernel, or the original one?

thanks again... (im learning quite a bit right now, thank you for your help)

---

### Post by zgornel on 2006-11-26
I'll give you a simple walkthrough:
1. You can use the kernel source from ubuntu (in edgy the latest version is 2.6.17.13) or the vanilla 2.6.18 (NOT 2.6.18.x) and a ck patch from [http://members.optusnet.com.au/ckolivas/kernel/](http://members.optusnet.com.au/ckolivas/kernel/) (you find both kernel, patch and patching instructions there).
2. Extract the kernel, install additional packages to make a *menuconfig* or better, a *xconfig*.
3. Copy from /boot the config-<kernel version> file as /path-to-linux-source/.config
4. make xconfig (menuconfig) - select deselect options, (leave the smp otion enabled). Exit and save.
5. as root do: *make-kpkg clean* first (it cleans the results of previous compiles) and then, [I]make-kpkg -initrd --revision=test1 kernel_image
[/I]. This will create a .deb package outside the linux source directory that contains the kernel, and modules.
6. *sudo dpkg -i kernel-image-*.deb* - installs the package. At this point, all modifications needed for the new kernel are done and you can reboot and test the new kernel. You can uninstall it later from synaptic as long as you booted with another kernel because it cannot uninstall a running kernel.

P.S. For hibernation to work check the suspend option in the .config file: *cat ./.config | grep SUSPEND*. You should see CONFIG_SOFTWARE_SUSPEND=y. Sometimes it happens that when you make xconfig after copying the config file from /boot, this option disappears. 
For wireless to work, make a directory with the name 'uname -r' (uname -r gives you the name of the running kernel) in /lib/firmware after you booted the new kernel and copy there all the contents of /lib/firmware/2.6.17-10-generic (the old kernel firmware). This is done because the drivers of the new kernel search for the firmare in /lib/firmware/<directory-with-the-name-of-the-kernel>

THis should be all. Hope it works.

---

### Post by hardyn on 2006-11-26
Thank you, you have a great deal of help, and thanks for the heads up on the suspend thing, my machine is a notebook, that is pretty important.

what does the ubuntu kernel have that the vanilla one does not? vice versa?

will using the vanilla kernel take anything away from an OE edgy system? power management, that new boot script system that such a big deal made, etc?

thanks again.

---

### Post by zgornel on 2006-11-26
Hmm, good question about the vanilla and ubuntu kernels. The ubuntu kernel should have some (or all) of Con Kaliovas performance patches and improved hardware support (more dirvers). This comparison between the kernel should be made between similar versions of the kernel. A 2.6.18-vanilla for example has, obviously,  better hw support than a 2.6.15-ubuntu. Also, I think ndiswrapper is not a feature of the vanilla kernel.

---

### Post by hardyn on 2006-11-26
i thought the ndiswrapper was module, and didnt need to be built into the kernel... of course this might also show my noobie-ness

---

### Post by zgornel on 2006-11-27
It is a module but the kernel consists of the core plus modules (drivers). If you patch the kernel for a certain hardware/software feature you will be able to compile it within the compilation process of the kernel and enable it if required more easily.

---

### Post by hardyn on 2006-11-27
okey i built my new kernel... and it works, although not has happy as i would like to be... 

i used the vanilla kernel, maybe i should have not, i now have some odd video performance.

i seem to have wiped out my marvel yukon eithernet, i guess this is a patch that i should have included?

i will try again using the ubuntu source.

anybody have ideas how to avoid killing the marvel lan?

and still ended up with no bus mastering control... ideas?



thanks.

---

### Post by zgornel on 2006-11-27
Well, you may have bu mastering control and the kernel can't see it for some reason. If your performance with the laptop is normal, then bus mastering is on.

---

