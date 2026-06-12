---
title: "Edgy: sane does not recognize scanner"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by lduperval on 2006-11-05
Hi,

I recently did an upgrade (not an install) to Edgy.

I mainly use xfce. Since the upgrade, I have not been able to recognize my Epson CX-5400 scanner.

When I plug it in, I see this message:

```

Nov  5 15:24:37 laptop kernel: [42957848.560000] usb 1-2: new full speed USB device using uhci_hcd and address 5
Nov  5 15:24:37 laptop kernel: [42957848.750000] usb 1-2: configuration #1 chosen from 1 choice
Nov  5 15:24:37 laptop kernel: [42957848.770000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x04B8 pid 0x0808

```

However, when I run xsane, it says that it doesn't recognize a scanner.

Any ideas?

L

---

### Post by raman15217 on 2006-11-11
I have an Epson CX-5400 too.. and the scanner isn't recognized after upgrading to Edgy. I would like to now the answer too. I tried to install the package libsane-extras but that didn't help ](*,)

---

### Post by mjpoetic on 2006-11-17
I found this at launchpad which seems like a helpful howto, but I didn't get it to work (yet).  Maybe you guys can try it and see if it works for you  (if it does, fill me/us in):

[https://launchpad.net/distros/ubuntu/+ticket/2479](https://launchpad.net/distros/ubuntu/+ticket/2479)

---

### Post by mjpoetic on 2006-12-08
[https://bugs.launchpad.net/distros/ubuntu/+source/sane-backends/+bug/67659](https://bugs.launchpad.net/distros/ubuntu/+source/sane-backends/+bug/67659) has a temporary fix.  It is actually reverting to the old libsane package in dapper.  Although it breaks two packages for me, it works.  Then if you want to prevent update notifications for libsane, just do:

```
sudo aptitude hold libsane
```

---

### Post by dolphinsonar on 2007-01-17
That solution worked for me, I am up and scanning, but it is definitely a work around.  Any ideas where I should troll to keep updated on getting a more permanent fix?

---

### Post by mjpoetic on 2007-01-17
I haven't been keeping up with it myself, but launchpad.net should have more information on it (if it ever gets fixed before the next release).  The workaround has been going just fine for me and for others.  So it's possible that they will just fix this in the next release of Ubuntu.

---

