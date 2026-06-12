---
title: "[SOLVED] Choosing HP printer for Ubuntu"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by Jaxilian on 2007-10-30
I would like people to give feedback here about which HP printer they think works good in Ubuntu, what's good and what's bad with 'em.
Please state full modelname, ex HP Photosmart C4380. Is laser better than ink one?

I am thinking of buying a HP printer but I am a bit unsure of what to look for. I am aware of the compability list, but I am more interested in what the Ubuntu community have to say. :)

---

### Post by dacap06 on 2007-10-30
Flodis,

There is no one model of printer, or even type of printer,  that is always best.  Which one is best for you depends on what you print, how often you print, and what your standards are.

For example, I do mostly text and short documents, and not a lot of them.  Mostly I use an ancient HP Laserjet 4 that I bought used around 1999.  It prints with only 600 dpi resolution, but that is good enough for documents.  It's huge cartriges print 6000 documents and are relatively inexpensive -- costing about $90.00.  That makes my per-page costs very low.  Best of all, it is a reliable workhorse that has performed flawlessly for all that time, and has even had very few paper jams.  Even though they have not been produced for over a decade, accessories and parts are still available and sell for reasonable prices.  I bought a used second paper tray for it on e-bay for next to nothing about 3 years ago.

But the LJ4  prints monochrome.  In one way that is good -- per-page costs for monochrome lasers are always much lower than for inkjet printers.  In other ways it is bad -- Its low resolution and monochrome output make pictures and graphics look terrible!

Ink jet printers are not always a good answer either.  I also have an Epson Stylus Color 800 I bought new a number of years ago, but I rarely use it.  I may print color once ever couple of months.  Whenever I do use it I have to dork around with it for an hour or so to unclog the heads so it prints properly.  Ugh!  Cartridges are expensive and don't last very long either.  Double Ugh!

Color lasers are still pretty expensive and are expensive to operate.  They still don't do graphics as well as ink jets either.

So good luck with your selection.  I think you would be well served to post information saying exactly how you intend to use the printer.

---

### Post by Jay.GO on 2007-10-30
Laser printers are good if you print mostly documents , inkjets are better in photo quality.
I have a Hp photosmart c5180 (which has been replaced) works fine for me on gusty.

---

### Post by war59312 on 2007-12-28
I have the HP Photosmart C4380 but sadly the version of HPIJS that comes with Ubuntu 7.10 is out dated as it does not include the PPD for it...

So for only found one for OS X.

Update:

OK sweet I see Version 2.7.7.dfsg.1-0ubuntu5 is available as a pre release. Dang still no PPD file for it...

OK no wonder support was not added till 2.7.10-0ubuntu1, but where can i find it?

Update 2:

OK found it here: [https://launchpad.net/ubuntu/hardy/+source/hplip/2.7.10-5ubuntu2](https://launchpad.net/ubuntu/hardy/+source/hplip/2.7.10-5ubuntu2) Sweet, working great now.. hehe

---

### Post by Jaxilian on 2008-02-05
thanks for info

---

### Post by asnd16 on 2008-04-07
So I am looking to purchase the Photsmart C4380 and just for the wireless . . How does this work with Hardy ? or gusty?    I am interested in the scanning feature . .   is it better to scan to a mem disk to transfer the scans or is it working in Ubuntu.   I noticed that with the following information [http://hplip.sourceforge.net/models/photosmart/photosmart_c4380_series.html]("http://hplip.sourceforge.net/models/photosmart/photosmart_c4380_series.html")   It works with hardy but claims only USB  not parell and no network . . I am assuming that the wireless would be through the network thus canceling out this feature with the wireless . . . errrr soooo can anyone comfirm?

---

### Post by patrickfromspain on 2008-04-25
up here!

My girlfriend has this printer, and works fine using HPlib, in ubuntu 7.10. She installed it using gksudo hp-setup without troubles. Connected to usb, you can also setup it using the gnome stuff, I believe as an HP C4200.

The only bad thing is wireless, since she had to set it up using windows... and then sudo hp-setup in ubuntu. After that it will work just fine.

Hope it can help someone

---

### Post by sputnik925 on 2008-04-30
> **asnd16 said:**
> ...   I noticed that with the following information [http://hplip.sourceforge.net/models/photosmart/photosmart_c4380_series.html]("http://hplip.sourceforge.net/models/photosmart/photosmart_c4380_series.html")   It works with hardy but claims only USB  not parell and no network . . I am assuming that the wireless would be through the network thus canceling out this feature with the wireless . . . errrr soooo can anyone comfirm?

In Ubuntu 7.10 (Gibbon), I just used the system-config-printer.py 0.7.75 (the packaged printing configuration utility) and created a new "LPD/LPR Host or Printer" with the IP address of my C4380 on my local wireless network. I used the HP Photosmart C4200 driver from the included database and it works perfectly over the 802 11g wireless network. I'm not sure why that chart you refer to on sourceforge says no network, because it works for me just fine. Should be the same for Ubuntu 8 (Hardy).

---

### Post by Jaxilian on 2008-05-01
I bought a HP Photosmart C6280 and it works good.

---

### Post by war59312 on 2008-05-20
Yeah super easy setup now in Ubuntu 8.04. :)

Everything works so far...

---

### Post by leona on 2008-05-26
Hi there, I had this working in 7.10 with my C5180 printer, but now on 8.04 and I an't get the hp-setup tool to fire up I get the following when I type
> 
gksudo hp-setup 

> 
............
warning: PyQt init failed. Reverting to interactive mode.
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
......
Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 395, in <module>
    f.output()
  File "/usr/share/hplip/base/tui.py", line 265, in output
    max_screen_width = ttysize()[1]
  File "/usr/share/hplip/base/tui.py", line 175, in ttysize
    return int(vals['rows']), int(vals['columns'])
...........
warning: PyQt init failed. Reverting to interactive mode.
Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 395, in <module>
    f.output()
  File "/usr/share/hplip/base/tui.py", line 265, in output
    max_screen_width = ttysize()[1]
  File "/usr/share/hplip/base/tui.py", line 175, in ttysize
    return int(vals['rows']), int(vals['columns'])
TypeError: int() argument must be a string or a number, not 'NoneType'
..............

A little help please, I tried resinstalling it.
Sorry should have ran sudo not gksudo d'oh! works ok now

---

