---
title: "Cinellera Installation Issue"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by eyevahn on 2009-03-07
Greetings,

I've been trying to install Cinelerra 4 for some time now. 

I've adhered to the following instructions:
[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

After I add the following akiad repository:
wget -q [http://akirad.cinelerra.org/pool/addakirad.deb](http://akirad.cinelerra.org/pool/addakirad.deb) && sudo dpkg -i addakirad.deb && rm addakirad.deb && sudo apt-get update

I run "sudo apt-get install cinelerra" in the Terminal.

Cinelerra installs and runs... however, not Cinelerra 4. 

Rather, I get Cinelerra 2.1 *Argh*

I've tried this several times now, and it seems that Cinelerra 2.1 is inescapable, every time I try to install the 4th version, 2.1 installs instead. :-/

My questions are the following:
1) How do I unsintall Cinelerra 2.1?
2) How do I install (or upgrade 2.1 to) Cinelerra 4?

I run the 64 bit version of Ibex and am generally a newbie as far as linux goes, so if you help me out, please be specific. :-)

Thank you very much,
-Ivan M-

---

### Post by Partyboi2 on 2009-03-08
>  1) How do I unsintall Cinelerra 2.1?From the terminal you can uninstall it by
```
sudo apt-get remove cinelerra
```>  2) How do I install (or upgrade 2.1 to) Cinelerra 4?Looking at the website it looks like Cinelerra 4 is only available in the hardy repo. So what you could do is remove the repo you added to install cinelerra, go to Software Sources (System>Admin>Software Sources>Third party Software, and remove deb [http://repository.akirad.net/](http://repository.akirad.net/) then add
```
 deb http://akirad.cinelerra.org akirad-hardy main 
```then install cinellera by typing
```
sudo apt-get update && sudo apt-get install cinelerra4-repack
```
You may then want to disable the  deb [http://akirad.cinelerra.org](http://akirad.cinelerra.org) akirad-hardy main repo afterwards to avoid any possible conflicts with other packages.

---

### Post by eyevahn on 2009-03-08
Thanks! It worked. 

=) 

Help much appreciated,
-Ivan-

---

