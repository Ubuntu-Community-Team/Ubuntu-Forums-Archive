---
title: "How do I make scanner &quot;ScanMagic 600 CP&quot; work in Xubuntu 9.10?"
date: 2010-03-16
forum: Hardware
---

### Post by Jorisvh on 2010-03-16
I have a scanner ScanMagic 600 CP. I ran the program XSane Image Scanner. Is says: "no devices available". 
What can I do so my scanner is recognized?
The scanner is connected to my computer with a parallel port.

joris@oudePC:~$ sudo sane-find-scanner -p
[sudo] password for joris: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # No Mustek parallel port scanners found. If you expected something
  # different, make sure the scanner is correctly connected to your computer
  # and you have apropriate access rights.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
joris@oudePC:~$

---

### Post by ellgor on 2010-03-17
Hi,

Check in synaptic to see if you have libxsane-dev installed, do so if not, then open a terminal and start xsane from there :

sudo xsane

it seems to be a permission issue and this solved mine.

Regards, Ellgor.

---

### Post by Jorisvh on 2010-03-17
I tried to install  libxsane-dev. The package couldn't be found!

---

### Post by ellgor on 2010-03-18
Hi again,

Still try that command, it might just be a permission issue.

Regards, Ellgor

---

### Post by Jorisvh on 2010-03-18
Still "no devices available"
I think the parallel port is not detected by Xubuntu. How can I verify this?

---

### Post by Jorisvh on 2010-04-29
After searching and asking aid, I found a solution.
It succeeded me to scan as root!
This I have done:
Source: [http://home.scarlet.be/eddy_de_greef/](http://home.scarlet.be/eddy_de_greef/)

Bios -> Integrated peripherals 
Parallel port mode: ECP + EPP

Terminal:
sudo gedit /usr/local/etc/sane.d/dll.conf
# (uncomment)
mustek_pp

sudo gedit /usr/local/etc/sane.d/mustek_pp.conf
# (uncomment)
option no_epp 
scanner Mustek-600CP * cis600 

scan:
sudo xsane

Option: I don't know if this is necessary for others.
via [www.sane-project.org/source.html](www.sane-project.org/source.html) download sane-backends-1.0.20.tar.gz
  
Then installed like following:
Terminal:
- Making me root:
sudo -i
- that file copied to root folder
- file uncompressed:
tar jvfx sane-backends-1.0.20.tar.gz
- file installed:
cd sane-backends-1.0.20
./configure
 make
make install

And finally scan:
sudo xsane

---

