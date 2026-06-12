---
title: "can't figured out if I can use ATI proprietary driver on 9.04..."
date: 2009-04-27
forum: Hardware
---

### Post by SOME1 on 2009-04-27
Hi, 

I am using ibm thinkpad t43p with an ATI graphic card. 
the output of the command

lspci -nn | grep VGA
> 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc M24GL [Mobility FireGL V3200] [1002:3154] (rev 80)

In ATI site I saw that firegl v3200 is supported in the new driver, but ubuntu don't give me the option to install the proprietary driver. 
I don't want to destroy anything in my system by installing the driver from ati site and get a black screen or something like that on one hand, but the open driver is really not good enough for me. 

can someone help me figured out if I can use ati driver or not? 

thanks a lot.

---

### Post by StuartN on 2009-04-27
> **SOME1 said:**
> Hi, 

I am using ibm thinkpad t43p with an ATI graphic card. 
the output of the command

lspci -nn | grep VGA


In ATI site I saw that firegl v3200 is supported in the new driver, but ubuntu don't give me the option to install the proprietary driver. 
I don't want to destroy anything in my system by installing the driver from ati site and get a black screen or something like that on one hand, but the open driver is really not good enough for me. 

can someone help me figured out if I can use ati driver or not? 

thanks a lot.

I don't see your card supported in the release notes for the latest driver Catalyst 9.4 ([https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_94_linux.pdf)). Check through the driver selection at [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx) and see if the version is 9.4, if not then you will have to use the open source drivers in Ubuntu Jaunty. You can see which driver is in use with "lshw -C video".

---

### Post by SOME1 on 2009-04-28
thanks a lot for the reply. 
[in this page]("http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.2&lang=English") I saw the the driver for firegl 3200v is out just a few days ago so I think it's the the new one... am I wrong? 

thanks again.

---

### Post by StuartN on 2009-04-28
> **SOME1 said:**
> thanks a lot for the reply. 
[in this page]("http://support.amd.com/us/gpudownload/fire/Pages/fire_linux.aspx?type=2.4.3&product=2.4.3.3.2.3.2&lang=English") I saw the the driver for firegl 3200v is out just a few days ago so I think it's the the new one... am I wrong? 

thanks again.

That link is to version 8.583 of the ATI Catalyst driver. Ubuntu Jaunty requires version 9.4, so your card will revert to support from one of the open source drivers.

You can see how your card will perform by running the Live CD without installing Jaunty.

---

### Post by SOME1 on 2009-04-28
Thanks a lot :)

---

### Post by William the Conquerer on 2009-05-11
SOME1, how did this go?  Did you ever get ATI Proprietary drivers to work on Jaunty?  I've got the T43p too and I'm investigating drivers that work because I want to use Boxee on my laptop and the open source drivers don't seem to work...

---

### Post by SOME1 on 2009-05-11
> **William the Conquerer said:**
> SOME1, how did this go?  Did you ever get ATI Proprietary drivers to work on Jaunty?  I've got the T43p too and I'm investigating drivers that work because I want to use Boxee on my laptop and the open source drivers don't seem to work...
well, ATI Proprietary don't work and probably never work from 9.04 version. the only drivers that work now is the open source drivers. I still can't get boxee to work with the open drivers. xbmc work but not boxee yet. 
we try to find a solution in [this thread]("http://forum.boxee.tv/showthread.php?t=7676").

---

