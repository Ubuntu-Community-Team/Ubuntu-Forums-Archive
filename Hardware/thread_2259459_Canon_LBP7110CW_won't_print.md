---
title: "Canon LBP7110CW won't print"
date: 2015-01-04
forum: Hardware
---

### Post by jnorris2 on 2015-01-04
I thought this was a networking issue initially, but have now confirmed that it's not.... I have two Ubuntu 14.04 systems that won't print to my new Canon LBP7110CW at all. I downloaded the drivers from Canon, installed them per their instructions (also installed lib32z1 lib32ncurses5 lib32bz2-1.0 libjpeg62:i386 as I had read online) but I can't get it to print, whether connected directly via usb or otherwise. Jobs leave the queue as though they're printing, but nothing happens on the printer.

My error log says this:

E [04/Jan/2015:13:36:51 -0600] [Client 26] Request for non-absolute resource "".
W [04/Jan/2015:13:36:51 -0600] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_LBP7100C_7110C-Gray..' already exists
W [04/Jan/2015:13:36:51 -0600] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon_LBP7100C_7110C-RGB..' already exists
E [04/Jan/2015:13:37:09 -0600] [Job 19] src = libcanon_pdlwrapper.c, line = 514, err = 0Â¥nDEBUG: Wrote 1 pages...


Edit:
I just tried installing another printer via USB, an HP LJ1018 and although it acted like it installed fine (and used the default drivers) it won't print either. How do I troubleshoot CUPS?

Edit 2: 
I CAN print thru shares. I connected to another Ubuntu box and printed on the LBP7110CW..... but still can't print locally (to ANY printer) or via network direct to printer

---

### Post by jnorris2 on 2015-01-04
Any ideas? If I can print thru shares, but can't print to local (USB) printers, I'd think that'd narrow it down considerably.

---

### Post by pdc on 2015-01-04
I think we might be able to help if you could lay out in more detail how your system is constructed; 

I am guessing you used the Canon UFR driver; 

can you tell us the result of some commands please

```
/usr/sbin/lpinfo -v
```

```
dpkg -l | grep cndrvcups
```

I think you have started 2 threads: I suspect a forum admin will roll them into one

---

### Post by jnorris2 on 2015-01-05
Thanks for the help... the other thread was semi-related, but resolved on one of my systems. To be clear, on this new one I can't print at all unless it's via a share. Local printing (USB) to two different printers fails... Here's the output though:

```
$ /usr/sbin/lpinfo -v
network ipp14
direct hp
network lpd
network ipps
network https
network http
network socket
network ipp
network smb
direct hpfax
network bjnp
network dnssd://Canon%20LBP7110Cw._printer._tcp.local/
network dnssd://LBP7110CW%20%40%20jnorris-Latitude-E6430._ipp._tcp.local/cups
network dnssd://Canon%20LBP7110Cw._pdl-datastream._tcp.local/
network socket://10.10.10.39

```

```
dpkg -l | grep cndrvcups
ii  cndrvcups-common        2.80-1    amd64        Canon Printer Driver Common Modules Ver.2.80
ii  cndrvcups-ufr2lt-us         1.00-1     amd64        Canon UFRII LT Printer Driver for Linux

```

---

### Post by pdc on 2015-01-06
> To be clear, on this new one I can't print at all unless it's via a share ..............I'm not clear what you mean; 

______________

Initially I had wondered if some feedback and help on the UFR driver might get things going; I fret that something in the install has created a more global printing issue;

Your UFR drivers seem installed fine; when I read the README file, I see Canon say ```
sudo apt-get install ia32-libs
``` and ```
apt-get install libjpeg62:i386
``` and you have the latter installed; so see if the first command installs things; those who use a 32bit system have a much easier time; 

________________

I wonder how your registered the printer with the print spooler? Canon say the format is 

> sudo /usr/sbin/lpadmin -p [printer name] -m [PPD file name] -v lpd:// [Device IP address]/[Printer Name] -E

so for an ipv4 and the 7110 they use the ppd file CNCUPSLBP7110CZNS.ppd and for an ip address of > 172.23.2.72 they suggest the command should be

> /usr/sbin/lpadmin -p LBP7110CW -m CNCUPSLBP7110CZNS.ppd -v lpd://172.23.2.72/LBP7110CW -E

________________

that is a command line registration

another way is [http://localhost:631/admin](http://localhost:631/admin) and click on ADD A NEW PRINTER and then enter your username and password

another way is ```
system-config-printer
``` and then click on the top-left button ADD A NEW PRINTER and select the network printer option and let your system find what is registered; 

___________________________

you talked of trying to connect by usb

I wondered if had a result to the command ```
/usr/sbin/lpinfo -v
``` with the printer connected and turned on; a usb command line registration may be simpler and if it printed; would suggest the main printing install was good

_______________

I hope some of the above may be of some use

---

### Post by jnorris2 on 2015-01-06
pdc,
   What I mean about printing to a share is that if another system shares the printer, I can connect to that share and print successfully... but if I try to connect directly to the printer (USB), then it won't print. I have tried several of the methods you describe above to add the printer, and they all failed... Or, more specifically, they install the printer and act as though everything is fine, but will not print anything.

---

### Post by pdc on 2015-01-07
so this post [http://jonathan.bergknoff.com/journal/printing-ubuntu-canon-mf3010](http://jonathan.bergknoff.com/journal/printing-ubuntu-canon-mf3010) described the successful install of the similar UFRII driver: ver 2.9

he suggested one needs

[COLOR="#FF0000"]libxml2:i386
libjpeg62:i386
lib32z1
libstdc++5:i386 
libstdc++6:i386
[/COLOR]
whereas you have installed

[COLOR="#FF0000"]libjpeg62:i386
lib32z1 [/COLOR]
lib32ncurses5 
lib32bz2-1.0 

he then restarted CUPS 

he used those as the ia32-libs now seems defunct

---

### Post by jnorris2 on 2015-01-07
The problem is that the setup I used works perfectly in another 14.04 build AND I can't print from ANY printer on this box. My HP 1018 (using the driver included with 14.04) won't print either. I think I may to create a new thread as the title and initial post in this one is misleading..... dunno.

---

