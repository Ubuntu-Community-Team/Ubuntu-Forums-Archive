---
title: "External display issues"
date: 2022-06-19
forum: Hardware
---

### Post by xorinzor on 2022-06-19
Hey Everyone,

Hoping someone here is able to help me, Dell support has been of absolutely no use at all unfortunately, and kept asking the same questions over and over.

I have a Dell Inspiron 7540 running Ubuntu 22.04, and am using the Dell WD18DC dock (connected via dual thunderbolt / USB-C) via which 2 displays (HP E223) are connected, both at 1080p60.

I've had Ubuntu 21.10 with the dock running flawlessly for a couple of weeks. Then the dock got a firmware update and the issues instantly started happening. The upgrade to 22.04 did not change anything, exact same behaviour.
The issue's I'm running into are:
- Screens being detected, but not turning on at all
- Screens being detected, working for a while, then sometimes randomly turn off? (Yet laptop still thinks they're connected)
- Putting the laptop to sleep, then resume a couple of hours later will often lock up the entire system showing only a couple of error messages (I'll try to add a photo of this later)

Things I've already tested / performed:
- Update all hardware firmware (including BIOS) to their latest version
- Install all available updates for Ubuntu (I do this on a daily basis)
- Test with different monitors
- Connected the dock to a different laptop that runs Windows, this seems to work without issues. (I am not able to run windows on this laptop, no 2nd drive available to install it on)
- Test on the, by dell, officially supported 18.04 LTS using a liveboot USB. Same issues.
- Test on 20.04 LTS using liveboot USB. Same issues.
- Swapped out the dock for a brand new one, came preloaded with the latest firmware unfortunately.
- Asked dell for older firmware multiple times, they kept repeating they are unable to provide me that.

Sometimes I can get the screens to turn back on by using arandr and just move the screen thats turn off a few pixels over, then apply that. Also xrandr --output <screen> --mode 1920x1080 usually works.

One of the errors that is showing up during boot / waking up out of sleep, and just repeats in the syslog over and over while the laptop is booted is:
```

Jun 19 11:56:07 LT-JORIN kernel: [ 6436.769582] [drm:lspcon_init [i915]] *ERROR* Failed to probe lspcon
Jun 19 11:56:07 LT-JORIN kernel: [ 6436.769653] [drm:lspcon_resume [i915]] *ERROR* LSPCON init failed on port D

```

Hoping someone here can help me further diagnose this issue and perhaps solve it.

---

### Post by xorinzor on 2022-06-27
After receiving more error messages about nvidia-drm I started to use different google search queries in order to try to figure out what was going on.
Eventually I started figuring out this might be having to do with the switchable graphics being poorly supported.

So today I went into my BIOS and reconfigured a few things:
- Changed Thunderbolt security from "no security" to "user authorization" (I had set this to "no security" earlier which did nothing, so I basically reverted this)
- Disabled "Switchable graphics", but left "discrete graphics mode" enabled.

As soon as I applied this, the system froze. Great sign when your own BIOS doesn't even realize it has to switch GPU's; luckely it wasn't anything a quick CTRL + ALT + DEL wouldn't fix.
After that, it started booting, got a black screen, then it rebooted and attempted booting again, this time succeeding. My guess is that because of the Thunderbolt security level change, Ubuntu had to change something internally before it was able to boot.

From the start, my screens had no issues waking up, and also the nvidia-drm modeset error messages were no longer showing up. A quick check in the terminal confirmed that only my external (nvidia) GPU is now in use.
So far, so good. I'll report back in a few days time if everything kept working properly. Hopefully this can help others with the same issue.

---

### Post by xorinzor on 2022-06-30
Happy to report I've no longer had issues with my external displays since this change.

The dock does inexplicibly sometimes disconnect my USB devices, and after a replug they work again.. but that's another kind of problem. The actual issues with the external displays via the dock seem to have been resolved by disabling the internal GPU.

---

