---
title: "Radeon Hd 7750 ATI Propriety Drivers not recognizing kernel headers"
date: 2012-12-01
forum: Hardware
---

### Post by rybateman on 2012-12-01
Hey guys,

I've been running into a consistent problem on a new 12.10 install where I can't get the proprietary drivers running for my Radeon HD 7750 graphics card. I've installed the fglrx and fglrx-updates packages through apt a number of times with no luck. Like many others with this problem, I'm able to login but I just don't get the unity interface or compiz, but I can get to terminal, etc.

I have also tried installing the 12.9, 12.10, and 12.11 beta drivers from AMD's website with no avail. However, when I run the installer for the 12.10 drivers it gives me a dialogue that says "one or more tools required for installation cannot be found on the system."

Tracing that to /usr/share/ati/fglrx-install.log gives me the following:

```
Supported adapter detected. check if the system has the tools required for installation. 
Check if the system has the tools required for installation. 
flgrx installation requires that the system have kernel headers. 
/lib/modules/3.7.0-4-generic/build/include/linux/version.h cannot be found on this system.
```

So I went ahead and tried to run ```
sudo apt-get install linux-headers-generic
``` but it tells me I"ve got the current version.

Running ```
uname -a
``` outputs ```
Linux ryan-ubuntu 3.7.0-4generic #12-Ubuntu SMP Wed Nov 28 09:30:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

So what is going on here? I tried forcing a reinstall of the kernel headers and I still get the same problem. Why won't the drivers recognize my headers? Is that problem even related to the unity/compiz issues on boot-up?

Thanks in advance for the help.

---

### Post by Jydskatomkraft on 2012-12-10
I got exactly the same problem as above with ATI HD 5870 installed.

Linux 3.7.0-4-generic #12-Ubuntu SMP Wed Nov 28 09:30:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Driver won't recognize 3.7.0-4-generic headers >_<

---

### Post by rybateman on 2013-01-13
I eventually went ahead switched back to 12.04 to get the Catalyst 12.11 beta drivers working properly because I've been running the Steam Beta on my machine and really needed the drivers to be working properly.

Nonetheless, I'm still interested in any solutions you guys might have, so I'm giving this a bump. I'd like to make my way to 12.10 eventually.

---

### Post by rybateman on 2013-01-15
I was able to find a workaround for my problem. Hopefully this will be helpful for everyone else.

As I mentioned in a prior post, I moved back to 12.04. I then installed the proprietary Catalyst 12.11 beta drivers from source (see the AMD website/wiki for instructions).

At that point I had everything working as needed - I have been in the Steam Linux beta and I was able to get really good performance in TF2.

Then today I was browsing the Steam Linux Beta forums and found [this post]("http://steamcommunity.com/app/221410/discussions/0/846940248705614457/#c846940248845761681") in which a Steam user describes how he got around the AMD driver problem on Quantal. Of course I tried updating the headers like he said, but it didn't work (as I also mentioned in an above post).

But I got hung up on one thing he said: "The guys that are making the Ubuntu 12.10 ISO file had forgotten to slipstream the linux-headers-generic package in the ISO."

So I thought that perhaps if the problem is only in the way that ISO is being bundled and the headers not being slipstreamed, perhaps I could just upgrade through Software Update and see if the problem remained.

When I booted into 12.10, the graphics enabled and compiz turned on, and I was able to see the interface. I checked my graphics drivers and it still showed me using AMD proprietary (fglrx).

**So, long story short: it would seem that if you upgrade through Software Update from a working 12.04 install with fglrx installed, the drivers will persist through the upgrade process.**

Hopefully this helps, and let me know if anybody else can replicate my process!

---

