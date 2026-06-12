---
title: "HELP NEEDED: SIS 662 video driver - motherboard Intel D201GLY"
date: 2008-11-22
forum: Hardware
---

### Post by MpegTv on 2008-11-22
HI I really need your help because I'm newbie with Linux and Ubuntu.

I need step by step instruction how to install SIS662 video driver since it flickers a lot on UBUNTU.

I've spent couple hours to figure out how to install but without any success.

Please help.

...MpegTv....

---

### Post by PaulCompton on 2010-01-13
If you are using 9.10 (Karmic) then proceed as follows:
Just download the current driver from intel [here]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2873&DwnldID=15443&strOSs=39&OSFullName=Linux*&lang=eng"), extract it and copy the .so file to /usr/lib/xorg/modules . I did this with the 64-bit version (these boards run AMD64 Ubuntu wonderfully) ten minutes ago, restarted xorg (actually, I rebooted) and it was fine.
Actually, I had previously installed the official sis driver - but maybe it was already there anyway.
Let me know if this works for you! All the forum threads on compiling are irrelevant for 9.10 - the binary from Intel is perfect.

---

### Post by picpak on 2010-01-24
Hi,

first off, thank you for that driver!

Secondly, now that I'm using this driver, my computer will only boot up in 800x600. If I log out and in again, it returns back to 1280x1024. Any ideas?

---

### Post by PaulCompton on 2010-08-08
Further update: the instructions above also work perfectly under Lucid, except that the .so file has to go in /usr/lib/xorg/modules/drivers .

---

### Post by PaulCompton on 2011-05-18
Also works with Maverick by putting the .so file in /usr/lib/xorg/modules/drivers .

---

### Post by Ashrael on 2011-06-17
I tried what u said in natty, no joy yet. I would like to have unity...

any suggestions are welcome...


TIA!

---

