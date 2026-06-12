---
title: "Michael Gruz's Canon Pixma iP4800 driver problems."
date: 2013-02-05
forum: Hardware
---

### Post by jimford on 2013-02-05
I've successfully used Michael Gruz's driver for my Canon Pixma iP4850 on previous Ubuntu installations, selecting the 4800 driver. The printed output has been excellent and paper source selection has worked properly.

I'm now trying to get the printer working on a 64bit Xubuntu Quantal 12.10 machine, but am having problems. I've tried using the latest daily builds with no improvement.

1) The colours are very muted and dark.
2) Paper source selection doesn't work and only prints from the rear tray, no matter what source is selected.

I've tried contacting Michael Gruz, but haven't had a response so far.

Ideas anyone, please?

Jim

---

### Post by ahallubuntu on 2013-02-05
~

---

### Post by jimford on 2013-02-05
The install script didn't find my printer because it's samba share. I'm scratching my head to find another way to install the driver.

Thanks for the reply.

Jim

Edit:
I ended up by temporarily connecting the laptop computer to the printer. It was then installed  as a USB connected printer, so I found the location of the PPD file and used it when configuring the printer on the network.

All works fine now!

---

### Post by pdc on 2013-02-05
Hi Jim:

the install script just looks to see if your system is rpm or deb and 32bit or 64bit:and proceeds accordingly

the deb.tar.gz you downloaded contains a folder called [COLOR="Blue"]packages[/COLOR] 

....inside that are 

[COLOR="SeaGreen"]cnijfilter-common_3.40-1_amd64.deb[/COLOR]

and 

[COLOR="SeaGreen"]cnijfilter-ip4800series_3.40-1_amd64.deb[/COLOR]

........if what you downloaded is in your Downloads directory, if you opened the tar.gz with archive manager and drilled down to see the above packages;

if you right-click on the [COLOR="Blue"]COMMON[/COLOR] package first and select "install with gdebi installer" ...........and then do the same with the [COLOR="Blue"]ip4800[/COLOR] deb, that should get the driver installed for you ........

........you could check what is ALREADY installed, before starting the above, by copying and pasting 

> [COLOR="Red"]sudo dpkg -l | grep cnijfilter[/COLOR]

into a terminal

---

