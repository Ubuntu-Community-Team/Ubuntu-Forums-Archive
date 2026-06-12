---
title: "Lenovo SL410 won't wake up after suspend"
date: 2014-01-30
forum: Hardware
---

### Post by Silas_Wolff-Goodri on 2014-01-30
Hi, 

I hope someone can help, I've been having the same problem: When I close  my laptop lid or use pm-suspend from the command line, my screen and  all input devices turn off, the power button flashes continuously, and  nothing will wake the system up short of a manual shutdown and reboot. I  went through the process of updating my BIOS and have tried various  grub boot options in my /etc/default/grub file, as described [here]("http://askubuntu.com/questions/361547/ubuntu-freezes-crash-after-wake-when-upgraded-to-13-10"), all with no success. Note that hibernate (save to  disk) does work and that I recently switched my HDD out for a SSD and  upgraded from 12.04 to 13.10. Suspend worked for 12.04 with the HDD but I  haven't tried to suspend in 12.04 with the SSD, so I can't say whether  it is the new distribution that is causing the problem or the hard drive  switch.

As requested by Toz:

1. My computer is a Lenovo SL410 with an Intel Celeron 925 processor  running a 64 bit architecture (please let me know if my usage of  terminology is faulty at any point, this is all new for me). Information  about hardware specifics can be found at [http://paste.ubuntu.com/6847391/](http://paste.ubuntu.com/6847391/)

2. The contents of my /var/log/pm-suspend.log file: [http://paste.ubuntu.com/6847396/](http://paste.ubuntu.com/6847396/)

3. Video card information is:

```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile  4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 09)  (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:213a]
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at f2400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 09)
    Subsystem: Lenovo Device [17aa:213a]
```

4. current kernel command line:

```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic  root=UUID=7b56df28-ca6c-4db6-8954-6fb4005d4edb ro quiet splash  vt.handoff=7
```

------------------------
Again, hopefully someone can help. This has been a nuisance.

---

### Post by Toz on 2014-01-30
*Moved post to its own thread.*

Hello Silas_Wolff-Goodri and welcome to the forums. [s]According to your pm-suspend log file, hibernate appears to be working fine. Can you please confirm that this is the case?[/s] (sorry, missed that in your original post,  I see that it does work).

Can you try another suspend but without the debug statements for now? Specifically:
```
sudo -i
mv /var/log/pm-suspend.log /var/log/pm-suspend.log.old
pm-suspend
```
...and on recovery, post again the /var/log/pm-suspend.log file.

And can you also post back the results of this command after the above attempt?
```
cat /var/log/syslog | grep PM:
```

---

### Post by Silas_Wolff-Goodri on 2014-01-31
Toz,

[Here's]("http://paste.ubuntu.com/6847665/") the new pm-suspend.log file, and the /var/log/syslog is [here]("http://paste.ubuntu.com/6847688/").

What are you looking for in these files?

---

### Post by Toz on 2014-01-31
> **Silas_Wolff-Goodri said:**
> Toz,

[Here's]("http://paste.ubuntu.com/6847665/") the new pm-suspend.log file, and the /var/log/syslog is [here]("http://paste.ubuntu.com/6847688/").

What are you looking for in these files?

In /var/log/pm-suspend.log, I'm looking to see if it completed, what modules are running, if any extra scripts are running and whether there are any error messages above and beyond the ordinary ones. In your case, everything looks good. I notice you have the r8169 module loaded (wired network card). In past experiences this has sometimes caused the process to hang. Are you connecting wirelessly or wired? To test this, I would recommend unloading this module and trying suspend:
```
sudo -i
modprobe -r r8169
pm-suspend
```

With "cat /var/log/syslog | grep PM:", I'm looking at all of the messages that the sleep/hibernate process logs to look for any errors. Sometimes, the culprit can be identified. In your case, nothing out of the ordinary appears.

Looking back at your original debug log of pm-suspend.log, it looks like you have uswsusp installed? Can you confirm?
```
apt-cache policy uswsusp
```
If so, can you try removing that package, running:
```
sudo update-initramfs -u
```
...rebooting and trying again?

If still not working, You might want to try running a [Resume-trace debug]("https://wiki.ubuntu.com/DebuggingKernelSuspend#A.22resume-trace.22_debugging_procedure_for_finding_buggy_drivers") to see if you can identify the culprit.

---

### Post by Silas_Wolff-Goodri on 2014-01-31
Toz,

I am connected wirelessly, but before I unload the r8169 module, I'd like to know how I can restore it in case this does not work. I looked at the man entry for modprobe and it wasn't clear to me how to reinstall removed modules. 

I installed uswsusp after reading [this]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html/comment-page-2") but it didn't help to make resume work so I uninstalled it before posting originally. What I hadn't done was to update initramfs after uninstalling it. I will reboot and try again. If it still doesn't work, I will try a resume trace debug and post how that goes. 

Thanks for the help so far!

---

### Post by Toz on 2014-01-31
> I am connected wirelessly, but before I unload the r8169 module, I'd like to know how I can restore it in case this does not work. I looked at the man entry for modprobe and it wasn't clear to me how to reinstall removed modules. 
Sorry, my omission. To reload the module you can:
```
sudo modprobe r8169
```
...or reboot.

Try this before the resume-trace debug.

---

### Post by Silas_Wolff-Goodri on 2014-01-31
I tried removing the r8169 module and I still had the same problem. 

When carrying out the resume trace debug, do I need to be booted into the latest mainline kernel, or is that only for when the bug-report is to be submitted? Either way, how do I boot into the latest mainline kernel? I installed the amd64 image from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.28-saucy/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.10.28-saucy/) and rebooted my system, but I saw no new options in my grub boot menu. Before I saw your last reply, I went ahead with the resume-trace debug and the dmesg.txt file can be accessed [here]("http://paste.ubuntu.com/6850711/"). I saw no "hash matches" in the file, but I did see a bunch of:

```
[    0.144688] pci 0000:00:1a.0: System wakeup disabled by ACPI
```
[FONT=arial]I haven't set my RTC clock back yet and I'm not quite sure how to do so, or even why its necessary.[/FONT]

---

### Post by Toz on 2014-01-31
Doesn't look like we're having any luck. The "system wakeup disabled by ACPI" only means that particular device isn't enabled to wake the system up - at a bare minimum, the power button will wakeup the system.

You don't need to install the mainline kernel unless you are going through the bug reporting process (they will ask you to try it). 

It is odd that hibernate works and suspend does not, since they basically follow the same process. If you have access to a Ubuntu Live CD, can you boot with it and see if suspend works?

---

### Post by Silas_Wolff-Goodri on 2014-01-31
> **Toz said:**
> It is odd that hibernate works and suspend does not, since they basically follow the same process. If you have access to a Ubuntu Live CD, can you boot with it and see if suspend works?

I booted into the Live USB that I used to install my current distro and suspend did not work there either.

A few other pieces of information that may or may not be useful in diagnosing this problem:

1. The device with highest precedence in my BIOS boot settings is "PCI LAN: Realtek Boot Agent"

2. The RAM modules I am using did not come default on this system (I don't imagine this makes a difference, however)

3. With this new distribution and hard drive (again, I don't know which caused this problem, as I installed them at the same time) I get occasional glitches in single characters that get printed to the screen, across multiple programs. If I scroll down past the place where the glitch is visible and back up, or refresh the page, it is always fixed. 

Any ideas where to go from here?

---

### Post by Toz on 2014-01-31
> 1. The device with highest precedence in my BIOS boot settings is "PCI LAN: Realtek Boot Agent"
Not sure what that means, I've never seen a setting like this. Is there anything in your bios about sleep mode or sleep states? If so, what is it set at?

> 2. The RAM modules I am using did not come default on this system (I don't imagine this makes a difference, however)
I don't believe so. If they were incompatible, you're system would be crashing left and right.

> 3. With this new distribution and hard drive (again, I don't know which caused this problem, as I installed them at the same time) I get occasional glitches in single characters that get printed to the screen, across multiple programs. If I scroll down past the place where the glitch is visible and back up, or refresh the page, it is always fixed. 
Pretty sure this isn't related to the drive, but rather to the intel driver. In 13.10, SNA acceleration has become the default (replacing UXA). Its supposed to be faster but it causes glitches like you are seeing. To remedy this, create (as root) the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
	Identifier 	"Intel Graphics"
	Driver 		"intel"
	Option		"AccelMethod"		"uxa"
EndSection
```
...and log out and back in again. It will revert to the previous method and should eliminate the graphical glitches.

---

### Post by Hughze on 2014-02-17
I was having this problem with my Lenovo ThinkPad T61.  When I closed the lid, the computer would suspend like it was supposed to. When I opened it up and tried to resume, it would only resume to the password prompt screen but it wouldn't display the password prompt. I would have to force a restart. I solved the problem by installing the additional drivers tool and then installing one of the three choices of the graphics driver. This not only solved the problem but the computer works a whole lot faster than before. I have Ubuntu 13.10 64 bit.

---

### Post by Silas_Wolff-Goodri on 2014-02-17
> **Hughze said:**
> I solved the problem by installing the additional drivers tool and then installing one of the three choices of the graphics driver.

The additional drivers tool tells me that no proprietary drivers are in use on my system and doesn't give me any alternative graphics driver options.

---

### Post by Silas_Wolff-Goodri on 2014-02-17
> **Toz said:**
> Not sure what that means, I've never seen a setting like this. Is there anything in your bios about sleep mode or sleep states? If so, what is it set at?

I did not see anything in the BIOS about sleep mode or sleep states. 

> **Toz said:**
> Pretty sure this isn't related to the drive, but rather to the intel driver. In 13.10, SNA acceleration has become the default (replacing UXA). Its supposed to be faster but it causes glitches like you are seeing. To remedy this, create (as root) the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
    Identifier     "Intel Graphics"
    Driver         "intel"
    Option        "AccelMethod"        "uxa"
EndSection
```
...and log out and back in again. It will revert to the previous method and should eliminate the graphical glitches.

The switch to UXA acceleration did fix the screen glitches, but there is no change in the suspend behavior, at least that I can tell. If I wanted to go back to SNA acceleration, would I simply change the "AccelMethod" option to "sna" in my **/usr/share/X11/xorg.conf.d/20-intel.conf **file?

I have been manually hibernating my computer every time I need to leave it, using sudo pm-hibernate. This is pretty inconvenient though, and I imagine it is causing more wear than normal to the swap space on my SSD. Are there any other suggestions you could give that could help me get suspend/resume working again, short of going back to 12.04?

Thanks for all the help by the way!

---

### Post by Toz on 2014-02-17
> **Silas_Wolff-Goodri said:**
> The switch to UXA acceleration did fix the screen glitches, but there is no change in the suspend behavior, at least that I can tell. If I wanted to go back to SNA acceleration, would I simply change the "AccelMethod" option to "sna" in my **/usr/share/X11/xorg.conf.d/20-intel.conf **file?
Yes.

> I have been manually hibernating my computer every time I need to leave it, using sudo pm-hibernate. This is pretty inconvenient though, and I imagine it is causing more wear than normal to the swap space on my SSD. Are there any other suggestions you could give that could help me get suspend/resume working again, short of going back to 12.04?
I was re-reading your initial post:
> When I close my laptop lid or use pm-suspend from the command line, my screen and all input devices turn off, the power button flashes continuously, and nothing will wake the system up short of a manual shutdown and reboot.
How are you trying to resume the system? Are you pressing (not holding down) the power button to get it come back?

---

### Post by Silas_Wolff-Goodri on 2014-02-17
> **Toz said:**
> How are you trying to resume the system? Are you pressing (not holding down) the power button to get it come back?

I have tried pressing the power button, tapping it, holding it for 1 second, holding it for 2 seconds, etc., as well as many different combinations of key strokes. Nothing that I have done so far has woken it from the suspended state or caused any change whatsoever.

---

### Post by Toz on 2014-02-17
> **Silas_Wolff-Goodri said:**
> I have tried pressing the power button, tapping it, holding it for 1 second, holding it for 2 seconds, etc., as well as many different combinations of key strokes. Nothing that I have done so far has woken it from the suspended state or caused any change whatsoever.

Hmmm. Can you post back the results of:
```
cat /proc/acpi/wakeup
```

---

### Post by Silas_Wolff-Goodri on 2014-02-17
The content of [COLOR=#000000][FONT=Ubuntu Mono]/proc/acpi/wakeup [FONT=arial]is [/FONT][/FONT][/COLOR][Here]("http://paste.ubuntu.com/6952615/")

---

### Post by Toz on 2014-02-17
> **Silas_Wolff-Goodri said:**
> The content of [COLOR=#000000][FONT=Ubuntu Mono]/proc/acpi/wakeup [FONT=arial]is [/FONT][/FONT][/COLOR][Here]("http://paste.ubuntu.com/6952615/")
Everything looks okay there. 
> I booted into the Live USB that I used to install my current distro and suspend did not work there either.
Perhaps it is best to create a bug report and follow through with the process there.

---

