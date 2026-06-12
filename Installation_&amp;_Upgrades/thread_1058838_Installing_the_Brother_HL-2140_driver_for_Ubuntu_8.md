---
title: "Installing the Brother HL-2140 driver for Ubuntu 8.0.4"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by badaveil on 2009-02-03
Extracted from [http://solutions.brother.com:](http://solutions.brother.com:)

BEFORE THE INSTALLATION: Pre-required Procedure Requirement
1. "sudo aa-complain cupsd" command is required before the installation.
2. "sudo mkdir /usr/share/cups/model" command is required before the installation.

Note:
Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)
2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model
3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)

Related distributions
Ubuntu 8.04/8.04.1, Ubuntu 8.10
Related products/drivers
cupswrapper printer/PC-FAX drivers

However having done that, I still had to make a few changes because the printed test page showed 2 half-test page on one page. Under make and model, there is a need to replace the Foomatic version for the "Brother HL2140 for CUPS". The steps are as follows:

system>administration>printing>setting>make and model>change>provide ppd file>select a file>file system>usr>share>cups>model>hl2140.ppd>open>forward>use the new ppd as is>apply

Other than that, I went over to printer options, changed the default media size from letter to A4, changed resolution from 600dpi to HQ1200dpi, set the toner save to "on", made a print test page and the output was just right!

---

### Post by Vendaval on 2009-02-18
Thank you so much for that! I've been trying to re-install the drivers this whole time, but that solved all of the problems.

---

### Post by badaveil on 2009-02-18
> **Vendaval said:**
> Thank you so much for that! I've been trying to re-install the drivers this whole time, but that solved all of the problems.

Thank you for making my day coz my effort sharing this information is not put to waste. ;)

---

### Post by sa-mejia on 2009-06-24
I would like to thank you too.  

I did not follow the first steps of your how-to, but followed instead those in [http://forums.linux-foundation.org/read.php?24,7128,9445](http://forums.linux-foundation.org/read.php?24,7128,9445).  However, after doing so, they did not quite work, and I had to apply the last part of your helpful walk-through.

That is to say, I had to:

1. sudo mkdir /usr/share/cups/model

2. Install cupswrapperHL2140-2.0.2-1.i386.deb

3a. Goto: system>administration>printing>setting>make and model>change>provide ppd

3b. file>select a file>file system>usr>share>cups>model>hl2140.ppd>open>forward>use the new ppd as is>apply


Santiago.

---

### Post by badaveil on 2009-06-25
We must really thank Brother of Japan. They spent 3 weeks with me separated by their December public holidays but they came back later and continued until they got word from me that I managed to install the drivers. That's Brother of Japan for you:D

---

### Post by ccroy on 2010-02-28
> **badaveil said:**
> Extracted from [http://solutions.brother.com:](http://solutions.brother.com:)

system>administration>printing>setting>make and model>change>provide ppd file>select a file>file system>usr>share>cups>model>hl2140.ppd>open>forward>use the new ppd as is>apply

Other than that, I went over to printer options, changed the default media size from letter to A4, changed resolution from 600dpi to HQ1200dpi, set the toner save to "on", made a print test page and the output was just right!

Thank You! :D

I just bought a 2140 today. I could not get it to print on 8.10 till I read what you did. I never would have found that ppd file.

Thanks,

Chris

---

### Post by badaveil on 2010-02-28
> **ccroy said:**
> Thank You! :D

I just bought a 2140 today. I could not get it to print on 8.10 till I read what you did. I never would have found that ppd file.

Thanks,

Chris

I am happy for you and we must first thank Brothers of Japan for showing us the way.By the way I've upgraded to Ubuntu 9.10 and the printer still works well.

---

