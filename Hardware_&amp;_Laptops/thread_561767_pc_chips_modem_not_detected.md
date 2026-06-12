---
title: "pc chips modem not detected"
date: 2007-09-28
forum: Hardware &amp; Laptops
---

### Post by enterprize on 2007-09-28
Hi All;

I have a computer with a pcchips HSP 56 micromodem installed in it.  Ubuntu does not detect the modem. I have the linux driver that I downloaded from pcchips.  Seeing I am a newbie to linux I am not sure how to install the updated driver.  What is the best way to get this done? Any help would be greatly appreciated.  

Thanks
Will:confused::(

---

### Post by geraldm on 2007-09-28
The HSP 56 micromodem is an analog modem, or a software modem, or winmodem or
linmodem.  It can be helpful to know more about the hardware to get it working, as
sometimes this is packaged with another sound chip, such as cmi8738, and in such cases 
you must enable sound and turn it on to get the modem to work.

With a linux driver, when you decompress the downloaded driver, there should be a
README file or an INSTALL file or documentation that should guide you on how to get
the package operational.  Look for it in the package.

If you do need to post to seek help, provide helpful information on the type of ubuntu OS, 
possibly the URL to the package you downloaded, or the package-version.  There are lots
of forums to google for your modem type: forums.modemhelp.net linmodems.org and others.
There may be information in [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/) ( I did not find any 
detailed howto for the software modem, but the documentation would be there if you 
are successful and would write it ! )  

Analog modems often are not in the hardware that is detected.

Gerald

---

