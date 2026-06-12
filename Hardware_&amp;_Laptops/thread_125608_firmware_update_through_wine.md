---
title: "firmware update through wine?"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by nashife on 2006-02-04
Does anyone know if it's possible to install a firmware update through wine? I don't want to mess around with it (and possibly irrepairably damage something) by trying it myself until I hear if anyone else has had success.

I'm trying to install firmware updates for my Pioneer DVD-RW 110D.

---

### Post by jonthysell on 2006-05-09
[QUOTE=nashife]Does anyone know if it's possible to install a firmware update through wine? I don't want to mess around with it (and possibly irrepairably damage something) by trying it myself until I hear if anyone else has had success.

I'm trying to install firmware updates for my Pioneer DVD-RW 110D.[/QUOTE]

Hi, I've been trying to get my 110d to work as well, cause I have a big stack of coasters here.

Mine's connected via firewire, so I still can't burn things (it reads fine).

But I have the 1.39 firmware flashed!

Here's what I did:

1. Installed wine.

2. Used wine to extract the firmware files from the archive here: [http://www.pioneerelectronics.com/pio/pe/images/portal/cit_3424/294863852R10_FW139.exe](http://www.pioneerelectronics.com/pio/pe/images/portal/cit_3424/294863852R10_FW139.exe)

```
wine 294863852R10_FW139.exe
```

3. Didn't use wine to install the firmware, instead download DVRFlash from [http://lasvegas.rpc1.org/DVRFlash_v2.2_linux.zip](http://lasvegas.rpc1.org/DVRFlash_v2.2_linux.zip) and unzip it.

4. Put everything one one folder, namely the following files:

DVRFlash
RB100011.139
RB100111.139

5. Run DVRFlash with:
```
./DVRFlash
```
 to find out what device your drive is (and to verify that it is a 110d).

6. Use the device with the RPC-2 setting (my output displayed two drives, one with RPC-2, one with RPC-1.

7. Install the flash:

```
./DVRFlash -v [device] RB100011.139 RB100111.139
```

Worked for me! Now to get the firewire working ...

---

