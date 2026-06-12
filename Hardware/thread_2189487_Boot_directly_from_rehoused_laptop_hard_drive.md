---
title: "Boot directly from rehoused laptop hard drive?"
date: 2013-11-22
forum: Hardware
---

### Post by iiullah on 2013-11-22
Hi all,

    I have kind of a wierd question that I was hoping someone might help me out with. This morning, the video card went out on my 4-year-old laptop, which is running Xubuntu 12.04. Most of my data is backed up on Ubuntu One, and the rest is mostly backed up on my once-weekly hard-backup to an external drive. However, there are several folders of data that I don't sync to U1 because they're too big, but have been modified since the last hard back-up I did.

  The laptop is too old for me to consider fixing, and I am instead thinking of just buying a cheap Chromebook to install a dual-boot of Ubuntu on (several tutorials on this floating around the nets). I did want to save the HDD out of my old laptop, however, and rehouse it as an external drive (to suplement the Chromebooks measly 16gb SSD), and it dawned on me: the OS on that drive is still completely intact. So, can I just boot up off it from another computer? In other words, if I re-house it, will it act like a 'live" usb installation of Ubuntu?

I know that it's more complicated make a dual boot on a Chromebook (have to root the thing first), but if I can just *use* my OS as it was before the old laptop died, that would _ideal_.

Many thanks for any thoughts you may give me...

---

### Post by sudodus on 2013-11-22
In principle, yes.

If you use the built in drivers, an Ubuntu based flavour or distro will be portable.

- But if you have proprietary drivers for graphics and wifi, you need to uninstall them (which is probably possible in text mode or recovery mode).

- But if UEFI cannot be switched off, it won't work. This excludes some new computers. The most general portability is for 32-bit operating systems in computers with Intel and AMD CPUs (what was called 'IBM compatible PC' once upon a time). Such a system works in 64-bit computers too, but 64-bit systems do not work in 32-bit computers.

See also the discussion in [this link]("http://ubuntuone.com/13HPbV48PmonVgkac8KK3l") at page 5 'The system was installed, not live. How can it work in another computer?'

---

### Post by iiullah on 2013-11-23
Thank you! That makes total sense... I do have the proprietary drivers running, and it is 64 bit. Ive got a few 64 bit desktop machines with similar hardware, so I might try to see if I can boot the disk on one of those, and "dumb" it down to a state that might work on the lower-end hard ware of a chrome book or other cheap laptop... Many thanks!

---

### Post by sudodus on 2013-11-23
Good luck :-)

---

### Post by iiullah on 2013-11-26
Just placed the orders for the external HDD enclosure and the Chromebook (Acer C720). Looks like the C720 supports legacy boot mode, and I've read multiple reports confirming it boots a live USB just fine. Also read that there are kernel patches that can be applied to get all the hardware working (and done up in a nice script too!), so I'm hoping it'll all work out well. Once I get the HDD enclosure, I'll try booting it up on one of my desktops, and then will go to town removing all proprietary drivers! Any other advice for "generalizing" the install?

I'll keep this thread updated with my progress in case there are other interested parties who find this info useful...

---

### Post by iiullah on 2013-12-03
So, just reporting back on stage 1: Success! I rehoused the HDD from the old laptop (used a USB 3.0 housing from Orico), and was able to boot one of my desktops off it with no trouble at all! In fact, I'm typing from within my old OS right now! Everything is *exactly* the way it was on my old laptop, and there seemed to be no issue with the drivers (although the desktop did also have an AMD GPU). I've been able to uninstall the proprietary drivers for the graphics, and get rid of all the non-standard system stuff that I can think of (mostly a set of laptop-specific drivers from System 76, where I bought the old laptop), so it *should* now be a pretty vanilla install of 12.04. 

Now for the harder part: getting the chromebook to play along. Instructions are to put the thing in "developer mode", which entales wiping all the data and settings. No issues there, because it's a brand new machine with nothing on it. According to the instructions I've found, booting from a USB drive is simply a matter of pressing Ctrl-U on start up... Seems easy. The issue, however, is whether I want to ALSO be able boot it to some sort of OS *without* the external plugged in (which would be pretty handy, since it *is* a laptop!). I think I have to kiss Chrome OS goodbye, because it seems like google has configured it so that it simply gets wiped if you try to load another OS (whether from an internal partion or not). Hence why the "Crouton" script to run Ubuntu on top of Chromeos was made. What is unclear to me is whether or not I can install ChrUbuntu to the internal SSD and *still* boot from the USB at start up. I _think_ it's possible, but I suppose I have to experiment. I've got some questions posted to other relevant message boards, so i'll wait to hear back about them before I do anything...

