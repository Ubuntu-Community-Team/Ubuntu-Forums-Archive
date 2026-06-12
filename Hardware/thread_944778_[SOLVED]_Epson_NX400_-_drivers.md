---
title: "[SOLVED] Epson NX400 - drivers?"
date: 2008-10-11
forum: Hardware
---

### Post by Zohso on 2008-10-11
I've searched the forums and have found nothing to help me on this.  I just purchased an Epson NX400.  I plugged it in and Ubuntu recognized that I had a "Epson NX400" plugged in and attempted to set it up for me.

I followed on through the screens and then it came to the "Choose a Printer Driver" page.  My printer isn't listed.  It did, however, default to "Epson DX4800".  I accepted, it installed, and I printed a test page.

All seems well minus the Scanning functionality.  I opened xSane and it says I don't have any devices.  Same in Kooka.

I don't know.  Help!

---

### Post by phidia on 2008-10-11
From the sane site it looks like [your scanner]("http://www.sane-project.org/cgi-bin/driver.pl?manu=epson&model=&bus=any&v=&p=") works in linux. It uses the epkowa backend.
The page [here]("http://avasys.jp/hp/menu000000500/hpg000000442.htm") contains download links and steps to getting it working.

---

### Post by Zohso on 2008-10-12
Excellent, thank you for such a speedy response.

I downloaded the .deb file from the link you supplied.  The scanner works flawlessly now.  

Can't thank you enough.  I was sweating bullets with class coming up next week.

Thanks again,

---

### Post by phidia on 2008-10-12
Glad it's working for you now. Welcome to Ubuntu!

---

### Post by Culito on 2009-03-22
Hey folks,
I'm also trying to install the Epson NX400.
Found the site, printer driver installed just fine.  Got to the scanner driver, and ran into some problems...
I'm running a dual-core AMD64.  So I downloaded the appropriate 64 bit package...and Gdebi gives me an error:  Wrong architecture: amd64.
I also tried the 32 bit package and Gdebi gives me a dependency error.

Any ideas?

---

### Post by nikolardo on 2009-06-21
It doesn't matter if you have a 64-bit processor, if you're running a 32 bit operating system, you need the 32-bit package.  I have dual-core amd64, but I run the 32 bit Ubuntu, so I need 32-bit packages.  I would guess that your dependency error is the same as everyone else has with this program.

---

### Post by lachelp on 2009-08-08
I downloaded the drivers as well, and they work fine if used as the user 'root', however, as a normal user -- no go.

I searched Avasys' site, but couldn't find anything on this.

Cheers!
Dan

---

### Post by dwpbike on 2009-12-06
tanks, man.  you ended a 1.5 day search.  i went from fedora 10 -> fedora 11 and got blindsided.  not first time i've found fedora answer on this site.  may have to jump ship.

---

### Post by Inodoro Pereyra on 2009-12-19
I have an NX 400 as well, and I'm having the same problem with the scanner. I downloaded "iscan" from the page Phidia provided, but when I try to scan it tells me "can't send command to scanner".
What am I doing wrong?

Thanks in advance.:)

---

### Post by manco on 2010-01-22
I'm going to check this out today

Glad to know the scanner works!

---

### Post by heltoupee on 2010-02-02
> **Inodoro Pereyra said:**
> I have an NX 400 as well, and I'm having the same problem with the scanner. I downloaded "iscan" from the page Phidia provided, but when I try to scan it tells me "can't send command to scanner".
What am I doing wrong?

Thanks in advance.:)

Yup.  You have to be root, or sudo to root when running this -- as lachelp hinted at.  From a terminal, type 'gksu iscan', and put in your password and see if it comes up then.  If so, and everything appears to work, you can change the command on the 'Applications' menu to that by using 'Main Menu' under 'System' -> 'Preferences'.  Happy hunting!

I'm now struggling with getting it to create a .ppd file so CUPS can print to it.  I think I remember it working using Gutenprint, but it was horribly slow.  I want to use the 'official' driver, but can't until I get this stupid 'pipslite-install' thing working.  Argh!

---

### Post by tonyk11 on 2010-04-13
I got this thing working under the terminal, but I can't seem to find a place to set it up with a shortcut or anything in the menu.  I tested the flatbed and the printer, and they both work.  The printer from the shortcut, and the scanner from the terminal.  Any ideas how to change it so I can just set up a shortcut?

Tony

---

### Post by dwpbike on 2010-04-16
> **tonyk11 said:**
> I got this thing working under the terminal, but I can't seem to find a place to set it up with a shortcut or anything in the menu.  I tested the flatbed and the printer, and they both work.  The printer from the shortcut, and the scanner from the terminal.  Any ideas how to change it so I can just set up a shortcut?

Tony

in fedora 11, it's system>preferences>main menu.  then you can do "add". sane is under "graphics".

should be something similar on ubuntu.

---

### Post by promail44 on 2010-10-31
Hi everybody I have a problem I have done anything that you explain in this problem but at the end I dont know how to execute the scanner from a terminal or an aplication so can you help me ?

---

