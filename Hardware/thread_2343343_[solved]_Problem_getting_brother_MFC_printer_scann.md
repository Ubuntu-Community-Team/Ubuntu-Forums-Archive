---
title: "[solved] Problem getting brother MFC printer scanner to work (Yakkety 16.10)"
date: 2016-11-15
forum: Hardware
---

### Post by eallaud-gmail on 2016-11-15
Hi all,
I upgraded to 16.10 recently. My brother DCP7055W scanner (its a multifunction printer) does not work anymore.
The printer works perfectly though.
This is a wifi printer.
I used the brother installer as I did for ubuntu 16.04 where it worked like a charm.

The brother scanner config program works and outputs the correct IP for my printer, also their own software works (brscan-skey for the ones who know about these).

So I think that the problem is the sane.d config: /etc/saned.d/dll.conf contains brother4 which is the brother backend.
Several problems: scanimage -L crashes (core dump), xsane works but detects no scanner.
Also saned is working as systemclt status saned.socket says it is active.

Any idea?
Thanks,
Manu

---

### Post by eallaud-gmail on 2016-11-20
Got it solved.I did 2 things, I don't know which was necessary, so here they are.
First I copied a few libs around as in [https://ubuntuforums.org/showthread.php?t=2321613&page=3](https://ubuntuforums.org/showthread.php?t=2321613&page=3).
I also did something from Brother's FAQ: install libusb-0.1-4
Apparently brother's drivers use an old libusb and although I own a networked printer scanner this seems to be the crucial step!
HTH
Manu

---

### Post by jcolton on 2017-05-04
changing the usb lib to that version alone resolved the segv

---

