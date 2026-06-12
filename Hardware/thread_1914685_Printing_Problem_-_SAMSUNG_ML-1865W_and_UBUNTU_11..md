---
title: "Printing Problem - SAMSUNG ML-1865W and UBUNTU 11.10"
date: 2012-01-24
forum: Hardware
---

### Post by virvet on 2012-01-24
Hi guys.
First of all, believe me: I've searched this forum, tried to implement some suggestions but I've got to nowhere, so I'm opening this thread.

My problem is, as mentioned, with a SAMSUNG ML-1865W printer.
The problem: It rarely prints what it's supposed to print. At most times, it will go frenzy and print non-stop pages of 1~3 lines containing odd chars (hearts, smiles, arrows, pipes...).

The driver I'm using is the samsungfp-driver, but I've tried also the driver provided by samsung (I haven't checked if they are the same - I guess so): UnifiedLinuxDriver_0.98.

I need a light! It is getting on my nerves.

And of course, I haven't tried getting it to work wirelessly. Will be happy if it prints my pdf's.

Addendum: even the test page functionality prints odd things. Sometimes. And sometimes the test page.

Thanks in advance.

---

### Post by virvet on 2012-01-26
Errr...
No one?

---

### Post by yahs on 2012-01-27
This is what works for me. Hopefully something here will help you out.

Before I continue I have to say that my test page prints normally, so I don't know if that is where the problem lies.

I have a scx-4500W which works as it should in Ubuntu 11.10 using a wireless connection.

The instructions from Samsung said that initaially the printer has to be connected using a network cable but after driver installation it can then be set up to work wirelessly. 

So I do a local installation with a cable attached, than a network without the cable and yes it does work.

The packages and support provided by Tweedledee are far superior to the samsung packages but I find the latest samsung drivers work okay.

In the past when I have had problems with printing I run a live session from CD or USB stick, download the unified driver and install to make sure there are no conflicts with other packages. If this works I usually just do a fresh install which I find easier than trouble shooting! 

These are the steps I follow

Run a live session from USB

Search for and download the Unified driver v 3.00.90 (it will probably come up under a samsung printer different to the one you have - this doesn't matter).

My download comes down as UnifiedLinuxDriver_1.14.tar.gz

I extract the files and change to the directory - in my case Downloads\cdroot\Linux.

I open a terminal and run the command sudo ./install.sh 

The GUI installer appears and in my case I have printing and scanning available.

I used to have lots of problems with samsung printing from Ubuntu 8.04 through to 10.04, but since then instant success fortunately.

---

### Post by saxonbeta on 2012-01-31
Hi there, I just bought my ML-1865w last sunday and I installed it without problems. Don't use the linux driver from Samsung, it has a lot of problems during installation. You can follow the instructions in this page [http://www.bchemnet.com/suldr/index.html]("http://www.bchemnet.com/suldr/index.html")
If you want further information about this drivers see this thread [http://ubuntuforums.org/showthread.php?t=341621]("http://ubuntuforums.org/showthread.php?t=341621")

Hope it helps
Cheers

---

