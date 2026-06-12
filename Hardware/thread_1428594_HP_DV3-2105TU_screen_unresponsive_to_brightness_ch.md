---
title: "HP DV3-2105TU screen unresponsive to brightness change"
date: 2010-03-13
forum: Hardware
---

### Post by shlape on 2010-03-13
I recently installed Ubuntu 9.10 on a HP DV3-2105TU notebook and have had no luck fixing a brightness issue. 

Before doing this, I tested functionality when vista was still installed and it worked. I then upgraded the BIOS to F.13 A from F.12 and started with the install. I seem to have forgotten to retest the brightness functionality after this and shudder at the thought of having to reinstall vista again for the sake of testing on an OS known to have worked.

I can find current settings in
/proc/acpi/video/OVGA/DD03/brightness

and pressing the Fn+F7 and Fn+F8 buttons, the applet responds but the screen brightness remains the same. Added to this, the mute button remains on however the volume buttons respond with the applet showing increase/decreasing volume levels.

I recall having this problem with Ubuntu a fair while back but cannot recall the package used to fix the LEDs and brightness. Something to do with 'backend'.

I'll wait a short while for a response otherwise I'll have to bite the bullet and reinstall vista to make sure the BIOS upgrade isn't at fault here. :frown:

---

### Post by shlape on 2010-03-13
OK I got bored and went ahead with the (32bit) winbloze reinstall, purely to see if the BIOS update went bad. Winbloze reinstalled and the dimmer function worked fine. I am missing something in Ubuntu to get this working but am unsure where to go from here.

The video I have is:
Intel Graphics Media Accelerator 4500MHD

Im seriously hoping this isn't a winbloze-only driver controlling the brightness. I don't want to burn out the LED display because it's constantly at 100%.

Any help is appreciated.

---

### Post by grege on 2010-03-15
I do not have an HP laptop, but I would try a live CD of 10.04 alpha.

I am running it on a Dell 11z with the same video chip set and my brightness buttons work. Your keyboard is different so that does not mean much, but worth a try

10.04 is stable enough to install if it works, the full release is only 6 weeks away.

---

### Post by shlape on 2010-03-16
> **grege said:**
> ...I would try a live CD of 10.04 alpha...

Thanks for the tip! I didn't even know about Lucid Lynx but it sounds promising.

I've been banging my head against the wall with a lack of LED screen brightness adjustment, no (alsa) sound, and a very dodgy way to connect the  wifi.

I'll d/l the iso tomorrow and mark this thread SOLVED if there is success. Hey, I'm trying to be optimistic. :p

---

### Post by shlape on 2010-03-16
I tried the alpha-3 release of Ubuntu 10.04 this morning, mostly with success! All the touch-sensitive multimedia icons were responsive and changed colour accordingly, and for the first time I heard sound!

There is one problem remaining... the screen is unresponsive to brightness change. The brightness applet pops up when pressing the Fn+F8 and Fn+F9 buttons, but the screen remains at 100% brightness.

Any suggestions... anyone?

---

### Post by shlape on 2010-03-17
This is a somewhat crude work-around compared to how screen brightness functionality ordinarily works, but hey it does the job... and then some!

A program called xbrightness is available [_here_]("http://disjunkt.com/xbrightness/"). I compiled up the program and it works great!

I'm assuming this functionality will appear in later versions of the Linux kernel. At the moment I'm using 2.6.33 and haven't been able to get the brightness working, but all other multimedia touch-sensitive buttons work now. I believe this was the case since kernel version 2.6.32-r10.

---

### Post by shlape on 2010-06-04
I have some good news related to this old problem. A better solution than the xbrightness fix has been found. Patches originally made to fix a Dell Studio 1558's brightness problem also worked to fix my laptop.

If you have an i915-based laptop that doesn't have brightness control, [_try this fix_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611/comments/11"). The source patches are [_available here_]("http://kernel.ubuntu.com/~kamal/i915_brightness/").

Note: this is a preliminary test fix but was functional on my laptop nonetheless. Hopefully it progresses to the next kernel release. Thanks Kamal! =D>

---

### Post by zeroseven0183 on 2010-07-20
I wonder why it didn't work for my HP Pavilion dv3-2106tu. I installed the .deb for i386 but after restarting, the brightness still is not adjusted with the controls.

---

### Post by shlape on 2010-07-20
> **zeroseven0183 said:**
> I wonder why it didn't work for my HP Pavilion dv3-2106tu. I installed the .deb for i386 but after restarting, the brightness still is not adjusted with the controls.

Post your problem with as much details [_here_]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568611/"). Kamal Mostafa is the guy who issued the solution and may be able to help you out.

---

