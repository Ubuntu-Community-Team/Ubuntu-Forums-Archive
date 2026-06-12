---
title: "Acer Travelmate 8104WLMI questions..."
date: 2005-12-03
forum: Hardware &amp; Laptops
---

### Post by [Jedi] on 2005-12-03
Hi all,
this is my first thread. I've read a lot about installing Ubuntu (or Kubuntu) on my Acer Travelmate 8104WLMI.
I've installed successfully Kubuntu 5.10 Breezy with kernel 2.6.12-10 and patched (via initramfs) DSDT table, but I have some questions:

1. How to make special keyboard buttons work? (I mean mail button, www button, "e" button and "p" button located in the up/right part of keyboard - I've tried acerhk with no success)

2. Is it possible to suspend or hybernate this notebook? (Everytime I do one of these actions my nb won't come up anymore and I have to restart it (hard reset))

3. Is it possible to control LCD brightness by acpi software or similar?

4. Sometimes when system boots up my nb shuts itself down without any desktop output, just one time I've read something like "critical temperature"... is it right?

Thank you for answers. Bye.

P.S.: custom 3C22 table won't work with 512MB RAM models (hangs on boot), if you have 512MB you can try attached DSDT table.

---

### Post by teaker1s on 2005-12-03
your keys if you can asign them as shortcuts in system-prefrences-keyboard shortcuts the great if not 
[look here for multimedia keys]("https://wiki.ubuntu.com/MultimediaKeys?highlight=%28multimedia%29")

suspend-I don't know works for some people others have problems search the forums

there are lcd brightrness controls for dell, it may be possible fine a program that works with you notebookto alter them to suit try googling your model linux and brightness or lcd

sorry I can't tell you more but at least you have a reply to point you in the right direction

---

### Post by [Jedi] on 2005-12-04
Thank you for answer, about LCD brightness now I will try to search for something by google.

About hotkeys: I've tryied to find scancodes in console, but when I press email button, www button, "e" button or "p" button no scancode is reported. It seems that they give no signal at all. Do you have some advices?

Another question: is it better to use kubuntu 5.10 embedded ati driver or ati fglrx driver?

I'm trying fglrx (also for tv-out) but I have a problem... when I switch to another terminal (CTRL-ALT-F1...Fn) instead of console my LCD keeps filling with strange colors and I can't turn back to X server neither switch to another terminal, I have to restart system with CTRL-ALT-Del.

Do you know how can I fix this problem?

---

### Post by er-ku on 2005-12-04
> **'[Jedi]']Hi all,
this is my first thread. I've read a lot about installing Ubuntu (or Kubuntu) on my Acer Travelmate 8104WLMI.
I've installed successfully Kubuntu 5.10 Breezy with kernel 2.6.12-10 and patched (via initramfs) DSDT table, but I have some questions:

1. How to make special keyboard buttons work? (I mean mail button, www button, "e" button and "p" button located in the up/right part of keyboard - I've tried acerhk with no success)
[/QUOTE]

Hey, I (well, my mom, to be exact) have a TravelMate 4061NLMi. www and e-mail buttons work for me. I don't remember if I left e and P unassigned, or if they don't work..

I used the following string in the Keyboard section of /etc/X11/xorg/conf to get more keys to work:
        Option          "XkbModel"      "acer_tm_800"

> 
2. Is it possible to suspend or hybernate this notebook? (Everytime I do one of these actions my nb won't come up anymore and I have to restart it (hard reset))


Mine does hybernate by default, and I managed to get it to suspend-to-RAM too. Suspending to RAM may work in your case too, that's what you do to try to make it work:

```
sudo dmidecode |less
```
find lines like the following:
```

Handle 0x0001
        DMI type 1, 25 bytes.
        System Information
                Manufacturer: Acer, inc.
                Product Name: TravelMate 4060
                Version: Not Applicable

```
in the output. You need the Manufacturer and Product Name lines. 

Edit /usr/share/acpi-support/YOUR_MANUFACTURER.config in your favourite editor. The syntax of the file is quite understandable, you just need to create another stanza for your Product Name. 

run ```
/etc/init.d/acpi-support restart
```, or, maybe, even restart your computer. Logging out/in may do the job without restart too.

**Edit (I should read more carefully): your issue looks very similar to the one described in [this bugreport](https://bugzilla.ubuntu.com/show_bug.cgi?id=1940) (it's for macs, though). You may need to check suggestions there, and try to apply them in your case. Hopefully, this will be fixed in later kernels...**

> 
3. Is it possible to control LCD brightness by acpi software or similar?


at least for me, the brightness control buttons do their job. That's not software control, though...  said:**
> 
4. Sometimes when system boots up my nb shuts itself down without any desktop output, just one time I've read something like "critical temperature"... is it right?


Might be, dunno. Maybe it's just you adjusting brightness, or something? ;)

---

### Post by [Jedi] on 2005-12-09
Thanks for answer er-ku.

Now I can use extra buttons, they work fine adding Option "XkbModel" "acer_tm_800" to xorg.conf and setting them with Gnome shortcuts.

My problems about Console switching, Suspend-to-RAM, Suspend-to-Disk and StandBy are still there. When I use any of these modalities, my system hangs (I'm using fglrx driver 8.20.8, but problem exists also with 8.19.10 and previous):

1. Console switching: with fglrx driver loaded (any version) I cannot switch between X and console by CTRL-Alt-F1...Fn. When I do it I have screen melting various colors, system is still funcional but won't let me do anything except CTRL-Alt-Del to restart.

2. Suspend-to-RAM: system can suspend itself to RAM but when I press a key to resume I have blank screen, frozen system, hard reset (power off) is required.

2. Suspend-to-Disk: system can suspend itself to disk, but when I press power key to resume and boot I have a screen that tells me swsusp need to load x pages, frozen system, hard reset (power off) is required. (I have resume=/dev/myswapdevice in grub, passed at boot time)

3. StandBy: system goes in standby, but when I try to resume I have blank screen, system is still funcional but won't let me do anything except CTRL-Alt-Del to restart.

What can I do to solve these problems? I'm surrending, I've tryied everything with no results at all...

Thank you.

---

### Post by daller on 2005-12-09
Please let others know about issues (and fixes) with this laptop:

[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)

Thanks!

---

### Post by [Jedi] on 2005-12-12
I post my status about Acer Travelmate 8104WLMI and Ubuntu (Kubuntu) 5.10 Breezy. 
I've also added it in Acer laptops WikiPage ([https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsAcer)):

=== Acer Travelmate 8104WLMI ===

 * Installation: Installation hangs, but worked when I used "noapic" option. Need to add "Option "MonitorLayout" "LVDS, AUTO"" in Section "Device"
   of xorg.conf (see [http://ubuntuforums.org/showthread.php?p=191715#post191715](http://ubuntuforums.org/showthread.php?p=191715#post191715)) cause blank screen at first boot (I switched to console with 
   CTRL+ALT+F1 and modified xorg.conf with vi editor).
 * Resolution: It's better to use 1680*1050, no problems detected.
 * LAN and WLAN work right out of the box, I've enabled led with this command: echo "options ipw2200 led=1" > /etc/modprobe.d/ipw2200. (You can set
   WLAN configuration using Gnome network configuration tool, it supports also WEP authentication).
 * Special keys work right out of the box after changing keyboard layout to "acer_tm_800" (you can edit xorg.conf and add line 
   Option "XkbLayout" "acer_tm_800" to your input device / keyboard section) and using Gnome shortcuts editor to assign a function to them.
 * ACPI: ACPI partially works. I've put a patched DSDT table (3c22 custom) in folder /etc/mkinitramfs and linked it to kernel with command 
   "dpkg-reconfigure linux-image-(uname -r)" (this table works well with 1024MB RAM models, if you have a 512MB one, you can try DSDT table that
   I've attached to this thread: [http://www.ubuntuforums.org/showthread.php?t=98413)](http://www.ubuntuforums.org/showthread.php?t=98413)). With this patch you can read battery state, you can control
   CPU frequency and read CPU temperature. Unfortunately none of standby, suspend-to-ram or suspend-to-disk are working for me. System hangs and I 
   have to hard reset it. (I've tryed with ati driver that come with Ubuntu 5.10 Breezy and fglrx driver until version 8.20.8).
 * Graphic driver: ati driver that come with Ubuntu (or Kubuntu) 5.10 Breezy works well but without hardware accelleration or TV-Out. FGLRX driver
   works but when I switch to console (CTRL+Alt+F1) screen starts melting strange colors and I have to reset with CTRL+Alt+Del. It seems that with
   kernel 2.6.15-rc5 this problem has gone but sometime system freeze when I restart it.
 * In conclusion my system is functional, but I really need standby, suspend-to-ram and suspend-to-disk. I will try software "Suspend2" hoping to
   solve problem. I will let you know. 
 * Sound works, I only unmuted device.
 * Modem untested
 * Cardreader untested
 * PCMCIA untested
 * IrDA untested
 * Bluetooth is recognized, but untested.

I hope that anyone can find a solution to solve standby, suspend-to-ram and suspend-to-disk problems and also hope that Ati will release a new driver solving known issues.

---

