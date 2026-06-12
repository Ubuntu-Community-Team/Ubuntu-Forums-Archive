---
title: "Epson Stylus C44 Plus"
date: 2005-03-02
forum: Hardware &amp; Laptops
---

### Post by teumima on 2005-03-02
Hi

I have the Epson Stylus C44 Plus. It seems that Ubuntu detects it, however it won't print on it. The printer doesn't even respond. The print icon comes on for a few seconds thn dissapears.

I tried to install it though System>Printing

Can't do it.

I switched from Fedora core 3. It used to work on FC3. Infact it was detected automatically.

What can I do?

I really like this Ubuntu, I need my printer also!

Thanx

a.t.

---

### Post by Joeb on 2005-03-02
Are you using the same driver for the printer in Ubuntu as you did in FC3?  I don't have a C44 Plus, but my Epson printer had several choices of drivers.  Just a thought.

Joeb

---

### Post by teumima on 2005-03-02
Hi

Thanx for the quick reply.

I went and setup the printer. I assume I used the same driver which was the c42 or something (there is no C44 on linux it seems, or at least I've never seen it).

I created the printer and it says says READY, but it doesn't work.

---

### Post by teumima on 2005-03-02
Ok. I deleted it and am reinstalling it step-by-step to show you what I did, or to anyone who can help me.

I clicked on Sytem config>printing the on add new printer.

The following screen comes up where I'm asked whether I want a local printer or a network printer, the default is local and it gives me the option to use a detected printer which in my case is Epson Stylus C44.

So it detects my printer!

So now I click next and it wants me to choose the manufacturer (?!?! why? it already detected it!) well I look for it anway....I click on epson and then it gives me a list od epson printers now of them are mine! Last time I just cliked on one which I thought would be similar but it didn't work.


Any ideas?

Thanx
a.t.

---

### Post by teumima on 2005-03-02
so i choose one of the stylus printers...but it seems to be more general than specific, like stylus color series, and stylus pro series, etc

---

### Post by Joeb on 2005-03-02
What happens if you don't use the automatically detected printer and set it up manually?  You would have to tell it what usb printer port it is on (most likely the first) and then select the actual printer from a list.  But, it should give your more choices.

If you don't have a lot of printer choices, you might need to install the cupsys-driver-gimpprint (or something like that).  You could do that through Synaptic or the command line with apt-get.


Joeb

---

### Post by teumima on 2005-03-03
How do I tell the printer what USB port to use?

Thanx man

---

### Post by teumima on 2005-03-03
?

---

### Post by Joeb on 2005-03-03
[QUOTE=teumima]How do I tell the printer what USB port to use?

Thanx man[/QUOTE]

I believe the computer figures it out for you.  Do you have more than one printer connected to a USB port?  If not, then you would use the USB Printer #1 choice in the wizard.  If you do, I'd disconnect one so that the other is printer 1 and then the install the second one as printer 2.  I'm not sure that will work, as I only have one printer on my computer.

Joeb

---

### Post by teumima on 2005-03-04
Thanx man

My problem is that my Epson list looks something like this: stylus pro, stylus color, style 2000-4000, stylus gray, I don't know which one is mine.

---

### Post by Joeb on 2005-03-04
[QUOTE=teumima]Thanx man

My problem is that my Epson list looks something like this: stylus pro, stylus color, style 2000-4000, stylus gray, I don't know which one is mine.[/QUOTE]

Did you load the cupsys-driver-gimpprint package?  I think it has the extra drivers.  You can load it through Synaptic or from the command line (sudo apt-get install cupsys-driver-gimpprint). 

Joeb

---

### Post by teumima on 2005-03-05
Reading Package Lists... Done
Building Dependency Tree... Done
Package cupsys-driver-gimpprint is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package cupsys-driver-gimpprint has no installation candidate

---

### Post by teumima on 2005-03-05
Ok ignore the previous msg. It worked on Synaptic.

So now I just do the same thing and my printer should be listed?

---

### Post by teumima on 2005-03-05
The closest thing I find to mine is Stylus color C440 

Mine is stylus C44 plus. It doesn't work.

---

### Post by Bogzla on 2007-07-07
> **teumima said:**
> The closest thing I find to mine is Stylus color C440 

Mine is stylus C44 plus. It doesn't work.

teumima, I had a similar problem with a stylus C42, I installed a couple of extra gutenprint packages through adept and it now lists all the stylus C## printers in the setup wizard

the package in question was, I think, foomatic-db-gutenprint which didn't seem to be installed by default..
anyway, the packages I have currently installed are:
cupsys-driver-gutenprint
foomatic-db-gutenprint
ijsgutenprint
libgutenprint2

and I was able to select the C42 through system>printers>add printer
(like you, it simply wasn't in the selection box before)
(mine is a Kubuntu box but I don't see that would make a difference)

hth,
Bogzla

---

