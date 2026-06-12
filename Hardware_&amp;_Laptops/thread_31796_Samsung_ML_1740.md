---
title: "Samsung ML 1740"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by apollyonis on 2005-05-04
I'm currently using the drivers for the 1710 and its printing, but all of the text is off center. The whole margin near the bottom is too low; the text is almost being cut off.  I've changed the paper type to Letter from A4 and its still doing it. Is there any way to fix this? Has anyone else had any luck with it?

---

### Post by apollyonis on 2005-05-05
:Bump:

I'm guessing no one else has the same laser printer?  :neutral:

---

### Post by apollyonis on 2005-05-05
I've been playing with the printing and it seems that the test page from the print properties is default to A4, regardless of what you put in. This is just an assumption. PDF files seem to print fine on letter sized paper, but Open Office is still printing as if it were on A4 paper. I've used oopadmin to alter the page type for Open Office, but it still defaults to A4 printing and each time I go back into oopadmin I see that it reverted back to A4. Any insight on this? Perhaps there is a config file I can change manually for Open Office printing?

Edit: I've found the actual file oopadmin saves to, but still to no avail.

/home/me/.openoffice/1.1.3/user/psprint/psprint.conf

---

### Post by Happy on 2005-06-23
Lucky you.
your ML-1740 actually works with Ubuntu...

Mine works on my current computer running windows XP in the parallel port (havn't tried the usb port)
It works running Ubuntu 5.04 on my current computer.
It fails on an old machine I was setting up as a print server.
the best I've managed to print out are along the lines of:

> INTERNAL ERROR - Incomplete Session by time out

POSITION : 0x482 (1154)

SYSTEM     : H6FWSIM/os_hook

LINE          : 1191

VERSION    : QPDL 1.16 10-29-2003
or a similar message with the internal error being 'FALSE' instead of time out

only once have I managed to sucessfully print out a test page, and this was running SME-server ([http://www.contribs.org](http://www.contribs.org)) with a raw printer driver and printing from my windows machine via samba share.

running FreeBSD and cups gets me the same result as with Ubuntu
running FreeBSD and lpd with the foomatic filters starts the printer churning and than nothing...

I wish I knew how I got it working perfectly with Ubuntu before, I'm hoping it's not a hardware issue since I changed machine...

---

### Post by David Haas on 2005-06-23
Appolyonis--I'm not familiar with Samsung printers, but wonder whether your ML-1740 might work better with one of the 1750 PPD files in Hoary instead of with the 1710. These are Samsung-ML-1750-hpijs.ppd.gz
Samsung-ML-1750-ljet4.ppd.gz
Samsung-ML-1750-pxlmono.ppd.gz
They are in /usr/share/cups/model/foomatic-ppds/Samsung. 
David

---

### Post by neurosion on 2005-06-23
Have you tried using the actual ML-1740 drivers on the Samsung website?  They don't operate under amd64, but if you're running i386 you're golden.

The URL is pretty hairy.  Just click [here](http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=70894&cntType=DR&cntId=303109&lang=ST).

---

### Post by Happy on 2005-06-23
the 1750 drivers don't work at all
I checked quite a while ago.
The Samsung drivers don't work with foomatic
You have to install the Samsung setup program and use that.
it requires a root password (not just sudo)

The best bet is to stick with the ml1710 foomatic drivers.
I read in the FreeBSD handbook somewhere that you can adjust the printer margins through some commands.
If I dig it up again I'll tell ya =P

as it is I am quite stumped for this printer... been thinking of making a windows print server =(

---

### Post by neurosion on 2005-06-23
OK, here's the full how-to (off the top of my head) for getting the ML-1740 up and running on Ubuntu i386:

1) Download the latest drivers from [here](http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=70894&cntType=DR&cntId=303109&lang=ST).

2) Extract the archive somewhere you can get at it.

3) Use the package manager to fetch libgtk 1.2

4) Open a terminal window.

5) Type: sudo adduser cupsys shadow

6) Type: sudo /etc/init.d/cupsys restart

7) Type: sudo passwd root [sets up a temporary root password]

8. Go to wherever you extracted the drivers and type: ./setup.sh

9) Follow the prompts.  If all goes well you should end up in Samsung's setup utility.  If you somehow don't get there, typing linux-config in a terminal will get you there.  

10) "Add printer"

11) Enter the root password you created in step 7

12) Follow the prompts; I can't help you here, these settings depend on your actual setup

13) When you're all done, type: sudo passwd -l root [disables root password]

Your printer should be configured and available in System -> Administration -> Printing.

