---
title: "Brother HL-5370DW network help"
date: 2011-01-15
forum: Hardware
---

### Post by onlineapps on 2011-01-15
I'm on Ubuntu 10.10 and just got a new HL-5370DW printer. All my Windows machines can connect to it fine. But when I try to connect Ubuntu to it, I get errors. Here's my process (using the printers that jockey-gtk installed for me):

1. System>Administration>Printing
2. Select the printer from under Network Printers (Brother HL-5370DW (BRW5CAC4C28913D). The same error occurs if  you try the ethernet connection (BRN001...).
3. Put "1" for "Input Trays" (I tried "3" too).
4. Apply printer name and description (defaults).
5. Print test page.
6. Ubuntu pops up a "Print Error" message: "There was a problem sending document 'Test Page' (job 424) to the printer."
7. Click Diagnose.
8. The troubleshooter tells me that the printer isn't enabled. "The queue 'Brother-HL-5370DW' is not enabled. The reason given is: 'Unable to locate printer 'BRW5CAC4C28913D'!'. To enable it, select the 'Enabled' checkbox in the 'Policies' tab for the printer in the printer administration tool."
9. Fair enough. I cancel the job and enable the printer. Then go into Properties > Test Page.
10. EXACT SAME ERROR WITH EXACT SAME DIAGNOSIS.

Help, anyone?

---

### Post by onlineapps on 2011-01-15
I'm using the drivers jockey installed for me, fyi.

---

### Post by onlineapps on 2011-01-15
Also, it works fine with a USB cable. Just not with a wireless connection. Or ethernet.

---

### Post by jorisctn on 2011-01-24
> **onlineapps said:**
> I'm on Ubuntu 10.10 and just got a new HL-5370DW printer. All my Windows machines can connect to it fine. But when I try to connect Ubuntu to it, I get errors. Here's my process (using the printers that jockey-gtk installed for me):

1. System>Administration>Printing
2. Select the printer from under Network Printers (Brother HL-5370DW (BRW5CAC4C28913D). The same error occurs if  you try the ethernet connection (BRN001...).
3. Put "1" for "Input Trays" (I tried "3" too).
4. Apply printer name and description (defaults).
5. Print test page.
6. Ubuntu pops up a "Print Error" message: "There was a problem sending document 'Test Page' (job 424) to the printer."
7. Click Diagnose.
8. The troubleshooter tells me that the printer isn't enabled. "The queue 'Brother-HL-5370DW' is not enabled. The reason given is: 'Unable to locate printer 'BRW5CAC4C28913D'!'. To enable it, select the 'Enabled' checkbox in the 'Policies' tab for the printer in the printer administration tool."
9. Fair enough. I cancel the job and enable the printer. Then go into Properties > Test Page.
10. EXACT SAME ERROR WITH EXACT SAME DIAGNOSIS.

Help, anyone?

Hi,

I had exactly the same problem with the same printer until I found a recipe that worked inmediately:
[http://www.liberiangeek.net/2010/10/add-network-printer-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/add-network-printer-ubuntu-10-0410-10-maverick-meerkat/)

Hope that it also works for you ;)
Joris

---

### Post by onlineapps on 2011-01-24
Unfortunately, my user was already set up with permissions to use printing. Anyone else?

---

### Post by jorisctn on 2011-01-24
> **onlineapps said:**
> Unfortunately, my user was already set up with permissions to use printing. Anyone else?

Printing permission was not the problem in my case.

I would suggest that you first delete the printer from the system and then follow the recipe to install it again.

HTH, Joris

---

### Post by onlineapps on 2011-01-24
> **jorisctn said:**
> Printing permission was not the problem in my case.

I would suggest that you first delete the printer from the system and then follow the recipe to install it again.

HTH, Joris

Did that too - no such luck.

---

### Post by alsac on 2011-03-28
> **jorisctn said:**
> Hi,

I had exactly the same problem with the same printer until I found a recipe that worked inmediately:
[http://www.liberiangeek.net/2010/10/add-network-printer-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/10/add-network-printer-ubuntu-10-0410-10-maverick-meerkat/)

Hope that it also works for you ;)
Joris


Found this and it worked great for me. Many thanks! 
Important part is to have the IP and /queue for location. Downloaded the drivers from Brother.

Works alike a champ!

Thanks again!

---

