---
title: "acer 1622 ?"
date: 2005-03-05
forum: Hardware &amp; Laptops
---

### Post by LK_gandalf_ on 2005-03-05
Hi, I have this laptop, and it seems to work well with ubuntu but...

- I can't hear anything
- the wireless isn't installed
- and i can't use the modem to go on the web, and this is bad  :-(  :-( 

Anyone have a solution? thanks...

---

### Post by Spif on 2005-03-06
I think I can help you with your wireless connection.

```
1.Download the Acer Hotkey driver from this site: http://www.informatik.hu-berlin.de/~tauber/acerhk/. This guide will assume you have downloaded the acerhk-0.5.21.tgz version.

2.Open the console and type

sudo mv acerhk-0.5.21.tgz /usr/src/

      to move the file and

cd /usr/src/

      to go to the directory yourself. Extract the file by writing

sudo tar zxf acerhk-0.5.21.tgz

3.Go to the newly unpacked folder:

cd acerhk-0.5.21

      Use make to test whether there will be any errors compiling it. If none came up, type

sudo make install 

      to start compiling.

4.Load the module by using these commands:

sudo modprobe acerhk usedritek=1 autowlan=1 force_series=290

     followed by

echo 1 > /proc/driver/acerhk/wirelessled

5.Enjoy your new wireless connection!
```

---

### Post by LK_gandalf_ on 2005-03-08
[QUOTE=][/QUOTE]
 thank you, I'll try soon!!

---

