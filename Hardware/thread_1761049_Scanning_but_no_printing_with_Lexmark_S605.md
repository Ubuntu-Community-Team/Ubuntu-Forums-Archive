---
title: "Scanning but no printing with Lexmark S605"
date: 2011-05-17
forum: Hardware
---

### Post by Pixtu on 2011-05-17
I have installed the Lexmark supplied driver for this printer on two Ubuntu 10.04 based systems.

On both, the printer is 'found' when installed for wireless operation as a printer.

It is found and works for Scanning using the simple-scan application on one but not the other, and it won't print from either.

Looking at the 'view attributes' for the print job, the 'job-printer-state-message' shows as: Printer error. The printer cannot communicate with the computer.

I presume that the problem will lie with permissions somewhere, but I'm not sure where.

The troubleshooting debugging reports the following:
<code></code>

Does anyone have any ideas on what I need to change please?

---

### Post by Pixtu on 2011-05-18
I appear to have resolved the issue but not by fixing the specific problem.

There are a number of downloads available on the Lexmark site, some of which are paired with/without an included JRE.

For my 32 bit system I selected the one described as being for Ubuntu based systems ('0.9'). For the 64 bit system I chose the one for 64 bit Debian without JRE ('legacy') as I already had a JRE installed (or I thought I did).

Once I investigated the problem a little more it was evident that the 32 bit and 64 bit versions were different. Also, the 64 bit installation ended earlier than the 32 bit, missing the final element.

So, as a start point I tried re-running the install script on a fresh installation of Ubuntu 11.04 (run as root). This highlighted an error with regard to not finding any JRE and the install script terminated, which had not happened on the 64 bit 10.04 previously (supporting my belief that I had a JRE installed).

I then added the OpenJDK Jave Runtime package. This time the script completed and printing and scanning worked.

Going back to the 64 bit 10.04 system, re-running the script resulted in an error that the two packages to be installed were already present and should be removed. As the install script didn't do this and didn't appear to support it, I ran dpkg -r on the two packages concerned: lexmark-inkjet-legacy and lexmark-legacy-wsu. I then ran the install script again, which this time completed all elements and now works for printing and scanning.

This just left the 32 bit 10.04 system. Figuring that the JRE required might be specific for some reason, I downloaded an alternative package from the Lexmark site, this time going for the more generic 32 bit legacy version (again without JRE).

I then installed the OpenJDK in addition to anything else I have, used dpkg -r to remove the previous driver package and then ran the new install script. Everything completed and printing and scanning now working.

I haven't tried any of the Lexmark packages that include the JRE, which might well be equally satisfactory (or even the best method), but using the generic Debian 'legacy' non JRE versions with the OpenJDK Runtime does appear to work so far.:)

---

