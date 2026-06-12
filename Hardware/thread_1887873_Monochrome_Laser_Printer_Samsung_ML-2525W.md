---
title: "Monochrome Laser Printer Samsung ML-2525W"
date: 2011-11-28
forum: Hardware
---

### Post by Aureschnoe on 2011-11-28
Hello,

I bought a monochrome laser printer (Samsung ML-2525W). It work not very well. Indeed, I cannot use the both side function (sorry, but I don't know how to say "Recto-Verso" in English ^^). I have to use this function for my job, so it's a problem for me.

I tried to install the samsung's drivers, or the default driver but no one can solve this problem. With the Samsung's driver, the "both side function" is not activated, and with the default driver (Ubuntu's driver) my laser printer crash and I have to restart it.

I send a message on the french Ubuntu Forum, but they didn't send me any answer. I hope I can found a solution hier :-).

Thanks for your help, and sorry for my english wich is not very well (I'm french), I understand it better than I speak it :-)

Bye !
Aureschnoe

---

### Post by Aureschnoe on 2011-12-12
Nobody ?

---

### Post by xyzzyman on 2011-12-17
The feature is called 'duplex printing' in English. If it's not enabled in samsungs driver you are probably out of luck. It's advertised as a feature, and they do list linux as a supported OS so you may need to contact their support.

---

### Post by Aureschnoe on 2011-12-20
I send a mail to the support. They answered me that I need to call them. I know it will be a waste of time, but I will try. 

This is a copy of their answer :
> 
Monsieur,

Tout d&#8217;abord, nous tenons à vous remercier de l&#8217;intérêt que vous portez à notre marque.

Suite aux éléments que vous nous avez communiqués et afin de vous fournir la réponse la plus complète
possible et faciliter le traitement de votre demande, nous vous invitons à contacter un de nos spécialistes au
01 48 63 00 00 (du lundi au samedi de 09h à 20h, prix d&#8217;un appel non surtaxé) muni de votre facture d&#8217;achat
et être à proximité de votre produit.


Sincères salutations,

SAMSUNG - Service Consommateurs. 


If someone have an idea to solve my Printer's problem... It will be more efficient than the samsung's support :)

---

### Post by xyzzyman on 2011-12-20
Does your print screen look anything like this: 

[http://downloadcenter.samsung.com/content/UM/201110/20111024094050631/EN/en/english/printing.htm#BABHJGEA](http://downloadcenter.samsung.com/content/UM/201110/20111024094050631/EN/en/english/printing.htm#BABHJGEA)

---

### Post by Aureschnoe on 2011-12-20
No, some options are disabled and I cannot enable them. For example, I can see duplex mode, but I can't select it. 

Two examples :
[IMG]http://www.uppy.fr/up-6784.png[/IMG] [IMG]http://www.uppy.fr/up-6785.png[/IMG]

I use the official driver. With splix, the duplex-mode is activated (with all the printer's funtions) but when I use it, the printer crash instead of pause (when I have to return the paper into the printer).

---

### Post by xyzzyman on 2011-12-20
I have a feeling they just didn't include it in the driver for your particular model. In that manual it does say, "Not all features are available in other OS's." Sorry.

---

### Post by Aureschnoe on 2011-12-21
Is there a chance I can solve the problem with Splix ?

---

### Post by xyzzyman on 2011-12-21
Support for your model was added to splix back in February:

  * New upstream release
     o SVN snapshot from February 19, 2011
     o New printer supported: Samsung ML-1660, ML-1910, ML-1915, ML-2525,
       ML-2525W, ML-2580, ML-2580N, ML-3471ND, SCX-4600, SCX-4623F, SCX-4623FW,
       SCX-5330N, SCX-5530FN, Toshiba eSTUDIO180S, Xerox WorkCentre PE114e
     o Corrected PPDs for Samsung ML-3050, ML-3051, ML-3051ND
     o PPD files rebuilt with ppdc of CUPS 1.4.5.
     o QPDL 3 support.
     o Fixed memory leak in the pstoqpdl filter.
     o Fixed problem of Samsung CLP printers producing random pixels at the
       bottom of the page.
     o Link with libpthread when building with multithreading.
  * debian/rules: "make" call does not need command line arguments for manual
    linking of libpthread.
 -- Till Kamppeter <till.kamppeter@gmail.com>   Sun, 20 Feb 2011 00:39:35 +0100

What sort of crash are you having with those drivers?

---

### Post by Aureschnoe on 2011-12-21
When the printer used to be in pause under Windows (when I need to return the paper in the printer), it crashed under linux. The red light is lit, and I have to turn off the printer.

---

### Post by bojo42 on 2011-12-27
Just to be precise: the ML-2525W does only have fake duplex aka manual duplex.

---

### Post by xyzzyman on 2011-12-27
> **bojo42 said:**
> Just to be precise: the ML-2525W does only have fake duplex aka manual duplex.

Yeah, but when it normally is to wait for him to flip the paper over, the printer is receiving some sort of data from the computer that causes it to crash. So idk what your point is.... Unless this is a riddle, and that the answer is his problem is fixed in Precise Pangolin????

---

