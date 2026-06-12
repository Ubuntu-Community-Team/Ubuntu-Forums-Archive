---
title: "hp 3050 prints but no scanner"
date: 2011-10-03
forum: Hardware
---

### Post by gmarcotte on 2011-10-03
I have installed the HP dieskjet 3050A and the printing works fine but simple can and Xsane.

I tried down loading HPLIP and running the install. it gets all the way though but when you run hp-setup command it cant find the device. 

the normal printer install works fine and I can print to the printer. 

I have had no problems with some older hp USB printer/fax/scanner.

any ideas on how to get the scanner working?

---

### Post by 2F4U on 2011-10-03
Did you install HPLIP following the instructions from HP?

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

---

### Post by gmarcotte on 2011-10-04
yes I did,

it downloaded some modules then .config make clean and make no errors

i am trying to run the whole thing over again...

---

### Post by gmarcotte on 2011-10-04
Got it to work this time. had to reboot serveral times but both simple scan and xsane are working now

---

### Post by nomko on 2011-10-04
> **gmarcotte said:**
> yes I did,
 
it downloaded some modules then .config make clean and make no errors
 
i am trying to run the whole thing over again...
 
Before trying to install the hplip driver again, do this first to avoid any problems:
 
Open synaptic and search for hplip. Mark the package for complete removal. After removing the packages using synaptic, close synaptic and open a terminal. Type over this command: **sudo apt-get purge hplip*** , this will remove all packages of hplip which where left behind by synaptic. 
 
Then downlaod the latest driver from [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html). Start the installation procedur and follow the steps given during the installation procedure carefully. It is important not to switch on your printer! At the end of the installation procedure you will be asked to switch on your printer or to restart your system. Choose here to restart your computer! After the restart and login, switch on your printer. Check if everything works properly.

---

