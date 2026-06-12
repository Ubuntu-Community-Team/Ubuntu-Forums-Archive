---
title: "HP Deskjet 612C"
date: 2006-03-30
forum: Hardware &amp; Laptops
---

### Post by benash on 2006-03-30
Hi,

I just installed Ubuntu 5.10 onto a machine with an HP Deskjet 612C attached through the parallel port.  The printer was not automatically set up.  

The System->Administration->Printers tool detected a 610C, so I tried both 610C and 612C drivers, but neither worked.  In both cases, a lot of garbage characters were printed on the test page, but there was some resemblance of a Ubuntu graphic.

Could anyone help?  This is  actually on my parents computer, who I don't live with. I can only work on this while I'm visiting.

Thanks,
Ben

---

### Post by Sef on 2006-03-31
First, on the first page of the printing dialog box, did you set the printer port to parallel?

Second, here is what wondering_jew did to get his printer running.  It was a PSC 1610, but it use the HPLIP driver like yours does.

```
sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds
```

> I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

---

