---
title: "Dell Inspiron 6400"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by jeenuv on 2007-03-04
Hi Forum,

This is my frist post to this forum (Obviously I'm stuck on something).

Mine is a DELL Inspiron 6400 with Intel 945GM graphics chipset. I would like to have a driver isntalled (for wide screen resolultion), but I can't find one (or an appropriate one). I mainly referred [http://www.linux-on-laptops.com](http://www.linux-on-laptops.com) but I couldn't find anything matching my need. If any body here know how to go for it, that would be great.

Thanks in advance
Jeenu V

---

### Post by caldevil on 2007-03-05
AFAIK wide screen resolution works out of the box with fglrx driver. So you may just want to install propriety driver for your video card. Hope this helps you:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by steel_lady on 2007-03-05
> **jeenuv said:**
> Hi Forum,

This is my frist post to this forum (Obviously I'm stuck on something).

Mine is a DELL Inspiron 6400 with Intel 945GM graphics chipset. I would like to have a driver isntalled (for wide screen resolultion), but I can't find one (or an appropriate one). I mainly referred [http://www.linux-on-laptops.com](http://www.linux-on-laptops.com) but I couldn't find anything matching my need. If any body here know how to go for it, that would be great.

Thanks in advance
Jeenu V

I have the same laptop and the same problem. People were trying to help me and puting some strange packages. I have better resolution now but still many fonts are displayed so ugly like from an old photocopy machine. I don't know if windows drivers that we have could be adjusted to use for this...

---

### Post by jeenuv on 2007-03-05
You said, you have better resolutions now - would you mind telling me how you achieved this?

---

### Post by steel_lady on 2007-03-05
> **jeenuv said:**
> You said, you have better resolutions now - would you mind telling me how you achieved this?

I wish I could!  I spent nights on ubuntu channel and people were giving different suggestions and commands and I was just doing copy/paste to terminal and then after one resetting it was finally working. I think they found some thread about some packages that might help but they were not sure. I am sorry. Do you also have SD card reader issue? Maybe we should stay in contact if we discover something new about out laptops. Good luck!

---

### Post by jeenuv on 2007-03-06
> **caldevil said:**
> AFAIK wide screen resolution works out of the box with fglrx driver. So you may just want to install propriety driver for your video card. Hope this helps you:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

:( That didn't. The link is for ATI cards! Mine is intel 945GM!

---

### Post by jeenuv on 2007-03-06
> **steel_lady said:**
> I wish I could!  I spent nights on ubuntu channel and people were giving different suggestions and commands and I was just doing copy/paste to terminal and then after one resetting it was finally working. I think they found some thread about some packages that might help but they were not sure. I am sorry. Do you also have SD card reader issue? Maybe we should stay in contact if we discover something new about out laptops. Good luck!

I too came across differet methods to get that working from different people. But, by any chance, do you remeber which one you did try last? I haven't tried with the memory card yet. May be I'll take up that once I'm done with this (If ever).

---

### Post by Ocxic on 2007-03-06
sudo apt-get install 945resolution
and reboot

---

### Post by nicorubiolo on 2007-03-13
It is sudo apt-get install 915resolution and then reboot...

945 does not exists.

regards.

---

