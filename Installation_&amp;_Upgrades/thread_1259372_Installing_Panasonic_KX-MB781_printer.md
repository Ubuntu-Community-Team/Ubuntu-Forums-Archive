---
title: "Installing Panasonic KX-MB781 printer"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by BetaoPCS on 2009-09-06
I found the information with OKI Printing Solutions but it doesn't work on my system, following is what they suggested:
**wget  -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)**
**tar zxf foo2zjs.tar.gz**
**make**
**sudo make install**
**sudo make cups**
 
...and then restart.
 
When I type **make** it says "No targets specified and no makefile found. Stop."
for **sudo make install **"No rule to make target 'install'. Stop"
for **sudo make cups **"No rule to make target 'cups'. Stop"
 
I am a very newbie !
 
Thanks for any help

---

### Post by Partyboi2 on 2009-09-06
Hi, there is a step missing, after 
```
tar zxf foo2zjs.tar.gz
```change into the newly create source directory with
```
cd foo2zjs
```
then
```
make
sudo make install
sudo make cups
```

---

### Post by amcsng on 2012-02-04
foo2zjs não tem nenhum driver para Panasonic, muito menos para Panasonic KX-MB781.
Verifiquem o que postam aqui, isso é brincadeira.
Pelo menos para min, NÂO !

---

