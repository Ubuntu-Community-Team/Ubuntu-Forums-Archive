---
title: "Network laser jet recommendations?"
date: 2011-07-16
forum: Hardware
---

### Post by BradleyAtkins on 2011-07-16
Hi folks

At home I have many Windows XP machines (My Wife's) and also Linux Ubuntu machines (Mine).

I am interested in any recommendations for laser jet printers that are wireless enabled and have drivers for both operating systems.

Thanks in advance :)

---

### Post by Bucky Ball on 2011-07-16
We recently bought the Brother HL-2270DW laserjet. It rocks. Wireless and works with either.

It fits our needs perfectly but maybe not yours:

Mono (black and white), duplex (double sided).

Was $190 AUS, we paid for the three year warranty. Cheap. Works great but was a hassle to work out@! Have been meaning to write a how to.

---

### Post by ajgreeny on 2011-07-16
Lots of HP machines also work very well, both wirelessly (I have one) and with USB cable.

See [HpAllInOne]("https://help.ubuntu.com/community/HpAllInOne")  and follow the links to see supported machines.

---

### Post by walt.smith1960 on 2011-07-16
I have 2 Brother MFDs networked.  One is an older MFC-7820N-wired networking-and MFC-6490CW-wireless inkjet MFD.  Both were quite straightforward and manufacturer support is available.  HP probably has better support but if you have reasonable Ubuntu savvy either brand should work for you.  HP does have a Linux utility available-HPLIP- which offers some benefits over what is available in Ubuntu.

---

### Post by Bucky Ball on 2011-07-16
+1. HP play well with the Linux/FOSS community. ;)

---

### Post by BradleyAtkins on 2011-07-17
The HP All in one machines just seem to be desk jets not lasers.

The brother looks interesting. Anyone know if it supports WPA?

---

### Post by Bucky Ball on 2011-07-17
> **BradleyAtkins said:**
> Anyone know if it supports WPA?

Yes. 

> WEP 64/128 bit, WPA-PSK (TKIP/AES), WPA2-PSK (AES), APOP, POP before SMTP, SMTP-AUTH... from here:

[http://www.brother.com.au/portals/0/Brother/Brochures/HL-2270DW_Brochure.pdf](http://www.brother.com.au/portals/0/Brother/Brochures/HL-2270DW_Brochure.pdf)

Printer:

[http://www.brother.com.au/products/printers/monochrome_laser_printers/hl-2270dw.aspx](http://www.brother.com.au/products/printers/monochrome_laser_printers/hl-2270dw.aspx)

---

### Post by walt.smith1960 on 2011-07-18
My Brother wireless MFD is running WPA2.  One thing that may or may not be an issue.  The wireless on mine is G speed, not N.  I don't know if that will impact your network speed or not.  To know which Brother devices are supported under Linux you can reference their driver page:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
Brother does not offer 64 bit drivers but their drivers work fine in 64 bit systems, you have to do a command line install. They have examples of the commands that you can copy & paste substituting the correct file name.  The 32 bit installs can be done via GDEBI or Ubuntu Software Center if you prefer.  Be sure to read through the "before the install". Most items won't apply, 2 or 3 do.  If you look around Brother's site you can find manuals and network setup supplements for most models.

---

### Post by BradleyAtkins on 2011-07-20
> **Bucky Ball said:**
> We recently bought the Brother HL-2270DW laserjet. It rocks. Wireless and works with either.

It fits our needs perfectly but maybe not yours:

Mono (black and white), duplex (double sided).

Was $190 AUS, we paid for the three year warranty. Cheap. Works great but was a hassle to work out@! Have been meaning to write a how to.

Hi Bucky

Would appreciate that how to if you've a mind to help.

Perhaps we could go through this here and work it out for others to find.

Brad

---

### Post by BradleyAtkins on 2011-07-24
Well that wasn't too painful, brother supply drivers

```
http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html

http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html

```
The instructions are straightforward and the printer now works wirelessly from my ubuntu laptop.

I also downloaded printershare from android apps and installed it on my Xoom. Found the printer straight away and prints just fine. I'll try getting the phone to print later using the same app.

So the brother seems a good choice for a mono laser jet for windows and ubuntu.

---

### Post by Bucky Ball on 2011-07-24
Did you go for the Brother HL-2270DW BradleyAtkins?

---

### Post by BradleyAtkins on 2011-07-24
Yep, that's the one.

---