Hope it helps.

---

### Post by timczer on 2005-06-24
When I extracted the driver file I got a folder called image.  Running ./setup.sh here did not work, as I would enter the password and nothing would happen.  I found that by opening a terminal in this file, then running sudo su, then following this process did work and I was able to install the drivers for the ml 1740.

---

### Post by hyperboloid on 2005-06-30
Regarding margin problems in Hoary, it seems that the Gnome printer tool is broken for setting the paper type. You can reset it from A4 to Letter, but your change is not registered and does not work.

This is a definite bug in the printer tool. Hope the folks at Ubuntu fix this on the next release. For that matter, when one selects "Noth America" on the locale in the install, the papersize should be reset automatically if the install folks would think a bit.

Anyway:

The fix I found is to edit the file /etc/papersize directly via an editor:```
sudo nano /etc/papersize
``` and change the entry manually from 'A4' to 'Letter'.

---

### Post by namedontwant on 2005-07-14
This also helped me with samsung ML -1520. Thanks neurosion!



> **neurosion]OK, here's the full how-to (off the top of my head) for getting the ML-1740 up and running on Ubuntu i386:

1) Download the latest drivers from [here](http://product.samsung.com/cgi-bin/nabc/support/b2c_downloadcenter_detail.jsp?eUser=&mobile=N&oid=70894&cntType=DR&cntId=303109&lang=ST).

2) Extract the archive somewhere you can get at it.

3) Use the package manager to fetch libgtk 1.2

4) Open a terminal window.

5) Type: sudo adduser cupsys shadow

6) Type: sudo /etc/init.d/cupsys restart

7) Type: sudo passwd root [sets up a temporary root password]

8. Go to wherever you extracted the drivers and type: ./setup.sh

9) Follow the prompts.  If all goes well you should end up in Samsung's setup utility.  If you somehow don't get there, typing linux-config in a terminal will get you there.  

10) "Add printer"

11) Enter the root password you created in step 7

12) Follow the prompts said:**
> 

Your printer should be configured and available in System -> Administration -> Printing.

Hope it helps.

---

### Post by bob k on 2005-08-07
I got this to work but I opend a root terminal, because in a standard terminal it didn't work.

I am now a happy camper, Thanks so much

Bob

---

### Post by Gezzer on 2005-08-07
[QUOTE=apollyonis]I've been playing with the printing and it seems that the test page from the print properties is default to A4, regardless of what you put in. This is just an assumption. PDF files seem to print fine on letter sized paper, but Open Office is still printing as if it were on A4 paper. I've used oopadmin to alter the page type for Open Office, but it still defaults to A4 printing and each time I go back into oopadmin I see that it reverted back to A4. Any insight on this? Perhaps there is a config file I can change manually for Open Office printing?

Edit: I've found the actual file oopadmin saves to, but still to no avail.

/home/me/.openoffice/1.1.3/user/psprint/psprint.conf[/QUOTE]

try
open OO set the page up as required with your print settings etc.

then file/templates
save this as a template
open up templates now set this as the default template

next time u open OO all your settings should be as u require ...

---

### Post by iamtheduff on 2005-10-29
Just wanted to throw down a thanks for the setup how-to. It worked great.

---

### Post by cbpxy on 2006-01-06
I wanted to also thank Neurosion for the how-to.  It worked well for my new Samsung ML-2010 (with the appropriate drivers, of course).

Thanks again

---

### Post by cvmostert on 2006-01-18
> Originally Posted by neurosion
OK, here's the full how-to (off the top of my head) for getting the ML-1740 up and running on Ubuntu i386:

1) Download the latest drivers from here.

2) Extract the archive somewhere you can get at it.

3) Use the package manager to fetch libgtk 1.2

4) Open a terminal window.

5) Type: sudo adduser cupsys shadow

6) Type: sudo /etc/init.d/cupsys restart

7) Type: sudo passwd root [sets up a temporary root password]

8. Go to wherever you extracted the drivers and type: ./setup.sh

9) Follow the prompts. If all goes well you should end up in Samsung's setup utility. If you somehow don't get there, typing linux-config in a terminal will get you there.

10) "Add printer"

11) Enter the root password you created in step 7

12) Follow the prompts; I can't help you here, these settings depend on your actual setup

13) When you're all done, type: sudo passwd -l root [disables root password]

Your printer should be configured and available in System -> Administration -> Printing.

Hope it helps.
ok, great! this worked... ! thank you! i think this can be made an official HOWTO!

edit: I tried it with a samsung ML-1610 and i could add printers with the samsung software...

---

