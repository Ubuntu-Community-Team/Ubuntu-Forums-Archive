---
title: "kde printer tools problem &quot;escputil&quot; not found"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by metalox on 2005-06-27
Hi there, I have just installed "Hoary" Kubuntu. I have a small annoyance with my printer an Epson Styluc C82. When I try to use the "Printer Tools" in the Print Manager (KDE) to check ink amount and nozzle alaignment etc I get the following error message:

The executable escputil cannot be found in your PATH make sure gimpprint is installed and that escutil is in your PATH.

OK- Gimpprint is installed (or at least libgimprint1 is installed)

So I do  
# locate escputil

/usr/share/apps/kdeprint/tools/escputil.desktop
/usr/lib/kde3/kdeprint_tool_escputil.la
/usr/lib/kde3/kdeprint_tool_escputil.so

So I guess escputil is installed but none of the above looks like an executable does it? So what should I add to my PATH entry?

Anyway any help much appreciated. 

Ben

---

### Post by Bob D. on 2005-06-27
I have the exact same problem in Kubuntu, so I'll be interested to see what answers you get.

Bob

---

### Post by claydoh on 2005-06-28
Maybe try installing escputil via apt or synaptic? Those files listed above are just the gui front-end bits to the escputil program that the print system has. Some distros include escputil by default, some don't.

---

### Post by foustware on 2005-06-28
i installed the latest escputil (v5) with gutenprint from sourceforge. gutenprint is the latest gimp-print, they just changed the name and added a lot more hardware support. the older escputil was a little more problematic. i have an epson cx4600 and my only problem is that the path to the printer in print tools doesn't exsist. i can align, clean, and check heads - but i can't view ink level status. it displays an error box stating:

"Cannot open /Stylus CX4600 read/write: No such file or directory"

i'm puzzled over this because it must need a raw device but why wouldn't it be set already? i guess i could make /Stylus CX4600 a simbolic link to /dev/usb/lp0. anyone else have suggestions? by the way,

sudo escputil -r "/dev/usb/lp0" -i -u 

works fine, but problems like this pick at me.

---

### Post by metalox on 2005-06-29
[QUOTE=claydoh]Maybe try installing escputil via apt or synaptic? Those files listed above are just the gui front-end bits to the escputil program that the print system has. Some distros include escputil by default, some don't.[/QUOTE]
 Thanks! I wrongly assumed that escputil was already installed. OK now it is installed but the print manager is still unsatisfactory. See other post below...
Ben

---

### Post by metalox on 2005-06-29
I simply installed "escputils" using kynaptic. I have a new, clean installation of Kubuntu just a few days old. I am new to Debian, but have been using Linux for years. 

With escputils installed I now get a series of different Error messages when trying to use the print manager. I still can't check the ink levels (similar to above "Cannot open /Stylus C82 read/write: No such file or directory"). There is a checkbox for "Use direct connection (might need root permissions)" but checking it makes some functions that were working now not work and others just have a different Error message now!

Function / Error (examples):

Clean Print Head (use direct connection unchecked) / works!

Clean Print Head (use direct connection checked) / "cannot open device /Stylus C82 permission denied"

Print a Nozzle test (use direct connection unchecked) / works!

Print a Nozzle test (use direct connection checked) / "cannot open device /Stylus C82 permission denied"

Align Print head (use direct connection unchecked) / "Error: Printer alignment must be done with a raw device or else the -m option must be used to specify a printer"

Align Print head (use direct connection checked) / "Output:alignment must be done with a raw device or else the -m option must be used to specify a printer."

Ink Level (use direct connection unchecked) / "Error: Cannot open /Stylus C82 read/write: No such file or directory"

Ink Level (use direct connection checked) / "Error: Cannot open /Stylus C82 read/write: No such file or directory"

Printer Identification  (use direct connection unchecked) / "Error: Printer identification requires using a raw device"

Printer Identification  (use direct connection checked) / "Error: Cannot open /Stylus C82 read/write: No such file or directory"

Conclusion: The (KDE?) print manager is broken for practical purposes in Kubuntu Hoary. I will try installing "Turboprint" it always worked (unless someone can explain what I am doing wrong here ;-) . pity. I still like (K)Ubuntu so far, but how can I tell my friends who are used to other OSes to use it if it takes three days to get a pretty common printer working? I might try just installing Ubuntu and see if this is a Kubuntu thing. Any comments welcome...Ben :???:

---

### Post by bittner on 2005-08-04
Hi there!

Where can I find the kubuntu-package escputil?
'sudo apt-cache search espcutil' does not find anything.   :(

My /etc/apt/sources.list contains the following (I have stripped out the comments) and I have performed 'apt-get update' but no luck either:

deb [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary main restricted
deb [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary main multiverse
deb-src [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary main multiverse
deb [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

Any suggestions?

---

### Post by bittner on 2005-08-04
Sorry guys if this is the wrong place for this question but I did not find a more suitable one for now...  :---) 

I have succeeded in installing escputil finally, but I have a permission problem executing some of the options:

 1. Clean head (ital.: pulisci testina)  ... works fine

 2. Print *** (ital.: stampa un motivo di prova ugelli) ... works fine

 3. Allign head (ital.: allinea la testa)  ... prints out the usage and the error message "Printer alignment must be done with a raw device or else the -m option must be used to specify a printer."

 4. Ink level (ital.: livello inchiostro)  ... says "Error: Cannot open /dev/usb/lp0 read/write: Permission denied"

 5. Printer identification (ital.: identificazione stampante)  ... says "Error: Printer identification requires using a raw device."

Problem 3 should be easy to fix -- if I knew where to set the parameters the gui front end app uses to call escputil. Anyone knowing this?

Problems 4 and 5: How can I fix this?

Any help greatly appreciated!
Cheers, Peter

---

### Post by oscarand on 2008-03-28
Hi, it's a escputil incompatibiity with the (K)ubuntu systems. If are you interested, I developped a graphical utility based on escputil to display ink levels (at the moment supports only 4 cartridge printers), clean and align print heads...if are you intersted mail me to [email]oscarand@libero.it[/email] and I'll send you my program for free. Thanx

---

