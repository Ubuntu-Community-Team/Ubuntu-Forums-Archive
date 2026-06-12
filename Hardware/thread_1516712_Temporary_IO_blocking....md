---
title: "Temporary I/O blocking..."
date: 2010-06-24
forum: Hardware
---

### Post by ectospasm on 2010-06-24
I'm having trouble with I/O apparently blocking, causing system unresponsiveness for a few moments, especially on startup.  I just upgraded this system to Lucid from Karmic 
```
Intel Core2 Quad CPU Q9550@2.83GHz
Mem: 8193640k total 
IDE Controller:  Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller
Hard Drive:  Western Digital 1TB HD in UDMA6

```

Basically the hard drive light will go solid on for several moments, and the computer will be nearly unresponsive.  I can move windows, minimize, etc. (basically anything that can be done via RAM and not HD) OK, but anything that requires the HD to be read will block until whatever it is consuming that I/O finishes.  Then the problem goes away and everything is normal (until it happens again).  Even simple things like terminal console command and filename completion will block until this problem subsides.  I've also noticed that it seems to be worse when my uptime is low, leading me to believe I reach a sort of equilibrium with loaded software where it doesn't seem to be an issue.

I ran hdparm tests, and my numbers appear to be respectable, so I don't think it's a problem with the hard drive or it's settings.  Here's the output, in case I'm misinterpreting things:

```
meth:~ # hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   11910 MB in  2.00 seconds = 5960.44 MB/sec
 Timing buffered disk reads:  310 MB in  3.06 seconds = 101.24 MB/sec

```

S.M.A.R.T. reports the drive as healthy as far as I can tell.  I do get occasional ATA bus errors in the log, but they don't appear to coincide with my experience of the problem (the last bus error occurred when I wasn't actively using the computer).  
iotop never indicates a particular process consuming an inordinate amount of I/O, but due to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493156") iotop doesn't function correctly so I don't trust its output.  
 
Since I've been using the computer for the past couple of hours, I haven't experienced the problem.  I even opened some seldom-used programs that I know have a lot of I/O loading, and I couldn't trigger the problem.  It may be I'm accessing mostly cache now, so therefore the problem doesn't exist.

Any ideas?

---

### Post by dino99 on 2010-06-24
check the sources.list: only use genuine ubuntu repo (no mixed releases, no third party, no untrusted ppa)

clean the system with gconf-cleaner (yes to all), and bleachbit as admin (but set the config carefully)

sudo apt-get clean/autoclean/autoremove (one by one)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo update-usbids && sudo update-pciids

---

### Post by ectospasm on 2010-06-24
> **dino99 said:**
> check the sources.list: only use genuine ubuntu repo (no mixed releases, no third party, no untrusted ppa)

clean the system with gconf-cleaner (yes to all), and bleachbit as admin (but set the config carefully)

sudo apt-get clean/autoclean/autoremove (one by one)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo update-usbids && sudo update-pciids

What purpose does this serve?

---

### Post by ectospasm on 2010-07-14
> **dino99 said:**
> check the sources.list: only use genuine ubuntu repo (no mixed releases, no third party, no untrusted ppa)

clean the system with gconf-cleaner (yes to all), and bleachbit as admin (but set the config carefully)

sudo apt-get clean/autoclean/autoremove (one by one)

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo update-usbids && sudo update-pciids

I've done all of these except for bleachbit.  "(but set the config carefully)" is too vague to be of use, and I cannot be bothered with looking up what you mean.  sources.list was stock (except for my VirtualBox repo already commented out), and I temporarily removed the google-chrome.list and related files from /etc/apt/sources.list.d.

We'll see if the problem persists.  While I was running "aptitude install -f", the hard drive was in constant use.  I tried loading two programs during this, KeePassX and Pidgin, with the latter taking a noticeable amount of time to even show that it was trying to load.  I think KeePassX had been cached in memory, so it loaded immediately.  At no time did rhythmbox pause playback, which is another symptom of the problem I'm facing.

---

### Post by ectospasm on 2010-07-28
I may have fixed the problem.  For my on board SATA controller, I changed the mode from IDE to AHCI.  It seems the hard drive light is still locking on *something*, but it does not seem to be causing the responsiveness problem I initially reported.  Also, my system latency seems to have been DRASTICALLY reduced.  hdparm is reporting significantly better cached reads, but buffered reads are about the same.  I also used cyclictest to monitor my system latency, and it looks extremely good.  Here are the commands I ran:

```
aptitude -y install rt-tests
chrt -f 99 cyclictest -t1 -p 80 -i 10000 -n -l 10000
hdparm -Tt /dev/sda

```

And here's the relevant output:
```
meth:~ # chrt -f 99 cyclictest -t1 -p 80 -i 10000 -n -l 100000
policy: fifo: loadavg: 0.82 1.03 0.99 1/424 3523          

T: 0 ( 3523) P:80 I:10000 C:  33116 Min:   -212 Act: -109 Avg:  -32 Max:    2005
^Cmeth:~ # hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   14096 MB in  2.00 seconds = 7056.13 MB/sec
 Timing buffered disk reads:  332 MB in  3.02 seconds = 110.10 MB/sec

```

I will continue to monitor, make a few more reboots, and report this as solved when confirmed.

---

### Post by ectospasm on 2010-08-21
Nope, my problem still exists.  It gets worse when I try to do something that involves a lot of I/O (such as installing an OS in VirtualBox).  top and iostat seem to disagree.  top reports iowait between 45% and 70%, while iostat reports around 15-20%.  I know what's causing it at the moment, but that doesn't explain why it occurs when the system is otherwise idle.  

I tried installing preload to perhaps get to steady-state sooner, but I haven't rebooted to determine whether that's workable.

---

### Post by ectospasm on 2010-08-28
I finally saw something which may be the culprit.  iotop gave me a glimpse that the Ubuntu One sync daemon was consuming a fair bit of Disk I/O, causing my HDD light to go solid on for a few moments.  And as I'd seen in the past, keyboard and mouse input would block until it was done.  As before, I could move windows about, and switch tabs (maybe).  I disabled File Synchronization with Ubuntu One, and the problem seems to have gone away.  I will need to test a bit longer to be sure.

Here's hoping I fixed it.  If this does solve it, I will need to file a bug report, maybe get help scheduling the sync daemon to work only when the computer is idle.

---

### Post by ectospasm on 2010-09-22
Nope, after a few weeks of testing, the problem is not gone.  Even with Ubuntu One set not to sync anything, I get the high I/O wait in top, and my system is unresponsive for a few seconds to a few moments.  Sometimes even my Audacious playback of Internet streams will pause or skip briefly.  It seems to get worse when I have both of my VirtualBox VM guests (Oracle Enterprise Linux w/ Oracle 11g for testing, and Windows 7 Professional) running, so I try to avoid having either of them running when I'm actively using the machine.    The problem also seems worse when I run Firefox:  it will gray out for several seconds quite frequently when this problem occurs.  I rarely get the same behavior out of Google Chrome.

---

### Post by ectospasm on 2010-09-22
Launchpad bug seems related:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/131094)

---

### Post by ectospasm on 2010-09-26
Looks like my problem is fixed.  I upgraded to Linux kernel 2.6.35 (see post #342 on the bug listed above).  Both the Ubuntu "stock" kernel and the one patched with iofix worked for me.

If this should change, I will report here.  Otherwise, I'm marking it as [SOLVED]!

---

