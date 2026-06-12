---
title: "Getting a little upset now!!!!"
date: 2005-05-11
forum: Hardware &amp; Laptops
---

### Post by Calgarian on 2005-05-11
I finally managed to get my printer/scanner (HP PSC 1610) recognized and working by reconfiguring it through localhost:631. I did the password bit so that I could use the browser. However, it gets lost every time I reboot my system. Is this a permissions issue?

---

### Post by defkewl on 2005-05-11
You should save your session :)

---

### Post by Calgarian on 2005-05-11
I do. I have Kontact, Firefox, and Kopete that come up each reboot. They do so as they are always active on my desktop. I've tried everything I know about (which is not a lot) and can't get the backend to remember that a device has been defined to it.

The HP Device Manager and Xsane drop the scanner at reboot. The printer drops as well. It says it's there, but nothing prints. If I go into KDE Print Manager I can see the job just sitting their, but I can't get it to the printer. I've started and stoped the printer in the manager and still no action. Power off and restart on the printer does nothing. I'm not sure what modules to check for permissions?

---

### Post by Kurse on 2005-05-11
Have you tried configuring your printer using gnome-cups-manager (if you use Gnome) or kprinter (if you use KDE), instead of the http method?

---

### Post by Calgarian on 2005-05-12
Yes, I did try Kprinter and it didn't seem to work either. I get that funny message about the run level issue when I make install HPLIP. I will delete all printers, ensure that HP Device Manager is running. Build a new printer on Kprinter and see what happens.

---

### Post by wondering_jew on 2005-10-24
hey I just got my psc 1610 working for both scanning and printing (yay me!)...
first I did

sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2
I selected psc 1600 from  'HP (HPLIP)'  in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

Then xsane told me it didn't find any scanning devices so I installed a package called libsane-extras from synaptic and tried xsane again and it worked.

I didn't have to mess around with the [http://localhost:631](http://localhost:631) or hp-toolbox or any of that (I couldn't when I tried anyways)

---

### Post by Sef on 2005-12-26
Wondering Jew: Thank you, Thank you, Thank you.   I followed your instructions, and now I can both print and scan.  :D

---

