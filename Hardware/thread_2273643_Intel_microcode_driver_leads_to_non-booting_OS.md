---
title: "Intel microcode driver leads to non-booting OS"
date: 2015-04-14
forum: Hardware
---

### Post by fondatommaso2 on 2015-04-14
Good morrow,
since 3 days I have been testing Kubuntu 15.04. The proprietary drivers installer told me that there was an available driver. So I opened the driver installer and I saw that this driver was the Intel Microcode driver. _On previous Ubuntu versions, the driver installer never told me that I needed this driver._ Anyway, I decided to install it and the result is that Kubuntu doesn't boot. This is what happens:
- the pc loads the bios
- grub shows up
- after selecting Ubuntu in GRUB the pc freezes and the "CAPS LOCK" led next to my keybord starts to blink. At this point the only way to turn off the pc is by disconnecting the power cable.
Is there any way to uninstall/downgrade the microcode driver (for example using chroot from my other linux OS)?
Thanks!!

---

### Post by weatherman2 on 2015-04-14
Try to boot in recovery mode, which you can choose from the Grub boot menu.

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

Then try to remove the package.

---

### Post by Geert_Jalink on 2015-04-24
Hi, I am just new at this forum. It is suggested you should search the package.
```
sudo dpkg -l|grep intel
```

example result on my system:
```
[FONT=monospace][COLOR=#000000]rc  [/COLOR][COLOR=#ff5454]**intel**[/COLOR][COLOR=#000000]-microcode  3.20150121.1 amd64 Processor microcode firmware for Intel [/COLOR]CPUs[/FONT]
```[FONT=monospace]

Now you know the package is called   '  intel-microcode   '

You could try to uninstall it with the following command.
```
sudo apt-get purge intel-microcode
```

This must be done from a root privelege shell mounted in safe mode by booting from the ubuntu DVD.

I also have uninstalled this Intel Microcode package, because it overheats my laptop. Also I created 1 root privelege account and it fails to boot into graphical environment. However a normal user just works in graphical environment. I do not know what causes this. I now work with a nonworking root privelege account and 1 normal non privelege account. For now since I installed twice. I will wait for updates to come. Release 15.04 has the new Plasma 5 desktop I think, and to sadly say it is so buggy.

 Sadly also the boot splash screen hides whats is going on behind the screens. But there is an easy solution to that problem. In a root priveleged shell do this.
```
cd /etc/default
```
[/FONT]```
[FONT=monospace][COLOR=#000000]sudo cp grub grub.bak0[/COLOR]
[/FONT]sudo nano grub
```
'sudo nano' starts a text editor. Use the left CTRL key together with the optional shortcuts below at the screen to save and exit nano text editor.
Search for following line inside /etc/default/grub
```
[FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
Change it into
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT=""[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
Now the system will show every command behind the splash screen. And you always have '  grub.bak0   ' in case of mistake.
Next what you must do is to update grub bootloader with:
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]sudo update-grub[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR][/FONT][FONT=monospace]Now enter the following command.
```
sudo reboot
```

In my opinion release 15.04 untill now sofar is still a beta. The NVidia Nouveau driver for example frequently crashes. Also the NVidia binairy blob driver frequently crashes. This was not the case with release 14.10. In 14.10 it was stable as rock. That is a temporary price to pay for innovation of the new Plasma Desktop environment. 
[/FONT]

---

### Post by dino99 on 2015-04-24
'caps-lock' blinking means a kernel crash, not an 'OS does not boot' which is way different
try to boot into recovery mode, then purge the intel-microcode as explained previously, and try to boot normally.
If it fails, then you are ready for a new fresh install (and report that issue to kubuntu devs, 'ubuntu-bug ubiquity')

---

### Post by Geert_Jalink on 2015-04-24
I forgot to mention that I used Kubuntu 15.04 and not Ubuntu 15.04, however the procedure to remove intel-microcode is the same. However I gave up and reinstalled Kubuntu 14.10 which is now up and running fine. Also I came to the conclusion in my case it is not intel-microcode that caused overheating my laptop but the NVidia binairy blob and NVidia Nouveau drivers respectively. These drivers in Kubuntu 15.04 (and perhaps Ubuntu 15.04) seem to get stuck at maximum clock rate of your NVidia graphics adapter which causes a lot of heat.

And now I installed Kubuntu 14.10 I did a 
```
sudo apt-get install intel-microcode
```
and the laptop works fine even with this microcode installed. I verified on every boot this intel-microcode is send to the CPU. 

So I am back to Kubuntu 14.10 and have Ubuntu 15.04 in a virtual machine. Since I prefer Kubuntu I had to revert to Kubuntu 14.10. 

Laptop Specs:
```

