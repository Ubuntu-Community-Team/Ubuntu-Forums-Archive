---
title: "Generic Printer Listing keeps returning"
date: 2019-01-11
forum: Hardware
---

### Post by angel mike on 2019-01-11
Since upgrading to Ubuntu 18.04 I cannot permanently remove the Generic Brother Printer listing which does not work anyway.

 I have a Brother Printer HL-3150CDW which I setup using the  Download Files from the Brother site.This works and if I make the de-fault I can forget about the other printer listed - however I find it annoying that I can remove it but it keeps reappearing on the next bootup. The rogue printer is listed as 'Brother_HL_3150CDW_series' with sub title below 'Local Raw Printer'

---

### Post by angel mike on 2019-01-13
I have found the solution to the problem by visiting the Cups site [http://127.0.0.1:631/printers](http://127.0.0.1:631/printers) then clicking on Printer heading to give a list of the printers. Then double click on the offending printer and choose delete.

---

