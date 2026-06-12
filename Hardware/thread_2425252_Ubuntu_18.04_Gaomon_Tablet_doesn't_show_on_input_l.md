---
title: "Ubuntu 18.04 Gaomon Tablet doesn't show on input list/drivers won't stay installed"
date: 2019-08-22
forum: Hardware
---

### Post by tamijo on 2019-08-22
Hi, everyone. Currently using Ubuntu 18.04, and I've just bought a Gaomon M106K. I'm struggling to get it working. When I use [xinput list] it doesn't show. The help section on the website I'm using ([http://digimend.github.io/tablets/](http://digimend.github.io/tablets/)) seems to just skip over this possibility. I have downloaded a driver set from that website, and that doesn't seem to help. The USB port is working fine, as I have used it for other things. The tablet and the pen seem to be working, as the tablet has a light that responds when you use it, which seems to work correctly, so I'm fairly certain it's a software, not a hardware issue.

---

### Post by mörgæs on 2019-08-24
> **tamijo said:**
> I have downloaded a driver set from that website, and that doesn't seem to help.

Please post the exact commands you used including the response.

---

### Post by tamijo on 2019-08-24
I downloaded the driver set by clicking on a download, which opened up Ubuntu Software, which I then clicked "Install" on. Once that was completed I opened up Terminal and tried

```
lsusb
```

Which returned

```
Bus 002 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The tablet is simply not listed, though it is responding, so it has at least got power through the USB, even if it isn't actually doing anything data-wise.

Is this what you were asking for?

EDIT: To clarify; I have been through the troubleshooting and browsed the github page for the drivers, but this feels like the issue is before then. Their troubleshooting starts with this, and assumes you find it.

---

### Post by mörgæs on 2019-08-25
For new hardware like your tablet the chances of getting something to work is better when using new software, that is 19.04 for now. 

I would begin with a fresh install (not an in-place upgrade) of this one. 

When that works and all updates have been applied it would be interesting to see how the driver install proceeds. Please run it from the command line in stead of using Ubuntu Software so we can see the output. 

Is the tablet now listed in lsusb?

---

### Post by tamijo on 2019-08-26
Could I get some help ugrading to 19.04 also, then? I keep getting a permission denied when attempting to edit the release upgrader.

Following the instructions on [https://linuxconfig.org/how-to-upgrade-ubuntu-to-19-04-disco-dingo](https://linuxconfig.org/how-to-upgrade-ubuntu-to-19-04-disco-dingo), I reach step 3 fine, and then I am unable to find the file listed.

```
~$ /etc/update-manager/release-upgradesbash: /etc/update-manager/release-upgrades: Permission denied
```

I attempted to find the file through the file manager, but the folder is empty. I am unable to find anything that would let me make hidden files visible.

---

### Post by mörgæs on 2019-08-28
Not from me, sorry. I don't recommend upgrades in general and in particular not when something is wrong. 

The less information brought along from the old system to the new one the better.

---

