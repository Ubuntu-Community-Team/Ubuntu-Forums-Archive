---
title: "Fingerprint reader on Lenovo Thinkpad X1"
date: 2011-07-14
forum: Hardware
---

### Post by jdpipe on 2011-07-14
Hi all

I have 32-bit Ubuntu 11.04 Natty on a Lenovo Thinkpad X1 with fingerprint reader. The fingerprint reader seems to work fine with "fprint_demo" and I can authenticate OK when running "sudo echo HELLO" from terminal.

However, when I attempt to actually login to Ubuntu with this setup, I get a message in the login screen saying "Could not find suitable fingerprints matched to available hardware".

I found a related post on this problem:
[http://www.softwaretalk.info/could-not-find-suitable-fingerprints-matched-to-available-hardware-error.htm](http://www.softwaretalk.info/could-not-find-suitable-fingerprints-matched-to-available-hardware-error.htm)

I *do* have my home directory encrypted... so the question is, can I still use fingerprint authentication for login? Has anyone succeeded in this case?

Cheers
JP

---

### Post by ziroday on 2011-07-14
Hi there,

Unrelated but I'm thinking of getting an X1, how compatible is it with Ubuntu and any regrets?

---

### Post by jdpipe on 2011-07-14
The X1 doesn't seem to support Ubuntu 10.04 LTS, so no LTS options unfortunately. All the basic stuff works fine. You might want to consider not using encrypted home dir, that might help this fingerprint reader issue. Setting up dual boot is fine, Windows 7 runs chkdsk after Ubuntu is installed (and you reboot to Windows the first time after that) but I didn't get any errors, and both systems now work fine. I haven't yet checked the camera or mike, but audio and video playback seem to be fine. Ubuntu is able to access the Windows 7 partitions, too.

---

### Post by harveyd on 2011-08-19
> **jdpipe said:**
> Hi all

I have 32-bit Ubuntu 11.04 Natty on a Lenovo Thinkpad X1 with fingerprint reader. The fingerprint reader seems to work fine with "fprint_demo" and I can authenticate OK when running "sudo echo HELLO" from terminal.

However, when I attempt to actually login to Ubuntu with this setup, I get a message in the login screen saying "Could not find suitable fingerprints matched to available hardware".

I found a related post on this problem:
[http://www.softwaretalk.info/could-not-find-suitable-fingerprints-matched-to-available-hardware-error.htm](http://www.softwaretalk.info/could-not-find-suitable-fingerprints-matched-to-available-hardware-error.htm)

I *do* have my home directory encrypted... so the question is, can I still use fingerprint authentication for login? Has anyone succeeded in this case?

Cheers
JP


Have a look at this [https://launchpad.net/~fingerprint/+archive/fprint](https://launchpad.net/~fingerprint/+archive/fprint)

---

### Post by iposner on 2011-08-20
I've got an X1 with Ubuntu x64 running via Wubi. Fingerprint reader doesn't seem to work (doesn't recognise the device). Haven't tried the WWAN card yet. And I've got to say that it takes just as long to load Ubuntu as it does the specially optimised Windows 7 x64. The Thinkpad software available under Windows for fine-grained battery control and battery charging options are not available, so I would say that you would definitely need to keep Windows 7 in a dual boot config so that you have full access to all the hardware settings.

On the plus side, Ubuntu is snappy and all the networking works correctly.

---

