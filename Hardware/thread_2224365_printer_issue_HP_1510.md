---
title: "printer issue HP 1510"
date: 2014-05-15
forum: Hardware
---

### Post by coral3 on 2014-05-15
Hi, not sure where my old profile went?

anyway - I bought a new printer yesterday, HPLIP says fully supported, plug in installs easy, test page prints, now its got issues. I send a file to print - message says job sent, printer half feeds a piece of paper and stops, a few minutes later the paper goes all the way through without printing, job remains in the print queue until I cancel it, then I keep getting pop up messages every now and then saying the same job has been sent to the printer and then completed. If I shut it all down and restart sometimes I can get one job to print, sometimes not. After trying to print, further print jobs cannot initialise the printer. I have up to date system. ASUS eeepc 1000HA + Lubuntu with Xubuntu installed instead.

thanks

---

### Post by plucky on 2014-05-16
> **coral3 said:**
> Hi, not sure where my old profile went?

anyway - I bought a new printer yesterday, HPLIP says fully supported, plug in installs easy, test page prints, now its got issues. I send a file to print - message says job sent, printer half feeds a piece of paper and stops, a few minutes later the paper goes all the way through without printing, job remains in the print queue until I cancel it, then I keep getting pop up messages every now and then saying the same job has been sent to the printer and then completed. If I shut it all down and restart sometimes I can get one job to print, sometimes not. After trying to print, further print jobs cannot initialise the printer. I have up to date system. ASUS eeepc 1000HA + Lubuntu with Xubuntu installed instead.

thanks

Open your browser and type in the address bar ```
localhost:631
``` and that should open the CUPS page.

You should be able to examine the logs in the "Admin" page.

Check the correct Paper Type is set in the "Default" Options for the printer.

Good Luck

---

### Post by bapoumba on 2014-05-16
> **coral3 said:**
> Hi, not sure where my old profile went?
..

You may want to start a thread in the Resolution Centre, an admin will be able to help you. Please point a your previous account.
[http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

---

### Post by coral3 on 2014-05-18
The settings all seemed to be correct, I deleted the printer and re-added it and now it seems to be ok

---

