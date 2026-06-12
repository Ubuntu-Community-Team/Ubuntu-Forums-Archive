---
title: "Install hung and never cleanly starts"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by Roper on 2009-03-09
Hello All,

Heard about Ubuntu last Friday from my boss.  After many frustrating years working with Windows, could not wait to give Ubuntu a try.  Downloaded ubuntu-8.10-desktop-i386.iso, downloaded and installed winMD5Sum, preformed the hash check, then downloaded and installed Infra Recorder. Hash checked out OK.  I created a Ubuntu DVD using Infra Recorder  

Put the DVD in the drive and restarted.  This is where things started to go wrong.  The Ubuntu logo came up with the status bar.  The status bar stopped.  After a few minutes I tapped the CNTL key and the status bar began moving.  Then stopped again.  Tapped the CNTL key and the status bar began moving.  This happened 5 or 6 times. Eventually the Ubuntu menu came up.  I selected the "Check CD...." option.  It was fine.  I then selected the "Memory Test..." option.  It was fine.  I then selected "Install...."  No dual boot, no partitions, just format the entire hard drive and intall Ubuntu.  After some time the install finished.  Screen said to take out the DVD, close the drive, press enter to restart.  I did this.  The Ubuntu background came up with the status bar.  The status bar stopped.  After a few minutes I tapped the CNTL key and the status bar began moving.  Then stopped again.  Tapped the CNTL key and the status bar began moving.  This happened 5 or 6 times.  (Sound familiar)?  Eventually Ubuntu loaded and began the configuration. Finished all of this.  Looks and runs great.  I'm really imopressed!

The problem is, Ubuntu will never just start.  When starting, the status bar will hang until I press a key a few times. I even let the machine sit there in this state for two hours.  Nothing until I press a key a few times.

Uninstalled and re-installed Ubuntu 4 times.  Same results.

Where is what I have:
- HP Pavillon dv9925nr notebook with 4 GB of memeory, 250 GB hard drive.  The notebook had Vista on it.

I feel this is not a clean install.  With the hanging at the beginning of the installation, something is wrong.  After all of this, I have not spent a lot of time with Ubuntu.  What time I did spend, Ubuntu looks good.

Any Ideas on what I should try to get a clean install which will enable Ubuntu to start correctly?

Thank You very much
Steve

---

### Post by avtolle on 2009-03-09
IMO, you have a clean install. The problem you are having with the "hang" is common to at least HP and Compaq laptops, with the kernel used in 8.10 (and Linux Mint 6, and openSUSE 11.1, all in my expereince).

I just hit the power key once at the first hang, and on my Compaq Presarion F750US laptop, the boot process completes with no further intervention on my part. I also had tried the control key, and found that I had to continue to press it at various times, but when hitting the power key, once is all it takes.

To my knowledge, there is no fix as such. There is a workaround that has been posted before, but it is simple enough for me to hit the power key just once and it goes on, with no problems once it has booted. Good luck.

---

### Post by Roper on 2009-03-09
Thank You.  

Power Key?

---

### Post by avtolle on 2009-03-09
My bad. Power button (on off switch, but don't turn it off; just press it once).

---

### Post by wpshooter on 2009-03-09
Have you tried installing Ubuntu from the ALTERNATE (text based) CD version ?

---

### Post by avtolle on 2009-03-09
> **wpshooter said:**
> Have you tried installing Ubuntu from the ALTERNATE (text based) CD version ?
Same problem once installed. It is the kernel and an issue with some proprietary "thing" with HP/Compaq, as nearly as I can ascertain.

---

