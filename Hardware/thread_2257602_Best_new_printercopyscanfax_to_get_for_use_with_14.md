---
title: "Best new printer/copy/scan/fax to get for use with 14.04LTS"
date: 2014-12-21
forum: Hardware
---

### Post by cybrsaylr on 2014-12-21
Have a wired HP printer, used it for years but want to get a new one that does it all.

Seems most everything is wireless now. Would like to know what's the best model/make that installs with the least problems? Never used one of these multi-combo printers before with Ubuntu. Also never used one that can fax with Ubuntu. Does both fax and scan install trouble free with Ubuntu now? Never used or installed one that can fax before.

---

### Post by carl4926 on 2014-12-21
HP has by far the best support
I can't give you a model but HP supply information relating to support so it will be easy enough to find

I have several friends with such printers and they work. Not sure about fax. I don't know anyone that uses that now...

---

### Post by kurt18947 on 2014-12-21
As Carl4926 says, HP is known to be very good.  I've had quite good luck with Brother using their installer script and I recently bought a refurbished Samsung laser multi-function for <$100 that also has a command line installer very much like Brother. If you find a printer that interests you, I would go to the manufacturer's web site support section and look for Linux support.  If you find linux drivers or signs of linux support, research further.  If there is no indication of linux support move on.

---

### Post by cybrsaylr on 2014-12-21
HP was always my first choice and had good luck with them. Lately through other brands are cheaper that do it all, print/copy/scan/fax. Have found printers usually install easy. It's scan and fax that can be a pain. See many new printers do it all and are wireless now and include fax at no extra cost.

Carl,
 My sister has fax and still uses it often but she still uses Win XP. Had dealings with a company last week and their rep said if I fax them a necessary document, they will resolve the issue right then and there! Couldn't do that so ended up going to an Office Max who did it next day for a couple bucks charge.

Kurt,
Saw a Samsung laser that did it all for ~$100, along with Brother, Cannon, and Epson that all were less than HP equivalents but just didn't know how tricky the install would be.

---

### Post by UltimateCat on 2014-12-21
Hi:

I have a HP Envy and it works great with Ubuntu, Debian and Slackware.

The only problem I have with the wireless is if I loose power I have to go to the online Cups website delete the printer and than open the terminal
and go through the hp-setup again.

Aside from that HP makes very good products.

Don't buy a Kodak, they don't work with Linux.

[http://www.bizrate.com/printers/hp-envy-printer/](http://www.bizrate.com/printers/hp-envy-printer/)



Good luck

---

### Post by sammiev on 2014-12-21
Epson for me after using many over the years.

---

### Post by houstonbofh on 2014-12-22
All-in-one solutions are a compromise and never last as long as they should.  I recomend a good color laser printer, a Cannon CanoScan scanner that is small protable and USB only like [http://www.amazon.com/Canon-Office-Products-LiDE120-Scanner/dp/B00LN0NUOO/ref=sr_1_3](http://www.amazon.com/Canon-Office-Products-LiDE120-Scanner/dp/B00LN0NUOO/ref=sr_1_3)  and an Internet fax service via e-mail.

You will get better quality out of the separate pieces, and they will last MUCH longer.  And that little portable scanner is wonderful.  Power from USB so take it with your laptop.  And e-fax beats paper any day of the week.

---

### Post by cybrsaylr on 2014-12-27
houstonbofh,
Agree, have always bought separate printers and scanner knowing they last longer than 'All-in-ones', just was hoping were made more to last now. Have a 16 yr old UMax scanner that still works with XP but is not Linux usable. 

As for fax will look more into Internet fax service via e-mail. Didn't know about them or how they work. 

Thanks for the tips guys.

---

### Post by kurt18947 on 2014-12-29
> **cybrsaylr said:**
> 
..........................................
Kurt,
Saw a Samsung laser that did it all for ~$100, along with Brother, Cannon, and Epson that all were less than HP equivalents but just didn't know how tricky the install would be.

Sorry I'm a bit late on this.  I didn't find the Samsung installation tricky at all, but then I'm familiar with Brother's installer which is similar.  It's just a matter of downloading Samsung's uld (Universal laser driver) and extract it to a known location.  The rest is via the command line.  cd to the location e.g. cd /Downloads/uld.  You'll find a few files in that folder.  Among them should be something about printer-install and scanner-install.  Run those (requires a SUDO account) then go to your distro's printer app, install a new printer and it should find any Samsung printers visible via USB or network.  Click the install or add button and you should be in business.  The scanner is even simpler, just run the script and the scanner should be found.  The only problem i had was if I already had a Brother scanner installed; the Samsung would not be found.  If I did a fresh install and installed the Samsung first then the Brother, both scanners would be found. I hope this is of some help.

There was one thing I found peculiar but it may be normal.  If I copied the Samsung installer files to a flash drive and from there to a PC to install, I had to set the 'executable' bit.  If I downloaded directly from Samsung, the executable bit was already set.  I'd seen this behavior with optical media with files being read-only. I thought when copying to/from flash media the execute bit would remain set.  It doesn't look like it.

---

