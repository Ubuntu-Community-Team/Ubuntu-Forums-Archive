---
title: "Openoffice 3.0"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by SuperIntense on 2009-03-28
How do I download and install openoffice 3.0 for 64bit?

---

### Post by bertolo on 2009-03-28
!google first before asking. that one it's pretty easy to solve imo.

---

### Post by jacksaff on 2009-03-28
Add the following repository to /etc/apt/sources.list (you can do this using the gui in synaptic)
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
You'll have to do a search on here to find the crypto key for this repo if you want to get rid of the warning messages. 
Run apt-get update, and ooo3 should show up in your package manager.

---

### Post by starchaser1 on 2009-03-28
Searching gives several different ways of adding OOo3. The repository suggestion, as jacksaff made, worked the best for me. 

I tried two other ways first and finally settled on the instructions here: [http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm]("http://community.zdnet.co.uk/blog/0,1000000567,10009699o-2000498448b,00.htm"), This fully integrated OOo3 into Ubuntu, though it does eliminate OOo2.4

---

