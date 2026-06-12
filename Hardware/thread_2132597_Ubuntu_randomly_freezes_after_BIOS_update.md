---
title: "Ubuntu randomly freezes after BIOS update"
date: 2013-04-05
forum: Hardware
---

### Post by MaZaMo on 2013-04-05
I use a Lenovo ideapad Z570. A few weeks back my bios was broken and I couldn't get into setup or boot options, so I temporarily installed a version of windows to update the bios (this is the new bios I downloaded: [http://support.lenovo.com/en_US/downloads/default.page?](http://support.lenovo.com/en_US/downloads/default.page?)). Then I uninstalled windows and went back to Ubuntu. The bios works fine now, but ever since the update my computer randomly freezes like every 10 minutes (even when I have no windows open), and all I can do is move the pointer. I also get a bunch of "system program problem detected" errors now. Reinstalling the OS doesn't help.

Any ideas?

Thanks a lot,
Mazamo

---

### Post by matt_symes on 2013-04-05
Hi

Can you rollback the BIOS to the version you were using before ?

Did you install the same version of *buntu and release you were using before ?

Same kernel version ?

Does booting into an older kernel version help ?

Have you looked in the logs to see why it may be freezing ?

Can you post the output of

```
uname -r
```

```
grep -i gpu /var/log/{syslog,dmesg,Xorg.0.log}
```

Capital X above.

Kind regards

---

### Post by MaZaMo on 2013-04-05
A while back I updated the kernel to a newer version (can't remember what since it was a while ago), but I have reinstalled Ubuntu a few times since then... so It would revert back to how it was before, right?
How do I look into the logs to see why it's freezing?

The output of **uname -r** is    **3.5.0-26-generic**
The output of **grep -i gpu /var/log/{syslog,dmesg,Xorg.0.log}** is    **/var/log/Xorg.0.log:[   366.936] (==) Automatically adding GPU devices**

I'll try booting into an older kernel and see how it works! :)

---

### Post by matt_symes on 2013-04-05
Hi

> **MaZaMo said:**
> A while back I updated the kernel to a newer version (can't remember what since it was a while ago), but I have reinstalled Ubuntu a few times since then... so It would revert back to how it was before, right?

When you reinstalled, it will use the kernel that was part of the iso you used to install. 

When it updates, if there is a new kernel, it will install that for you and update grub so the new kernel becomes the default kernel selected at boot (unless you tell grub not to do this).

> 
How do I look into the logs to see why it's freezing?

The output of **uname -r** is    **3.5.0-26-generic**
The output of **grep -i gpu /var/log/{syslog,dmesg,Xorg.0.log}** is    **/var/log/Xorg.0.log:[   366.936] (==) Automatically adding GPU devices**

You can visually check the log looking for error. In this case i was looking to see if you were getting the gpu_hung error that has been affecting a number of people.

In this case, it looks like it not affecting you

> I'll try booting into an older kernel and see how it works! :)

That's where i would start. If you still get the same issue then we should check your logs to try to identify why.

Kind regards

---

### Post by MaZaMo on 2013-04-05
I went back to kernel 3.5.0-17-generic and it isn't freezing! Good so far. :) But the kernel can't be the only problem, because windows users have the same issue; and if I were to reinstall the Operating System, Ubuntu would have that newer kernel again and the same thing would happen. When I first got this computer everything was fine with the default kernel.

---

### Post by matt_symes on 2013-04-05
Hi

> **MaZaMo said:**
> I went back to kernel 3.5.0-17-generic and it isn't freezing! Good so far. :) But the kernel can't be the only problem, because windows users have the same issue; and if I were to reinstall the Operating System, Ubuntu would have that newer kernel again and the same thing would happen. When I first got this computer everything was fine with the default kernel.

Keep playing and, if it does not freeze, then i can show you how to keep that kernel and ensure you will boot into the failing kernel again.

There are certain security risks with doing this but you will have a working system.

Later you can install a new kernel and see if you get a freeze with that.

Sometimes you have to skip certain kernels as regressions and bugs happen.

Post back tomorrow if there are no freezes.

Kind regards

---

### Post by MaZaMo on 2013-04-06
I'm busy today but I'll take more of a look at it tomorrow. Thanks for your help!

---

### Post by MaZaMo on 2013-04-07
Yes, this older kernel seems to be working fine. How would I now make this default?

What are the disadvantages of an older kernel?

---

### Post by matt_symes on 2013-04-07
Hi

I'll answer these in reverse order

> What are the disadvantages of an older kernel?

You will not get security updates for the kernel, bug fixes, etc.

> **MaZaMo said:**
> Yes, this older kernel seems to be working fine. How would I now make this default?

I've thinking about the best way to do this for you. You can pin a kernel but i'm not sure if this is the best option.

What you can do is get grub to remember your last kernel selection and it will boot into that. 

Then when you get a new kernel update you can test that and if it does not work then select the old kernel on next boot and grub will remember that and boot into the old kernel.

If the new kernel works, when you select that it will keep booting into the new kernel.

Please read this

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

> 
Saved

Saving an OS can be achieved by running sudo grub-set-default if *GRUB_DEFAULT=saved* is set in /etc/default/grub. It may also be saved if *GRUB_SAVEDEFAULT=true*  is also set in /etc/default/grub. In this case, the default OS remains  until a new OS is manually selected from the GRUB 2 menu or the grub-set-default command is executed.

If you need help with understanding this then please wait until tomorrow as the beers kicking in :)

Kind regards

---

### Post by MaZaMo on 2013-04-10
Actually this 3.5.0-17-generic kernel is freezing too, though not as bad. The computer *usually* recovers after 4 or 5 seconds.

---

### Post by matt_symes on 2013-04-10
Hi

> **MaZaMo said:**
> Actually this 3.5.0-17-generic kernel is freezing too, though not as bad. The computer *usually* recovers after 4 or 5 seconds.

First things first, open a terminal and type

```
sudo apt-get install pastebinit
```

That does not sound like a kernel issue, although it could possibly be.

Next time it freezes - while it is still frozen - press the caps lock key. Does the Caps lock led toggle ?

Maybe the logs have some clues.

After it returns from being frozen (do this as soon as possible after the freeze) , open a terminal and

```
tail -n 150 /var/log/syslog | pastebinit
```

```
tail -n 150 /var/log/Xorg.0.log | pastebinit
```

Post back both URLs display on the command line back into your next post.

During the freezes, what is your CPU usage ? Disk IO usage ?

You can check with top and iotop. You may have to install iotop.

```
sudo apt-get install iotop
```

Keep them running in a terminal while using the PC.

Kind regards

---

### Post by MaZaMo on 2013-04-30
Thank you for your help. I ended up solving this by upgrading to Ubuntu 13.04.

---

