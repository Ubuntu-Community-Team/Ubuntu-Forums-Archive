---
title: "Lexmark 2050"
date: 2005-06-09
forum: Hardware &amp; Laptops
---

### Post by bigJcope on 2005-06-09
Hello everyone. :) I'm new to the Linux world, and after playing around for a bit with Fedora Core 3 on my second computer, I began messing with various Linux Live CDs (Knoppix, SLAX) as well as attempting to install other Linux distros. 

I came across an older PC for a family member, and I've recently completed setting up Ubuntu 5.04 on the PC. Today I attached a Lexmark Color Jetprinter 2050 to the PC, and configured it within the System>Administration>Printing menu. The printer is auto-detected by the OS, and I have selected the make and driver from the menus presented. Within the Printers window it is shown as the Default, and is in a Ready state. 

When I attempt to print a test page, or anything else, the icon indicates that one job is printing, and then this job clears from the queue. However, nothing ever prints out. I've tried rebooting (old Windows habit), but to no avail. I'm now at a standstill with this, and was wondering if anyone had any ideas on what I might need to do. The printer was not attached during the initial build, but I'm not certain that matters (I would think it does not). 

EDIT: I should note that I'm not very familiar with the ins-and-outs of Linux, so any instructions in newbie format would be greatly appreciated. :D

Thanks!

bigJ

---

### Post by jrhodes on 2005-06-10
What print driver is it using? Most lexmark printers (especially the older ones) support raw postscript streams but can get fouled up if you try to feed them PCL or anything complex.

---

### Post by bigJcope on 2005-06-10
Thanks for the reply jrhodes. The printer make, model, and driver were auto-detected by the OS, and they are shown on the Driver tab for printer Properties as:

Make: Lexmark
Model: 2050
Driver: c2050 (recommended)

bigJ

---

### Post by David Haas on 2005-06-11
I'd check via the terminal to see whether the PPD (Postscript Printer Definition) file for the Lexmark 2050 is installed. It's present in Ubuntu Hoary. It's "Lexmark-2050-c2050.ppd.gz" and it's in the "Lexmark" directory at "/usr/share/cups/model/foomatic-ppds/Lexmark". Did you select this one in the printer manager GUI by clicking through the files as noted above? If so, then an unzipped copy should be listed at /etc/cups/ppd. Of course, you need to have the cupsys and foomatic packages installed. They should be by default. You can check this in Synaptic Package Manager. I've found that if a selection mistake has been made, it's best to begin anew by deleting the selected printer and starting over with "NewPrinter".
David

---

### Post by bigJcope on 2005-06-11
Thanks for the reply David, I'll let you know the results as soon as I get a chance to try that out.

Thanks,

bigJ

---

### Post by bigJcope on 2005-06-12
David,

 I checked the directories as indicated, and found the following:

In the directory:

/usr/share/cups/model/foomatic-ppds/Lexmark

the following file is present:

Lexmark-2050-c2050.ppd.gz

In addtion, within this directory:

/etc/cups/ppd

the following file is present:

c2050.ppd

Both cupsys and foomatic show a number of installed packages within Synaptic, though not every single package is installed. As you noted, these are the default installed packages.

I uninstalled the Lexmark Color Jetprinter 2050, then rebooted and attempted to reinstall it. However, this time Ubuntu would not auto-detect the printer. I was, however, able to set it up manually. Once again the printer would not print.

Following this I hooked my HP Deskjet 952c to see if I could make it work. Following setup I printed a test page, which printed out immediately; I was also able to print from within Firefox.

So, any ideas on why Ubuntu will not print to the Lexmark Color Jetprinter 2050? :)

Thanks,

bigJ

---

### Post by David Haas on 2005-06-12
bigj--HP printers generally work great with Linux, but not Lexmark. But this, of course, doesn't answer your question. So, your Lexmark is detected and the proper PPD file has been selected, as shown by its listing in /etc/cups/ppd, and still it doesn't print. I see that it's a parallel port hookup. You can check to see whether the OS has detected  it by looking at the list of URIs via the command "lpinfo -v". This lists all the options for devices. Once detected, the Lexmark should be listed as such in "direct parallel". You can see this for your HP--but it won't be under parallel if it's a USB connection, of course. 

The Web site in "Linux Printing" for the 2050 is at <http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-2050>. You might get some valuable information here. Perhaps other more knowledgeable forum members with Lexmark experience will jump in to help. One more thought: sometimes turning off and then on the printer while Ubuntu is running may, I believe, help detection. 

David

---

### Post by bigJcope on 2005-06-12
David,

 Thanks again, I'll take a look at the items you indicated, and return once I have more information. Hopefully you or some other forum members will be able to help me out here. :)

 I got the PC for free in exchange for working on someone's Windows PC  :wink:   and the family member I'm giving it to got the printer separately for $1. So, hopefully we can get this thing going for a grand total of $1 and a little bit of technical work. :)

Thanks again,

bigJ

---

