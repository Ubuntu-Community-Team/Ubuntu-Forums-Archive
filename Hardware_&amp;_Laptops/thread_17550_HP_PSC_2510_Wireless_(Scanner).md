---
title: "HP PSC 2510 Wireless (Scanner)"
date: 2005-03-01
forum: Hardware &amp; Laptops
---

### Post by JGJones on 2005-03-01
I have a HP PSC2510 All-in-One printer/scanner device, connected to the wireless network. Printing is fine in Ubuntu (in fact there was zero problems there :))

My problem is the scanner on the device. xsane does not find it and I've looked in the forums/wiki but all mentions of the HP PSC devices are all connected by cables ie USB. My printer is on a wireless network (as it is inbuilt the printer) so how would I get xsane to work with it?

The printer does allow scanning from the web interface but only if I email it to myself (if just scanning then it works with HP Director software on Windows, but by email, the scanner sends it out by itself) - I have no control over the scanning function there so it's not really of use.

Many thanks

---

### Post by totalshredder on 2005-04-05
Hello, 

   I also have this printer; and would like to know how to scan. I'm basically just bumping the thread :)

   Also, I haven't got the printer to work; period. So if anybody can give me a little advice that'd be great.

Luke

---

### Post by Pinkydead on 2005-09-20
Just in case anyone else comes along and can't find the answer.

(Make sure XSane is installed)

In package manager search for hpoj

Install it

Run ```
ptal-init setup
``` as root - ignore the parallel and usb stuff (unless you have them), put in the IP address of your printer.

Run XSane - enjoy.

---

### Post by JGJones on 2005-10-25
Can I kiss you? I've been searching for this high and low with no luck until this! Wonderful! Works excellently!

Thanks! xxx ;)

(ps I'm now on Breezy...and this is in Warty(!))

[QUOTE=Pinkydead]Just in case anyone else comes along and can't find the answer.

(Make sure XSane is installed)

In package manager search for hpoj

Install it

Run ```
ptal-init setup
``` as root - ignore the parallel and usb stuff (unless you have them), put in the IP address of your printer.

Run XSane - enjoy.[/QUOTE]

---

### Post by eeclark on 2005-12-05
HPLIP replaces HPOJ...can use xsane if I use the IPP URI, but that is at the command line. Cannot launch Sane from the icon since you cannot specify the IPP at that point.
I have asked backports to release a new rev since HPLIP 0.9.7 is out with mods for debian/ubuntu users...currently 0.9.5 is in the repos.

---

### Post by goodtimetribe on 2007-04-22
> **Pinkydead said:**
> Just in case anyone else comes along and can't find the answer.

(Make sure XSane is installed)

In package manager search for hpoj

Install it

Run ```
ptal-init setup
``` as root - ignore the parallel and usb stuff (unless you have them), put in the IP address of your printer.

Run XSane - enjoy.

I'm assuming the ptal-init setup was part of the install on Edgy Eft. It was *easy* and worked immediately on my Photosmart c6180 after installing the hpoj package. How do I run the LCD program?

---

### Post by dtvarnum on 2007-11-08
> **goodtimetribe said:**
> I'm assuming the ptal-init setup was part of the install on Edgy Eft. It was *easy* and worked immediately on my Photosmart c6180 after installing the hpoj package. How do I run the LCD program?

Hi and thanks, this worked great. I can now scan to my computer wirelessly. I have been reading the forums for others who have this AiO and are using windows and they are having a horrible time. I am using Ubuntu and with the help on this forum, it couldn't be any easier. I am glad I don't have to use the bloatware that came with the printer. 

I have another older HP scanjet 2200 that scans great. I wonder if I can get more than 300dpi on this scanner? ? 

thanks. 

dtv

---

