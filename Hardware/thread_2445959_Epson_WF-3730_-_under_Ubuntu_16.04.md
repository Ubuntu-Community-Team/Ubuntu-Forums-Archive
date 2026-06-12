---
title: "Epson WF-3730 - under Ubuntu 16.04"
date: 2020-06-22
forum: Hardware
---

### Post by Priswell on 2020-06-22
tl;dr: install ```
sudo apt install printer-driver-escpr
``` as a printer driver for Epson printers if you can't find one to work.

I had to get a new printer. My Epson Workforce 840 died. I like Epson, so I got another one, the Epson Workforce Pro (WF-3730). 

I had recently upgraded my husband's computer to Ubuntu 20.04, and I was able to download the .deb file from a link on the Epson's site and install the printer, but my older 16.04 desktop was being more problematic. I've been slow to upgrade, for a couple of reasons. I use my computer long hours and *relentlessly*, and it's hard to find a time to upgrade. The Covid-19 situation makes it worse, and rely on my computer even more. I could upgrade to at least 18.04 with a software upgrade, but I prefer a clean install. The final issue is that my computer use UEFI to boot, and I don't have experience with that - I'm a regular CMOS baby.

So, I'm running around with my hair on fire, sneakernetting/emailing files to print, and today I spent some serious quality time trying to get/install Epson's drivers. No dice. Then I found a little notation on 

[http://devmartin.com/blog/2016/04/installing-an-epson-wf-3520-on-ubuntu-16.04-xenial-xerus/](http://devmartin.com/blog/2016/04/installing-an-epson-wf-3520-on-ubuntu-16.04-xenial-xerus/)

regarding installing using Ubuntu provided drivers. I installed those Ubuntu-given drivers using the code above, and now the printer at least, works, and I'm grateful. Thought I'd give a good report on a reasonably happy ending, and my solution to any who might need it.

---

