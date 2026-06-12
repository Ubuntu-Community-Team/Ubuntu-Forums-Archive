---
title: "Xorg Crashes after installing Catalyst"
date: 2014-11-07
forum: Hardware
---

### Post by Vilsol on 2014-11-07
I am trying to install the AMD Catalyst, but after reboot I hit a black screen. I checked the ```
/var/log/Xorg.0.log
``` and everything is fine up to the point where it has a segmentation fault.


```
    [    16.320] (EE) Backtrace:
    [    16.320] (EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x7f760efa8d28]
    [    16.320] (EE) 1: /usr/bin/X (0x7f760ee00000+0x1aca19) [0x7f760efaca19]
    [    16.320] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f760defd000+0x10340) [0x7f760df0d340]
    [    16.320] (EE) 3: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f760946c000+0x15660) [0x7f7609481660]
    [    16.320] (EE) 4: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f760946c000+0x10dfe9) [0x7f7609579fe9]
    [    16.320] (EE) 5: /usr/lib/xorg/modules/drivers/intel_drv.so (0x7f760946c000+0x10e545) [0x7f760957a545]
    [    16.321] (EE) 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs115_atiddxPxScreenInit+0x72) [0x7f7609f30ec2]
    [    16.321] (EE) 7: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/extra-modules.dpkg-tmp/modules/drivers/fglrx_drv.so (xdl_xs115_atiddxScreenInit+0x11fa) [0x7f7609f0d7fa]
    [    16.321] (EE) 8: /usr/bin/X (AddScreen+0x71) [0x7f760ee55ca1]
    [    16.321] (EE) 9: /usr/bin/X (InitOutput+0x3c8) [0x7f760ee96ce8]
    [    16.321] (EE) 10: /usr/bin/X (0x7f760ee00000+0x596bb) [0x7f760ee596bb]
    [    16.321] (EE) 11: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f760c93cec5]
    [    16.321] (EE) 12: /usr/bin/X (0x7f760ee00000+0x44dde) [0x7f760ee44dde]
    [    16.321] (EE) 
    [    16.321] (EE) Segmentation fault at address 0x18

```

