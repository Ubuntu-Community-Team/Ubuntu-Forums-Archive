---
title: "HP Deskjet 810C"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by Dylan103 on 2006-02-28
Hello,
I am fairly new to Linux ( had for about 5 days )
and I have a printer connected to my Windows XP computer, prints and works fine, I also have it so sharing is allowed. But, How do I get it working on my Ubuntu 5.10? I tried, but I think im doing something wrong. Could somebody please help?

---

### Post by Dylan103 on 2006-02-28
Sorry for double post/bump.
But Ireally need help.

---

### Post by DonVla on 2006-02-28
hello,

first install CUPS 
synaptic -> search "cupsys" -> mark for installation: cupsys and cupsys-client
then -> search "hpijs" -> mark for installation: hpijs and foomatic-db-hpijs
then apply (install).
now you open a browser and go to [HTML]http://localhost:631/[/HTML]
->  menage printers -> add printer ... and follow the cups wizard.

vlad

---

### Post by Dylan103 on 2006-02-28
Downloading Package files now, Thanks for the help, even if it doesn't work :).

---

### Post by Dylan103 on 2006-02-28
Username and password?
Use my login?

---

### Post by DonVla on 2006-02-28
or get this here:
[https://wiki.ubuntu.com/HPPrinterInstallation?highlight=%28printer%29](https://wiki.ubuntu.com/HPPrinterInstallation?highlight=%28printer%29)
i think that's the recommended way.

vlad

---

### Post by DonVla on 2006-02-28
try the official ubuntu.wiki way.

vlad

---

### Post by Dylan103 on 2006-02-28
Doesn't seem to work. i entered
sudo mv /etc/rc2.d/S19hplip /etc/rc2.d/S18hplip in terminal and it didn't do anything, just a new line. and the  $ sudo mv /etc/rc2.d/S19hplip /etc/rc2.d/S18hplip  came with an error about it not being a command.

---

### Post by DonVla on 2006-02-28
ok then type into terminal
> cd /etc/rc2.d (press ENTER)
ls (press ENTER)
now look if there's a file "S18hplip". perhaps it is already renamed.

vlad

---

### Post by Dylan103 on 2006-02-28
its there, so what do i do

---

### Post by DonVla on 2006-02-28
the "$"-sign means only that you have to type it in a terminal:
"$" - for user
"#" - for root.
it is not a part of the command.

vlad

---

### Post by Dylan103 on 2006-02-28
k, so do i reboot now? or what? i still needa setup my printer

---

### Post by DonVla on 2006-02-28
> 1. Open a console/terminal.

$ sudo mv /etc/rc2.d/S19hplip /etc/rc2.d/S18hplip

->>>> 2. Reboot your PC. <<<<-

and then go on like it is described in the wiki...

vlad

---

### Post by Dylan103 on 2006-03-04
Ok, I get this error in the [Http://localhost:631](Http://localhost:631) or w/e it is
   	Description: DeskJet-810C
Location:
Printer State: processing, accepting jobs.
"Connection failed with error NT_STATUS_UNSUCCESSFUL"
Device URI: smb://192.168.1.102/Dylan

---

### Post by Dylan103 on 2006-03-04
bump

---

