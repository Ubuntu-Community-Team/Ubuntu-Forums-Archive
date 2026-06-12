---
title: "[SOLVED] Changing this hard drive to another box"
date: 2008-09-08
forum: General Help
---

### Post by DougieFresh4U on 2008-09-08
I want to put this hard drive I use now into another machine. The current machine is a real old Intel Celereon with the i810 chipset.
I am not sure what chip set is in this newer  Intel machine. It has no hard drive currently. The thing that worries me, when I put this HD in, am I bound to have a broken x upon start up? This hard drive has Ibex but like I stated, it's set for i810 intel. Will hard drive make adjustments on start up. 
I really need some one to guide me on this before I end up with a broken machine

---

### Post by mb_webguy on 2008-09-08
You may possibly have more problems than that.  If I were you, I'd just back up all my data and reinstall Ubuntu on the new machine after you install the hard drive.

However, if you want to leave everything intact, I'd suggest booting from the LiveCD and updating the GRUB entry before booting from the hard drive.  Then boot into recovery mode and reconfigure X.  Then you *should* be able to boot into Ubuntu normally.

---

### Post by ryanhaigh on 2008-09-08
Actually moving an ubuntu install to a new PC is rather simple, especially if you don't have a Nvidia or ATI graphics card. If you are concerned about X not starting, re-configure the graphics system on the current install to use the vesa driver at a low resolution.

The other thing that you might notice is that your network card will be called something different (if it was eth0 the new one will be eth1). If this bothers you just remove the entry from /etc/iftab

---

### Post by DougieFresh4U on 2008-09-09
Was told today that new box has the i865. Will I see much of a difference?
I went into Synaptic to find it but all I see is i810 and then a bunch of i8xx which are all installed. Also vesa is already installed.
I am quite confused about how to proceed with the swap I want to do.

---

### Post by Tanker Bob on 2008-09-09
When I built my latest box over a year ago, I [transferred over two hard drives](http://www.mobiletechreview.com/ubbthreads/showflat.php?Cat=0&Number=27345&an=0&page=0#Post27345), one with Kubuntu Gutsy on it and the other with WinXP Pro. I booted the new machine with kubuntu first. The boot took a little bit longer than normal, but it booted just fine. It was totally transparent--and I have an NVida card. After it booted to a generic vesa display on its own, I used Envy to update the NVidia drivers. My only problem was caused by using an old version of Envy. Once I downloaded the current version, everything went fine. In retrospect, it would have been prudent to set the display to vesa before swapping the drive just in case.

The WinXP drive was another story. It refused to boot even in safe mode. I had to eventually [reinstall WinXP on it to get it running](http://www.mobiletechreview.com/ubbthreads/showflat.php?Cat=0&Number=27604&an=0&page=0#Post27604). That was over a year ago and I haven't booted the XP drive since fixing it.

Although you should always back up your data before making any large change, you should be able to plug your Ubuntu drive in the new computer and boot off of it without serious problems.

---

### Post by DougieFresh4U on 2008-09-09
> **Tanker Bob said:**
> When I built my latest box over a year ago, I [transferred over two hard drives](http://www.mobiletechreview.com/ubbthreads/showflat.php?Cat=0&Number=27345&an=0&page=0#Post27345), one with Kubuntu Gutsy on it and the other with WinXP Pro. I booted the new machine with kubuntu first. The boot took a little bit longer than normal, but it booted just fine. It was totally transparent--and I have an NVida card. After it booted to a generic vesa display on its own, I used Envy to update the NVidia drivers. My only problem was caused by using an old version of Envy. Once I downloaded the current version, everything went fine. In retrospect, it would have been prudent to set the display to vesa before swapping the drive just in case.

The WinXP drive was another story. It refused to boot even in safe mode. I had to eventually [reinstall WinXP on it to get it running](http://www.mobiletechreview.com/ubbthreads/showflat.php?Cat=0&Number=27604&an=0&page=0#Post27604). That was over a year ago and I haven't booted the XP drive since fixing it.

Although you should always back up your data before making any large change, you should be able to plug your Ubuntu drive in the new computer and boot off of it without serious problems.

Thanks for your input.
Two questions, do uninstall the i810 or just leave it? Also vesa is installed already so how do I get it to recognize it?

---

### Post by Tanker Bob on 2008-09-09
> **DougieFresh4U said:**
> Thanks for your input.
Two questions, do uninstall the i810 or just leave it? Also vesa is installed already so how do I get it to recognize it?
I'd leave the basic system as is, changing only the video driver.

You can change the video driver in the setup screen for your display. Edit the hardware setup, choosing vesa from the pull-down list box. I'm using Kubuntu, so don't know the exact sequence for Gnome. I assume that it's under system administration or something like that.

Alternately, you can edit the /etc/X11/xorg.conf file directly. Change the Driver entry to vesa. You can also change the Device and Identifier entries to Generic or Vesa if you want. Then restart X to make sure that the changes took OK.

---

### Post by DougieFresh4U on 2008-09-09
Unbelievable!! Ibex is great (Ubuntu also) 
I just put hard drive in and turned on machine and booted right up. 
Of course screen res was messed up. It gave me more choices as other box would only get 800x600 and now I have many more to pick.
Thanks for support

---

### Post by Tanker Bob on 2008-09-09
You're welcome. I'm glad that it worked out for you. Enjoy the freedom!

---

