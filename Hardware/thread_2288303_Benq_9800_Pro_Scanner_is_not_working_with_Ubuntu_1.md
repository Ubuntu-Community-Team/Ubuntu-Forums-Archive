---
title: "Benq 9800 Pro Scanner is not working with Ubuntu 15.04"
date: 2015-07-25
forum: Hardware
---

### Post by Yukumi on 2015-07-25
lsusb output:
Bus 002 Device 003: ID 04a5:2119 Acer Peripherals Inc. (now BenQ Corp.) 
I installed the Windows driver and copied the MT9800N.bin to /usr/share/sane/snapscan, then I edited  /etc/sane.d/snapscan.conf, but still not recognize my scanner.

---

### Post by ajgreeny on 2015-07-26
I have no idea about that scanner or the drivers you need, but the Windows drivers will be useless for you to use with Ubuntu.

You have the MT9800N.bin file on disk but I do not think you should have put it in the /usr/share/sane/snapscan folder.  Bin files should be run by the system to install the driver needed for linux, and I imagine you need to run that in terminal, or you could try double clicking on it, but it depends on the file itself whether or not it will run that way.  You may need to make the .bin file executable first by right clicking on it and putting a check mark in the appropriate box in the permissions tab.

See what happens if you try running the .bin file in terminal c but not from the /usr/share/sane/snapscan folder.  First copy it back to your /home folder if you do not already have it there and use command ```
sh MT9800N.bin
```to run it.

Come back again if this does not help and I or someone else will try to help you more.

---

### Post by Yukumi on 2015-07-27
I followed the guide here but not working. [http://askubuntu.com/questions/101025/benq-5000-scanner-not-working](http://askubuntu.com/questions/101025/benq-5000-scanner-not-working)
I have MT9800N.bin and MT9800P.bin from the folder of Windows partition which I installed the windows driver. I tried sh MT9800P.binMT9800P.bin: 1: MT9800P.bin: 2005/08/23: not found
MT9800P.bin: 1: MT9800P.bin: Syntax error: Unterminated quoted string

---