Here is the full log: [http://paste.ubuntu.com/8868827/](http://paste.ubuntu.com/8868827/)


I have been fighting with fglrx and PowerXpress all day, and this is how far I have got.

---

### Post by QIII on 2014-11-07
Hello!

It would be quite helpful if you would tell us your hardware specs.

What is the Intel adapter model?  What is the ATI model?  Is this a laptop or a desktop?  If a laptop, are the graphics muxed or muxless?

---

### Post by Vilsol on 2014-11-07
Hey, thanks for a reply!

It is a laptop 

Here is the output of lshw: [http://paste.ubuntu.com/8869436/](http://paste.ubuntu.com/8869436/)
Here is the output of inxi -Fx: [http://paste.ubuntu.com/8869518/](http://paste.ubuntu.com/8869518/)

Not sure what muxed or muxless means, sorry.

---

### Post by QIII on 2014-11-07
A mux is a multiplexer.  That is, it takes two possible inputs and produces a single output. In this case we are talking about the graphics output.  Some systems use the Intel CPU/on-die GPU as the mux for both the ATI and Intel graphics.  Pxpress does not work in a multiplexed system.

Unfortunately, that does not tell us if this is a muxed or muxless system.  Could you please research that?

How are you attempting to install the ATI driver?

---

### Post by Vilsol on 2014-11-07
I used their installator, which compiled distro specific packages, which it then installed. I then went into recovery and ran aticonfig --initial and rebooted, that is when this showed up.

Is there any easy way I can check whether it is muxed or muxless? I have another partition with windows. In the windows catalyst center I can switch between high performance and power saving for certain applications, does that tell you anything?

---

### Post by QIII on 2014-11-07
The only way to tell is to research the technical documents.

That it works in Windows tells me no more than I already know:  the OEMs concerned know that if they do not make sure their drivers work with Windows they will go out of business.  At 2% market share, Linux does not command that level of effort from the OEMs.  From a business standpoint it would be foolish for them to expend the same amount of resources to produce drivers that work for such a small share of the market.

Microsoft doesn't care if ATI dies.  They won't lift a finger.  If ATI's driver does not meet their criteria for the coveted "Windows Compatible" designation, they say "Too bad for you."  That's also a good business decision.  Why should Microsoft expend its resources doing something the OEMs should do?

It is possible that someone in the Linux community has already done and published the research on your model, so you might see if you can find that.  Unfortunately, there is no definitive list for each and every one of tens of thousands of possible hardware configurations by OEM and model by distro that one may consult.

This is a simple and inescapable condition.

Your other option is vgaswitcheroo, but that only works with the open source Radeon driver, which does not expose the full range of your ATI adapter's capabilities, but which has gotten very much better over the last few years and is suitable for the vast majority of users.

---

### Post by Vilsol on 2014-11-07
My laptop is Novatech Elite N1716

In the technical manual it only says "Intel Integrated GPU and AMD Discrete GPU. (GPU is dependent on the Processor)" and that is it other than specifying its a 7970M

My warranty has run out, so is it possible to just open it up and tell it from there?

Is there a way where I can avoid using PowerXpress but still install the proprietary drivers?

---

### Post by QIII on 2014-11-07
That indicates that it is muxed through the CPU.  I know of no way around this -- it has been a source of a great deal of frustration in the Linux community for some time now.

While I hold out very little hope, you might try looking at [this]("http://ubuntuforums.org/showthread.php?t=1930450") thread. ***I would not actually recommend any approach in this thread***, but I'll present it to you as a resource.  Notice that it starts out saying up front that it only works with muxless systems.  The thread is very long, you would have to be very careful because a lot has changed and there is *absolutely no guarantee* that anything there will work.  You might end up with a system so entirely borked that you would have to reinstall.  I would be very surprised if anything there actually works since this was posted before Precise was finally released -- and a lot has changed with X Server since.  This would not have even been the same graphics stack.

I have only ever gotten an ATI/Intel hybrid to work on one machine, and that one was muxless.

I wish I had better news.  The OEMs have left us hanging on this one.

---

### Post by Vilsol on 2014-11-07
Well that just means I am saying goodbye to AMD on this one. Never will I ever buy any of their products again.

What is the easiest way I can get back now? Im guessing apt-get purge fglrx, but that probably won't be enough.

---

### Post by QIII on 2014-11-07
NVIDIA/Intel hybrids are the same.  Muxless only.  The laptop OEMs are as much to blame as the graphics OEMs.  

I wish there were something to be done about it.

---

### Post by Vilsol on 2014-11-07
What is the easiest way I can get back now? Im guessing apt-get purge fglrx, but that probably won't be enough.

---

### Post by QIII on 2014-11-07
Look at my post #4 [here]("http://ubuntuforums.org/showthread.php?t=2251520").

That should get you back to a clean, default installation.

Don't worry about the vgaswitcheroo part.

---

### Post by Vilsol on 2014-11-07
Oh well, thanks for helping. Back to open source, I guess.

---

### Post by pqwoerituytrueiwoq on 2014-11-07
have you tried the xorg edgers ppa for the latest open source drivers? also try a newer kernel
this will add the xorg edgers ppa and install the latest drivers
```
sudo apt-add-repository ppa:xorg-edgers/ppa -y && sudo apt-get update && sudo apt-get dist-upgrade -y
```
in the event it goes south here is the revert command
```
sudo apt-get install ppa-purge -y && sudo ppa-purge ppa:xorg-edgers/ppa
```

here is a simple way to install the latest kernel
[https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater](https://github.com/GM-Script-Writer-62850/Ubuntu-Mainline-Kernel-Updater)
i suggest either the 3.16.7 or the 3.17.2 kernel (step 4 of instructions)
```
# for the 3.16 kernel
KernelUpdateChecker -r utopic -v 3.16
# for the 3.17 kernel
KernelUpdateChecker -r vivid -v 3.17
```
save the script it makes, if you want to remove the kernel that script can do it with the [FONT=courier new]--uninstall[/FONT] parameter (it will auto delete on reboot)

With budget AMD GPUs (eg: apu graphics) i have found the performance lacking to the point of a integrated intel gpu being significantly superior under linux

---

