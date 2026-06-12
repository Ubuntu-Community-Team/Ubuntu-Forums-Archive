---
title: "Verizon Wireless 3G"
date: 2011-03-09
forum: Hardware
---

### Post by hgpot on 2011-03-09
I have a laptop with a Qualcomm Gobi 2000 CMDA 3G Antenna. When I first install Ubuntu 10.10 32bit Desktop Edition, the network manager gives me options for Wi-Fi, CMDA, and Ethernet. When I connect to Wi-Fi, the other options seem to disappear, leaving me with only Wi-Fi. I would very much like to use the built-in 3G antenna (for which I have a contract with active service and an account with a Mobile Broadband Provider) on my laptop. Any thoughts?

---

### Post by nmaster on 2011-03-17
bump.  i have a similar issue on my cr-48

---

### Post by ccesare on 2011-03-18
i also have the identical issue on a cr-48.

---

### Post by nmaster on 2011-03-20
Try this: [http://www.chromeoslounge.com/cr-48-chrome-notebook/807-cr48-gobi2000-use-other-oses-4.html#post10861](http://www.chromeoslounge.com/cr-48-chrome-notebook/807-cr48-gobi2000-use-other-oses-4.html#post10861)

**STOCK ubuntu install, driver installation**

 Don't try this on the chromium-os "easy install" with  ubuntu and it sharing the filesystem, that's a whole 'nother issue. If  you have ubuntu (tested on 10.10) installed, and wiped chromium-os and  want to use the 3g follow these steps to do so:

Note if you update to a new kernel version you may have to do this again, but its simple...
Note  also if you are running a 64 bit ubuntu you will need x86 compatibility  - I cannot for the life of me remember what package that is. If you get  an error google it, its somewhere on the first four or so links.

1. Grab the files here: [https://docs.google.com/leaf?id=0Bwp...thkey=CP_tuvUJ]("https://docs.google.com/leaf?id=0Bwpoogux26tSNDQ4MDc5N2UtZWM2YS00NjQyLWIzMjctZjg2ODczZTYxNzcz&hl=en&authkey=CP_tuvUJ") [INDENT]and here: [https://docs.google.com/leaf?id=0B5q...N2UxNzhl&hl=en]("https://docs.google.com/leaf?id=0B5q4VrdHGcnQNmZlOWQ4ZDUtNTRjYy00NGE4LThmZjItMmRiYTE5N2UxNzhl&hl=en")
2. Extract the first - qcserialusb.tar.gz (wherever) and get to a bash terminal in that location.
3. Run ./installthreeg.sh
4. Run (as root) modprobe QCSerial2k and then modprobe QCUSBNet and ensure no errors appear.
5. Extract the second, qc.tar.gz to /opt.
6. Run ./startthreeg.sh (from a bash terminal or by double clicking it).
7. Create a new connection using the network manager panel app, of the mobile broadband flavor. Enter #777 for the number.
8. Connect, browse, etc.

Note you will need to run startthreeg.sh  after power has been lost (via sleep or shutdown - reboots shouldn't  need it). I set it up for CTRL+F3 to make it simple. Also later wrote a  rules.d addition for it, but I'll post that when it isn't so close to  the rooster.

Post your thoughts, etc, and have fun.[/INDENT]

---

