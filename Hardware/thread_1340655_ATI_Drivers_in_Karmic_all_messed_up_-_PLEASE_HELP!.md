---
title: "ATI Drivers in Karmic all messed up - PLEASE HELP!"
date: 2009-11-28
forum: Hardware
---

### Post by turinturambar on 2009-11-28
After I installed the last updates on my laptop for Karmic, including a new kernel version, my graphics card isn't supported.  There's no compositing and I can't enable any visual effects.

I have Karmic on a Dell Latitude D610 with an ATI Mobility Radeon X200.  I have been looking this up on the internet and I cannot figure out how to fix it.  My understanding is that there is an open-source driver and a proprietary driver, but I don't know which one I'm using or how to change or anything.

Please help me!

---

### Post by adalal on 2009-11-28
When you installed the driver, did you install it from System > Administration > Hardware Drivers? If so, that's the proprietary driver from ATI.

If you had to compile it yourself, it's definitely open source.

But, did you install anything at all with regards to the video card, and if so, what files?

---

### Post by turinturambar on 2009-11-28
When I go to Hardware Drivers, there is no option for my graphics card.  Nothing at all.

I'm not sure exactly what happened because everything worked before the update...then I restarted and it went kablooey.

---

### Post by adalal on 2009-11-28
> **turinturambar said:**
> When I go to Hardware Drivers, there is no option for my graphics card.  Nothing at all.

I'm not sure exactly what happened because everything worked before the update...then I restarted and it went kablooey.

Try checking [this one]("http://ubuntuforums.org/showthread.php?t=1212509") out...

---

### Post by turinturambar on 2009-11-28
So if I understand correctly, there's an open source and proprietary driver, and the proprietary driver won't support Karmic.  So this [link]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&l ang=English") has the open source driver.

I found instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#1._Download_the_latest_Catalyst_package.") to install--I think--the open source driver.  I got as far as step 6 and then the terminal command "sudo aticonfig --initial -f" returned

"aticonfig: No supported adapters detected"

???  What do I do now?

---

### Post by adalal on 2009-11-28
> **turinturambar said:**
> So if I understand correctly, there's an open source and proprietary driver, and the proprietary driver won't support Karmic.  So this [link]("http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&l ang=English") has the open source driver.

I found instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#1._Download_the_latest_Catalyst_package.") to install--I think--the open source driver.  I got as far as step 6 and then the terminal command "sudo aticonfig --initial -f" returned

"aticonfig: No supported adapters detected"

???  What do I do now?

try with --adapter=all option...

---

### Post by turinturambar on 2009-11-28
So that would be:

"sudo aticonfig --initial -f --adapter=all"

If so, no go.  I can't even run "aticonfig --help"  I should be able to do that, shouldn't I?

In other news, in the Software Center, if I search for "ati", there is an application installed called "ATI binary X.org driver".  It claims it's proprietary.  Maybe if I uninstalled that and then tried installing the open-source one?  If that is the driver it is strange that it wouldn't be listed in Hardware Drivers...

---

### Post by adalal on 2009-11-28
> **turinturambar said:**
> So that would be:

"sudo aticonfig --initial -f --adapter=all"

If so, no go.  I can't even run "aticonfig --help"  I should be able to do that, shouldn't I?

In other news, in the Software Center, if I search for "ati", there is an application installed called "ATI binary X.org driver".  It claims it's proprietary.  Maybe if I uninstalled that and then tried installing the open-source one?  If that is the driver it is strange that it wouldn't be listed in Hardware Drivers...

Seems like the ati driver didn't install properly for some reason, beyond this, I'm out of ideas :S sorry.

---

### Post by turinturambar on 2009-11-28
So I rebooted to go into a live cd to check what the driver situation was, and again, there's no driver listed in Hardware Drivers.  The driver I was talking about in Software Center was NOT installed by default, so I figured I'd uninstall it on my laptop and go from there.

Unfortunately the login screen is replaced by a flickering command line login that only recognizes keystrokes occasionally.  Not sure what to do...If I can't find a way to login soon I will probably reinstall...

---

### Post by turinturambar on 2009-11-28
Hooray!  Problem solved!

Long story short, I deleted xorg.conf and removed everything that I had installed that related to ATI (except of course Hardware Drivers).  Compositing is back, I have my desktop cube and rain and fire-painting again!

I'm not sure exactly what happened but I think I'm using the open-source driver...

Thanks for the help!

---

### Post by u.b.u.n.t.u on 2009-11-29
> **turinturambar said:**
> So if I understand correctly, there's an open source and proprietary driver, and the proprietary driver won't support Karmic.

The default driver is open source but does not have 3d functionality. This driver works. The proprietary ATI 9.11 driver does have 3d functionality but it may not work for some GPUs.

> **turinturambar said:**
> Hooray!  Problem solved!

Long story short, I deleted xorg.conf and removed everything that I had installed that related to ATI (except of course Hardware Drivers).  Compositing is back, I have my desktop cube and rain and fire-painting again!


The drivers from ATI create an xorg.conf file. Deleting that reverts the system back to the default open source non 3d driver, VESA.

I am unsure how you have managed to delete, not have a xorg.conf file and still have 3d functionality, as such to my understanding is mutually exclusive ... xorg.conf is needed for 3d.

Anyway you say all is good and so all the best!

---

