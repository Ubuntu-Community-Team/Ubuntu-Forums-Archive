---
title: "RaLink RT2860 on Laptop"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by Xanth on 2009-09-06
Hi,

I bought a Laptop and have been trying to install Ubuntu on it, I'm having a problem with the wireless.  It will display the list of wireless networks but hangs and asks for the password again when I try to connect.  I googled around for a while and found this:

[http://ubuntuforums.org/archive/index.php/t-1110957.html](http://ubuntuforums.org/archive/index.php/t-1110957.html)

In particular:

"April 6th, 2009, 08:19 AM
A solution involves downgrading the RT2860 driver to version 1.7.1.1 (the last know fully working driver). It seems to work much more reliably for me at least on 1000h.

1) Get the driver from [http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb](http://www.array.org/ubuntu/dists/intrepid/eeepc/binary-i386/rt2860-dkms_1.7.1.1_all.deb)

2) Go to terminal, and move the pre-installed driver so it won't get loaded.

cd /lib/modules/2.6.28-11-generic/kernel/drivers/staging/rt2860/
sudo mv rt2860sta.ko rt2860sta.bak


3) Install rt2860-dkms_1.7.1.1_all.deb. It will also install dependencies needed to compile the driver. If it doesn't retrieve the right packages, make sure "build-essential", "linux-header-generic" and "dkms" is installed. Let it run and it should complete without a problem.

4) Restart. The new driver should work automatically."


I'm using 64-bit Ubuntu 9.04.  The laptop is MSI EX630.

I get to step 3) and it says: "install: missing destination file operand after 'rt2860-dkms_1.7.1.1_all_deb'" The help menu is confusing and I have no idea what to make of it.

If you can't tell already, I'm a complete noob with Ubuntu.

Any help appreciated

---

### Post by Xanth on 2009-09-06
So I've discovered the dpkg command
[http://ubuntuforums.org/archive/index.php/t-6365.html](http://ubuntuforums.org/archive/index.php/t-6365.html)
and I attempted to install using that, it said it needed a dependency so I installed "build-essential" and afterwards it recommended I do install -f or something (I thought I found a solution so I blew through it) and I did, I think it installed dkms as well, but I did it again just in case.  But it said it couldn't find "linux-header-generic", I ignored it and continued with installing the driver, it said it installed.  But my wi-fi still does not work.

**So I've managed to fix it:**

After doing the above 4 steps, I tried a multitude of different things, none of which worked.  Eventually I came back to it and instead of doing "sudo mv rt2860sta.ko rt2860sta.bak" I removed the file entirely and then proceeded with installing the .deb.... It works for now, supposedly whenever Ubuntu updates I will have to do this again, but it's not that big of an issue.

:D :D :D

---

### Post by mojobo on 2009-09-13
It's nice you bought a laptop....what kind? Before I would attempt your solution,  I would l need to know if your situation was similar to mine. From most of the messages about the ralink 2860, the solutions vary according to,  not only the brand and model, but down to the very sub species. This ralink thing has been persistent, intermittent and really flaky.

---

