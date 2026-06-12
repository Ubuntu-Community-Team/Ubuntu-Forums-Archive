---
title: "[SOLVED] Cut off speakers when headphones are plugged in?"
date: 2008-10-23
forum: General Help
---

### Post by rob-h on 2008-10-23
Hello,

I'm fairly new to the Ubuntu world. I installed Wubi on my Vista laptop and am fairly happy with it, except the fact that I don't seem to be able to set the option of the speakers on my laptop (which are built in), to turn off when headphones are plugged in...could I at least turn them off manually each time?

Also, is Wubi only designed for testing purposes? Are there any disadvantages than using it from a real installation of Ubuntu? What happens when I reach the limit for space I set when installing Wubi?

Any help appreciated, and remember I am a newbie to the Ubuntu world.
Cheers.

---

### Post by d_skillz on 2008-10-23
I've also experienced this issue, when posting please provide your model laptop or desktop specs. I am running ubuntu on a Sony vaio VGNN325e. To solve the problem manually double-click the volume control icon on your gnome panel, fully turn up Master & Front (both levers) beneath the **front** levers are link and mute, select mute. What this does is mute your audio from/built-in speakers. WUBI is not for testing purposes solely but more of an option to allow you to fully experience ubuntu natively on your hard drive and give you the option of uninstalling at any time without damaging your host Windows partition. The only disadvantage to a wubi installation as opposed to a seperate partition install is performance. The performance of the OS is ranked like this:
Live CD - slowish but usable
Wubi - usable but "slightly slower" than a clean partition install
Full install - Fastest performance possible dedicating a single partition and swap disk for virtual memory managment and improved system responsiveness.
If you want to do a dual boot with ubuntu I recommmend viewing this thread
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=2")

---

### Post by rob-h on 2008-10-23
Thanks for your reply. I tried the above but to no avail - in fact, no sound comes from the headphones, when plugged into the only socket (other than the microphone one).

In response to the specifications:

Processor: Intel Core 2 Duo CPU T5250 @ 1.50 GHz
Memory: 2.00 GB
32-Bit
Realtek High Definition Audio (latest drivers)

^ those were found Windows side..

Cheers.

---

### Post by NoWayBill on 2008-10-23
Make and model please.
Then post console the output of...

**lspci**

---

### Post by d_skillz on 2008-10-23
Gonna encourage you to open up your terminal. In order to do this, on your gnome panel click acessories>terminal. Type the command "lspci" without the quotes, select the output generated pressing Ctrl+Shift+C (This copies the text result) and pasting the output lets see if we can figure out the problem. I also have a Realtek Audio driver so it is detected in Ubuntu.

---

### Post by Interpreter on 2008-10-24
Hi rob h and his helpers.
The Ubuntu approach is different from windows as in that you dont' auto-switch between speakers and headphones by pluging in the latter... or not. To use yer headphones go to
```
System > Settings > Sound
``` and that way tell the system to use the device of your desire for multimedia tasks, or whatever you want to do with it, hope that helps abit.

---

### Post by rob-h on 2008-10-24
Thanks for the responses.

This is a Realtek High Definition Audio.

Output from lspci:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

Interpreter, I've experimented with that all sorts of options including selecting only Headphones in "Device Mixer Tracks" - but sound will only come from laptop speakers.

Thanks again.

---

### Post by rob-h on 2008-10-25
Could anyone shed some light on this issue?

---

### Post by Interpreter on 2008-10-25
Sorry for the let down, my headphones are connected via a USB soundcard, if I plug em into "the green front thingy" they "just work" while my speakers go mute just fine. As a result I don't know how to fix your problem ((.

Help this man, he's in need of some tuneage!!

---

### Post by d_skillz on 2008-10-25
Please check out this thread [here]("http://ubuntuforums.org/showthread.php?t=806620") let me know if it solves your problem, if it doesn't I can try something else.

---

### Post by rob-h on 2008-10-25
Just tried that tutorial, restarted and I don't have a tab next in the Volume Control when Alsa Mixer is selected. I followed the instructions carefully, is it still possible I did something incorrectly?

---

### Post by d_skillz on 2008-10-26
Just want to confirm, you say you cannot see the switches tab with the headphone checkbox?

---

### Post by rob-h on 2008-10-26
I have the switches tab, but no "enable headphone jack sense" checkbox:

[img]http://i294.photobucket.com/albums/mm119/dwrovin/volume_alsa.png[/img]

---

### Post by rob-h on 2008-10-27
Still looking for advice. :)

---

### Post by rob-h on 2008-10-27
d_skillz, thanks for the PM.

Just tried the tutorial again..I did something incorrect last time...I've also tried that tutorial many times with no luck...my switches tab looks like it does as above still. ^

---

### Post by riahc3 on 2008-10-28
[http://ubuntuforums.org/showthread.php?t=931089](http://ubuntuforums.org/showthread.php?t=931089)

---

### Post by rob-h on 2008-10-28
I have now fixed this problem, thanks to all, especially d_skillz.

---

### Post by d_skillz on 2008-10-28
Glad I could help.

---

### Post by Interpreter on 2008-10-29
> **rob-h said:**
> I have now fixed this problem, thanks to all, especially d_skillz.

Would you mind scrolling up abit >>thread tools >> mark as solved ,thanks.

---

### Post by rob-h on 2008-10-29
> **Interpreter said:**
> Would you mind scrolling up abit >>thread tools >> mark as solved ,thanks.

Have done, cheers.

---

