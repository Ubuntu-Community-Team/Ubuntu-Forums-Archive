---
title: "Pesty automatic printer installation"
date: 2020-04-27
forum: Hardware
---

### Post by bill-wilken-wilkenmail on 2020-04-27
After determining that 20.04's drivers for my networked Canon MX922 printer were unsatisfactory, I downloaded and installed Canon's proprietary CUPS drivers from its Asian website.  20.04 in its infinite wisdom, however, continues to automatically install its unsatisfactory setup in addition to my own.  As soon as I remove what Ubuntu has installed, it quickly re-installs.  I wonder whether someone from Redmond has gone to work for Canonical.

---

### Post by linux4me on 2020-04-27
> **bill-wilken-wilkenmail said:**
> I wonder whether someone from Redmond has gone to work for Canonical.

LOL. They're trying to make things "just work" for everyone, but if your printer isn't compatible without outside plugins it can be complicated.

I have an HP, for which Ubuntu 20.04 loads the correct (working) printer driver, but not the extra plugin required for scanning to work. The fix there is to let Ubuntu discover and install the network printer itself, then use the "hp-plugin" package which comes with hplip to install *only* the necessary plugin for the printer. That way, I get a fully functional printer with no duplicate installations. You might check to see if Canon provides something similar.

If not, you might find that one of the solutions [here]("https://www.scivision.dev/stop-ubuntu-printer-added-on-network-connect/") or [here]("https://askubuntu.com/questions/345083/how-do-i-disable-automatic-remote-printer-installation/") will work to turn off the printer auto-discovery. Make sure to read the comments in the latter thread; some of the recommendations appear not to work after 18.04. I think I'd try the edit of /etc/cups/cups-browsed.conf first.

---

### Post by slickymaster on 2020-04-27
*Thread moved to **Hardware**.*

---

### Post by gja on 2020-05-04
I had a similar problem with USB printing:

I noticed I had a problem with permission on a file.

Found a solution on German forum:
[https://forum.ubuntuusers.de/topic/hp-photosmart-5525-konfigurationsproblem-unter/4/](https://forum.ubuntuusers.de/topic/hp-photosmart-5525-konfigurationsproblem-unter/4/)

Apparently ippusbxd causes problems and can simply be removed.

I tried this instruction:
sudo apt purge ippusbxd

---

