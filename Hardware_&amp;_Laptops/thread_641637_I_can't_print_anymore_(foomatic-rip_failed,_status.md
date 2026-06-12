---
title: "I can't print anymore (foomatic-rip failed, status 3)"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by Sciamano on 2007-12-15
Hi,
my Epson Stylus Photo R220 has been working fine with Ubuntu until now.
I can't print anything anymore. This is the /var/log/cups/error_log:

E [15/Dec/2007:22:26:54 +0000] PID 7807 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [15/Dec/2007:22:26:54 +0000] [Job 15] Job stopped due to filter errors.
E [15/Dec/2007:22:29:43 +0000] PID 7843 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [15/Dec/2007:22:29:43 +0000] [Job 16] Job stopped due to filter errors.
E [15/Dec/2007:22:30:32 +0000] PID 7865 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [15/Dec/2007:22:30:32 +0000] [Job 17] Job stopped due to filter errors.

But when I try printing a test page, it works!

I've tried reinstalling all the foomatic packages, but with no success.
Any suggestions? Thanks!!

---

### Post by Sciamano on 2007-12-17
No one? Please help!
It used to work when I first installed Kubuntu Gutsy. Then, suddenly, it stopped working... :(

---

### Post by Sciamano on 2007-12-17
Ok, now this is even stranger than before: I've uninstalled a few packages and reinstalled a few others. 

Now it prints correctly from Firefox (for example), but not from Acrobat Reader (acroread), which still gives the 'foomatic-rip error status 3'

Any comment?

---

### Post by jludeman on 2007-12-18
I'm sorry I don't have an answer. In my case my printer stopped working entirely after I installed acroread. 

/var/log/cups/error-log
E [18/Dec/2007:19:13:41 -0500] PID 6367 (/usr/lib/cups/filter/foomatic-rip) stopped with status 3!
E [18/Dec/2007:19:13:41 -0500] [Job 3] Job stopped due to filter errors.

I spent about three hours searching the web for an answer. No luck so far.

The task I wanted to accomplish was:

Print one page from a pdf document.

Fortunately I dual boot to Windows. It's starting to look like if I need work done I should be in Windows and linux should be left strictly for browsing and emails.

I'll post back if I find an answer.

---

### Post by jludeman on 2007-12-18
After further checking I discovered that somehow my printer files had been removed. I suspect that it happened during the acroread install.

After reinstalling my printer and associated files I was back in business.

Seems like very bad behavior from whatever uninstalled my printer files.

I would check all your printer files and see if they are still on your machine.

---

### Post by Myomax65 on 2007-12-18
My printer (HP DJ 712C) stopped working after an upgrade from 7.04 -> 7.10. I kept getting the foomatic-rip failed error message. I tried reinstalling cupsys, foomatic, ghostscript, etc; then I came across a post with this command:

sudo aa-complain cupsd

it worked for me.

---

### Post by Sciamano on 2007-12-19
> **jludeman said:**
> After further checking I discovered that somehow my printer files had been removed. I suspect that it happened during the acroread install.

After reinstalling my printer and associated files I was back in business.

Seems like very bad behavior from whatever uninstalled my printer files.

I would check all your printer files and see if they are still on your machine.

Hmmm, I can print from other programs, therefore I suppose all the files are there.
Anyway, what "printer files" are you referring to, exactly?
Thanks

@Myomax65: I've already tried with "sudo aa-complain cupsd", it did not work :( Thanks anyway

---

### Post by Arrdee on 2007-12-25
I have no idea *how*, or *why*, but after an upgrade to Gutsy/an update to acroread, the "sudo aa-complain cupsd" got rid of the foomatic-rip error and allowed me to print again on a network-shared HP. Much thanks!

---

### Post by Sciamano on 2007-12-27
Good to know, Arrdee.
I still can't print with acroread. :(

---

### Post by phosphoricx on 2008-01-13
I was able to solve this by installing package "hplip"

---

### Post by Sciamano on 2008-01-13
> **phosphoricx said:**
> I was able to solve this by installing package "hplip"

What printer do you have?
I have hplip installed, but I have an Epson, and I don't think this works... :-)
I also have an old HP Laserjet 4L, but it does not work either. It only happens with acroread anyway... other softwares print!

---

### Post by nouma on 2008-01-16
Yep, every time 'proprietary' hardware is around, there is issues configuring things.  Just think about Nvidia. I had the following error too while trying to print: /etc/.../foomatic-rip failed

Installed hplip like proposed before (HP Linux Printing and Imaging System), because I have a HP printer...

It now prints like a charm!

---

### Post by Sciamano on 2008-01-16
Actually both of my printers now work. I only keep receiving this error when trying to print from acrobat reader.
I assume the problem must be in the "acroread" software more than in my hardware setup/drivers...

---

### Post by gnychis on 2008-01-20
i get this error with my Brother HL-2040 printer, installing hplip did nothing for me... probably because it's not an HP printer, any ideas?

---

### Post by Sciamano on 2008-01-20
Brother supplies proprietary drivers for linux. Have you installed them?

---

### Post by gnychis on 2008-01-20
i believe I'm using the PPD file from openprinting found here:
[http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2040](http://www.linuxprinting.org/show_printer.cgi?recnum=Brother-HL-2040)

---

### Post by miscellanyous on 2008-02-01
hey, I had a similar error when trying to print pdf documents using the evince viewer. I already have the hplip package so I am not sure if it is a related problem.

system: Ubuntu 7.10
printer: HP Laserjet 1300 (over a network)
driver: foomatic/hpijs

Apparently [this driver]("http://www.linuxprinting.org/show_driver.cgi?driver=hpijs&fromprinter=HP-LaserJet_1300") is used with a wide variety of printers. For me the same document in ps format printed without difficulty through evince. You can try using pdf2ps to convert the file. I also found printing pdf via the Xpdf viewer was problem free (mind you I haven't tested extensively).

[some people think there is a bug]("https://bugs.launchpad.net/ubuntu/+source/evince/+bug/176634") in printing pdf with evince using this driver

---

### Post by danburyct on 2008-02-18
I ran into this same problem when I upgraded to Ubuntu 7.10.  My HP 6300 stopped printing.   Here is how I solved it

I turned on debug level in the loglevel for the cupsd.conf in /etc/cupsd

I restarted the cups server  ( pgrep -fl  cupsd,  kill the pid it gives back then run cupsd)

I did a tail -f /var/log/cups/error_log 

I opened the system->administration->printing  gui

Print a test page and watch the error messages

I saw an error about hpijs not being able to locate libnetsnmp.so.9

I ran a  ldd on /usr/local/bin/hpijs

and saw that libnetsnmp.so.9  was not found

Checked for the library   with a  ls /usr/lib/* | grep libnetsnmp

It appears that the library was upgraded to libnetsnmp.so.10.0.1  

I created a symbolic link   ln -s  /usr/lib/libnetsnmp.so.10.0.1 /usr/lib/libnetsnmp.so.9 

I tried to print a test page and the printer started working again

---

