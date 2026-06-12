---
title: "Constant crashing after update (possibly NVIDIA)"
date: 2015-09-29
forum: Hardware
---

### Post by mistcloud-misty on 2015-09-29
My laptop is: Asus X555L-ns51, 64-bit, with an NVIDIA Geforice 940M graphics cord, and Intel i5 processor.

I have had it for approximately a week, with little to no bugs after installing the Wifi driver other than crashing quite often while rebooting (while shutting down, not starting up) and very rarely crashing while logging back in. 

I did updates this morning before leaving to work, and after, I was on campus with public Wifi and the wireless was constantly dropping out and in, usually in 1 second intervals between the out-in, and a few minutes to 5 seconds between the outs. At one point, it stopped coming back at all, so I rebooted. This time, although there were obvious video issues, it didn't crash (there was a triple Ubuntu logo with the 5 icons all blinking at once before it rebooted and flickering of the screen), but when I tried to log back in, it crashed. I tried again, and was able to get into the laptop before it crashed almost instantly when trying to open Firefox.

Again, I rebooted, and went into recovery mode. I ran the fdisk or similar option and it said there was a dirty bit that was fixed and two errors that were fixed, so I rebooted again. It crashed not too long after. Back into recovery mode, I tried to switch to the NVIDIA proprietary drivers. I rebooted again into that, without crashing, but had no Wifi. Upon re-installing the Wifi card, it crashed once more. 

A google search in between crashes had me find the 'install nvidia-current' command which I did, then crashed in recovery mode because I closed the laptop to move to a new location (oops!).

I finally figured out that there was a new kernel that I hadn't noticed in all the subsequent 'recovery mode' options (my laptop boots into Grub in such a way that it has an Ubuntu option, a More options for Ubuntu option, an option to boot to Windows Boot manager, and some system option (goes into BIOS, I think). So I clicked the second kernel (the one I had been using since I got it), and so far, there have been no issues. The Wifi is working fine, and the driver has reset itself to the open source one. No crashing. 

I was wary from the start about anything with Nvidia because I had previous problems with a different computer.

Is there any file I can check that could determine what went wrong (I had no popups about system problems or bug reports), and if so, what I can do / if I already fixed it with that installation? 

Thanks for any help!

Update: It crashed. I found some info when in recovery mode, trying to boot to Failsafe graphics mode (it refused, and gave me some info about a log file which I'll check and update again with).

---

### Post by tim134 on 2015-09-29
Hiya,
Just posting to 2nd your claim re nvidia.  Almost identical problem with my laptop today: nvidia graphics driver fail after updating.  In my case however, upon reboot, the screen was a jumbled mess of pixels.  Unable to do anything at all.  Attempted a live cd repair but my skills are not up to par.  Became simpler to just reinstall as this is an old laptop for general internet browsing only.

Anyway, good luck!

Tim

---

### Post by mistcloud-misty on 2015-09-29
If I load in recovery mode, and then 'resume boot', Nvidia fails to load, allowing my laptop to boot with the integrated intel graphics that come with the processor - not very pretty, at 800x600 pixels (hurts my eyes), but it doesn't crash. The wireless is still a bit wonky, so I'm wondering if there's a bug with that driver.

There was a crash in the xorg that was actually noticed by my computer but my computer crashed before I could send it, and I can't open the log in 'crash' from sudo or by nautilus. Something about xorg crashing with apporg (or a similar program). 

I will be uploading a few screenshots and the xorg log once I get home - I am thinking it might be the public wifi that's problematic so I will find that out. I had enough trouble trying to boot off a flashdrive to re-install Ubuntu (I dual boot with Windows 8).

---

