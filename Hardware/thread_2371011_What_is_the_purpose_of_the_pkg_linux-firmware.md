---
title: "What is the purpose of the pkg linux-firmware?"
date: 2017-09-09
forum: Hardware
---

### Post by DAB4970 on 2017-09-09
I just had a thought since I have acquired a new motherboard for my Toshiba AIO, and it needs the BIOS upgraded.  The question is what the title of this post says.  Isn't the BIOS basically firmware for the system components?  or is the BIOS more simplistic than that?

---

### Post by Bashing-om on 2017-09-09
DAB4970; Hey -

> **DAB4970 said:**
> I just had a thought since I have acquired a new motherboard for my Toshiba AIO, and it needs the BIOS upgraded.  The question is what the title of this post says.  Isn't the BIOS basically firmware for the system components?  or is the BIOS more simplistic than that?

Terminal command:
```

apt show linux-firmware

```

where the package is specific for linux. So yeah, you want it if the manufacturer provides .

[INDENT][INDENT]it's a thing
[/INDENT][/INDENT]

---

### Post by jeremy31 on 2017-09-09
I don't think there is a way with Linux to update BIOS.  I have heard of people using freedos to boot into so they can use the BIOS updater but that depends on what kind of file the BIOS update is.

I just did a search for Toshiba AIO BIOS Update and it seems they might use a bootable CDROM to update BIOS based on the instructions but you may need a Windows computer to use the exe file to make the CDROM

---

### Post by Yellow Pasque on 2017-09-09
linux-firmware does not have BIOS updates. If your question is about updating your BIOS, linux-firmware has nothing to do with it.

---

### Post by Yellow Pasque on 2017-09-09
> **jeremy31 said:**
> I don't think there is a way with Linux to update BIOS.

If your system is good, it lets you update using a BIOS image on a USB stick, so you don't have to boot an OS at all.

---

### Post by him610 on 2017-09-09
The motherboard manufacturer has two or three methods to update the BIOS. I recently came into possession of a fairly new AsRock MB that has three different methods to update BIOS. Update process normally documented in the MB manual. Does not require operating system to update.

---

### Post by vasa1 on 2017-09-09
And this is for updating the BIOS for some Dell machines: [http://www.dell.com/support/article/us/en/04/SLN171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=EN](http://www.dell.com/support/article/us/en/04/SLN171755/updating-the-dell-bios-in-linux-and-ubuntu-environments?lang=EN)

And two links that explain a bit about linux-firmware found using [https://www.findx.com/search?q=linux-firmware&type=web:](https://www.findx.com/search?q=linux-firmware&type=web:)

[http://www.scrye.com/wordpress/nirik/2014/11/10/fun-with-linux-firmware/](http://www.scrye.com/wordpress/nirik/2014/11/10/fun-with-linux-firmware/)
[http://www.scrye.com/wordpress/nirik/2014/11/11/fun-with-linux-firmware-part-2/](http://www.scrye.com/wordpress/nirik/2014/11/11/fun-with-linux-firmware-part-2/)

---

### Post by gordintoronto on 2017-09-10
But what is the package linux-firmware?

---

### Post by SeijiSensei on 2017-09-10
See /usr/share/doc/linux-firmware/README.gz.

> This file attempts to document the origin and licensing information,
if known, for each piece of firmware distributed for use with the Linux
kernel.

Some of those pieces of firmware are licensed under something other than the GPL.  The Intel i915 video driver is listed in that README file as "Redistributable." The file /usr/share/doc/linux-firmware/licenses/LICENSE.i915 provides these details:

> Redistribution.  Redistribution and use in binary form, without
modification, are permitted provided that the following conditions are
met:

* Redistributions must reproduce the above copyright notice and the
  following disclaimer in the documentation and/or other materials
  provided with the distribution.
* Neither the name of Intel Corporation nor the names of its suppliers
  may be used to endorse or promote products derived from this software
  without specific prior written permission.
* No reverse engineering, decompilation, or disassembly of this software
  is permitted.

Limited patent license.  Intel Corporation grants a world-wide,
royalty-free, non-exclusive license under patents it now or hereafter
owns or controls to make, have made, use, import, offer to sell and
sell ("Utilize") this software, but solely to the extent that any
such patent is necessary to Utilize the software alone, or in
combination with an operating system licensed under an approved Open
Source license as listed by the Open Source Initiative at
[http://opensource.org/licenses](http://opensource.org/licenses).  The patent license shall not apply to
any other combinations which include this software.  No hardware per
se is licensed hereunder.


Some pieces of firmware are marked as GPLv2 or v3, and some are marked as "Licence: Allegedly GPLv2, but no source visible."

---

### Post by DAB4970 on 2017-09-14
Thanks for the replies.

---

