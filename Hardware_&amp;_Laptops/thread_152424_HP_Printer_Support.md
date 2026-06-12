---
title: "HP Printer Support"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by kelsey23 on 2006-03-29
Hi, a friend of mine is wondering about using Ubuntu GNU/Linux, however he needs to be sure that his 'HP PSC 2400 AIO' device is supported. Is there a place I could look or would someone happen to know offhand? I am aware of ndiswrapper, however if there is a native solution I would much prefer that ^_^

---

### Post by Sef on 2006-03-29
LinuxPrinting.org is the place and the PSC 2400 will work:

[http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2400]("http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_2400")

Also see this post by wondering_jew on how he got his PSC 1600 to work:

[http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610]("http://ubuntuforums.org/showthread.php?t=39625&highlight=PSC+1610")


hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.

---

