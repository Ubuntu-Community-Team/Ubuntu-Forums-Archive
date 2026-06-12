---
title: "Install Ubuntu on Samsung Series 7 Slate (dual boot with Windows)"
date: 2011-12-07
forum: Hardware
---

### Post by AussieDave on 2011-12-07
Hello.

I'm looking at buying a Samsung Series 7 Slate. Whilst I am mainly a Windows user, I'd like to be able to use Linux occasionally. Will it be possible to do a dual boot install of Ubuntu with Windows on this machince? I have done dual boots on my computers before without many issues so should I expect some here?

I'm also interested in using the Windows 8 developer preview. Would that change things at all?

Any tips/knowledge/experience would be greatly appreciated.

---

### Post by Mark Phelps on 2011-12-07
> **AussieDave said:**
> Hello.

I'm looking at buying a Samsung Series 7 Slate. Whilst I am mainly a Windows user, I'd like to be able to use Linux occasionally. Will it be possible to do a dual boot install of Ubuntu with Windows on this machince? I have done dual boots on my computers before without many issues so should I expect some here?
Unless someone here has actually tried this on this machine, you would really need to boot into an Ubuntu Desktop CD and see how well it works.  If there is no way to boot from a CD drive, then check out "unetbootin" to see how to make a bootable USB stick -- and use that.

> I'm also interested in using the Windows 8 developer preview. Would that change things at all?
Actually -- quite a lot.

I've been using the Win8DP and believe me, when they call it a pre-alpha, they mean it!  It's OK to experiment with, but the Beta is coming out late February, it most likely will NOT upgrade from the DP, and it's going to be different enough that it will bear little resemblence to the DP.

If you want to read about actual experiences with the Win8DP (BEFORE you use it), then go to the Windows 8 forum: eightforums.com.

Also, as far as I know, Wubi does NOT work with Win8 -- so  that's not an option.

If you do decide to dual-boot, then do NOT use the Ubuntu installer to shrink the Win7 OS in side-by-side mode. Doing this risks corrupting the Win7 OS partition and rendering it unbootable.  Instead, use the Win7 Disk Management utility to shrink the partition.  Then, reboot into Win7 a couple of times to allow the filesystem to make any adjustments.

When in Win7 Disk Management, check to see how many partitions exist on the Slate.  If you already have the maximum of 4 partitions, you can't create anymore -- and you will have a LOT of work ahead of you to install Ubuntu.  Don't try forcing the creation of another partition because, if you do, you'll convert your partitions into Dynamic Disks -- causing you even more grief.

---

### Post by nickelpro on 2011-12-08
(Non Ubuntu user, and I haven't tested with Ubuntu)
I have a Samsung Series 7 slate, and I suspect most distros run fine on it. So far I've tried Arch and Fedora

Unfortunately, the drivers for the Atmel touchscreen and Wacom digitizer aren't upstream yet. The touchscreen tries to use a generic mouse driver and the 
digitizer doesn't work at all. It's not hard to write or patch the code for the drivers and compile yourself ([http://comments.gmane.org/gmane.linux.drivers.wacom/6159](http://comments.gmane.org/gmane.linux.drivers.wacom/6159) 
It's mostly just a matter of entering the device ID and some parameters), but if you're uncomfortable doing that than I would wait a couple months before 
installing Linux once the drivers propagate downstream.

---

### Post by latchr on 2012-01-05
I recently purchased a Samsung Series 7 Slate, and have put Ubuntu on it.  Firstly I tried the current release 11.10.

The Wacom stylus didn't work at all.  I modified wacom_wac.c and compiled my own kernel as suggested in [http://comments.gmane.org/gmane.linux.drivers.wacom/6159](http://comments.gmane.org/gmane.linux.drivers.wacom/6159) but this didn't fix it.  I probably did something wrong manually editing the kernel driver.  I tried the daily build of Ubuntu 12.04, and the pen worked perfectly.

With 11.04 the touchscreen did work, but like a trackpad (the cursor moved as I moved my finger, but the cursor was not at my finger position).  I was able to make it work like a touchscreen by using the xinput ABSOLUTE command mentioned in the thread I linked to above.

However, there was still some strange behaviour.  Leaving the cursor over a window caused the window to scroll up continuously, even without any touch on the screen.  Somewhere I read that the trackpad behaviour was due to it pulling in the Synaptic driver rather than the proper touchscreen driver, so perhaps there was some spurious keypress event being registered by the Synaptic driver.

[https://wiki.ubuntu.com/Multitouch/HardwareSupport](https://wiki.ubuntu.com/Multitouch/HardwareSupport) says that 12.04 does have support for the Atmel touch.  My installation of 12.04 fixed the Wacom pen as I said, but the touchscreen does not work at all.  It is not even listed in xinput -list, so I'm sure the problem must be at the kernel.  I am trying to find out more about the testing that was done to list it as supported in 12.04, but have not found anything yet.

I'm sticking with 12.04 at the moment and using the stylus.  The volume buttons work, but the screen rotation and the "start" button do not seem to be registered at all.  Everything else seems to work nicely.

This is still quite new hardware, so I'm assuming that support will come.  I'd say by the time Ubuntu 12.04 is properly released it should work on this slate.

---

### Post by buda81 on 2012-04-07
Hi, I'm having an issue with the usb boot of Ubuntu 12.04 on the S7S. I've used both unetbootin and the usb installer. everytime I choose to run ubuntu off the usb the screen goes black and nothing loads. waited for 20 min. and still nothing. any ideas on how to solve this?

---

### Post by de1nonly on 2012-05-02
If it is in the dock my screen stays black.  Just pulling it out fixed my problem.

---

