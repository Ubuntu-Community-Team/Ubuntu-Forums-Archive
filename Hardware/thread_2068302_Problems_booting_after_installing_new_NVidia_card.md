---
title: "Problems booting after installing new NVidia card"
date: 2012-10-08
forum: Hardware
---

### Post by viperdvman on 2012-10-08
I had previously ditched my old AGP and PCI Nvidia 6-series cads *(I needed them for dual displays in Windows, but the dual displays never worked right in Ubuntu)* since my replacement motherboard had no AGP slots. So I had to go with the onboard Intel GMA X4500HD, which worked like a charm under Ubuntu 12.04.

Do note, both the nouveau and proprietary drivers worked like a charm in single-display mode in both Ubuntu 11.04 and 11.10 (and their derivatives)... basically using the newest drivers avaible in the repos.

Now, I've installed a much more powerful dual-head **MSI NVidia GTX 560**, and am running Ubuntu 12.04. Now, I am unable to boot Ubuntu. I get a messed up screen, and nothing happens after that. The kernel should have the nouveau drivers built in, and it should be booting with the nouveau drivers.

On top of that, I have a non-persistent Ubuntu 12.10 beta and Kubuntu 12.10 beta LiveUSB's, and neither of those will boot up either. Again, the built-in nouveau drivers should be working even for the LiveUSB's.

Any suggestions other than nomodeset?

I'm trying a few other things, more updates to come.

Updates: Running Ubuntu 12.04 in LiveUSB doesn't boot either. It won't go past the Unetbootin screen. I also have Ubuntu 11.10 on a DVD, and running it in LiveDVD mode doesn't boot up either. It freezes in the middle.

---

### Post by viperdvman on 2012-10-08
I'm starting to think that my newer NVidia GTX 560 is incompatible with the built-in "nouveau" drivers... on the Linux 3.2.0-x kernel.

However... quick update:

I did the **nomodeset** boot option in GRUB and got Ubuntu to boot up no problem, however, I'm left stuck with the single display at a 1280x1024 resolution, which sucks. However, **[COLOR=Blue]after installing the proprietary nvidia drivers[/COLOR]** *(I used Additional Drivers method, and the nvidia-current instead of the post-release)*, I was able to boot into Ubuntu with absolutely no problems :)

The upside is... it works. The downside... it makes it very difficult for me to try out other distros in a LiveUSB environment without having to do a nomodeset on every single bootup. It could, however, give me an opportunity to use my virtualbox :D

I wouldn't call this solved yet. My question is:

Does anyone else run an NVidia GeForce GTX 560? *(not the SE, Ti, nor M models)* Has anyone else run into this problem when trying to boot Ubuntu without "nomodeset"? If so, and if you have, how'd you fix it?

---

### Post by typhoon_tip on 2012-10-08
Before do anything else, try:
```
sudo cat /etc/X11/xorg.conf
```

If it says file not found, or it looks very short, then run:
```
sudo nvidia-xconfig
```

... then reboot.

The above will create a proper XOrg file for you. Don't know why, but nvidia installer is not creating one properly when installing the debians.

---

### Post by BicyclerBoy on 2012-10-08
The OP is not using the nVidia driver..

Neither nouveau or nVidia drivers need the xorg.conf file.
Can be better to delete it.

I note there is a nouveau/kernel bug with this model video card.

The OP might have to use the proprietary driver; install via jockey..

---

### Post by viperdvman on 2012-10-09
I had already installed the proprietary drivers after adding "nomodeset" in GRUB. It was the only way I could get it to boot. And xorg.conf did generate, but it was a pretty bare one. I did do the nvidia-settings to get it all set up, and to get my dual monitors to work. So on that front, all is well.

Yeah, I read a few bug reports here and there regarding this particular unit... but, the bug reports looked like very few were having this problem, and they all were a little over a year old, but nothing more than that. Still, it sucks that there is a problem with the nouveau drivers working with these newer NVidia cards. But like I said, until the nouveau problem is fixed, I can probably use VirtualBox on my desktop, or just use my netbook for testing out other distros. But having to nomodeset if I intend to install it is gonna be a major PITA.

So the getting Ubuntu to boot on an NVidia GeForce GTX 560 has been solved... with the nomodeset and install proprietary drivers workaround. But it hasn't solved the linux not wanting to boot with the nouveau driver problem.

I could've gone ATI/AMD... but then again I haven't had much luck with the Catalyst drivers running Flash. Plus, it's tougher to install the AMD drivers than it is to install the NVidia ones... at least in Ubuntu.

---

### Post by BicyclerBoy on 2012-10-09
Did you use nomodeset to get any GUI desktop up?
You have removed nomodeset now eh ? I assume yes..

None of the latest drivers will load if nomodeset is used. You get the fall-back VESA.

The nouveau (open source nvidia GPU h/w project) driver has kernel module bug in kernel 3.4 & later.
Kernel 3.4 has not hit *buntu 12.04 yet..

If you want to try the latest kernel 3.5 & xorg etc.. try xorg-edgers ppa.

I would say your video card GPU is not recognised via its PCI ids..

---

### Post by viperdvman on 2012-10-09
> **BicyclerBoy said:**
> Did you use nomodeset to get any GUI desktop up?
You have removed nomodeset now eh ? I assume yes..

None of the latest drivers will load if nomodeset is used. You get the fall-back VESA.

Nomodeset is only temporary unless I edit the GRUB entry directly. In Unetbootin, I can set a nomodeset pretty easily.

And Ubuntu 12.04 runs the 3.2.x kernel and it has that problem. I have yet to try it with later kernels, though I'm sure the 12.10 betas are using the 3.5 kernel, which still has the nouveau bug as I couldn't get Ubuntu nor Kubuntu 12.10 to boot up either.

> **BicyclerBoy said:**
> I would say your video card GPU is not recognised via its PCI ids..

Recognised via its PCI id's? I'm not sure how that's possible.

---

### Post by BicyclerBoy on 2012-10-10
PlugNPlay..
If the PCI id is not recognised then how can the right driver be loaded.
Some assumptions might be made thou, the id reveals the manufacturer.

Old kernels have trouble with new h/w that requires a kernel space driver module.

You can get a very recent ubuntized kernel & xorg & nvidia from xorg-edgers ppa.
This could have the nouveau patch.

---

