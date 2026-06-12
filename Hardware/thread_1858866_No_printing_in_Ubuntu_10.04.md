---
title: "No printing in Ubuntu 10.04"
date: 2011-10-13
forum: Hardware
---

### Post by enverhoxha on 2011-10-13
I cannot print in Ubuntu 10.04. My printer is a Xerox Phaser 3117, the system recognizes it (in Printers) and everything seems to be OK. All settings seem OK too. 

But when I want to print something from OpenOffice or AbiWord or Document Viewer (pdf), nothing happens. Just the printer icon shows up for a couple of seconds on the panel. 
Still, the system tells me that the printing job is... completed! I have tried a dozen times and all what I get is a list of ”completed jobs”. (This includes the ”test page” printing...)

The printer is perfectly functional, because in Windows I can print normally. No problem there.

What is the catch??

---

### Post by ajgreeny on 2011-10-13
Are you sure that the Xerox printer is selected in the print dialog and not "Print to file" by mistake?

---

### Post by nomko on 2011-10-13
Try downloading the driver from here: [http://www.support.xerox.com/support/phaser-3117/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB](http://www.support.xerox.com/support/phaser-3117/downloads/enza.html?operatingSystem=linux&fileLanguage=en_GB) 
 
Remove the printer first under ubuntu (System >Administration)
 
 
You can also check here for solutions: [http://www.google.nl/search?q=%22Xerox+Phaser+3117+under+ubuntu%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images&oq=%22Xerox+Phaser+3117+under+ubuntu%22&aq=f&aqi=&aql=&gs_sm=e&gs_upl=227642l227642l0l229032l1l1l0l0l0l0l140l140l0.1l1l0]("http://www.google.nl/search?q=%22Xerox+Phaser+3117+under+ubuntu%22&hl=nl&num=10&lr=&ft=i&cr=&safe=images&oq=%22Xerox+Phaser+3117+under+ubuntu%22&aq=f&aqi=&aql=&gs_sm=e&gs_upl=227642l227642l0l229032l1l1l0l0l0l0l140l140l0.1l1l0")

---

### Post by Linux_junkie on 2011-10-13
I had a similar problem with 10.04 and HP D1660 printer. The default Ubuntu driver for this printer was called HPIJS (I think) and it caused the same problem you  are having.  I downloaded and installed HPCUPS driver and printer now works.

Search for a CUPS driver for your printer.

---

### Post by enverhoxha on 2011-10-13
> **ajgreeny said:**
> Are you sure that the Xerox printer is selected in the print dialog and not "Print to file" by mistake?
Yes, no mistake. 

There could be another problem, but I don't know how to solve it. When I installed the printer, since the system's printer driver database doesn't include Xerox Phaser 3117, I had to choose another driver (Xerox DocuPrint 4508). Although the system identifies my Xerox Phaser 3117...

Now, maybe that's why it doesn't work, but I don't get any error message about the driver. 
And there is no driver for Phaser 3117 in Linux. 

I tried a minute ago with a Samsung driver from the database, but nothing changed. What can I do?

---

### Post by nomko on 2011-10-13
Did you checked the site i gave you? It's the site of Xerox themselve with a downloadable pirnterdriver.

---

### Post by enverhoxha on 2011-10-13
Thanks, I have downloaded the Linux printer support file from Xerox. Now I have to see how I install it.

---

### Post by nomko on 2011-10-13
> **enverhoxha said:**
> Thanks, I have downloaded the Linux printer support file from Xerox. Now I have to see how I install it.
 
If it is a .tar file, just right click on the file and select extract here. In the folder created there must be a readme file. Read that file carefully for installation instructions.

---

### Post by enverhoxha on 2011-10-13
It's a tgz file. I extracted and then I ran a file called setup.sh.
Unfortunately, in the end I got the messages:

get-printers failed: client-error-not-found
get-jobs-failed: client-error-bad-request

I'm afraid I'm stuck with Windows for printing...

---

### Post by enverhoxha on 2011-10-14
Sorry to have bothered you, but now I've solved it the dummy way: in Synaptic Package Manager! There where a couple of packages there not installed by default: 

printconf
openprinting-ppds-extra

After installation, the list of printer drivers was updated and in it I found Xerox Phaser 3110. Works fine for Phaser 3117.

So, search Synaptic first, shoot later. (Now I'm gonna try it for my scanner, which doesn't work either.)

---

