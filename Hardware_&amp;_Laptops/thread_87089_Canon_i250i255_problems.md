---
title: "Canon i250/i255 problems"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by sheryl on 2005-11-07
Hi, I've been using Hoary for a while now and I have not gotten my printer to work. It's a Canon i255 but from what i understand i250 drivers work too.

Anyhoo I've tried everything, went to the Canon website followed the instructions to install the drivers for linux, nothing! rebooted the computer with the printer on, also nothing. 

i typed sudo tail -f /var/log/cups/error_log in the command line and then launched a test page but nothing happens: here's the log:

I [07/Nov/2005:14:23:38 +0100] Full reload is required.
I [07/Nov/2005:14:23:39 +0100] LoadPPDs: Read "/etc/cups/ppds.dat", 2752 PPDs...
I [07/Nov/2005:14:23:39 +0100] LoadPPDs: No new or changed PPDs...
I [07/Nov/2005:14:23:39 +0100] Full reload complete.
I [07/Nov/2005:14:23:49 +0100] Adding start banner page "none" to job 17.
I [07/Nov/2005:14:23:49 +0100] Adding end banner page "none" to job 17.
I [07/Nov/2005:14:23:49 +0100] Job 17 queued on 'i255 ver.2.3-1' by 'sheryl'.
I [07/Nov/2005:14:23:49 +0100] Started filter /usr/lib/cups/filter/pstops (PID 9 131) for job 17.
I [07/Nov/2005:14:23:49 +0100] Started filter /usr/lib/cups/filter/pstocanonbj ( PID 9132) for job 17.
I [07/Nov/2005:14:23:49 +0100] Started backend /usr/lib/cups/backend/usb (PID 91 33) for job 17.
I [07/Nov/2005:14:27:06 +0100] Adding start banner page "none" to job 18.
I [07/Nov/2005:14:27:06 +0100] Adding end banner page "none" to job 18.
I [07/Nov/2005:14:27:06 +0100] Job 18 queued on 'i255 ver.2.3-1' by 'sheryl'.
I [07/Nov/2005:14:27:06 +0100] Started filter /usr/lib/cups/filter/pstops (PID 9 239) for job 18.
I [07/Nov/2005:14:27:06 +0100] Started filter /usr/lib/cups/filter/pstocanonbj ( PID 9240) for job 18.
I [07/Nov/2005:14:27:06 +0100] Started backend /usr/lib/cups/backend/usb (PID 92 41) for job 18.


So if anyone can help me, please please do so cause my printer's been sitting here for like almost a year! thanks, i'll be really really grateful!

