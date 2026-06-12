---
title: "HP psc1210 all-in-one...how to make the scanner part work"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by matthew on 2005-07-15
I have the HP psc1210 all-in-one printer/scanner/copier and have used it for over a year...first under winxp and now in ubuntu since I have made the switch.

Printing works well with no problems, both in color and b/w.
Copying does not require the computer to even be on, so that's a moot question.

I can't get the scanner to work or even be recognized. Xsane does not recognize the device.

Any way to make this work?

---

### Post by matthew on 2005-07-16
An update...

I removed the hpoj (HP Office Jet) driver that I was using and installed the hplip driver via synaptic. No change. I can still print beautifully, but I cannot scan at all or even get the scanner recognized as existing.

The HPLIP Toolbox that installed in my System->Preferences menu says "No installed HP devices found" and to set up the device in [http://localhost:631](http://localhost:631) (Common UNIX Printing System web interface).

From there I selected "Manage Printers" and my printer shows up. If I try to select "Configure Printer" it asks for a name and password (mine don't work) and then tells me that "printer administration has been disabled in the web interface for security reasons" and that I must do all printer administration using the Gnome CUPS Manager found in System->Administration->Printing in the Gnome toolbar menu. In fact, it will tell me this no matter what option I choose.

That does allow me to administer the printer functions perfectly, but I still have no way to administer/use the scanner functions.

This page [http://www.cups.org/articles.php?L301](http://www.cups.org/articles.php?L301)  suggests the Linux cups-config-daemon program needs to be disabled in order to do what I am attempting, but it is neither running nor even installed in the location mentioned (/etc/init.d/cups-config-daemon and /sbin/chkconfig cups-config-daemon)

I am out of ideas. Can anyone help?

---

### Post by mbjbdc on 2005-07-16
i have same printer had to power down printer after installing hplip
also did you add the the line hpaio to etc/sane.d/dll.conf.
right after hpoj.
make sure you are using the printer listed under other.
there are two listed 

if you use hpoj
run in console  sudo ptal-init setup reboot then setup printer

---

### Post by matthew on 2005-07-16
[QUOTE=mbjbdc]i have same printer had to power down printer after installing hplip
also did you add the the line hpaio to etc/sane.d/dll.conf.
right after hpoj.[/QUOTE]

This was what I needed to do. It works beautifully now with xsane. Thank you!!!

---

### Post by OBnascar on 2005-10-02
[QUOTE=mbjbdc]run in console  sudo ptal-init setup reboot then setup printer[/QUOTE]
mbjbdc, thank you so much, this is a old post I ran onto and the above worked perfect for my[COLOR="DarkOrange"] PSC HP 1315 all-in-one scanner[/COLOR]. I now have everything in ubuntu Hoary 5.04 set up and can start enjoying it.

---

### Post by Foxmike on 2006-03-11
[QUOTE=OBnascar]mbjbdc, thank you so much, this is a old post I ran onto and the above worked perfect for my[COLOR="DarkOrange"] PSC HP 1315 all-in-one scanner[/COLOR]. I now have everything in ubuntu Hoary 5.04 set up and can start enjoying it.[/QUOTE]
> HP psc1210 all-in-one...how to make the scanner part work
i have same printer had to power down printer after installing hplip
also did you add the the line hpaio to etc/sane.d/dll.conf.
right after hpoj.

Wonderfull!  It works perfectly on PSC1310.

Thanks very much!

-FM

---

### Post by matthew on 2006-03-11
[quote=Foxmike]Wonderfull!  It works perfectly on PSC1310.

Thanks very much!

-FM[/quote]Woo hoo!! Glad it worked for you and you're welcome.

---

