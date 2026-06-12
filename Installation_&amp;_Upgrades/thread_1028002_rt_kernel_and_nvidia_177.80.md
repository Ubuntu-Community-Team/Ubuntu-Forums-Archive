---
title: "rt kernel and nvidia 177.80"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by kvk on 2009-01-01
When attempting to install the rt kernel from the current Ibex repository, I encounter the following and can't get past it:

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-3-rt                                                                                                                                                            
 *  nvidia (177.80)...                                                                                                                                                                                                      nvidia (177.80): Installing module.
  Kernel source for 2.6.27-3-rt not installed.  Cannot install this module.
                                                                                                                                                                                                                     [fail]

run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-image-rt (2.6.27.3.4) ...

After running the installation, the machine requires a restart but is still running the generic kernel, according to the system information.

Any ideas on this one?

Thank you!

---

### Post by kvk on 2009-01-06
I also tried installing the rt kernel with the Nvidia 173 driver with the same result.

Is this because these drivers are proprietary? And if so, is there any workaround?

---

### Post by Steve H on 2009-01-29
I'm having the same problem. I can't install the 177 drivers either.

I have to run to get a usable desktop
```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

I'm also running the generic kernel which uses the 177 driver perfectly.

Someone mentioned about having to uninstall the drivers in both and then reinstalling them again to get it working, but that seems a bit extreme to me!!

---

### Post by markbuntu on 2009-01-29
The rt kernel is broken, don't use it.

---

### Post by Steve H on 2009-02-11
That's not really very helpful though, I need the rt-kernel for audio recording (with minimal latency).

TBF I don't really need glx running to use the desktop, but it would be nice.

---

### Post by kvk on 2009-02-15
I managed to solve the issue by removing the Nvidia driver, installing the RT kernerl, and then reloading the newer Nvidia driver. I've no problems with either of them, and the RT kernel works fine with JACK and 16 or 32 frames per period, no Xruns at all.

---

### Post by Steve H on 2009-02-22
I'll definitely give that a go then.

Thanks

;)

---

### Post by Steve H on 2009-03-06
Still no joy :(

I've deactivated the nvidia drivers, reinstalled ubuntu-studio, then reboot. boot into either kernel activate nvidia (both are working at this stage!) then once either loads the nvidia driver then when i reboot into the rt-kernel the nvidia module complains about not loading. The X Server fails saying "no screens found". I've tried this about four times now.

This is annoying as I need the nvidia driver in the vanilla kernel to watch stuff from my pc to my TV, but I need the rt-kernel for audio recording with low latency. Seems I can't have both....shame!?!

I'll keep looking...

:(

---

### Post by raygj on 2009-03-07
> **kvk said:**
> I managed to solve the issue by removing the Nvidia driver, installing the RT kernerl, and then reloading the newer Nvidia driver. I've no problems with either of them, and the RT kernel works fine with JACK and 16 or 32 frames per period, no Xruns at all.
notice that Steve H said "to solve the issue by removing the Nvidia driver(uninstalled it),installing the RT kernerl, and then reloading(installed/reinstalled ????) the newer Nvidia driver."(
whereas you just "deactiveated nvidia/installed rt/reactivated nvidia".maybe thats why it worked for Steve H and it did not work for you?
PS. Just a Thought:-  you DID  boot up into the 'running RT kernel' and then "installed" the "nvidia" whilst you were running/using the "RT kernel"?????

---

### Post by Steve H on 2009-03-07
I've got mine all sorted now. Uninstalled the Nvidia driver, reinstalled rt-kernel and ubuntu studio. Booted back in to vanilla kernal, reinstalled the nvidia drivers. Rebooted into rt-kernel recovery mode, choose fix x server, and now it all works in both kernels. FINALLY!!

:D

---

