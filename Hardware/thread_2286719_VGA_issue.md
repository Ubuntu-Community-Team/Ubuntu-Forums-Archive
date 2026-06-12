---
title: "VGA issue"
date: 2015-07-14
forum: Hardware
---

### Post by Net_Spy on 2015-07-14
Hello,

I've Dell Inspiron shipped with Ubuntu. How do I  test my hybrid graphic card is supported and to switch between Intel and  AMD . 

Below is the out put of lspci. Ive DELL Inspiron 5520 Laptop.

```

VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) 
VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series]

```

Do I need any driver for it? I'm using Ubuntu version 14.

Regards

---

### Post by grahammechanical on 2015-07-14
As this machine was supplied by Dell with Ubuntu pre-installed then the supplier should have made sure that the correct proprietary video drivers were installed. 

There will be a proprietary video driver setting utility installed. It comes with the installation of the proprietary video driver. You will find it through the Dash. I think that you can use that utility to switch between graphic adapters. I think that it is Catalyst Control Centre. You might also want to take a look at this.

[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)

Or search for something similar.

Regards.

---

### Post by Net_Spy on 2015-07-15
how would I check if the driver is installed .

Regards

---

### Post by coffeecat on 2015-07-18
*Thread moved to **Hardware**.*

And free bump

---

### Post by tokyobadger on 2015-07-19
@Net_Spy: that model appears to have shipped with Ubuntu 11.10 or 12.04 as installed by Dell (custom Ubuntu image) - did you purchase the laptop direct from Dell? Who upgraded to 14.x (is it 14.04 or 14.10)? Is there still a support service from Dell? Which country (Dell does not offer linux laptops in all countries)?

You'll have to provide a lot more info before anyone can help

---

