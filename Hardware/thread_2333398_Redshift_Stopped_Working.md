---
title: "Redshift Stopped Working"
date: 2016-08-09
forum: Hardware
---

### Post by joelbitar1986 on 2016-08-09
Ubuntu 16.04:

Redshift is a program that changes the gamma levels/screen temperature of your screen when it gets late. It's been working for me for the past month and it stopped working today seemingly out of the blue. The Redshift site says the following:

>  Certain **video drivers** do not support adjustable gamma ramps. In some cases Redshift will fail with an error message, but other drivers silently ignore adjustments to the gamma ramp.

I am not getting any error messages when I manually attempted to change the gamma ramps with Redshift, it's just not executing my commands. This leads me to believe it's most likely a graphical issue, something with the video drivers. I am on a laptop with onboard video. The driver that I have in 'additional drivers' is currently listed as:

'Using processor microcode for Intel CPU's from intel-microcode (proprietary)'

I've uninstalled redshift and reinstalled but still no luck. My only guess is that the graphics drivers got changed on my system. How can I revert back to the default graphics settings when installing Ubuntu?

Thanks,

---

### Post by papibe on 2016-08-09
Hi joelbitar1986.

Could you open a terminal, run these commands, and paste back the results? (you can copy/paste the text):
```
redshift -V

apt-cache policy redshift
```
Regards.

---

### Post by joelbitar1986 on 2016-08-10
redshift -V:

> redshift 1.10

apt-cache policy redshift:

> redshift:
  Installed: 1.10-5ubuntu1
  Candidate: 1.10-5ubuntu1
  Version table:
 *** 1.10-5ubuntu1 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status

I'm less inclined to think it is a driver issue now, it seems to be an issue with randr. When I manually set the color temperature with redshift there is no effect.

> redshift -O 5500:
Using method `randr'.

Then no effect...

P.S. Also realize now that this probably shouldn't be in the hardware section of the forums, apologies...

---

### Post by sadboy2 on 2016-08-10
Same here, on Intel Sky Lake integrated graphics (i915-bpo). Culprit is the 4.4.0-34-generic kernel. Booting the old 4.4.0-31-generic kernel fixes the problem.

---

### Post by joelbitar1986 on 2016-08-11
Thanks for that info! I booted up the previous kernel and it is indeed working again. How can we go about submitting a bug report?

---

### Post by papibe on 2016-08-11
> **sadboy2 said:**
> Same here, on Intel Sky Lake integrated graphics (i915-bpo). Culprit is the 4.4.0-34-generic kernel. Booting the old 4.4.0-31-generic kernel fixes the problem.
Thanks for the info sadboy2.
> **joelbitar1986 said:**
> How can we go about submitting a bug report?
[Here]("https://help.ubuntu.com/community/ReportingBugs")'s how.

Regards.

---

### Post by Bashing-om on 2016-08-13
Hey all ;

What worked for me when redhift did not function with the latest kernel:
```

sudo apt install --reinstall redshift

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by conwrite on 2016-08-22
> **sadboy2 said:**
> Same here, on Intel Sky Lake integrated graphics  (i915-bpo). Culprit is the 4.4.0-34-generic kernel. Booting the old  4.4.0-31-generic kernel fixes the problem.

Thanks very much for this information, I've been searching all over for a  solution -- Madness can be restrained for a bit longer.

---

### Post by jimmyjx51 on 2016-08-27
> **Bashing-om said:**
> Hey all ;

What worked for me when redhift did not function with the latest kernel:
```

sudo apt install --reinstall redshift

```
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


That doesn't seem to have worked in my case. I've already filed a bug report at [https://bugs.launchpad.net/launchpad/+bug/1617686](https://bugs.launchpad.net/launchpad/+bug/1617686)

---

