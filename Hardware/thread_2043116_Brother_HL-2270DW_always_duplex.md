---
title: "Brother HL-2270DW always duplex"
date: 2012-08-15
forum: Hardware
---

### Post by bsharitt on 2012-08-15
I was able to successfully install the drivers for the Brother HL-2270DW wireless laser printer via [this script]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104"). It technically prints everything okay, but for multiple pages, it duplexes everything, no matter what the setting are set for the printer. So for things I don't want duplexed, I have to print them one page at a time. 

Has anyone else encountered this problem and solved it? I've tried to change the setting via the Ubuntu printer setting and the direct CUPS settings via the web controls for CUPS.

---

### Post by n08rak35 on 2012-10-08
I have been running that printer for a couple of years and not found a way to fix that problem either...

---

### Post by pdc on 2012-10-08
I don't have the answer

.....but I wonder if some google searching on editing the .ppd might be of value.....

I enclose a thumbnail of the ppd file from a Canon that I have; that has a duplex capability; (I confess I have just left it as duplex..)

....I wonder if you use gedit to look at your ppd......

........I wonder if you are having this issue with LibreOffice;

......and I wonder if you change the settings there;

if you issue the command

> ln -s /usr/lib/libreoffice/program/spadmin ./spadmin

.......this sets up a link so your system can find spadmin easily

If you then type the command

> ./spadmin

you get the LibreOffice settings page

..select properties for your printer..

I enclose a thumbnail of the settings for my printer..

---

