---
title: "Installing Brother printer drivers breaks dependencies"
date: 2012-02-26
forum: Hardware
---

### Post by lukjad on 2012-02-26
I installed my Brother MFC465CN printer drivers using [this guide]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html") and the commnads: 

```
Command (for dpkg)  :  dpkg  -i  --force-all  (lpr-drivername)
```

and 

```
Command (for dpkg)  :  dpkg  -i  --force-all  (cupswrapper-drivername)
```

Now whenever I try to install something I get these errors:

```
lukjad007@StationY:~/Desktop/test$ sudo apt-get install kobodeluxe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kobodeluxe is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 brother-cups-wrapper-extra : Conflicts: mfc465cncupswrapper:i386 but 1.0.1-1 is to be installed
 brother-lpr-drivers-extra : Conflicts: mfc465cnlpr:i386 but 1.0.1-1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I tried running apt-get -f install but it just uninstalls my printer.

---

### Post by lukjad on 2012-02-27
Bump.

---

### Post by lukjad on 2012-02-28
Bump..

---

### Post by plucky on 2012-02-28
Brother MFC465CN :-

According to [Brother Driver Packaging Wiki](https://wiki.ubuntu.com/BrotherDriverPackaging),your printer drivers are already packaged in the Multiverse Repository.

Open Synaptic Package Manager and remove the drivers you installed and then search for **brother-cups-wrapper-extra** and **brother-lpr-drivers-extra** and install them.

Then connect and power on your printer and your system will try to install it.Select the correct driver for your printer from the list of drivers it finds.

If your printer has a scanner,you will still need to download and install the correct driver for the Brother Website.

Good Luck

---

### Post by lukjad on 2012-03-01
Thanks! It finally works!

---

