---
title: "HP Envy 4500 Wireless Scanner"
date: 2014-12-06
forum: Hardware
---

### Post by Quarkrad on 2014-12-06
I have two machines - both running 14.04 and they can both print to my HP Envy 4500 wirelessly.  Both machines have the latest hplip software installed and as far as I can tell both are identical (I ran hp-check on both machines and the output was the same).  However, on one machine it will not scan - no matter what I do no scanner is detected.  Any advice on what to try appreciated - I know wireless scanning works so there is something specific on the machine that refuses to see the wireless scanner.

---

### Post by Quarkrad on 2014-12-07
I don't know whether this is a factor but in System Setting/Printers/HP-ENVY-4500-series the option (right click) to make it the Default Printer is greyed out.  I have deleted the hp driver software and re-install the latest hplip driver twice now and still no scanner.

---

### Post by Quarkrad on 2014-12-12
In my case the answer was my kernel.  The difference between the two machines was Kernel: 3.13.0-24-generic #47-Ubuntu (this one didi not scan/work) and  Kernel: 3.13.0-43-generic #72-Ubuntu (this one did scan).  I upgraded to 3.13.0-43 and I can now scan.

---

