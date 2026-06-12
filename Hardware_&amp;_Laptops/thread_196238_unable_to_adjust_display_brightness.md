---
title: "unable to adjust display brightness"
date: 2006-06-13
forum: Hardware &amp; Laptops
---

### Post by saab340 on 2006-06-13
Hello,

I am running Ubunu 6.06 on my Sony Vaio PCG-K17 laptop. The video card is an ATI Radeon IGP 345M. 

When I first installed Ubuntu, I was able to adjust the screen brightness by adjusting the "Set Display Brightness" slider that appears under System->Preferences->Power Management Preferences. 

Sporadically I find that this brightness control doesn't work. That is, when I move the slider to the left from 100% to 99% there is a small, but noticable reduction in the brightness, but no further reduction when I move it any further to the left.  Previously, I was able to reduce the brightness in six or seven increments by moving the slider to the left.

An lsmod reveals that the modules, sony_acpi, pcc_acpi, radeon, video, and and sonypi (which controls the brightness) are all loaded.

In case its relevant, when the brightness control was working, I also remember seeing a green battery icon on my panel, which I could double click to get into the Power Management Preferences mentioned above. Now all of a sudden it has vanished.

Suggestions?

Thanks,

Vasanth

---

### Post by saab340 on 2006-06-13
Update. I restarted my computer. Now the green battery icon (gnome power manager) appears on my panel. However, I am still unable to adjust the brightness, using the slider that is in the power management preferences window.

---

### Post by evil_elman on 2006-06-14
Aren't there keys to adjust the brightness up / down on your keyboard? I've got an Acer and I don't even need an OS to adjust screen brightness. :-)
It's
fn + LEFT
fn + RIGHT
on my laptop...

However, I don't even have the above mentioned slider in the power management window. I wonder why?

---

### Post by saab340 on 2006-06-14
No, function keys don't work on my laptop. This is because of Sony's decision to not connect these keys directly to hardware, but to instead require their own hotkey drivers. So anytime you install a new OS (even if its windows) the function keys will stop working.

This morning when I rebooted my computer I found that the green battery icon (gnome power management) has again vanished. This is very strange. It appears/disappears whenever it wants to.

---

### Post by atm0sph on 2007-11-17
I have a Sony Vaio PCG-TR3A and in Windows XP, you can download the drivers to make your Fn key brightness and volume and such work - You have to install the Shared library first, but it can be done.

In Ubuntu, my Fn Mute & Fn Volume keys act as Volume Up/Done..  I haven't figured out the Brightness though - It's real dark and quite annoying...


LOL!  As I was looking for the submit button, sure enough - the two keys to the right ( Fn Brightness buttong dims, whereas Fn F6 brightens), so I guess they

---

### Post by rosegarden78 on 2008-01-19
Or type the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

**[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)**

---

### Post by matt.raffel on 2008-04-14
> **rosegarden78 said:**
> Or type the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

**[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)**

This works until the screen saver kicks in.  When the screen saver terminates the brightness is back to the pre-adjusted levels.

Btw I'm not running a laptop.  What is the equiv for function key on a standard PC keyboard?

---

