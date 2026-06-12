---
title: "LaserJet 4000 not working at all"
date: 2006-06-21
forum: Hardware &amp; Laptops
---

### Post by jclyons on 2006-06-21
I have a LaserJet 4000 connected via parallel port to my system running Ubuntu 6.06. When I add a printer it seems to auto-detect fine, but then when I print to it(test page, document, anything) nothing happens - no error on the printer's display, the print job just hangs in the print queue. After getting frustrated, I decided to compile and install hplip fresh. I ran hp-setup -a instead of the Gnome printer setup, and again it seems to autodetect fine, and sends a test page which doesn't print. Worse, after auto-detecting and a print attempt, the printer no longer auto-detects in the Gnome print management software or when I run hp-setup -a.  



This is what tail -f /var/log/messages log is showing:
 parport0: INFO: open print channel failed; will retry in 30 seconds...
over and over again - so it seems like it's trying. What should I do to get this working?
I look forward to any help you can give me! Thank you very much.

---

### Post by wolfchri on 2006-07-01
Did you check your computers BIOS?

You have to enable EPP or ECP for the Parallel Port - I had the same problem (exactly same error message) with a Laserjet 1100 and solved with changing  my BIOS settings. Now printing works fine.

---