CPU= 2.0 GHz Intel Core2Duo
Graphics=256 MB NVidia 8400GS Mobile
Ram=3.2 GigaByte

```
I looked for other people with overheated video cards in release 15.04 and found 2 similar cases, yes even with ubuntu.

---

### Post by dino99 on 2015-04-24
wow, running plasma on a 8400gs, you are an optimist dreamer; that explain the power drain

---

### Post by Geert_Jalink on 2015-04-25
> **dino99 said:**
> wow, running plasma on a 8400gs, you are an optimist dreamer; that explain the power drain
Well as I said with Plasma 4 the temperatures are fine on Kubuntu 14.10 and its NVidia 331.113 driver. This is because the NVidia binairy blob doesn't lock on maximum clockrate. However I sincerely hope that Plasma 5 has important bugs that cause both Nouveau driver and NVidia driver of 15.04 release to lock the videocard at maximum clockrate. I will try again when 15.10 is released.

You don't have to believe me, but running Crysis at 800x600 (16:9 rendering ) is playable with Windows 7 on it. Besides that just displaying a static rendered 'landscape' (The desktop called Plasma 5) should not drain that much power. I don't consider it normal. And the proof in the pudding is that in Kubuntu 14.10 Plasma 4 it just works fine. Plasma 4 by browsing runs at 200 MHz, Plasma 5 locks the CPU at maximum 800 MHz.

If one has a powerful videocard like a 970M NVidia card I wonder if it will be locked at maximum frequency too. I consider Kubuntu 15.04 dangerous for my laptop since it heated the laptop over 72 degrees Celsius where Kubuntu 14.10 just is 43 degrees Celsius.

But anyway Plasma 5 is to unstable in my opinion even with compositing disabled (The CPU doing everything) the problem is still there. And without compositing the video card is mainly doing just Blitting Bitmap from memory in a framebuffer.

Sad story that Kubuntu 15.04 requires either better hardware than Windows Vista/7/8 or has serious beta bugs. With Kubuntu Karmic ( 2009 ) I used to play Doom 3 on this laptop and it ran fine. I am optimistic indeed that bugs in Plasma 5 will be solved, and that hardware drivers will be released to fix it. 

However if it are not bugs, but 'features', I feel sad because 14.10 will then be the latest release ever for this laptop.

Linus Torvalds once made a statement to NVidia with his middle finger.

For those with similar GPU overheating problem with NVidia video cards I have good news. You should obtain the 331.13 driver which is not affected by the described problem. I confirm this because I installed NVidia driver 340 current on Kubuntu 14.10 and then, bang, same problem as in Kubuntu 15.04. It is almost certainly a NVidia driver problem. 

This might help: But remember do not install the NVidia 340 driver on e.g. 8400GS Mobile and try to get NVidia driver 331.13 so be just installing driver 340 I encountered the same problem on Kubuntu 14.10 from which I conclude it is a driver problem causing overheating of GPU. Powermizer in 340 seems to be broken for some reason I don't know. It is not Plasma 5. However I still consider Plasma 5 to unstable and will wait for Kubuntu 15.10, since Plasma 4 is mature over years and Plasma 5 isn't. Good luck. Remember before you install other NVidia binairy blob drivers to always go back to Nouveau first to clean up NVidia remnants.
[B]
How to install the latest Nvidia drivers[/B]

[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

---

