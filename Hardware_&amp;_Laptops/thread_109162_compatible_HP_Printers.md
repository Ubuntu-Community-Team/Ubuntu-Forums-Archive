---
title: "compatible HP Printers"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by rjay3 on 2005-12-27
I just installed Ubunto alongside WindowsXP Pro and installation went fine except Ubunto won't recognize the HP Deskjet 3620. Does anyone have a list or recommendation of an HP printer that come with linux drivers? I'm pretty much a newbie. Thanks

---

### Post by audax321 on 2005-12-28
Most HP printers just use the hpijs driver, so you could try installing it as HP Deskjet 3650 and see if that works.

1. Restart CUPS (this sometimes helps detect printers you might have added), by opening up a terminal (Applications > Accessories > Terminal) and typing: sudo /etc/init.d/cupsys restart

2. Close the terminal window after it is done restarting the CUPS service.

3. System > Administration > Printing

4. Double-click 'New Printer'.

5. Tell it you want to use a 'Local Printer', and either select it in the detected printers list, or select USB Printer from the drop down box and click Next.

6. Select HP Deskjet 3650 and complete the wizard.

I had a problem with my Deskjet 5440 like this in v5.04, and just using another model that was close to the one I had (I think it was 5500) worked.

---

### Post by rjay3 on 2005-12-28
thanks audax321, I'll give it a try.............:cool:

---

### Post by kaamos on 2005-12-28
Try installing the packages "hpoj" and "hplip" and then try again.

Hope this helps!

---

### Post by quincunx on 2005-12-29
[QUOTE=audax321]Most HP printers just use the hpijs driver, so you could try installing it as HP Deskjet 3650 and see if that works.

1. Restart CUPS (this sometimes helps detect printers you might have added), by opening up a terminal (Applications > Accessories > Terminal) and typing: sudo /etc/init.d/cupsys restart

2. Close the terminal window after it is done restarting the CUPS service.

3. System > Administration > Printing

4. Double-click 'New Printer'.

5. Tell it you want to use a 'Local Printer', and either select it in the detected printers list, or select USB Printer from the drop down box and click Next.

6. Select HP Deskjet 3650 and complete the wizard.

I had a problem with my Deskjet 5440 like this in v5.04, and just using another model that was close to the one I had (I think it was 5500) worked.[/QUOTE]


I had a problem with my HP OfficeJet G85 until reading your post.  THANKS!  My printer worked fine with a Fedora distro (using Gnome), so I was surprised when the test page wouldn't print under Ubuntu.  After restarting CUPS it works!

Thanks,

Quincunx

---

### Post by rjay3 on 2005-12-29
I got Ubunto to see my HP Deskjet 3620 and it's working now. Thanks audax for your fix and to all that replied. I'm loving this Ubunto more and more!!

---

