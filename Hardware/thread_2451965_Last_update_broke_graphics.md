---
title: "Last update broke graphics"
date: 2020-10-13
forum: Hardware
---

### Post by metacell on 2020-10-13
After today's Ubuntu update, my computer couldn't boot. It fails with the message
> [    61.591428] uvcvideo: Failed to query (GET_INFO) UVC control 2 on unit 1: -32 (exp. 1).

When I selected an older kernel (5.4.0-42), the computer booted, but Vulkan had stopped working:
[IMG]https://imgur.com/qTmTbzN.png[/IMG]

Using a Pegasus GeForce GTX 1650 SUPER, an Intel Core 2 Quad Q8300 @2500MHz, and Xubuntu 20.04.

---

### Post by Autodave on 2020-10-14
What driver do you have installed for the GPU and where did you get it from?

---

### Post by metacell on 2020-10-14
> **Autodave said:**
> What driver do you have installed for the GPU and where did you get it from?

The standard proprietary nVidia driver, through the official Ubuntu repositories.

After the update it was set to version 450 (in software-properties). I tried changing it to version 440-server, 435-server, and noveau, but the results were the same. With kernel 5.4.0-48, Ubuntu failed to boot, and with kernel 5.4.0-42, Ubuntu booted normally, but Vulkan was disabled.
[EDIT: I mean I tried changing to 450-server, 440-server, and Nouveau]

I also unplugged my USB webcam (since it seems to use the uvcvideo driver). That made the error message at boot disappear; instead, boot stalls at an empty screen, with only a blinking cursor.

---

### Post by CatKiller on 2020-10-14
> **metacell said:**
> instead, boot stalls at an empty screen, with only a blinking cursor.

Yep, that is a symptom of not having the Nvidia driver properly installed. The nouveau driver struggles to set the resolution correctly: you can use the **nomodeset** kernel parameter as a temporary workaround to allow you to boot.

The Nvidia driver needs a shim to go between the GPL'd kernel and the proprietary driver module. That's either kernel-version-specific (meaning it breaks every time the kernel updates) or it uses DKMS (meaning it needs to be compiled every time the kernel or driver get updated). Recently my other half's computer ended up without a compiler, so DKMS couldn't make the shim, so the Nvidia driver failed. I don't know whether that is widespread or was specific to the history of that machine, but make sure that you have **build-essential** installed.

The other thing is that the Nvidia driver sometimes doesn't upgrade cleanly between driver branches. The existence of stuff from the old branch stops the new branch from installing, so you end up with neither working. The package maintainers seem to be pushing everyone from the 440 branch to the 450 branch. The easiest way to deal with it is to purge *all* the Nvidia stuff (note that apt-get supports globbing like "nvidia*" but apt doesn't) and then install just the driver branch that you want.

---

### Post by mastablasta on 2020-10-15
yes, sometimes update just doesn't work. i had similar issue. in my case driver was set to 4.40 and just didn't work.  but it was resolved when i moved it to 4.50 - which essentially meant that 4.50 was installed. in other words if switching doesn't help, remove and reinstall via CLI or just remove/uninstall, boot with nouveau and then install using the additional drivers application. that should fix it.

i experienced this on my kids GTX 1650. on my GT 730 i decided to stay on LTS kernel, so i have same kernel & driver, just security updates and i never saw this issue. then again i think that card/chip is now already legacy anyway.

---

### Post by webaake on 2020-10-15
I had problems with kernel 5.4.0.48 too. No sound from Nvidia HDMI with Nvidia's driver, so I  activated 5.4.0.47. 

If you're bothered by troublesome automatic kernel updates you can change the defaults in grub to always boot from the last good kernel (that you chose). Default on Ubuntu install is to boot the last installed kernel (newest), which can lead to problems. I mean, if you're in for a nice evening of Netflix and you have to hack on your kernel and drivers instead, it's a bummer!

Here's how to do it: [https://askubuntu.com/questions/148662/how-to-get-grub2-to-remember-last-choice#:~:text=Saving%20an%20OS%20can%20be,%2Fetc%2Fdefault%2Fgrub](https://askubuntu.com/questions/148662/how-to-get-grub2-to-remember-last-choice#:~:text=Saving%20an%20OS%20can%20be,%2Fetc%2Fdefault%2Fgrub).

(Yes, I know, you CAN miss out on kernel security updates. But you can, with these Grub settings, decide yourself when to try out new kernels and drivers for that kernel. In your own time)

---

### Post by metacell on 2020-10-15
Thanks for the suggestions.

My system doesn't boot with Nouveau either (on kernel 5.4.0.-48).

I changed the video driver to Nouveau using software-properties. Then I did
> sudo apt-get remove *nvidia*
... but there were no nvidia packages installed.

Rebooting yielded the same empty screen with a blinking cursor as before.

I can still boot with kernel 5.4.0.-42 just fine, whether I have the Nouveau or the proprietary nVidia driver enabled.

---

### Post by CelticWarrior on 2020-10-15
```
sudo apt-get remove **nvidia***
```

There are no packages starting with '*nvidia'...

---

### Post by metacell on 2020-10-15
> **CelticWarrior said:**
> ```
sudo apt-get remove **nvidia***
```

I tried it, and got the same result. All nvidia packages were already gone because I switched to Nouveau.

---

### Post by metacell on 2020-10-15
And now I noticed another error. VirtualBox' kernel driver also stopped working:

[IMG]https://imgur.com/DWcNeVB.png[/IMG]

I have both [FONT=courier new]build-essential[/FONT] and [FONT=courier new]virtualbox-dkms[/FONT] installed -- I just checked.

