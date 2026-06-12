---
title: "Bad Hardware - Ubuntu Won't Boot"
date: 2018-10-17
forum: Hardware
---

### Post by steve77777772 on 2018-10-17
My 8 year old PC that I assembled is on its last legs I believe. There are problems with the SATA ports from time to time that I was hoping were software related. 
A few months ago I did a fresh install of Ubuntu 18.04 and added an SSD drive. All was well until last night it wouldn't boot up after rebooting. Updating the BIOS to the latest made no difference. I noted the errors and then booted from the Ubuntu 18.04 Live CD. 

I was able to get the data off of the drive, but (and this is the important part) I got the same errors booting up form the Live CD as from the hard drive.

```
ACPI Exception: Could not find/resolve named package element: LNKD (20170831/dspkginit-381)
```

Here's a photo of boot from the Live CD:
[IMG]https://drive.google.com/file/d/1PTkWPEjL1Sg0GptYTFRT9ZWgzucD8hIX/view?usp=sharing[/IMG][IMG]https://i.imgur.com/pkoBSlh.jpg[/IMG]

Based on this info does it look like bad motherboard? I'm asking because if that is highly likely I'll buy a different motherboard and re-use the rest of the parts.  DDR4 is $$$ these days and other the old system (not my primary machine) had very decent performance for my needs.
The system has a AMD Phenom II X4 955  and Gigabyte motherboard.

Thanks!
[IMG]https://drive.google.com/file/d/1PTkWPEjL1Sg0GptYTFRT9ZWgzucD8hIX/view?usp=sharing[/IMG]

---

### Post by him610 on 2018-10-17
I may be wrong, but I do not see anything that indicates a mainboard issue. Maybe corrupted installation software? What are the specs of the SSD in your system? System specs? 
If you can get it to boot, how about showing the output of* inxi -F *from command line?
> There are problems with the SATA ports from time to time
Can you describe the problems?

---

### Post by steve77777772 on 2018-10-18
> **him610 said:**
> I may be wrong, but I do not see anything that indicates a mainboard issue. Maybe corrupted installation software? What are the specs of the SSD in your system? System specs? 
If you can get it to boot, how about showing the output of* inxi -F *from command line? 

Did you not see what I wrote in my post above?

**I got the same errors booting up form the Live CD as from the hard drive.**

This was with the SSD drive disconected

> Can you describe the problems?

I wrote - [B]The system won't boot.
[/B]
I ordered an identical main board and have save Clonezilla images that can be restored.

---