---

### Post by sudodus on 2013-12-03
Thanks for sharing :-)

---

### Post by iiullah on 2013-12-03
You are quite welcome!

FWIW, I've done the "developer mode" thing to the Chromebook, and it does indeed boot the disk (although bootup is pretty slow). Once booted, it runs very well. Nice and snappy! touchpad doesn't work, but that was a known issue. I'm trying to download and install some kernel patches to fix that, so we'll see how that goes. For the time being I can use a USB mouse just fine.

 It turns out that I can boot into ChromeOS in developer mode, and give it all my google credentials. As long as I keep the chromebook in developer mode, it keeps all my google info, so it really is a dual boot for the time being... Looks like there are a lot of options on how to proceed. Perhaps the best one is to buy a larger SSD (there's a compatible 128 M2 SSD on Amazon for $99), and to just install a full Xubuntu, then copy all my files and download all the programs I use to it. That would make it a full-fledged linux laptop, and I could still boot off my external from time to time, or simply just use it as backup storage...

Here's a really good guide that I found, and will be following as I get this thing up and configured: [http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/](http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/)

All in all, I'd say pretty much success on all fronts at this point. Some minor issues to be ironed out, and I've got to think what my best options are moving forward, but I think this is a VERY workable solution. The little chromeboook seems like it's going to be one hell of a mobile linux solution for me! :)

---

### Post by iiullah on 2013-12-05
Well, at the risk of sounding like one hand clapping, I thought I'd quickly add a post about what I've decided to do, now that I've had a couple of days of playing around with both the rehoused drive and the chromebook. First, the kernel patches don't work for 12.04, so unless I upgrade the OS on my now-external drive to 13.10, I'm relegated to using a USB mouse on the chromebook. Second, although the rehoused drive is very small and light, I've realized that having an external drive dangling from the chromebook at all times really defies the point of having a chromebook (it's a small, light, and yet pretty fast little laptop). However, the native 16GB ssd is just too small for it to be worth using the chromebook as your #1 computer on a daily basis. Sooo... the only real solution was to buy the $99 128gb replacement drive for it, and that's what I've done. I know that it'll void my warranty, but there really seems to be no other practical solution. That means that I'll have spent a total of about $350 on this machine, which is still a really good price for it. 

So now, the next decision I have to make is do I keep ChomeOS on a small partition, and dual boot ChrUbuntu? Or do I just do a straight install of 13.10 from an official ISO, and apply the kernel patches to make everything work? ChromeOS is kinda cool, but after using it a little while, it really doesn't seem to hold any benefits other than that all the "cool new hotkeys" of the chromebook work with it, and the trackpad gestures are also cool. However, I could still just install the Chrome browser in 13.10, and have access to all my Chrome apps and google stuff with no issues. As you can see, I'm leaning towards the straight install of 13.10! :) 

Either way, I'll be transfering all my data to the new SSD of the chromebook, but not wipeing my rehoused drive. Instead, I'll still use it to boot one of my workstations at the lab, so that I can still use my old version of 12.04, with all it's software. I'll need to take more strategic advantage of UbuntuOne to keep everything synced, but I think it'll be an eminently workable solution. This is even more practical, because I'm a post-doc, and will be leaving this position in a year's time. If I use my external as my main lab OS, then all my stuff is easily tranportable to my next position with 0 transition time. That's a huge benefit! Also, for what it's worth, although it takes a pretty long time to boot the chromebook off of the external, it takes only negligably longer than normal to boot the workstation off of the external, and it only has USB 2.0!

I'll likely be posting one more follow up post when the new SSD arrives, so if anyone out there is follwoing this thread, stay tuned! :)

---

### Post by iiullah on 2013-12-19
Well, here's my last and final follow up: it all has worked out brilliantly! For those that find this thread because they bought a C720 and want to put Ubuntu/Xubuntu on it, head on over to this Reddit thread, where full guide to all that you'll need to do is being curated: [http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/](http://www.reddit.com/r/chrubuntu/comments/1rsxkd/list_of_fixes_for_xubuntu_1310_on_the_acer_c720/) Several users (including myself) have contributed a list of "fixes" needed to get a fully functional (and might I say, *very* zippy) install of Xubuntu 13.10 up and running on an Acer C720 Chromebook. Enjoy!

---

