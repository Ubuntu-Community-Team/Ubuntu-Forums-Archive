---
title: "Canon MX7600 (Network- wired) No Can Scan"
date: 2010-08-10
forum: Hardware
---

### Post by decidedlyno9 on 2010-08-10
Dear Forum,

I am attempting to use 10.04 (64) running on VMware Fusion 3.1.0 on a MBP, all is going well but I have found a sticking point.

Lucid finds the MX7600 in the System-Administration-Printing and I can use it to print, however I cannot scan.

Using Simple Scan I get an error saying No scanners detected (is it connected and turned on? Yes).

$ scanimage -V gives me “scanimage (sane-backends) 1.0.20; backend version 1.0.20“.

$ scanimage -L gives me No scanners were identified.

$ sane-find-scanner does not find the scanner.

[http://www.sane-project.org/sane-backends.html](http://www.sane-project.org/sane-backends.html) says the MX7600 is completely compatible.

[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html) I added the MX7600 IP address as is suggested. (this is for my benefit... $ sudo gedit /etc/sane.d/pixma.conf added #bjnp://MX7600IP:8612)

From the same address above I don’t know how to configure the firewall in Ubuntu.

[http://www.sane-project.org/man/sane-dll.5.html](http://www.sane-project.org/man/sane-dll.5.html) under configuration no # next to pixma.

Someone mentioned root access was needed so I created a root account, but no joy there as I just got the same messages as I did in my normal admin account.

Scanner Sharing is turned on in the Mac’s System Preferences.

[http://mp610.blogspot.com/](http://mp610.blogspot.com/) these instructions were posted in 2008 and apparently (someone has suggested) git packages are nightly builds. I would prefer stable builds. And to be honest I kinda get a bit lost with the author (not his fault but mine).

What do I have to do to get it to scan?

I really feel I am running round the houses looking for a fix (that would appear to be a rather unfortunate term).

---

### Post by decidedlyno9 on 2010-08-11
C’mon somebody, what am I doing wrong? (No facetious replies please.)

If SANE is present (which according to the Terminal it is) then the [http://mp610.blogspot.com/](http://mp610.blogspot.com/) (compiling and installing SANE) does not apply.. Y/N?

If permissions are the cause of my scanning woes then the root account should have taken care of this Y/N?

I have installed Gufw and enabled incoming: allow, and outgoing: allow, so that should take care of all the ports if this is a port issue Y/N? (The Ubuntu virtual machine shares the Mac’s network connection (NAT) I don’t know if this is ideal or not, but for the sake of the exercise it is an option... unfortunately, this has not worked Simple Scan gives me the same “No scanners detected” message.)

I see SANE-Backends is now 1.0.21. Should I update or do I have to do a full reinstall? (Answer SANE says if you want a more updated version of SANE build from source (ask on a distro-specific forum for advise; oh brother!))

If anyone reading this can answer just a little bit or impart some general advise then that is fine, I am not expecting all the answers from a single source, but some help would be gratefully received.

---

### Post by IcarusR on 2010-08-11
I don't think this is correct, it looks like a name & a port ?

>  #bjnp://MX7600IP:8612)


The linked man page says...

>  bjnp://<host>
              where  host  is  the hostname or IP address of the scanner, e.g.
              bjnp://10.0.1.4 or  bjnp://myscanner.mydomain.org.  Define  each
              scanner on a new line.


This would mean you should have entered something like this...

```
bjnp://10.0.1.4
```

Can you ping the printer at the address you used ?

Having said all this I have no experience of VMware or MBP.
I assume it is a stand alone printer/scanner ??

---

### Post by decidedlyno9 on 2010-08-11
Dear IcarusR

Many thanks for the reply. As far as the IP address in the #bjnp line goes, you are absolutely correct, however I was being overly safety conscious so I substituted the actual IP for the phrase MX7600IP when I wrote the post. Thinking about it, I don’t know why I did this as the majority of private IPs are very similar.

However, I will delete the :8612 off the end of the line to see if that makes a difference. I cannot do it at the moment as I have just deleted the virtual machine and started again.

As far as Pings go I can ping the MX7600 from the Mac Book Pro at it’s IP address (not my substitution phrase MX7600IP) and I get the desired results. I‘ll try and find an equivalent Pinger in the Ubuntu OS and give that a try.

As for your final query, the MX7600 is a stand alone multifunction (printer/fax/scanner/copier, and while I can use the fax and copier in such a manner, the scanner is needed to get pdfs into the system. Now you may well ask if I can scan with Mac why am I worrying about scanning with Ubuntu? Well I am looking to buy an inexpensive laptop and load Ubuntu on it, but I wanted to make sure everything that currently works with the Mac will work with Ubuntu).

Finally why start again? I went a bit terminal with the Terminal and entered a cacophony of commands from one of the blogs and made lots of things happen, but still could not get the thing scanning, so I though it better to undo my hamfisted approach and create a new virtual machine (hopefully this time I will remember to make backups before changing anything with the Terminal so I don’t have to do this again).

Finally I have just downloaded 9.10 to see if the scanner will work in that (I know I’m getting a bit desperate now). So that’s where I am at.

Anyway, anything else you can think of that might get it working please drop me a line and I’ll give it a whirl, but for the moment thanks again.

---

