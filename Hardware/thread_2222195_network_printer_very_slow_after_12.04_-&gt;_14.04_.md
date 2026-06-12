---
title: "network printer very slow after 12.04 -&gt; 14.04 upgrade"
date: 2014-05-05
forum: Hardware
---

### Post by talz13 on 2014-05-05
I upgraded my parents PC from 12.04 to 14.04 to go along with their new hardware a couple weeks ago.  Since then, their network printer, a brother hl-5250dn, has been very slow to print from ubuntu.

Printing a test page seems to work quickly, and printing from a windows VM running on the ubuntu PC works fine as well.  However, when printing from ubuntu, the job takes nearly 5 minutes or longer before the printer will start.  The job gets sent to the printer, but it gets stuck at "PROCESSING" for a long time.

I've tried removing the printer and re-adding it, but that did not change anything.  Are there log files somewhere that could possibly tell me what is holding up the job?

---

### Post by talz13 on 2014-05-08
Bump... any suggestions?

---

### Post by bovender on 2014-05-21
No suggestions, but similar problem here, on two laptops with Ubuntu 14.04 in our household. It takes up to 10-15 minutes until the page is printed. This is with a Postscript-capable HP LaserJet P2015dn on wired lan. I'm trying to print text pages, no graphics, so it's not due to high-res rendering.

As there are a couple of reports about very slow printing with 14.04 on the internet, maybe someone knowledgeable could look into this. (How to file a bug report, and on which package?)

---

### Post by talz13 on 2014-08-07
Their PC is still very slow to print, and sometimes spits out errors when it does print.

Any others having this problem?

---

### Post by martinrame on 2014-09-11
> **talz13 said:**
> Their PC is still very slow to print, and sometimes spits out errors when it does print.

Any others having this problem?

I have the same problem here. XUbuntu 14.04 trying to print to an Ricoh Aficio 220.

---

### Post by talz13 on 2014-09-12
I purged the cups packages that I could find and reinstalled them, but that didn't seem to affect the printing speed:

```
sudo apt-get purge cups
sudo apt-get purge cups-common
sudo apt-get autoremove --purge
sudo apt-get install --install-suggests cups
```

I watched the print queue on the cups web interface, and saw the spooling percentage slowly count up, taking almost 5 minutes before the spooling was complete.  This was for a simple webpage that came out to be 4 pages of printed material.

I came across this link on [another thread]("http://ubuntuforums.org/showthread.php?t=1984224&p=12349722#post12349722") and gave it a try:

[Brother Driver Install Tool]("http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=hl5250dn_all&os=128&dlid=dlf006893_000&flang=4&type3=625")

I went through that setup, noticed that there was no ia32-libs package anymore in 14.04 so I quit the setup process.

I installed these packages to hopefully provide the required libraries:

```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32gcc1 lib32stdc++6 libc6-i386
```

Then restarted the driver install tool again.  This time I went through the whole install process.  I went back into the cups web interface afterwards and changed the connection for this new printer from the usb:// address to the proper url ( http://{ip address}:631/ipp ).  I printed a couple test pages, and they seemed to go okay, so I had my dad print some test pages from firefox again and could hear the printer immediately start warming up and start spitting out pages.

Hopefully this is all resolved now!

---

