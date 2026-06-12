---
title: "No brightness control"
date: 2010-05-28
forum: Hardware
---

### Post by Tenyuu on 2010-05-28
I can not adjust brightness of my screen with shortcut keys but brightness applet works, however i would like for my shrotcut keys to work (FN+F6 & FN+F7) I am running ubuntu 10.04 under keyboard shortcuts there is nothing for brightness.

Toshiba Satellite L505-S6946

I am a noob to ubuntu/linux

thanks for your time

---

### Post by Tenyuu on 2010-05-29
Can no one help me? :confused:

---

### Post by rell666 on 2010-05-30
run [I]sudo setpci -s 00:02.0 F4.B=40 in terminal you have to play with the B value till u get what you want :)
have a look at setpci on the net m8 probably will give it you some where.
[/I]

---

### Post by Tenyuu on 2010-05-30
thanks, i will look setpci on the net :)

---

### Post by Tenyuu on 2010-06-02
does not really help me... ](*,) :-(

---

### Post by shlape on 2010-06-06
You have the same chipset as my laptop.

> Intel® Graphics Media Accelerator 4500MHD

There is a fix for this issue which is progressing toward a future Ubuntu kernel release. For now, download [_these *three* .deb files_]("http://kernel.ubuntu.com/~kamal/i915_brightness/latest-lucid/"), follow the instructions in post #20, reboot and [_post your feedback here_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611/") for the sake of developing this fix. The more laptop models tested for this fix, the better. :)

---

### Post by bbmadzky on 2010-06-07
[B]I am also having this "shortcut" brightness control. But instead of having a fix, a brightness control can be found in the power management preferences.
[/B]

---

### Post by mgiblets on 2010-06-07
In my case both the short cut and the power management tool won't change the brightness. 

The *sudo setpci.... *command works, but this is no saved as a preference, so I have to re type in the command every time I reboot my computer. Any help on a *permanent *fix?

---

### Post by alexjohnc3 on 2010-07-21
> **mgiblets said:**
> In my case both the short cut and the power management tool won't change the brightness. 

The *sudo setpci.... *command works, but this is no saved as a preference, so I have to re type in the command every time I reboot my computer. Any help on a *permanent *fix?
The best thing I can suggest is going to System -> Preferences -> Keyboard Shortcuts and mapping that command to a shortcut so you can easily change your computers brightness. It's a bad fix, but hopefully someone else can help. :)

---

### Post by Tenyuu on 2010-08-09
I get this when trying to install the top and bottem .deb files:

"Error: Wrong architecture 'amd64'"

however the middle one 
(linux-headers-2.6.32-23_2.6.32-23.38~kamal~i915bri~3e_all.deb)

installed fine.

when I rebooted, I still have no brightness control except through the brightness applet....

---

### Post by highflyr on 2010-10-28
> The best thing I can suggest is going to System -> Preferences -> Keyboard Shortcuts and mapping that command to a shortcut so you can easily change your computers brightness. It's a bad fix, but hopefully someone else can help. 


What would the command be +/- for mapping the power management/dimmer function in 'keyboard shortcuts'?

---

### Post by solnyshok on 2010-10-28
go to the menu "system>preferences>keyboard shortcuts", add new

---