When I do [FONT=courier new]modprobe vboxdrv[/FONT], I get the error:
```
modprobe: FATAL: Module vboxdrv not found in directory /lib/modules/5.4.0-42-generic
```

Maybe the problems are caused by a failure to load kernel modules (not with the graphics driver as such)?

---

### Post by CelticWarrior on 2020-10-15
Disable Secure Boot in UEFI. That's actually the root of all your current problems.

---

### Post by mastablasta on 2020-10-16
you don't boot to old kernel and then remove. you need to boot using the kernel that is giving you the issue, then remove the driver. boot into text mode only and then remove the driver and kernel modules.

how to start ubuntu in console mode: [https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode](https://askubuntu.com/questions/859630/how-to-start-ubuntu-in-console-mode)

---

### Post by metacell on 2020-10-16
> **CelticWarrior said:**
> Disable Secure Boot in UEFI. That's actually the root of all your current problems.

I don't have a UEFI BIOS. I have an old ASUS P5E motherboard from ca 2008. But I see how that could be the cause for other users.

> **mastablasta said:**
> you don't boot to old kernel and then remove. you need to boot using the kernel that is giving you the issue, then remove the driver. boot into text mode only and then remove the driver and kernel modules.

Thank you, I'll try that. I naively assumed apt added or removed the drivers from all kernels at the same time.

Should I use [FONT=courier new]apt-get purge nvidia*[/FONT] to make sure all configuration is removed?

---

### Post by metacell on 2020-10-16
Ok, I used the GRUB boot menu to boot into recovery mode for the newest kernel (5.4.0-48-generic), enabled networking, and went to the root prompt.

Then I tried to uninstall all nvidia packages:
```
apt-get remove nvidia*
```

... which removed zero packages.

Then I tried
```
apt-get purge nvidia*
```

... which did remove a bunch a nvidia packages.

To be safe I also uninstalled Virtualbox:
```
apt-get remove virtualbox
```

I rebooted kernel 5.4.0-48-generic into normal mode, and the same problem occurred: the boot process stalled with an empty screen except for a blinking cursor.

So I rebooted into recovery mode the same way again, and did:
```
apt-get install nvidia-driver-450
```

Then I rebooted into normal mode and got the same error.

Rebooted into recovery mode again and did:
```
apt-get purge nvidia*
```

Rebooted into normal mode and got the same error.

Rebooted into recovery mode and did:
```
apt-get install nvidia-driver-440
```

During the install, I noticed kernel modules for both 440 and 450 were prepared (even though I only specified 440). I don't know if this is normal.

Rebooted into normal mode and got the same error.

I then rebooted with kernel 5.4.0-42-generic (normal mode), and according to [FONT=courier new]software-properties[/FONT], I'm using [FONT=courier new]nvidia-driver-450[/FONT].

I'm considering just reinstalling from scratch. Which is a shame, since I did a clean install just one or two weeks ago, and haven't done anything unusual with the system.

---

### Post by mastablasta on 2020-10-16
and the error is still just blinking cursor.

if you press crtl+alt+F1 or F2 does it go to text console?

i once had this issue on the old machine. i never could resolve it, because it is very hard to say what is actually wrong. i sent back the card. 

there is a possibility that display doesn't recognise monitor correctly (through EDID) and sets wrong resolution. another thing with these nvidia chips is that they output on different port.

for example mine throws everything to TV and only at later boot stage moves picture to monitor. when i start application which has different resolution set (for example 800x600) as is the desktop default (1024x1280), the picture is stretched and thrown to TV (1920 x 1080) output (even though that output is disabled in all nvidia and system settings + TV is off) until i correct the resolution in the game's settings. interestingly during this time all i get on PC monitor is blinking cursor. 

as you probably figured out from my data this is a very old (single core) PC. however, my point is that sometimes output is not where it is supposed to be. thi swas the case only with nvidia drivers. nouveau work relatively OK (though defualt output is TV there as well) as did the Radeon driver when i still had the old ATI card.

---

### Post by metacell on 2020-10-16
> **mastablasta said:**
> and the error is still just blinking cursor.
Yep.

> **mastablasta said:**
>  if you press crtl+alt+F1 or F2 does it go to text console?
Yes, it does! Why didn't I think of that?

I can login (in text mode) and confirm that the kernel is 5.4.0-48-generic.

When I do startx, I get:
> Fatal server error: (EE) no screens found(EE)  Please consult the The X.Org Foundation support

My card has three outputs (DVI, HDMI, and DisplayPort), and I have monitors on two of them, if it makes any difference. I can't test the third output, since I don't have a DisplayPort monitor.

And it's apparently a software issue, since it works fine when I reboot to the older Ubuntu kernel, to Debian, and to Windows 7.

---

### Post by mastablasta on 2020-10-17
is ubuntu setup to use xorg or wayland? 

the error looks as, if it can't detect the monitor. there are ways to manually tell the monitor edid number & output. unfortunately i am not versed in that. i just saw it can be done somewhere when i battled my own nvidia demons. 

in xorg there was also a config file. could that one be created and causing the issues?

when i was setting up my kids GTX 1650, i got him a new monitor and all that. it too didn't want to work after drivers install. i don't know why, but i changed the HDMI cable that came with monitor to the one i was using on RaspberryPI. and it imediatelly recognised the monitor and all worked. i then  went to computer shop and asked them to test the HDMI cable that came with the monitor. it worked fine. i got home & replaced the RPi cable with the one from the monitor and it all worked as if nothing happened. morel of the story is... i am thinking here that somehow something prevented nvidia to pickup the monitor data and configure it propperly.

---

### Post by metacell on 2020-10-17
Could be something like that.

But I gave up and reinstalled.

Thanks for the help, anyway.

---

