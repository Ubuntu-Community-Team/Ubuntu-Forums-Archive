---
title: "How to get Parallel Port Scanner to work"
date: 2009-05-05
forum: Hardware
---

### Post by MrsZoiby on 2009-05-05
I have an UMAX Astra 1220P scanner.  It's listed as "good" on SANE's website but I can't get it to work since SANE doesn't automatically detect it.  Running sudo sane-find-scanner says it doesn't check for parallel port scanners so I'm guessing that's why it doesn't work.  I've installed the libsane-extras and I tried deleting the # from in front of umax_pp in the etc/sane.d/dll.conf file.  Any help would be greatly appreciated.

---

### Post by simonrodan on 2012-06-12
I am having the same issue with a different sanner (Microtek CX330) which according to the sane documentation is suppoted.

Any help would be greatly appreciated.

---

### Post by dandnsmith on 2012-06-13
Since you have a different scanner, and the thread you added to was 3 years old, with no replies, you'd do better to start your own thread.
Report (see guidelines on posting) the version of Ubuntu you're using, details of the scanner and method of connection (is it really parallel port?).
Outputs of 'lspci -nn' and 'lsmod' might help as well

---

