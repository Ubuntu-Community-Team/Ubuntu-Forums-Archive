---
title: "Trying to use a pretty old monitor along side a VERY old monitor"
date: 2016-05-15
forum: Hardware
---

### Post by RagusLive on 2016-05-15
My main monitor is a pretty old [Hyundai]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824179047") 24" screen which has worked fine enough for my use in audio editing and mixing.  I found a _*very*_ old [Samsung]("http://www.cnet.com/products/samsung-syncmaster-151v-lcd-monitor-15-series/") 15" 4:3 monitor and wanted to add it to my rig to display secondary information at whatever resolution it could muster.
I hooked them both up (DVI to the main monitor, RGB to the secondary) and they both display without any issues that were apparent upon first booting.  However, when I move a window over to the second monitor that window (namely the mixer window and/or various plugins within Ardour) is WAY too big for that screen.  If that window displays as ~18" wide on my main monitor it tries to carry that same ~18" over to a ~12" wide monitor, which is no good.
I tried to alter the resolution with the default display manager in Ubuntu but the non-default resolutions it allows you to pick only push it further in the wrong direction.

I would be happy with just some dumb brute-force "zoom out" program/function if such a thing exists, cause like I said this will only be displaying secondary information and does not need to have even a remotely high image quality.

Also, for some reason my mouse and cursor seems to have gotten much larger since integrating this secondary monitor, even though nothing else has changed on my main monitor.


If you can't tell I am not exactly an Ubuntu wiz, so please be as complete as you can with any help you may have for me on this.  Thanks!

---

### Post by Bucky Ball on 2016-05-15
*Thread moved to **Hardware**.*

May be a silly question, if so, apologies, but do you have the correct resolutions, etc., setup for each monitor in 'Display'?

If you want to get a bit more fine grained, try arandr. It is in the repos and might give you a better look at what's going on and a bit more flexibility to change it.

---

### Post by RagusLive on 2016-05-15
> **Bucky Ball said:**
> *Thread moved to **Hardware**.*
May be a silly question, if so, apologies, but do you have the correct resolutions, etc., setup for each monitor in 'Display'?
If you want to get a bit more fine grained, try arandr. It is in the repos and might give you a better look at what's going on and a bit more flexibility to change it.

Of the several options available in 'Display' the current/default one is 1024x768 and is the closest to being what I need.  The other options are 800x600, 720x400, 640x480; all of which make the windows display even larger.

Also, what are the "repos"? How do I access and interface with them?  I assume that is different from the basic Software Center?

---

### Post by Bucky Ball on 2016-05-15
No, the Software Centre uses the repos (Ubuntu repositories) to access software. You can access the repos with any package manager or even the terminal. 

If you are only getting resolutions 'close' to what the actual resolutions of the monitors are, you will continue to get problems. Generally, close enough is not good enough when it comes to screen resolutions, probably more so when you have two monitors.

Which video driver are you using? The open-source one? Please post the output of this from a terminal:

```
sudo lshw -C video
```

Please use code tags for the output (see green link in my signature below). 

Also, open Additional Drivers and see if it is offering a driver in there. If so, which? Perhaps take a screenshot.

---

### Post by RagusLive on 2016-05-15
> **Bucky Ball said:**
> No, the Software Centre uses the repos (Ubuntu repositories) to access software. You can access the repos with any package manager or even the terminal. 
If you are only getting resolutions 'close' to what the actual resolutions of the monitors are, you will continue to get problems. Generally, close enough is not good enough when it comes to screen resolutions, probably more so when you have two monitors.
Which video driver are you using? The open-source one? Please post the output of this from a terminal:
sudo lshw -C video
Please use code tags for the output (see green link in my signature below). 
Also, open Additional Drivers and see if it is offering a driver in there. If so, which? Perhaps take a screenshot.

Thank you for the clarification on the repos.  I installed arandr but it gave me the same resolution options the basic display control did.
I already looked at 'Advanced Drivers' but it came back with nothing.

What *seems* to be the case is that I am getting the correct resolution, it's just that it is the correct resolution for a monitor built in **2002**...  I linked the info that I could find on the monitors I have in my original post, some of the specs there might give some more insight than I can provide.

Here is what 'sudo lshw -C video' returns:
```
  *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:51 memory:f8400000-f87fffff memory:c0000000-cfffffff ioport:f000(size=64)
```


Like I said this monitor is OLD, as in like 14-15 years, so it isn't at all surprising to me that it displays strangely when hooked up with more modern (probably 4-5years old) hardware.
I just need a way to force it into playing nice, even if it is at the cost of image quality.

---

### Post by Bucky Ball on 2016-05-15
Can't really add much as not my area of expertise, but you might want to take a look and [read on from here]("https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:__Wrong_resolutions.2C_refresh_rates.2C_or_monitor_specs") and see if it gives any clues.

You might also [try this]("http://ubuntuforums.org/showthread.php?t=1818564&p=11121878&viewfull=1#post11121878"). It is dated but may shed some light.

* Update: [or is this of any help]("https://help.ubuntu.com/community/Unable%20to%20change%20Screen%20resolution%20in%20Ubuntu")?

---

