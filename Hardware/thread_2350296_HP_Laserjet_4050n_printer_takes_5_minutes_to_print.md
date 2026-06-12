---
title: "HP Laserjet 4050n printer takes 5 minutes to print"
date: 2017-01-23
forum: Hardware
---

### Post by Nailhac on 2017-01-23
I have a networked HP laser printer 4050N and running Ubuntu 16.04. My problem is that whilst the printer prints eventually it can take the printer 5 minutes to process the print job and print. It is networked and printing with Win 10 is instantaneous. I have installed  HPLIP - 3.16.11. Can anybody advise what the problem could be?. I did have a recent problem with a USB Canon 9000 mkii printer which was resolved using CUPS but do not know if that is the correct approach with the HP Printer? Thanks in advance.

---

### Post by slickymaster on 2017-01-23
*Thread moved to **Hardware**.*

---

### Post by dragonfly41 on 2017-01-23
You should see status of all installed printers at [http://localhost:631/printers/](http://localhost:631/printers/)

Check for any queued jobs (Jobs tab) which need to be cleared.

---

### Post by pdc on 2017-01-23
Nailhac: could I interject in your thread and ask you about the Pixma Pro9000 mk2 that you have printing from ubuntu? Canon don't seem to have released drivers yet for it in linux format: I was interested it worked for you

---

### Post by Nailhac on 2017-01-25
Hi pdc
I installed CUPS and the 9000 Mkii works brilliantly link below and follow instructions,
[http://localhost:631/](http://localhost:631/)
if you cannot connect to this site go directly to

[https://www.cups.org/](https://www.cups.org/) 

I use Ubuntu 16.04

---

### Post by Nailhac on 2017-01-25
Hi dragonfly41
I had already checked the queue. Cannot figure it out at all. Any other comments would be appreciated.

---

### Post by dragonfly41 on 2017-01-25
I found a few hits when I google search "Cups delay in printing"


e.g. pick first hit in above search  ...


But I cannot say if above will work for you.  
Browse through other users' experiences. 
Look at CUPS log files.

---

