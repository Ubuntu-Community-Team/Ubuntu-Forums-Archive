---
title: "Printer Problem (HP Deskjet F4280)"
date: 2008-08-18
forum: General Help
---

### Post by dmt.flash on 2008-08-18
I am really new to Ubuntu and linux in general. I am running 8.04 on a 64 bit HP pavilion machine. 

In system>administration>printing the Deskjet F4280 model is not listed. Tried to do a generic driver with no luck. 

I installed hplip - which says they support the F4280 - but I can't seem to run the program. 

Any help for this noobie would be appreciated. 

Thanks,   James

---

### Post by timcredible on 2008-08-18
you can't 'run' hplip, it's a service, not an application, and it's installed by default on 8.04.  if you installed it second time, not sure what that would do.  with the default 8.04 install, it should automatically find your hp printer.  if not, make sure your printer is connected via usb, is turned on, and reboot your pc

---

### Post by lynchauj on 2008-08-26
I am running Kubuntu 8.04 HH with the HP Deskjet F4280 All-In-One. I was experiencing the same problem and the classic Windows reboot-and-pray didn't work.

Turns out the HPLIP I was running was 2.8.2, while the latest is 2.8.7. I updated and it works.

Also, it works as a scanner now too. I am using KDE Scanning Kooka.

---

### Post by gdboytyler on 2008-08-27
> **lynchauj said:**
> I am running Kubuntu 8.04 HH with the HP Deskjet F4280 All-In-One. I was experiencing the same problem and the classic Windows reboot-and-pray didn't work.

Turns out the HPLIP I was running was 2.8.2, while the latest is 2.8.7. I updated and it works.

Also, it works as a scanner now too. I am using KDE Scanning Kooka.

Thanks for the HPLIP 2.8.7 tip!  I got my HP F4280 working properly.  I am using XSane scanning.

I've been using Linux for about a week now.  For the other newbies, here's the "how to" for installing HPLIP:

[http://hplip.sourceforge.net/install/install/index.html]("http://hplip.sourceforge.net/install/install/index.html")

In the instructions, they left out that you need to be in the same directory as the "hplip-2.8.7.run" file when you run the "sh hplip-2.8.7.run" command.  I was stumped for a couple of minutes.

If you have a USB printer, you should connect and power up your printer before you run the "sh hplip-2.8.7.run".  It will save a reboot.

---

### Post by zcartist on 2008-08-27
can somebody walk me through the install.I have the run file on my desktop I go do what the directions say and it won't install

---

### Post by boblounsbury on 2008-09-04
If the run file is on your desktop, open a terminal and:

cd ~/Desktop
sh hplip-2.8.7.run

and follow the instructions.

On a side note has anyone had any luck using xsane to scan with this hp f4280 printer? Or even better setting up the scanning on an ubuntu server and scanning over a LAN?

Cheers,
/Bob

---

### Post by Darrell Lawrence on 2008-09-05
> **gdboytyler said:**
> Thanks for the HPLIP 2.8.7 tip!  I got my HP F4280 working properly.  I am using XSane scanning.

I've been using Linux for about a week now.  For the other newbies, here's the "how to" for installing HPLIP:

[http://hplip.sourceforge.net/install/install/index.html]("http://hplip.sourceforge.net/install/install/index.html")

In the instructions, they left out that you need to be in the same directory as the "hplip-2.8.7.run" file when you run the "sh hplip-2.8.7.run" command.  I was stumped for a couple of minutes.

If you have a USB printer, you should connect and power up your printer before you run the "sh hplip-2.8.7.run".  It will save a reboot.


I really appreciate this information. I just received my HP F4280 and after installing hplip 2.8.7 it works like a charm. Thanks again. I wonder why Ubuntu has not updated their repository to the latest version?

Darrell

---

### Post by PsychoBee90 on 2008-09-10
I was using HPLIP from the repos and after installing the version from the HPLIP website it works like a charm!

---

### Post by CFBauer on 2008-09-14
> **PsychoBee90 said:**
> I was using HPLIP from the repos and after installing the version from the HPLIP website it works like a charm!
Same here. Thanks everyone.

---

### Post by BananaCakes471 on 2008-10-01
> **boblounsbury said:**
> 
On a side note has anyone had any luck using xsane to scan with this hp f4280 printer? Or even better setting up the scanning on an ubuntu server and scanning over a LAN?
/Bob

i'm having difficulties as well. it'll scan but the picture it shows is just a skinny white line. i need to scan for work. and need help immediatly

---

### Post by tschaub on 2008-10-14
> **gdboytyler said:**
> Thanks for the HPLIP 2.8.7 tip!  I got my HP F4280 working properly.  I am using XSane scanning.

I've been using Linux for about a week now.  For the other newbies, here's the "how to" for installing HPLIP:

[http://hplip.sourceforge.net/install/install/index.html]("http://hplip.sourceforge.net/install/install/index.html")

In the instructions, they left out that you need to be in the same directory as the "hplip-2.8.7.run" file when you run the "sh hplip-2.8.7.run" command.  I was stumped for a couple of minutes.

If you have a USB printer, you should connect and power up your printer before you run the "sh hplip-2.8.7.run".  It will save a reboot.

Looks like the page above has moved.  I found what looks like the same install instructions here: [http://hplipopensource.com/hplip-web/install/install/index.html]("http://hplipopensource.com/hplip-web/install/install/index.html")

---

