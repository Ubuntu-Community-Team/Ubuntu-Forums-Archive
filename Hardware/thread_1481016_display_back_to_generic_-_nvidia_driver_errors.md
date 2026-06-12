---
title: "display back to generic - nvidia driver errors"
date: 2010-05-12
forum: Hardware
---

### Post by lgastmans on 2010-05-12
Hi All,

Recently updated to 10.04 and all has been working beautifully up till today. I booted my machine this morning and I had an error with the nvidia driver. Here are the details found in /var/log/jockey.log:

I tried removing and re-enabling the nvidia proprietary driver, which gave the following errors. And when I did apt-get install nvidia-current, it said the latest version is installed.

any help would be greatly appreciated - i am down to a low resolution for the time being.

Unpacking nvidia-current (from .../nvidia-current_195.36.15-0ubuntu3_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up nvidia-current (195.36.15-0ubuntu3) ...
Loading new nvidia-current-195.36.15 DKMS files...
Building for 2.6.31-14-generic and 2.6.32-22-generic
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
Building initial module for 2.6.32-22-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-22-generic/updates/dkms/

depmod......

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for python-support ...

2010-05-12 15:42:36,488 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-05-12 15:42:36,489 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-05-12 15:42:44,188 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:42:44,291 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:43:06,353 DEBUG: nvidia_173 is not the alternative in use
2010-05-12 15:43:06,604 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:43:06,708 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:43:07,005 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:43:07,107 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:43:07,377 DEBUG: nvidia_173 is not the alternative in use
2010-05-12 15:43:07,625 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:43:07,730 DEBUG: nvidia_current the driver is not enabled in all of the relevant device sections
2010-05-12 15:43:15,114 DEBUG: Shutting down

---

### Post by dino99 on 2010-05-12
into synaptic repo, check that you only have lucid genuine repo activated, then update

remove/purge, into synaptic, 
ALL the nvidia packages installed,
 remove xorg.conf (sudo rm -f /etc/X11/xorg.conf)
install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

reboot

check: system admin hardware driver, nvidia-current might be activated

if you need more recent packages, add x-swat ppa: 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by ratcheer on 2010-05-12
That was one of the problems we encountered on the Lucid Xorg Drivers team. If the nvidia kernel module was removed or damaged, jockey (the hardware drivers GUI) would not reinstall the driver. This was consistent throughout Lucid testing, I do not believe it was ever corrected.

I am not sure how you should proceed. Possibly a manual installation of the driver would fix it, but you could end up with worse problems than you have now. There are several threads on manually installing the driver, if you want to look at them.

edit - Follow Dino's advice.

Tim

---

### Post by lgastmans on 2010-05-12
> **dino99 said:**
> into synaptic repo, check that you only have lucid genuine repo activated, then update

remove/purge, into synaptic, 
ALL the nvidia packages installed,
 remove xorg.conf (sudo rm -f /etc/X11/xorg.conf)
install: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

reboot

check: system admin hardware driver, nvidia-current might be activated

if you need more recent packages, add x-swat ppa: 
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

thanks for the quick response!

i followed your instructions, but unfortunately i still have the same problem :( what did you mean by your check, though? should i check whether nvidia-current is active - and how do i do that?

---

### Post by ratcheer on 2010-05-13
Run jockey (System >> Administration >> Hardware Drivers). It should look something like this screenshot.

Tim

---

### Post by lgastmans on 2010-07-03
i must admit that i nearly decided to switch back to windows, however much i love working with linux - with each distro, the only problem i always had was display problems. bear with me, it really is frustrating when you need to get work done.

anyway, got it to work finally, but now i get this error message:

Could not launch 'NVIDIA X Server Settings'
Failed to execute child process "/usr/bin/nvidia-settings" (No such file or directory)

any advice from the masters?

and thanks for the help, always

figured this one out - that was embarrasingly simple. but now, if i try to access the settings, a message comes that i should run the following command:

```
sudo nvidia-xconfig
```

this created a fresh copy of the xorg.conf file, which again created the same error i was faced with in the first place. i removed this copy, and renamed the backed up copy to xorg.conf, and the resolution was fine again. then i found out that the line

```
Driver  "nvidia"
```

was the problem. changing this line to 

```
Driver  "nv"
```

made the resolution come back to normal.

anybody have an idea of what is going on? my resolution is fine now, but i can't access display settings or things get messed up again...

---

### Post by ratcheer on 2010-07-03
"Driver nv" means you have forced it back to nouveau, the open source driver. So, you are no longer using the nvidia proprietary driver.

As long as you do not need Compiz special effects, nouveau should be fine.

Tim

---

### Post by fleaaccela on 2010-11-19
Man, I am having the worst time. I have an old Toshiba Satellite laptop that I just spent the last 3 days watching update the system. Yup, 3 days with 300mb of updates from a fresh install of Ubuntu 10.04.

Anyhow, I woke up this morning and everything was finished! Immediately, I stupidly installed the proprietary closed source driver from the "hardware Drivers" window in Administration. Now my computer boots, I see the Ubuntu prompt and then - a blank screen.

What's worse is I don't even see grub when my system boots. Sitting here looking at a Live-CD boot desktop feeling really sad. How can I revert back to the generic display settings while being on a Live CD? Also, where's my grub? Any chance I could get to like a safe mode or something?

UPDATE:

Nevermind. Figured out how to do it - and this is how I did it:


[b]For 10.04 LTS

Hold down shift upon booting for the GRUB load screen. Select the newest version and choose the "Recovery Mode" for that version. You will get a box asking you to do different things. Choose the one that says "Low Graphics Mode" or something along those lines. Run it just once if it asks. Then, log in like you normally would, go into System > Administration > Hardware Drivers and deactivate the selected video driver that is giving you problems. Reboot. Back to normal.[/b]

---

