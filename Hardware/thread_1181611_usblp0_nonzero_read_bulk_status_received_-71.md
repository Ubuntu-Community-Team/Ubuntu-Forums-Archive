---
title: "usblp0: nonzero read bulk status received: -71"
date: 2009-06-08
forum: Hardware
---

### Post by kruescho on 2009-06-08
Hi all,

on Ubuntu 9.04 my printer (Canon MF4120) does not print anymore. I installed Ubuntu 9.04 shortly after it became available and managed to get the printer work with the Canon drivers (cndrvcups-ufr2, cndrvcups-common available at [http://support-asia.canon-asia.com/contents/ASIA/EN/0100093001.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100093001.html)).

But suddenly (I assume after the updates for CUPS where installed some days ago), printing does not work. When trying to print, dmesg shows the error message [FONT=Courier New]usblp0: nonzero read bulk status received: -71[/FONT] and the printer does nothing. There is a [FONT=Courier New]cnpkmodule[/FONT] process, consuming a lot of cpu time, the print job stays stuck in the printing queue.

I tried to install the older CUPS packages, I reinstalled the Canon drivers, but the result is always the same: the printer does not work an the message [FONT=Courier New]usblp0: nonzero read bulk status received: -71 [/FONT]appears.

Any suggestions how to get printing work again?

---

