---
title: "Open Office printing: jobs queued but are 'stopped'"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by TimGS on 2008-02-19
I can print to my HP Photosmart 8750 from Evince and Eye of Gnome, but Open Office just puts jobs in the queue where they are 'stopped'. There is no option to unstop them!

It has worked in the past. Unfortunately there has been no obvious change that could have caused this.

spadmin is sure the 8750 is present. So is HPLIP. The print option on Open Office appears to recognise its there, and CUPS on localhost:631 recognises both the job and the printer (although it has nothing indicated after 'Location' on [http://localhost:631/printers/](http://localhost:631/printers/)).

It is connected via USB.

-- Tim.

---

### Post by diddums on 2008-02-19
Check page size in open office - Format=>Page=>PageTab 

Then when you select ctrl-p and the printer dialogue opens click preferences and make sure the page size option in preferences for your printer is the same as the page size for the Open Office Document - 

Quite often if there is a conflict between the 2 sizes, printing will not go ahead - On printers that have an LED Screen it will tell you to load a different size stock to match the Document Size


diddums

---

### Post by TimGS on 2008-02-21
Thanks for the reply.

I checked the settings but both OO and HPLIP are set to A4 portrait anyway.

Still stuck! 

-- Tim.

---

### Post by TimGS on 2008-02-22
bump

---

### Post by TimGS on 2008-02-29
Further to the above I have uninstalled and re-installed Open Office. No change.

I cannot seem to do likewise with foomatic or cups as Synaptic wants to remove ubuntu-desktop if I do.

Still stuck. Help!

-- Tim.

---

### Post by popch on 2008-02-29
> **TimGS said:**
> Further to the above I have uninstalled and re-installed Open Office. No change.

I cannot seem to do likewise with foomatic or cups as Synaptic wants to remove ubuntu-desktop if I do.

Still stuck. Help!

-- Tim.

I have an HP LaserJet 2100. It will not start printing until I press the larger of the two buttons after the file has been sent. I have yet to find where you turn that 'feature' off.

---

### Post by TimGS on 2008-03-01
The Photosmarts seem to be different. The largest button is the off button, and pressing the few other buttons doesn't do anything.

Maybe I'll try Gnome office instead as this is proving a rather crucial problem...

thanks anyway,
Tim.

---

### Post by TimGS on 2008-04-27
This problem was solved by uploading the latest HPLIP and installing manually. 

Hopefully 8.04 will use the latest HPLIP in the repositories.

-- Tim.

---

