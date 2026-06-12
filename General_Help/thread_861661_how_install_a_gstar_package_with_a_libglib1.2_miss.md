---
title: "how install a gstar package with a libglib1.2 missing??"
date: 2008-07-16
forum: General Help
---

### Post by g_rus on 2008-07-16
I use a gstar software to do my starcharts. Since some (k)ubuntu versions is not anymore in repositories. Well, i have a .deb package, and always was easy to isntall, but in new 8.04 at install, i get this:

Seleccionando el paquete gstar previamente no seleccionado.
(Leyendo la base de datos ...
226539 ficheros y directorios instalados actualmente.)
Desempaquetando gstar (de gstar_1.0-9_i386.deb) ...
dpkg: problemas de dependencias impiden la configuración de gstar:
 gstar depende de libglib1.2 (>= 1.2.0); sin embargo:
  El paquete `libglib1.2' no está instalado.
dpkg: error al procesar gstar (--install):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 gstar

That means that gstar depend of libglib1.2 and that library is not installed, and is not anymore at repositories too.

I can install gstar with option --all-force and work fine. But, every time when i want use Adept (like Synaptic to Kubuntu) or apt-get,gstar is remove because have "broken dependencies".
I have installed:

libglib1.2-dbg
libglib1.2-dev
libglib1.2ldbl

It's posible do something with that .deb, or reconfigure, or i don't know to work fine?

Here is posible to get a .de [http://ubuntu2.cica.es/guadalinex/mirror/debian/pool/main/g/gstar/](http://ubuntu2.cica.es/guadalinex/mirror/debian/pool/main/g/gstar/)

And here is the main site of gstar (not .deb here)
[http://www.ecn.wfu.edu/~cottrell/gstar/](http://www.ecn.wfu.edu/~cottrell/gstar/)

---

### Post by scragar on 2008-07-16
huh, looks like the package was in gutsy by that name but not in hardy...

you could try to install the gutsy version, then reinstall the hardy libaries over the top so apt is happy...

[http://packages.ubuntu.com/gutsy/libglib1.2](http://packages.ubuntu.com/gutsy/libglib1.2)

---

### Post by g_rus on 2008-07-17
Well, didn't work, because the installation process say that libglib1.2 have conflict with libglib1.2ldbl

I think, libglib1.2ldbl is the new name of libglib1.2 (I think, i'm not sure) and for that, when i install with option --force-all, the software work without problems.

What can i do that the .deb recognize a libglib1.2ldbl for libglib1.2? ... (if that is the way)

---

### Post by scragar on 2008-07-17
I don't think you can, since it's the packages dependencies that are the problem, you could unpack it, edit the dependencies list and repack it if you wanted, but that's more effort than it's likly to be worth:
```
dpkg --extract **Desktop/my_package.deb**
```
edit the controll file(not too hard to find), remove it's dependency/change it, save and run:
```
dpkg --build **[b]Desktop/my_package**
```
when it asks you wanna build a single package(press **s**).

---

### Post by yangzhi148 on 2008-12-15
Welcome to [www.fashioncorners.com](www.fashioncorners.com) there are many model of our products, our company  selling brand name shoes,hoodies,jeans,caps,belts, underwear,(R3,R4,TN,Air Jordan shoes ,Air Jordan woman shoes, Air Jordan children shoes ,nike max,nike shox ,gucci,bape,dunk,prada,dsquared,D&G,rift,converseshoes,evisu,coogi,bape,bbc,lrg,ggg,e-handy,artful lacoste t-shirt,hoodies,sweater evisu,bape,red monkey jeans, New era ,lv ,ed-hardy caps, underwear, belts, handbags )UGG boot, AF1/air jordans 5 mix style shoes, AF1/air jordans 12 mix style shoes,coach handbag,coach purse.,newera caps, fendi sunglasses .
 msn: [email]fashioncorners@hotmail.com[/email]	
email: [email]fashioncorners@yahoo.cn[/email]

I can offer low price and good quality for you.,if you are interested in them,please remember to contact me.

Jordan six(6) Rings : [http://www.fashioncorners.com/product_list.aspx?pcid=322](http://www.fashioncorners.com/product_list.aspx?pcid=322)
Jordan true flight:    [http://www.fashioncorners.com/product_list.aspx?pcid=347](http://www.fashioncorners.com/product_list.aspx?pcid=347)
Jordan 23 shoes :    [http://www.fashioncorners.com/product_list.aspx?pcid=338](http://www.fashioncorners.com/product_list.aspx?pcid=338)
Air Yeezy  shoes :      [http://www.fashioncorners.com/product_list.aspx?pcid=356](http://www.fashioncorners.com/product_list.aspx?pcid=356) 
ATO shoes              [http://www.fashioncorners.com/product_list.aspx?pcid=355](http://www.fashioncorners.com/product_list.aspx?pcid=355)
LRG hoodie:            [http://www.fashioncorners.com/product_list.aspx?pcid=78](http://www.fashioncorners.com/product_list.aspx?pcid=78)
Ed hardy hoodie:       [http://www.fashioncorners.com/product_list.aspx?pcid=90](http://www.fashioncorners.com/product_list.aspx?pcid=90)
Christian Audigier hoodie: [http://www.fashioncorners.com/product_list.aspx?pcid=87](http://www.fashioncorners.com/product_list.aspx?pcid=87) 
Coogi hoodie :       [http://www.fashioncorners.com/product_list.aspx?pcid=89](http://www.fashioncorners.com/product_list.aspx?pcid=89)
Affliciton hoodie:    [http://www.fashioncorners.com/product_list.aspx?pcid=350](http://www.fashioncorners.com/product_list.aspx?pcid=350)   
True Religion jeans: [http://www.fashioncorners.com/product_list.aspx?pcid=154](http://www.fashioncorners.com/product_list.aspx?pcid=154)
Coogi jeans :     [http://www.fashioncorners.com/product_list.aspx?pcid=138](http://www.fashioncorners.com/product_list.aspx?pcid=138) 
Ed hardy jeans:   [http://www.fashioncorners.com/product_list.aspx?pcid=143](http://www.fashioncorners.com/product_list.aspx?pcid=143) 
EVISU jeans :    [http://www.fashioncorners.com/product_list.aspx?pcid=144](http://www.fashioncorners.com/product_list.aspx?pcid=144) 
UGG boots :       [http://www.fashioncorners.com/product_list.aspx?pcid=304](http://www.fashioncorners.com/product_list.aspx?pcid=304)

---

