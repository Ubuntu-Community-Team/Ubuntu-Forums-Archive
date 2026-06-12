---
title: "mii-tool not working on 64-bit ubuntu with e1000e drivers"
date: 2009-07-02
forum: Hardware
---

### Post by Curtor on 2009-07-02
Hey guys,

I'm having trouble getting mii-tool to work properly when running with my NIC on a 64-bit Ubuntu machine (as thread title reads). The error that I get is a print-out as such:
```
SIOCGMIIREG on eth0 failed: input/output error
SIOCGMIIREG on eth0 failed: input/output error
eth0: negotiated 100baseTx-FD, link OK
SIOCGMIIREG on eth0 failed: input/output error
SIOCGMIIREG on eth0 failed: input/output error
    No MII transceiver present!.
```
Note also that if I unplugged or plugged in any cables, it still reported the same setup as that which I had at boot. Definitely not what I want.

The expected output should be:
```
eth0: negotiated 100baseTx-FD, link OK
eth1: no link
```

I've placed the card in a 32-bit machine, and it loads up with the e1000 (not e1000e) driver and it seems to work fine.

So, my first thought was, let's get it working without using the e1000e driver on the 64-bit machine. I blacklisted it in 

```
/etc/modprobe/blacklist.conf
```

and then ran 

```
update-initramfs -u
```

in order for it to take affect during the boot sequence. Lucky me, instead of picking up the e1000 driver as an alternative, the NIC was set as UNCLAIMED. So, then I ran

```
modprobe e1000
```

which, to my dismay, did absolutely nothing.

I tried the same NIC in a different 64-bit machine. The machine ran mii-tool fine with the NIC it had before this, but not this one.

Is this a problem with the e1000e driver, the hardware, or with mii-tool? Any suggestions on the next step that I should be taking?

Thanks

---

### Post by Curtor on 2009-07-03
So, I took a single system, installed Ubuntu 8.04 on it and installed the NIC. Running mii-tool wored fine. I then installed 8.10, and then 9.04, and both had the problem. So this seems like a driver or kernal change that has caused this to start happening. Is there someone more specific that I should possibly be contacting about this, or am I SOL?

---

### Post by Curtor on 2009-07-03
The 8.04 us using the e1000 (not e1000e) drivers. Therefore, for at least a quick fix (if the real question is not going to be answered) is "how do I get the e1000 drivers working on 9.04?".

---

### Post by Curtor on 2009-07-03
So, first off, an interesting article relating to this can be found here:
"e1000 v. e1000e"
[http://lwn.net/Articles/278016/](http://lwn.net/Articles/278016/)

Secondly, this problem persists on 8.10 and 9.04 on 32-bit and 64-bit systems. The reason for this can be found in the link above.

As for a solution to it, well, I'm still looking.

---

