---
title: "connection from biostar tf8200 to hp laserjet 4M plus printer"
date: 2008-07-09
forum: Hardware
---

### Post by johnlvs2run on 2008-07-09
My hp laserjet 4M plus printer goes on, but doesn't print from the keyboard.
The issue might be the connection from the biostar motherboard to the printer.

The mobo has a 25 pin connection;
I plugged a cable from an older computer into the mobo;
then plugged the 25 pin printer cord into the other end of the cable.

According to Linux Foundation, the printer should work perfectly.
[http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4M_Plus](http://openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4M_Plus)

Some guidance on this will be much appreciated. Thanks.

---

### Post by hansdown on 2008-07-09
Hi johnlvs2run, Have You downloaded python-qt3 and hplip from synaptic package manager? These worked for me.

---

### Post by johnlvs2run on 2008-07-09
Hi hansdown,
Yes, as per your message I ran "sudo aptitude install python-qt3" and "sudo aptitude install hplip" from the terminal.

Then 
"file > print" or "ctrl-p"
a screen comes up with "print" at the top and the following 3 choices:
1)  print to file
> output format > pdf
> output format > postscript
2)  pdf
3)  pdf_file generator xxx-desktop unable to find printer

Does it sound like the internal cable, or the "cntr-p" screen set up?
Or do I need to download something else?

Suggestions appreciated, thanks.

---

### Post by johnlvs2run on 2008-07-10
.

---

### Post by johnlvs2run on 2008-07-17
The HP printer is still not working with the Biostar TF8200 motherboard.
I sent several emails to them and got the following three replies.

#1> Does Windows XP have the same issue?

#2> Sorry, we don't have support for Linux so unsure if it's driver related.
The port is standard, so suppose Linux should have the drivers by default.

When you mention Windows XP doesn't work at all, what do you mean?

#3> [COLOR="DarkRed"]if Linux does not recognize this boards I/O chipset, it may not install the drivers correctly. [/COLOR]  
If possible please try Windows XP to see if it’s a software or hardware issue.

I wonder if the Biostar chipset was designed to only work with MS, and if I am SOL with this motherboard. 
Any comments or suggestions?

---

### Post by johnlvs2run on 2008-07-26
The printer is not working with Biostar yet, and Biostar's only suggestion is use Microsoft.  

This link shows how Foxconn's Bios messes with Linux ACPI; perhaps Biostar's antics are similar.

[http://ubuntuforums.org/showthread.php?t=869249](http://ubuntuforums.org/showthread.php?t=869249)

---

### Post by hansdown on 2008-07-26
Hi johnluvs2run. Have you tried any other drivers?

Here is a page for postscript driver. [http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus)

---

### Post by johnlvs2run on 2008-07-27
> **hansdown said:**
> Hi johnluvs2run. Have you tried any other drivers?

Here is a page for postscript driver. [http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus](http://www.openprinting.org/show_printer.cgi?recnum=HP-LaserJet_4_Plus)

Hi hansdown.  Yes, it says this printer should work automatically.
Also I did try the other driver as you suggested, and had done this before.

Still, the printer is not working, the same scenarios as above.

---

### Post by hansdown on 2008-07-27
Hi johnluvs2run. Don't give up. If you keep posting, it will bump your post to the top, and someone more knowledgable than myself will see it.
Two more possible drivers,if that is what's needed, are gutenprint and gutenprint52. Sorry I can't be more helpful. I'll keep looking here.
Is there any way to make sure your cables are o.k?

I found a link that may help you with the connections. [http://www.jlaforums.com/viewtopic.php?t=4279621](http://www.jlaforums.com/viewtopic.php?t=4279621)

Also found a manual (it costs $6.99). [http://www.2manuals.com/product_info.php?products_id=93](http://www.2manuals.com/product_info.php?products_id=93)

---

### Post by hansdown on 2008-07-27
Hi johnluvs2run. Alternatively, another option is to run on fedora 7, fedora core 5, redhat 9.0, or solaris 7 and 9. There is support with a monthly charge.

---

### Post by cariboo on 2008-07-27
Stupid question, are you using a proper paralell printer cable to connect to your printer? 

Jim

---

### Post by johnlvs2run on 2008-07-27
> **cariboo907 said:**
> Stupid question, are you using a proper parallel printer cable to connect to your printer? 

Jim

Yes

---

### Post by johnlvs2run on 2008-07-29
> **aysiu said:**
> [Ubuntu Wiki page on HP printers](https://wiki.ubuntu.com/HardwareSupportComponentsPrintersHp)
just use the regular Add Printer dialogue and select HP Laserjet 4 instead of HP Laserjet 4M, and it should work.

Thank you for finding this, though it's still not working.

The Ubuntu system > administration > printers dialogue might be the issue, as the only choices under Local Printers are as listed below.

system > administration > printing
> server settings
> local printers
>> pdf
>> pdf file generator

new printer > the choices below are all that come up
> print into pdf file
> internet printing protocol (ipp)
> lpd/lpr host or printer
> windows printer via samba
> other

There is no choice to add a LOCAL PRINTER.

local printer
> pdf file generator
>> location > desktop
>> device lpd://
>> make and model > hp laserjet 4
>> printer state stopped
>> default printer > this is the default printer

Suggestions appreciated, as the HP printer is still not working with Ubuntu.

---

