---
title: "How to tweak your Thinkpad t60 after installing Oneiric Ocelot 11.10"
date: 2011-10-12
forum: Hardware
---

### Post by kolinab on 2011-10-12
If you're running an older version of Ubuntu, check [How I tweak my Thinkpad t60 after installing Ubuntu Maverick 10.10]("http://ubuntuforums.org/showthread.php?t=1681672").

I cannot take credit for any of the tweaks applied here - most solutions have been found either here, [Thinkwiki]("http://www.thinkwiki.org/wiki/Category:T60") or elsewhere on the web. Many adjustments require a restart or logout to take  effect and may not be optimal nor elegant. They  work for me. Where possible, I have tried to show a command line solution.

I am picky  about getting everything running properly when I upgrade my Ubuntu. I  choose a clean install and use a separate partition for /home. When  upgrading, I only keep data directories in my home partition - not  application preferences. Before upgrading, I first make a complete backup of my /home partition.  Once or twice I have been thankful for it. Since I reinstall my  applications, there are only a few hidden folders in /home that I preserve. I don't mind setting up  program preferences again, but if you want to keep your preferences, you can  probably safely leave the hidden directories on your /home partition alone.

**Tweaks applied to clean install of Ubuntu Oneiric Ocelot 11.10 on my IBM Thinkpad t60:** (Type 2007-72U)

[U][B]Thinkpad specific modifications
[/B][/U][B]
Make the middle mouse button work as a scroll button with the trackpoint:[/B]

This seems to work out of the box in 11.10. Hooray!

**Enable the volume control buttons:**

```
sudo gedit /etc/rc.local
```and add the line:

```
cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask  /sys/devices/platform/thinkpad_acpi/hotkey_mask 
```**Enable Thinkpad Active Protection System**:

This is supposed to enable hard drive parking when the laptop is moved, as well as some other Thinkpad specific features.

```
sudo apt-get install hdapsd tp-smapi-dkms
```**Map the ThinkVantage button to some useful function:** 

I use mine to launch a terminal window.

Go to: Dash . . . Keyboard . . . Shortcuts . . . Custom Shortcuts

Click Add (+) . . . and name the button 'Launch Terminal.' In the 'command' box type: gnome-terminal

Now highlight this new entry (click and hold on the label 'disabled'), then push  the ThinkVantage button. This  should successfully map the button to  launch a terminal window. You  can adapt this process  to launch any application you like.

**Set blue bluetooth default to 'off' on startup:**

```
sudo gedit /etc/rc.local 
```and add the line:

```
rfkill block bluetooth
```Save and close.

Make sure to restart in order for all changes to take effect.

Good luck with your tweaks: post what works or doesn't work for your  Thinkpad. If you have a better solution to any of the above problems or additional t60 tweaks please share!

I will edit this post as necessary as I get more familiar with Oneiric.

Kolin

[edit] April 12, 2012 - I experience a major sound problem on this system which has a bug report here: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370). This held me back to 11.04 for a long time, but my final workaround which avoids this sound trouble is selecting the unity2d session at login. I suppose I lose a bit in visual flash but I retain usable sound. We'll see what 12.04 brings.

---

### Post by zob on 2011-11-05
Thanks for sharing Kolin, it's a great help.:D

You could (once again) add the link to thinkwiki if you feel for it.

---

### Post by kolinab on 2011-11-06
I'm glad it helped!

Yeah, I should. Thanks for the reminder. I'll head over there soon. I've neglected this thread because I ended up rolling back to 11.04 because of a so far unresolved audio problem. I won't give up :)

---

### Post by zob on 2011-11-09
Do you have an audio problem with your T60??

That's strange. I have never had audio problems with this machine, except of course, for the volume buttons.

Maybe you should try to test it without the volume button fix. Becuase you could have turned the hardware volume control down (that's the one that is working independently of the software volume control if you don't apply the fix - then having applied the fix, you couldn't actually turn up the hardware volume control - I think....)

And also check
```
alsamixer
```

---

### Post by scottbomb on 2011-11-10
I asked this in it's own thread [http://ubuntuforums.org/showthread.php?t=1876810](http://ubuntuforums.org/showthread.php?t=1876810) but since no one seems to have any answers or suggestions, I thought I might post it in this thread in the hope that someone who is familiar with the T60 might have some insight.

I am running Xubuntu 11.10 on a Thinkpad T60. Using "pcie_aspm=force" in grub, I see the following that would suggest the command doesn't work:

[ 0.000000] PCIe ASPM is forcedly enabled

Then later on...

[ 0.249577] ACPI _OSC control for PCIe not granted, disabling ASPM

This machine typically fluctuates between 10 and 27 watts according to powertop, even with the other suggested grub entries (i915.i915_enable_rc6=1 & i915.i915_enable_fbc=1 and i915.lvds_downclock=1).

Any ideas?

---

### Post by kolinab on 2011-11-10
Yes, unfortunately I'm experiencing garbled audio quality caused by raising a few screens, then occasionally persists until a restart. I've filed a bug report and it might be graphics driver related:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/873370)

I've also poked around in alsamixer and haven't seen anything out of the ordinary. 

Anyway the whole thing runs wonderfully on 11.04 so I'll happily run that for a while until I have more time to troubleshoot some of those little problems. 

@scottbomb - Sorry, I don't have any experience with the problem you're having!

---

### Post by danielbu on 2012-01-21
thanks, I was wondering about this. If I use the hardware buttons, I see a nice blue line like on a TV at the bottom showing my mute status, volume, brightness, etc. But If I use the GUI mute or volume control in UNITY, then the hardware buttons don't work.

---

### Post by kolinab on 2012-01-29
Hi zob: Somehow long ago I missed your suggestion to try the sound before applying the volume buttons fix. I should have tried that long ago. The bug reports over on launchpad don't seem to be getting much action and I suspect what I'll end up doing is skipping over Natty anyway (just a few months until Precise anyway) and test how 12.04 is before getting to excited. 

I'm glad to see these tweaks are useful to some people!

---

