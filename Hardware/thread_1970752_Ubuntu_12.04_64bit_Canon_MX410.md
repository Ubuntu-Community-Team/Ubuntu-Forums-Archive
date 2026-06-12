---
title: "Ubuntu 12.04 64bit Canon MX410"
date: 2012-05-01
forum: Hardware
---

### Post by zylden on 2012-05-01
Hi
I am running ubuntu 12.04 64bit my wife is using 32bit. We both have the same problem.
I have a Canon MX410 printer, which works fine except:
It wont print if I select Grayscale or if I change the resolution. At the moment its printing very high quality and using up all my ink. It says it print successfully but nothing ever prints. This is on both our laptops.

Any help?

Thanx
Zylden

---

### Post by aikishugyo on 2012-05-04
> **zylden said:**
> Hi
I am running ubuntu 12.04 64bit my wife is using 32bit. We both have the same problem.
I have a Canon MX410 printer, which works fine except:
It wont print if I select Grayscale or if I change the resolution. At the moment its printing very high quality and using up all my ink. It says it print successfully but nothing ever prints. This is on both our laptops.
Hello, I am currently the maintainer of the Canon backend of the gutenprint project. The current development version of Gutenprint is much better equipped to automatically adjust options to avoid these problems, but even so, I hope I can help you print using the 5.2.7 version and see if there are further bugs I should correct.

Can you tell me if you have the gutenprint 5.2.7 driver installed, or if you are using some other driver for your printer?
If you are using the 5.2.7 driver, probably you have not selected compatible options for printing monochrome.
[LIST=1]
[*]you need to set the mode/resolution. If you want to print in Mono, you have to select a mono mode from the list of modes.
[*]you need to select "Grayscale" as the color model (as you inidicate you already have done).
[/LIST]
See if you get any results using this method. You can also see if changing the InkType to "K" in addition to the above 2 settings makes any difference (it should not, but since we are looking for bugs...).

I am curious what you mean you cannot print if you changet the mode/resolution. Is that for color (Color Model set to RGB) or only in combination with trying to print grayscale?

Regards,
Gernot Hassenpflug

---

### Post by zylden on 2012-05-14
> **aikishugyo said:**
> Hello, I am currently the maintainer of the Canon backend of the gutenprint project. The current development version of Gutenprint is much better equipped to automatically adjust options to avoid these problems, but even so, I hope I can help you print using the 5.2.7 version and see if there are further bugs I should correct.

Can you tell me if you have the gutenprint 5.2.7 driver installed, or if you are using some other driver for your printer?
If you are using the 5.2.7 driver, probably you have not selected compatible options for printing monochrome.
[LIST=1]
[*]you need to set the mode/resolution. If you want to print in Mono, you have to select a mono mode from the list of modes.
[*]you need to select "Grayscale" as the color model (as you inidicate you already have done).
[/LIST]
See if you get any results using this method. You can also see if changing the InkType to "K" in addition to the above 2 settings makes any difference (it should not, but since we are looking for bugs...).

I am curious what you mean you cannot print if you changet the mode/resolution. Is that for color (Color Model set to RGB) or only in combination with trying to print grayscale?

Regards,
Gernot Hassenpflug


I am using the drivers that the 12.04 picked up. I did not install anything else.
What I change is the resolution in the print preferences or/and the color.

I am going to try find this  gutenprint to see if that helps the problem.

---

### Post by aikishugyo on 2012-05-29
Any luck yet? You should use the gutenprint mailing lists or the gutenprint sourceforge bug report facilities to get more detailed help from, um, me :D

Project main page:
[http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)

mailing list information:
[http://gimp-print.sourceforge.net/p_Mailing_Lists.php](http://gimp-print.sourceforge.net/p_Mailing_Lists.php)

Sourceforge page with archives, forums and bug tracker:
[https://sourceforge.net/projects/gimp-print/files/](https://sourceforge.net/projects/gimp-print/files/)

Getting the latest code:
[http://gimp-print.sourceforge.net/p_Download.php](http://gimp-print.sourceforge.net/p_Download.php)

Regards,
Gernot

---

### Post by tim.hoeffel on 2012-06-07
I have the same problem with my canon ip4300. I'm running 11.1. I finally got Scribus to recognize my printer, but when I print the document it shows up in the spooler for a few seconds the disappears. 

But in other programs the color is way off (very dark) and the resolution only goes up to 600x600. I downloaded the [B]gutenprint-5.2.7.tar.bz2 but can't make heads or tails of how to install it from the ReadMe file. Any suggestions in "non-geek" language?

Tim
[]("http://sourceforge.net/projects/gimp-print/files/latest/download?source=files")[/B]

---

### Post by tim.hoeffel on 2012-06-07
Update: I downloaded the Gutenprint 5.2.7 tar package to my download file and extracted it. I followed the instructions on 
[http://gimp-print.sourceforge.net/p_Download.php](http://gimp-print.sourceforge.net/p_Download.php) . Went to the terminal and typed in the following instructions after getting sudo use:

tar xjvf gutenprint-5.0.0.tar.bz2
tar (child): gutenprint-5.0.0.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
     and
bunzip2 -c gutenprint-5.0.0.tar.bz2 | tar xvf -bunzip2: Can't open input file gutenprint-5.0.0.tar.bz2: No such file or directory.
tar: This does not look like a tar archive
tar: Exiting with failure status due to previous errors
  and
tar xjvf gutenprint-5.2.7.tar.bz2
tar (child): gutenprint-5.2.7.tar.bz2: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
    and 
./configure [options} with no results

I'm sure there is something simple I'm missing here.

---

### Post by pursak on 2013-03-23
Thanks for helping..

---

### Post by aikishugyo on 2013-03-23
Hi,
How to install gutenprint, well by now there are lots of such informations out there on these very forums, cut and pasted many times. Still, if you do not find them, here is a link to my dynamic DNS-enabled site:
[http://aikishugyo.no-ip.org/blog/](http://aikishugyo.no-ip.org/blog/)
Look at the article entitled "compiling gutenprint CVS and adding Canon printers".
You should most certainly not use 5.2.7, that is ancient with loads of bugs that have been fixed in 5.2.9 (don't use 5.2.8).
Please try downloading and compiling from the 5.2.9 source.

---

