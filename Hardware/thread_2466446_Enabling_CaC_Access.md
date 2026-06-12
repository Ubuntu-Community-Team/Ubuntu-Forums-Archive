---
title: "Enabling CaC Access"
date: 2021-08-27
forum: Hardware
---

### Post by james83605 on 2021-08-27
ALCON,

Need a bit of help. I am utilizing my device, Ubuntu 20.04.3 LTS. Trying to utilize my laptop to access DOD CaC enabled websites that can operate outside of AC/AR networks. For example, email and mypay. I have a device reader compatible. I have installed PCSC (and all of the libraries). When I run PCSC_Scan, it detects my inserted CaC. I downloaded the DOD Certs and updated them in Firefox to show as trusted device. I manually attempted to add cackey.so to the security device module but firefox crashed and refused to re-open. I had to open in safe mode and refresh to default in order to even get it to re-load.

What am i missing, or is there a more effective method then cackey?

V/R,
Eric

---

### Post by Objekt on 2022-03-09
This is probably way too late to be of any use to you, but I had that exact problem you describe in the last few days.  I do have a partial solution.

For context: I am running Ubuntu 20.04 LTS on an Acer Swift 3 laptop, attaching an HP Slim Smartcard keyboard (model TPC-C100K) for its embedded CAC reader.

FWIW, this shows up in pcsc-scan as a "Chicony HP Skylab USB Smartcard Keyboard."

I don't think the exact hardware matters - just mentioning it for completeness.

As part of CAC access setup, I downloaded this package:
```
cackey_0.7.5-1_amd64.deb
```
Don't remember exactly where I got it, but it comes up if you search for using CAC on Linux.

Next, I manually created the folder:
```
/usr/lib64
```
Then I installed the above *.deb file using command:```
sudo dpkg -i cackey_0.7.5-1_amd64.deb
```
At this point, I was able to go into Firefox as you describe, & loaded a new security device with /usr/lib/libcackey.so as the module.

There was a pause on clicking "OK," but Firefox did not crash.  CAC login worked after that.

Later that day, CAC login stopped working.  I was not even prompted for my PIN, but was directly denied access every time I tried to open my DoD email.

I tried removing and re-adding the security device for the CAC reader.  But, I found that libcackey.so was not where I left it.  Something had removed it from /usr/lib64.

I did eventually find another file named libcackey.so in a different folder.  Don't remember the path, I'll maybe post that when this happens again.

The problem: when I tried to use that new version of libcackey.so as a module to add back the CAC reader to Firefox, Firefox would crash every time - same issue you had.

Eventually, I tried reinstalling the *.deb package mentioned previously.

During the install, I got an error message stating that I was installing an older version of libcackey.so.  Hmmm..interesting.

I went back and added the CAC reader to Firefox yet again, using the newly-restored, old version of libcackey.so as the module.  It worked, just like the first time.

Since then, I've had to reinstall cackey_0.7.5-1_amd64.deb a few more times, to reassert the old version of libcackey.so.

I don't know what keeps messing with /usr/lib64/libcackey.so, not only removing it from that location but "upgrading" it to a newer version which doesn't work (causes Firefox to crash).

I've written a script to semi-automate reinstalling the *.deb package while I look for a real solution.

Anyone know what might be messing with libcackey.so?  Does something in Ubuntu not "like" that I manually created /usr/lib64?  Is some process trying to "help" by silently "upgrading" libcackey.so to the newer, non-working version?  If so, how do I turn that off?

---

