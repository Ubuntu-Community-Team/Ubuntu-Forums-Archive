---
title: "How to prevent opening the laptop lid from waking my system?"
date: 2024-08-12
forum: Hardware
---

### Post by Jackie78 on 2024-08-12
I recently installed Xubuntu LTS release: 24.04, Noble Numbat, using  XFCE on my laptop. I have really struggled a lot to make suspend mode  not do anything to wake up my system except for a short press on the  power button, i.e. no mouse movement, no keyboard presses, nothing  should allow the system to wake up.

 I managed to disable most USB dewvices from waking up the computer, but there still is an anoying thung, and that's the laptop lid of my Lenovo Miix 310, an Intel Atom based little notebook that previously was running Windows 10, and which became unusable in that Microsoft OS with every update, but still runs smoothly as an internet and writing machine, so basically XUbuntu is really working fine here. But still, that laptop lid remains: I want it to do nothing, when closed or opened, so I added the following to my config:


In logind.conf, I added the following lines:

 ```
HandleHibernateKeyLongPress=ignore
HandleLidSwitch=ignore
HandleLidSwitchExternalPower=ignore
HandleLidSwitchDocked=ignore

``` And in UPower.conf:
 ```
IgnoreLid=true

``` 
I now have come to a point where closing the laptop lid does nothing, but when the system is suspended, and I close the laptop lid, and open it again, it wakes the system which is not what I want. Actually, every little movement of the laptop lid makes the computer resume from suspend, which is anoying.

Is there any way to completely get rid of any reaciton to the laptop lid and simply ignore it?

One additional information: In my /proc/acpu/button/lid/LOD0/ directory, there is an entry state, when I open it in nano it gives me a line that says state: open. So my guess is that any change to that states triggers the wakeup, but how can I disable this state from being set or at least from being evaluated?

Any hints are appreciated. Thank you!

---

### Post by TheFu on 2024-08-12
I also don't want the lid to control anything. I'm happy to run a command to enter standby and press the power button to exit standby mode.

Seems you've done what I would have tried first.  I've noticed that laptops sometimes have lid controls in the BIOS. I don't know about Lenovo, but Dell business laptops do.  I'd check the BIOS settings.  Don't know if it will help or not with Lenovo.  There are some Lenovo specific tools, especially around power management. Have you loaded those already?

I had to change a bunch of BIOS settings in a Dell to get Linux to boot and some Ubuntu Flavors (22.04 XFCE!) wouldn't boot at all even with those changes.  Oddly, 20.04 versions did boot and ran reasonably fine off the USB AFTER I changed some BIOS settings to even allow that.  Also had to disable Intel RAID.  By default, booting from external storage is disabled on new Dell business laptops and the function key row is swapped in the BIOS so the Fn modifier key wasn't needed/didn't work to enter the BIOS or boot menus.  This laptop was a recent acquisition, so it doesn't have any OS installed yet.  As a laptop, I'll probably skip Ubuntu completely and go with a non-snap distro.  I want whole drive encryption using 2FA, LVM, X/Windows, and my lite WM (no DE) for a laptop.

---

### Post by &amp;KyT$0P# on 2024-08-12
Have you tried [FONT=monospace]acpitool[/FONT] ?

Install with
```
sudo apt install acpitool
```

List wakeup devices, see which one is the lid
```
acpitool -w
```

Then toggle it with the number on the left:
```
sudo acpitool -W [COLOR="#FF0000"]number[/COLOR]
```

Refer to [FONT=monospace]man acpitool[/FONT] for more info

---

### Post by Jackie78 on 2024-08-12
acpitool -w gives me an empty list with heeader Device, S-State. STatus, Sysfs, node, but no further entries.

Unfortunately,  the UEFI BIOS of this Atom based notebook is very limited, anly very  few options are available, none of them concerning power management or  lid settings or similar. Do you have any additional ideas? Thank you!

---

### Post by him610 on 2024-08-12
> Atom based notebook
What is the make and model of your Atom based notebook?

---

### Post by TheFu on 2024-08-12
> **him610 said:**
> What is the make and model of your Atom based notebook?

Lenovo Miix 310 is in the first post.

I have to confirm that on my new-to-me Dell laptop running Mint 22 Cinnamon, the power settings have specific choices for what to do with the lid open/closed on battery and plugged in. I didn't test them all, but I disabled the lid and that worked.  I also setup suspend and that worked as expected, including wifi coming out of the suspect.

I'm thinking the power settings and controls for Lenovo are the best bet.  Google for those.

---

