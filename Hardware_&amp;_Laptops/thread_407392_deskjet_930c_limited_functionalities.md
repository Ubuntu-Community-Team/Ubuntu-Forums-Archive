---
title: "deskjet 930c limited functionalities"
date: 2007-04-12
forum: Hardware &amp; Laptops
---

### Post by hades_6_6_6 on 2007-04-12
I've installed my deskjet 930c onto 2 different computers. 1 running Edgy and 1 running Feisty.
Installation was very easy and the printer is running at once. :) 
However, I have very limited functionality (compared to the same printer under Windows):
- no ability to select print mode (draft, presentation, etc...)
- no ability to print recto/verso
- no ability to print several page on 1 page
- etc

More over, however I've set (in cups) "A4" as the standard format, "letter" is always selected as default.

Does the linux driver only provide basic functionalities, or is it miss-configured?

---

### Post by ramjet_1953 on 2007-04-12
The Deskjet 9130c is a perfect printer for Linux,

Check out this link: [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_930C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_930C)

Do you have HPLIP installed?

That allows to to control everything and monitor your ink levels, as well..

See the attached screenshot.

Regards,
Roger 8-)

---

### Post by hades_6_6_6 on 2007-04-12
- Yes, have installed HPLIP and ran it but found nothing to setup there.
- The link you provided (thx by the way) says:>  For basic printing functionality use the HPIJS driver . For advanced functionality such as printer status and maintenance features, use the  HPLIP driver 

However HPLIP is installed, I can only choose between hpijs and a couple of not hp-drivers.

How to use the hplip driver instead of the hpijs?

---

### Post by ramjet_1953 on 2007-04-12
When you click on [COLOR="Blue"]System>Administration>HPLIP Toolbox[/COLOR] , does the HP Device Manager GUI open?

If so, if you click on the Tools and Settings tab, is there a configure print settings option?

If you are running Feisty, it will be under [COLOR="Blue"]System>Preferences>HPLIP Toolbox[/COLOR].

Regards,
Roger :cool:

---

### Post by hades_6_6_6 on 2007-04-12
> **ramjet_1953 said:**
> When you click on [COLOR="Blue"]System>Administration>HPLIP Toolbox[/COLOR] , does the HP Device Manager GUI open?
There is nothing in Administration. But "sudo hp-toolbox" in a terminal starts the GUI.
> **ramjet_1953 said:**
> 
If so, if you click on the Tools and Settings tab, is there a configure print settings option?

Yes button is there and opens a html page (see screenshot).
but still, "letter" is the default format and I have no advanced options (i.e. under firefox/print)

---

### Post by ramjet_1953 on 2007-04-12
Ok, were getting there.

Some applications do not allow you to change print settings from within them.

However, with Firefox I just clicked "Print" and then clicked on "Properties", to get the following menus.

See attachment.

Regards,
Roger :cool:

---

### Post by hades_6_6_6 on 2007-04-13
OK Roger. The good news is you seem to have the same limitations as I have (no draft, multiple pages, etc.) :) 
But I don't think this is an application issue, since Firefox offers much more print options under M$.
Do you have more print options, printing from oo?

---

