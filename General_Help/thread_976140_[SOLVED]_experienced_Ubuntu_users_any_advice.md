---
title: "[SOLVED] experienced Ubuntu users: any advice?"
date: 2008-11-09
forum: General Help
---

### Post by ieBrazil on 2008-11-09
You see, 

I have Ubuntu and ... OpenOffice. Im downloading BrOffice, the Brazilian version of the suite.

And Im a new on this linux stuff... lay person.

So, do you have any advice to me before installing BrOffice? Shall I uninstall OpenOffice first etc.?

Thank you!

---

### Post by daniel of sarnia on 2008-11-09
Install it through Synaptic Package Manager under "System" and "Administration" than search for broffice.

 Or just type this into your terminal:

sudo apt-get install broffice

---

### Post by ieBrazil on 2008-11-09
> **daniel of sarnia said:**
> Install it through Synaptic Package Manager under "System" and "Administration" than search for broffice.

 Or just type this into your terminal:

sudo apt-get install broffice


is there any different if I install it downloading from its (brOffice) website?

---

### Post by ieBrazil on 2008-11-09
Hi. Sorry for sending you privately, but see if u can say sth about it:

sudo apt-get install broffice

After this, I type my password and then it says "E: Impossible finding broffice" (that's my translation from Portuguese).

Whats going on?

---

### Post by ad_267 on 2008-11-09
I think the package should be "broffice.org", i.e.:
```
sudo apt-get install broffice.org
```

Also you can go to System - Administration - Synaptic Package Manager and search for broffice to install this package. It does the exact same thing as that command.

The advantage of this method over installing from the website is that you get automatic security updates and the package is specifically configured for use with Ubuntu.

---

### Post by ieBrazil on 2008-11-09
ok, tnx. I am doing the thing on Syn. P. Manager... that might work!

thank you all so much.

---

### Post by ad_267 on 2008-11-09
Cheers, this is probably worth a read: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

