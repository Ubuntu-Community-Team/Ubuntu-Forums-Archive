---
title: "Epson Stylus C82"
date: 2004-10-13
forum: Hardware &amp; Laptops
---

### Post by craigaa on 2004-10-13
Hi,

Can anyone give me some pointers on getting my Epson Stylus C82 working?

There appears to be no support for it in the printer configuration.

Regards

---

### Post by mark on 2004-10-13
I have the same problem, no explicit C82 support.  When I tried using what looked like a "generic" Stylus driver, I just got multiple form-feeds of blank pages...

---

### Post by mark on 2004-10-15
I think I got it!  I did a search in Synaptic for *cups**, trying to find any kind of trail.  In the file listing it returned, it looked like only the server, client &amp; system stuff had been installed.  I then marked *cupsys-driver-gimpprint* for installation, applied, and then ran the printer setup (*Computer-&gt;System Configuration-&gt;Printing*). Lo and behold, there was my C82 driver selection!  (And many other specific Epson models that had been missing...)  Now I am happily able to print from any app.

One more note - I had enabled the "universe" repository selections in Synaptic; I don't know if this was necessary, but if you have problems, try that.

Good luck!

Mark

---

### Post by jeffjj on 2004-10-24
>>I had enabled the "universe" repository selections in Synaptic

I had to enable the "universe" selection in the repositry also. I'm new and it wasn't obvious how to do it...so to claify in Synaptic go to Settings --> Repositories. Then there will be two selections not selected, so go ahead and select them. The word 'universe' shows up under the section header, but you have to full screen Synaptic to see that header. 

Also...my printer works again!!  I have a Epson CX5400 that uses the C84 drivers and under other distros the margins were always off. In my new Ubuntu world it works great!

---

### Post by craigaa on 2004-10-25
Hi All,

Thanks for the assist. Works like a charm now.

---

