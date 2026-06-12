---
title: "Messed up synaptic"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by afderrick on 2009-06-07
So I was trying to downgrade from 9.04 to 8.10 because i have had nothing but problems with this distro.  It failed, but part of what I had to do was mess with my sources.list file.

Now when I try to install or open up Synaptic I receive an error message:

```
E: Invalid record in the preferences file, no Package header
E: _cache->open() failed, please report.
```

I looked at my sources.list and removed everything that I had added and included everything I deleted to no avail.  Anyone know of a good fix for me?  

On a side note, I have an 8.10 disc now, so I may try and re-install from the disk, but having to reinstall all my programs is going to suck.

---

### Post by merlinus on 2009-06-07
Did you try:

```

sudo apt-get update

```

---

### Post by albinootje on 2009-06-07
> **afderrick said:**
> So I was trying to downgrade from 9.04 to 8.10 because i have had nothing but problems with this distro. 

Downgrading is not supported, and will also fail most probably in most cases (if only because of the different libc version).

What you can do is "save markings" in Synaptic PM. 
And use that resulting markings text file to reinstall your applications ... after a fresh reinstall of 8.10

You can do that also in the console or terminal like this :
```

dpkg --get-selections > markings.txt

```
Save it to usb-stick or email to yourself etc.

You probably need to tweak that file afterwards before "importing" it into Synaptic PM, e.g. removing lines of libraries that have different numbers, but it can be done. (I did it, so you can do it too!)

---

### Post by afderrick on 2009-06-07
Yeah, I'm in the process of updating my 8.10 install.  That I, for some reason, cannot connect to my wireless router that has a hidden ID, WPA, and MAC address filtering on it.  I don't think it's Ubuntu since I just installed 8.10 on the laptop and connected without issue.

---

### Post by ORBstacle on 2009-11-15
[http://ubuntuforums.org/showthread.php?t=453824](http://ubuntuforums.org/showthread.php?t=453824)

---

