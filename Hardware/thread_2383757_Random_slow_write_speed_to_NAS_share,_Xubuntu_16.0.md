---
title: "Random slow write speed to NAS share, Xubuntu 16.04 (Win7 ok)"
date: 2018-01-29
forum: Hardware
---

### Post by turrican32 on 2018-01-29
I am experiencing some very slow write speeds (about 12-15 MB/s, sometimes even less than that - over a gigabit network) under Xubuntu 16.04 lately.

At first I thought it was due to the recent upgrade of the NAS software (OpenMediaVault user here) but since it runs off a USB pendrive I immediately reverted to the old distribution and the issue is still there.

Some details about the tests I made:

- client PC is a Core i3 6100, 16GB RAM, main drive is a Samsung SSD, test data being copied to the NAS is on a separate WD Green 500GB hard disk
- network is gigabit (ethtool confirms gigabit full duplex)
- client PC has dualboot with Windows7 64bit, and NAS is working flawlessly there (100+ MB/s), _as it did under Xubuntu until recently_
- iperf benchmarks on both Xubuntu *and* the NAS shows about 950 Mb/s
- the network share is accessed via cifs/smb
- sometimes write speed (data used for the test is usually huge files ranging from 500 MB to 2-3 GB) goes back to normal, then horribly crawls at 1 MB/s or even less

Considering the huge performance differences between Xubuntu/Linux and Windows7 on the very same hardware I have to guess the issue isn't on the server side (i.e. the NAS) but on the client instead.

But I really have no idea what to look for, so any suggestion is surely appreciated.

---

### Post by turrican32 on 2018-01-30
Whoops sorry, I just noticed this is NOT the appropriate forum for this kind of issue, could a moderator please move it to the right section accordingly?

Thanks.

---

### Post by slickymaster on 2018-01-31
Thread moved to **Hardware** for a better fit

---

### Post by turrican32 on 2018-03-28
Problem has not been solved yet, but I have some additional information to provide.

First of all, I did a test install replacing openmediavault with Ubuntu Server 16.04 LTS 64bit on the NAS.

Some *interesting* things happen depending on what I do:

- under Xubuntu, copying a ~3GB mp4 file to the NAS via OS GUI takes about 210+ seconds, but...
- ...if I use scp via command line to copy that file to the NAS, it only takes more or less the same as under Windows7, i.e. about 50 seconds
- if I boot via LiveUSB a standard Ubuntu 16.04 desktop and map the same network drive via the built-in file browser, write speed is ok copying via OS GUI (same file as below, same 50-ish seconds to write) BUT read speed from the NAS becomes horribly slow, like 4-500 KB/s

Hope this helps further isolating the issue, because frankly I don't know what to do anymore :-\

---

