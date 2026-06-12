---
title: "Wireless scanner no longer detected by scangearmp"
date: 2015-12-15
forum: Hardware
---

### Post by ubifree on 2015-12-15
I have a wireless multifunction printer/scanner device which I can usually print to, or scan from, wirelessly from two different ubuntu 14.04 computers. However scangearmp has recently started to fail to detect the scanner. For example, when I click 'Update scanner list' in scangearmp it fails to detect the scanner. I can switch the printer off and on, or the computers off and on, but they still fail to detect the scanner. Wireless printing still works fine however.

I originally set up my computers as described at [http://ubuntuforums.org/showthread.php?t=2222922](http://ubuntuforums.org/showthread.php?t=2222922). This worked fine for well over a year and then, a few weeks back, the scanner failed to be detected. Then, after a week or two, it *was* detected again. Now it's no longer detected again!  Have there been recent updates to ubuntu (to cups maybe?) that are alternately breaking and fixing this functionality?  The device is a Canon Pixma MG7150.

In case it helps:
```

$ dpkg -l | grep scangear
ii  scangearmp-common                                     2.20-1                                              amd64        ScanGear MP for Linux.
ii  scangearmp-mg7100series                               2.20-1                                              amd64        ScanGear MP for Linux.

```

Has anyone else experienced a recent break like this, and does anyone know of a fix please? (Wireless scanning works fine from Windows so I doubt this is due to the printer failing.)

---

### Post by deepakdeshp on 2015-12-18
Try connecting to another computer to test the scanner . I*t may have failed, first i**intermittently*
Please try this

[https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo)

---

### Post by ubifree on 2015-12-18
@deepakdeshp: Thanks for the suggestion but, as I said in my original post, I already connect to the scanner via LAN from 2 different computers. Or at least I *could* from ubuntu 14.04 (64 bit), but not any more.  But I can still connect to it over the wifi from the same computers when they're booted into Windows (one in Vista, the other in Win 7).  Thanks for the link, but that doesn't look relevant to Canon devices and it's also pretty old, last edited over 2 years ago.

When the scanner first failed to be detected a few weeks back I also tried the solution at [http://askubuntu.com/a/281027](http://askubuntu.com/a/281027) but that didn't work (I can't remember why right now).  I see someone else had a similar problem at [http://forums.linuxmint.com/viewtopic.php?f=51&t=168021](http://forums.linuxmint.com/viewtopic.php?f=51&t=168021) : > It worked a few weeks ago, same installation. The only thing I did since then was reboot my computer.. I might ask them if they ever solved their problem...

---

### Post by ubifree on 2015-12-24
My scanner is still not detected over wifi:(. I took another look at the instructions at [http://askubuntu.com/a/281027](http://askubuntu.com/a/281027). I noticed when I did `man sane-pixma` it was dated 31 Jul **2012** (old!) and it didn't list MG7100 among the supported models. However 'PIXMA MG7100 Series' is listed as supported at [http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html), and the sane-pixma it links to [here]("http://www.sane-project.org/man/sane-pixma.5.html") is dated 30 Sep **2015** and *does* list MG7100 among the supported models. So I reckon that if I could update sane (or some other associated library?) to the later version then my scanner *would* be detected.

So does anyone know how I could update sane easily please in ubuntu 14.04?  Is there anything easier than [compiling the latest sane from source]("https://help.ubuntu.com/community/CompileSaneFromSource")? For example, does anyone [know of a ppa]("https://help.ubuntu.com/community/UpdateSaneWithPpa") that works with a Canon Pixma MG7150 over LAN?

This still doesn't explain how the scanner was detected in the past, but not recently, unless ubuntu back-levelled sane in an update for some reason.

---

### Post by weatherman2 on 2015-12-24
You could try booting an earlier kernel to see if a hardware update broke it.  Or, try booting a Ubuntu 14.04 live USB and see if you can install the Canon drivers again and see if they work.  If they do, then it's a matter of figuring out what changed - which versions of various things.

---

### Post by ubifree on 2015-12-24
Thanks for the suggestion. Yes, the scanner was detected over wifi (and scanned a document successfully) when I booted the PC into the 3.13.0-68 kernel:
```

uname -a
Linux zorro 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

but it was not detected when I booted it into the 3.13.0-70 kernel (no '69' version was listed by GRUB):```

Linux zorro 3.13.0-70-generic #113-Ubuntu SMP Mon Nov 16 18:34:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

...so at least I have a work-around for scanning over wifi other than rebooting into Windows now! (The latest version on the PC is 3.13.0-74.) But do you know how to narrow down where the break occurred within a human's lifetime?!;)

---

### Post by ubifree on 2015-12-25
I've raised a bug against the kernel: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1529232](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1529232)

---

