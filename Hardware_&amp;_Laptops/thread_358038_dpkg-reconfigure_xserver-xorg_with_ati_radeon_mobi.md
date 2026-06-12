---
title: "dpkg-reconfigure xserver-xorg with ati radeon mobility x1300"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by bns on 2007-02-10
I have a Dell Inspiron with an ATI Mobility Radeon x1300.  I'm trying to get the video driver working properly.  I downloaded the latest driver from ATI and installed it per the instructions from their website.  Several people posted on the forums that they then ran
> dpkg-reconfigure xserver-xorg

When I did that and restarted the system locked up.  Probably because I have no idea what I'm doing.  Can anyone tell me what values I should set for the xserver?

---

### Post by kevinatkins on 2007-02-10
Hi,

you might need to prevent the ati-agp module from being loaded when the fglrx module is loaded - if it does get loaded, it will cause the symptoms you are seeing. for more detailed information, please refer to this thread -

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Oh, and one more thing - you'll need to make sure the fglrx module is loaded at boot - append fglrx to the end of /etc/modules.

---

### Post by bns on 2007-02-10
That didn't help.  Thanks for the reply though.  My problem seems to be similar to this

[http://ubuntuforums.org/showthread.php?p=2134848#post2134848]("http://ubuntuforums.org/showthread.php?p=2134848#post2134848")

I can make the video work as long as I don't reconfigure xorg after installing the video driver.  Seems strange to me.

---

