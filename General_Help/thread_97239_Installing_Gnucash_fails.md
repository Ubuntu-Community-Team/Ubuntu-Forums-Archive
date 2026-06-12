---
title: "Installing Gnucash fails"
date: 2005-11-30
forum: General Help
---

### Post by ThomasArildsen on 2005-11-30
When I attempt to install Gnucash using synaptic, it fails due to depency trouble.
I get the following errors (it's the Danish version - "Afhængigheder" = "Dependencies", "men den bliver ikke installeret" = "but it will not be installed":

gnucash:
 Afhængigheder: gnucash-common, men den bliver ikke installeret
 Afhængigheder: bonobo (>=1.0.22) but it is not installable
 Afhængigheder: gdk-imlib1  but it is not installable
 Afhængigheder: libart2 (>=1.2.13-5) but it is not installable
 Afhængigheder: libbonobo2 (>=1.0.22) but it is not installable
 Afhængigheder: libgal23, men den bliver ikke installeret
 Afhængigheder: libgconf11 (>=1.0.7) but it is not installable
 Afhængigheder: libgdk-pixbuf-gnome2 (>=0.22.0-8) but it is not installable
 Afhængigheder: libgdk-pixbuf2 (>=0.22.0-8) but it is not installable
 Afhængigheder: libglade-gnome0  but it is not installable
 Afhængigheder: libglade0  but it is not installable
 Afhængigheder: libglib1.2 (>=1.2.0) but it is not installable
 Afhængigheder: libgnome32 (>=1.2.13-5) but it is not installable
 Afhængigheder: libgnomeprint15 (>=0.29-1) but it is not installable
 Afhængigheder: libgnomesupport0 (>=1.2.13-5) but it is not installable
 Afhængigheder: libgnomeui32 (>=1.4.2-3) but it is not installable
 Afhængigheder: libgtk1.2 (>=1.2.10-4) but it is not installable
 Afhængigheder: libgtkhtml1.1-3, men den bliver ikke installeret
 Afhængigheder: libguppi16, men den bliver ikke installeret
 Afhængigheder: libgwrapguile1, men den bliver ikke installeret
 Afhængigheder: liboaf0 (>=0.6.10) but it is not installable
 Afhængigheder: libofx2, men den bliver ikke installeret
 Afhængigheder: liborbit0 (>=0.5.17) but it is not installable
 Afhængigheder: libxml1 (>=1:1.8.14-3) but it is not installable
 Afhængigheder: libzvt2 (>=1.4.1.3-3) but it is not installable
 Afhængigheder: oaf (>=0.6.10) but it is not installable
 Afhængigheder: guile-1.6-slib, men den bliver ikke installeret
 Afhængigheder: libfinance-quote-perl  but it is not installable
 Afhængigheder: libdate-manip-perl  but it is not installable
 Afhængigheder: libgconf11 (>=1.0.9-7) but it is not installable

gnucash-common:
 Afhængigheder: gnucash, men den bliver ikke installeret

grisbi:
 Afhængigheder: libofx2, men den bliver ikke installeret

libguppi16:
 Afhængigheder: libgnomeprint15 (>=0.32-1) but it is not installable

This looks like pretty serious trouble to me :( . I'm trying to install it on a freshly installed Ubuntu 5.10 Danish and the only things I installed so far are Firefox and Thunderbird.
Can anyone help me?
Best regards,

Thomas Arildsen

---

### Post by yoyoned on 2005-11-30
are you using apt??  Try "sudo apt-get install gnucash" at a terminal.

---

### Post by ThomasArildsen on 2005-12-03
Unfortunately, that gives me the same reply...
Best regards,

Thomas Arildsen

---

### Post by derrick1985 on 2005-12-03
Try

sudo apt-get -f install
Open Synaptic and look under the broken filter to see if any packages are broken.

sudo gedit /etc/apt/sources.list and uncomment out any lines that start with deb, BUT, comment out the first line that is your cd rom. Save and run 

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gnucash

---

### Post by ThomasArildsen on 2005-12-10
Hmmm, except for a couple of the dependencies, it didn't solve the problem.
Thanks for helping anyway.
Could the problem be my Danish version of Ubuntu?
Best regards,

Thomas Arildsen

---

### Post by greywolf73 on 2005-12-10
I have the same problem, I am usable to install gnucash by either apt-get or Synaptic Package Manager:(

---

### Post by John Jason Jordan on 2005-12-10
[QUOTE=greywolf73]I have the same problem, I am usable to install gnucash by either apt-get or Synaptic Package Manager:([/QUOTE]
Me too, and I have US English version, Ubuntu-64 Breezy. So the problem is not limited to the Danish version.

Gnucash worked fine under Hoary, but broke after the upgrade to Breezy. I had to uninstall it because Synaptic kept bitching about broken packages. Uninstalling was the only solution. I tried reinstalling (via Synaptic), but it still failed and resulted in broken packages again. If there's a fix I wish someone would post it.

---

### Post by wildnfree on 2005-12-28
Me too!

I've been an expert user of Debian since 1996, and never had a problem with any Debian distribution until I tried installing Breezy!

I tried synaptic and apt-get to get it to install. Just blocks on a circular dependency between gnucash and gnucash-common.

I tried using grisbi to replace it, but I can't read french so can't rtfm to learn grisbi.

Therefore, unless I can find a way of installing gnucash before the weekend, I'll have to return to vanilla Debian, and throw the Ubuntu CDs to my dog as frisbees. Ubuntu is totally useless to me if I can't install the necessary software.:(

---

### Post by wildnfree on 2005-12-28
[QUOTE=wildnfree]Me too!

I've been an expert user of Debian since 1996, and never had a problem with any Debian distribution until I tried installing Breezy!

I tried synaptic and apt-get to get it to install. Just blocks on a circular dependency between gnucash and gnucash-common.

I tried using grisbi to replace it, but I can't read french so can't rtfm to learn grisbi.

Therefore, unless I can find a way of installing gnucash before the weekend, I'll have to return to vanilla Debian, and throw the Ubuntu CDs to my dog as frisbees. Ubuntu is totally useless to me if I can't install the necessary software.:([/QUOTE]
:D 

I have now found the solution to getting gnucash to install without any dependency errors.

I tried again apt-get install gnucash
this downloaded the .deb files from the ubuntu site.

but installation failed on the following message:
  
Fetched 4194kB in 13m58s (5003B/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/libh/libhtml-tagset-perl/libhtml-tagset-perl_3.04-1_all.deb  Size mismatch
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/libu/liburi-perl/liburi-perl_1.35-1_all.deb  Size mismatch
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/pool/main/libw/libwww-perl/libwww-perl_5.803-4_all.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

individual apt-get install commands for each of these three files on the cdrom failed for the same reason. So I installed them manually using dpkg, and then forced a configuration of them using:

 dpkg --force-configure-any -i  /media/cdrom2/pool//main/libw/libwww-perl/libwww-perl_5.803-4_all.deb

I then again tried apt-get install gnucash to get the final files which had been abandoned after the former size mismatch errors on the three files I manually installed.

This resulted in apt-get configuring gnucash, which now works! :cool:

---

