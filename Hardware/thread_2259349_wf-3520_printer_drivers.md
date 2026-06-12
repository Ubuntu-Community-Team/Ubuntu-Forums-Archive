---
title: "wf-3520 printer drivers"
date: 2015-01-03
forum: Hardware
---

### Post by raf7 on 2015-01-03
Another printer problem.  Newbie having a problem getting a printer to work.  No printer driver for this printer on the list of wf.. drivers.  Epson is a common printer, I think....

---

### Post by Mike_Walsh on 2015-01-03
Hallo, raf7.

Yes, you're quite correct in your assumption; Epsons ARE common printers.

You don't say which version of Linux you're using; I assume you're running Ubuntu? I only ask, because if you are, then you want the same driver that I use on my SX218.....at least, according to Epson's download page.

Epson don't make life easy for Linux users; they won't even admit to doing Linux drivers.....they insist they 'don't do Linux'.....

Let us know which version you're using; and specs of your machine would help, too.....CPU, RAM, graphics adapter, stuff like that, please.

Regards,

Mike. ;)

---

### Post by raf7 on 2015-01-03
Hello Mike....   HP dv7   7g ram  500g hd   That's all I remember.  Machine is reloading now due to corruption of playing, with only hacking mentality.  Umbuntu 14.10  thanks.....

---

### Post by Mike_Walsh on 2015-01-03
Well, even though you're using an HP system, you are at least using an Epson printer.....these are easy to get running (usually!) HP's own printers are a PITA to install.....

My old Compaq is basically an HP (dates from the year HP bought out Compaq), and it works great with my Epson SX218 printer/scanner.

Are you using 64 or 32-bit? Need to know as drivers are different.

Regards,

Mike.

---

### Post by raf7 on 2015-01-03
Intel i7 quad core @ 1.6 ghz.  64 bit  gallium 0.4 redwood graphic......

---

### Post by Mike_Walsh on 2015-01-03
Okay. Have Googled your machine; definitely 64-bit.

You need to go to the following two pages:-

For printer driver:
[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=32949&DSCCHK=fe91afdd267711fc4a49aa597d911d10095c2867](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=32949&DSCCHK=fe91afdd267711fc4a49aa597d911d10095c2867)

And for scanner driver & data package:
[http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=33473&DSCCHK=358a41ac4f7191b7847c24f698a73a3ecc33dc12](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=33473&DSCCHK=358a41ac4f7191b7847c24f698a73a3ecc33dc12)

In both cases, scroll to the bottom of the page and click on 'Accept'.
This will then extend the page; scroll further down, and

For printer;
Download the amd_64.deb version. 

For scanner; 
Download the iscan_2.30.0-1~0.1.ltdl7_amd64.deb **scanner** package, and the iscan-data_1.33.0-1_all.deb **data** package.

When you've downloaded these, they will install through the Software Centre. For the printer driver, there's a little trick to perform first. Open a terminal, and enter:

```
sudo apt-get install lsb
```

and enter your password. Let this do its thing.

Then, double-click on the printer driver in your downloads folder; it will install via the Software Center. It may take a little while, but then your CPU's more modern than mine, so maybe not! Then repeat this for the scanner and data packages, BUT: [COLOR=#ff0000]**THIS NEXT BIT IS VERY IMPORTANT**[/COLOR]: you MUST install the data package BEFORE the scanner package, as it needs to be able to read the 'data' package to install correctly. Once again, they'll install through the Software Centre.

Hope that helps. Let me know how you get on, please.

There's a couple more little 'tricks' after you've got your drivers installed!


Regards,

Mike.

---

### Post by raf7 on 2015-01-03
I gotta say "wow"...  How does one figure this stuff out.  Well beyond the casual user.  Sure do appreciate the help.  Can't say I know how to reply later on how it goes.  Will be tomorrow before I try it.  NFL playoffs are on tonight......Thanks

---

### Post by Mike_Walsh on 2015-01-03
Plenty of practice, that's how!

Get back to me as and when; there's no rush. I know how you Americans like your football..! Not my bag; I'm more into motorsports, and golf...

If you don't get on with the printer driver as mentioned, there IS another, more full-featured driver available, but I always recommend this one to start with, as it's a wee bit easier to install. I've only been using Linux since last May myself, but in that time I've re-installed these drivers into that many different distros, I could do it with my eyes shut....

And 30-odd years of 'faffing about' with computers in general probably helps, too..!


Regards,

Mike. :)

---

### Post by raf7 on 2015-01-03
Seeing you in the UK,  I thought not to use "football" for our sport.  More into college than NFL, PennState here, but watch it all.  Play when in school, Pacific Univ.  Later and Thanks again.....

---

### Post by Mike_Walsh on 2015-01-03
No worries, as the Aussies say.

Strictly speaking, our 'football' is more correctly called 'soccer'. Your 'football' has more in common with our 'rugby'; which is why we Brits can still understand your game. I don't know what the US view of soccer is..!

I would be interested to know whether this works or not. In theory it SHOULD; but there's a lot of difference between theory, and real-world implementation. There again, there's a lot of mites in a pound of cheese, too...

Catch you tomorrow. Bed's calling...

BTW: As for finding all this stuff out, remember one thing, and you can sort near enough anything out; 'Google is your friend'..!

Regards,

Mike. ;)

---

