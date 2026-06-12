---
title: "Unable to update BIOS"
date: 2022-08-27
forum: Hardware
---

### Post by erotavlas on 2022-08-27
Hello,

I would like to update the BIOS of my 15-db1400ng notebook. After following the official procedure on the HP website to create a USB drive from the operating system, I rebooted the machine in the BIOS with F10, but I could not find the entry to update the BIOS. Also, at startup, if I press ESC and F2 with the USB drive inserted, it does not start flashing the BIOS and there is no entry to start it.
I have updated several PCs and notebooks of various brands, usually updating the BIOS is quite easy once you have the USB drive. Finally, I tried without success this [guide]("https://blog.frehi.be/2022/05/04/updating-hp-bios-firmware-from-linux/").

Do you have any advice?

Thank you

---

### Post by TheFu on 2022-08-29
Contact HP.
Not really an Ubuntu question.

Off-topic HP stories:
I got burned by HP in the late 1990s with a camera and desktop computer that were really terrible, which useless support, and have never forgotten that.  For a long time, at work I was buying HP servers - HP-UX and Intel. These all had their quirks too.  HP Intel servers are in the Official Supported Ubuntu hardware release, but HP servers much over 3 yrs old seem to have issues with newer Ubuntu Server releases. They don't "just work" as other server vendors do.  There's always some manual tweak needed to get them working, if they do work.  I don't know why, but suspect it is because HP designs their own motherboards.

Anyway, since I was personally burned, I stopped buying HP anything for use at home.  At work, my projects must have spent around $75M on HP servers, easily. Most of those were HP-UX systems, not Intel.  Their PA-RISC systems were probably the most reliable and best made of all Unix servers. They lasted far too long, beyond the point where it would be cheaper to retire the hardware and replace it with much, much, cheaper, faster, fewer CPU models that would cost much less in software costs to use.  Trying to convince a business person that their 32-CPU servers could be replaced by 8-CPU servers that were 1/8th the price and that 2yrs of savings in Oracle licenses alone would pay for the new hardware wasn't an easy sell.  Oracle licenses are by CPU, not total performance.

---

### Post by oldfred on 2022-08-29
Some more similar instructions. 
Exactly what does not work. Do you not get the .bin file?
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)
[https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux](https://wiki.archlinux.org/title/Flashing_BIOS_from_Linux)

Many vendors now support fwupdate. HP only has a few systems on the site. Many vendors have at least some of their newest models.
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist) & 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

[https://github.com/fwupd/fwupd](https://github.com/fwupd/fwupd)

If you want to use Linux, best to check devicelist and see if system is update able. Even if vendor's support (often Windows only) says they do not support Linux, if updates are available, then at least they indirectly will work with Linux system.

---

### Post by erotavlas on 2022-09-02
Hi,
I have solved it. In short, I was not performing the boot procedure correctly.

[LIST=1]
[*]Simultaneously press the WINDOWS logo key and the B key.
[*]While holding down both keys, press the power button for 2 seconds.
[*]Release the power key and continue pressing the other keys for 30 seconds.
[/LIST]

---

### Post by TheFu on 2022-09-02
In Linux, there is no "WINDOWS" key.  There is a "SUPER" key, but not on 101 keyboards.
;)

---

### Post by erotavlas on 2022-09-02
> **TheFu said:**
> In Linux, there is no "WINDOWS" key.  There is a "SUPER" key, but not on 101 keyboards.
;)

In my HP notebook without the Windows operating system (free DOS indicated as non-Windows in the BIOS), there is the Windows key.

---

### Post by TheFu on 2022-09-02
> **erotavlas said:**
> In my HP notebook without the Windows operating system (free DOS indicated as non-Windows in the BIOS), there is the Windows key.

Whooosh.  I was attempting to be funny, pointing out that the SUPER key is what we call it on any non-MSFT OS.  It is the same key, but when reading Linux how-to guides, documentation, and blog posts, understanding that terminology difference could be critical.

---

### Post by erotavlas on 2022-09-02
> **TheFu said:**
> Whooosh.  I was attempting to be funny, pointing out that the SUPER key is what we call it on any non-MSFT OS.  It is the same key, but when reading Linux how-to guides, documentation, and blog posts, understanding that terminology difference could be critical.

If you prefer I can call it Super, but it remains the button with the Windows. :o

---

### Post by TheFu on 2022-09-02
> **erotavlas said:**
> If you prefer I can call it Super, but it remains the button with the Windows. :o

Whatever.  
[https://en.wikipedia.org/wiki/Super_key_(keyboard_button)](https://en.wikipedia.org/wiki/Super_key_(keyboard_button))
[https://help.ubuntu.com/stable/ubuntu-help/keyboard-key-super.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-key-super.html.en)

---