ps: oh when i try to add a printer, there are two Canon i255s automatically detected.. but i tried using both, to no avail :(

---

### Post by Teroedni on 2005-11-07
you got no erreors when you installed??



Could you link where you download the driver?

---

### Post by Teroedni on 2005-11-07
[http://www.canon.co.nz/products/printers/colour_bj_printers/i250_drivers.html](http://www.canon.co.nz/products/printers/colour_bj_printers/i250_drivers.html)


is it the
File: bjfilter-2.3-0.tar.gz?
[http://www.linuxforums.org/forum/topic-34535.html](http://www.linuxforums.org/forum/topic-34535.html)
maybe that help

---

### Post by sheryl on 2005-11-07
yep! i got the drivers from the canon new zealand website, and nope, there were no errors!

when i try to print a test page i used to get a blinking light but now nothing happens, not even a blinking light! my driver does show up when i try to add a printer though so is that a plus point? there weren't any errors when i installed the drivers..

maybe i should try installing again? sorry but i'm a newbie, could you tell me how to reinstall them? 

thanks a whole lot ;)

---

### Post by Teroedni on 2005-11-07
Okay i see there are several drivers there. I think the cups driver is better to try

[http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjcups-2.3-0.tar.gz](http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjcups-2.3-0.tar.gz)
or

[http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjcupsmon-2.3-0.tar.gz](http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjcupsmon-2.3-0.tar.gz)

maybe one of thoose wil function better:)

---

### Post by sheryl on 2005-11-07
:( according to the guide, i installed all the additional cups/etc etc (including the two links you gave me)

but still.. nothing!!

---

### Post by Teroedni on 2005-11-08
so you got no error on installing?
use the cups driver [http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjcups-2.3-0.tar.gz](http://www.canon.co.nz/drivers/confirm.aspx?f=http%3a%2f%2fdownload.canon.com.au%2fbj%2fi250linux%2fbjcups-2.3-0.tar.gz)

could you post the whole process  of it in pastebin,
[http://pastebin.com/](http://pastebin.com/)
so can i look at it and see if i find anything.



if that not work we may try with ghostscript
[http://prdownloads.sourceforge.net/espgs/espgs-7.07.1-source.tar.gz?use_mirror=peterhost](http://prdownloads.sourceforge.net/espgs/espgs-7.07.1-source.tar.gz?use_mirror=peterhost)
If not you may have to use wine in order to get it to work:(

Anyone else been succesfull in installing this driver?

---

### Post by arctosh on 2005-11-24
hai everyone... i am new for this ubuntu linux... i just using this os for the past 2 days... now i had same prob how to configure [COLOR="Red"]canon i255 [/COLOR]... i really dun understand wat u all post up's there... plzz do help me... it make me sick to switch os everytime i wanna print notes or document....plz explain in detail...thx

---

### Post by vivek_yadav on 2006-10-15
i posted the same thing on linuxforums also hoping someone might solve the problem..

need help with canon i255 printer. anyone succeeded yet?

i jus installed ubuntu
i have canon i255

i have got the drivers in the form .rpm files and the .gz filesfrom the canon's new zealand web site
[http://www.canon.co.nz/products/printers/colour_bj_printers/i250_drivers.html](http://www.canon.co.nz/products/printers/colour_bj_printers/i250_drivers.html)

then i went to [COLOR="DarkOrange"]system>administration>printing[/COLOR] and then i tried to add printer. it detected the printer as canon i255 correctly. i pressend next. then it asked me to select the drivers from the list. i255 was not there in the list. so i selected [COLOR="DarkOrange"]install driver[/COLOR] then selected the ppd file  for i255 which i had extracted from the driver package i had downloaded earlier from tht NZ site. and then it added the printer in the list.

but sadly it wont print.  :confused:   even the light wont blink and in the printer jobs it shows the printing job as 'stopped'
what did i do wrong? can someone please help?   :(

---

### Post by Sef on 2006-10-15
Checked [LinuxPrinting]("http://linuxprinting.org/printer_list.cgi?make=Canon") usually the i series doesn't work well at all, if it works at all. You printer is not listed, but others around it work poorly, if at all.

---

### Post by vivek_yadav on 2006-10-15
oh..  so no hope??  :(

---

### Post by bedfojo on 2006-10-15
If you speak French, I got my i250 working just fine using this page. Or just babelfish it.

[http://doc.ubuntu-fr.org/materiel/imprimante_canon_i250](http://doc.ubuntu-fr.org/materiel/imprimante_canon_i250)

---

### Post by baryah on 2007-03-21
the driver mentioned in the french page does not work for i255 -- even though it shows i255 to be available. I have the driver for i255 for fedora. I 'm going to try to make it work on ubuntu and let u know

---

### Post by basibanget on 2007-08-18
geez I got the same problem and I was hoping I could get the answer here but no. one of my friend [write in indonesia]("http://fajran.web.id/tutorial/canon-i255-di-debian"). he used the ldd command
```
ldd /usr/local/bin/bjfilteri255
```

I've tried using that but didn't solve my problem. anything new? I've got an office with 5 same printers and I am suppose to make them work in Ubuntu.

---

### Post by vilbara on 2007-11-04
I've got my Canon i250 working under Ubuntu Gutsy following instructions on the french page mentioned above.

The only difference was the last command:
sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.2

---

