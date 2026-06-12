---
title: "Howto install Ati driver?"
date: 2004-10-17
forum: Hardware &amp; Laptops
---

### Post by Ozxobez on 2004-10-17
Hey,

Today i installed Ubuntu. I have everything working except for the Ati driver. I searched this forums and found nothing usefull i also searched google and found nothing...  :cry: First i want to know how to install the drivers before i go and try it myself and screw everything up...  Can anybody help me with this?

---

### Post by bdoetsch on 2004-10-17
Have a look at the Ubuntu Wiki at the official Ubuntu web site. All explained there...

---

### Post by FLeiXiuS on 2004-10-17
Yes it should be located in the FAQ, [http://ubuntulinux.org](http://ubuntulinux.org)

---

### Post by Vulc on 2004-10-21
call me stupid but I can't find it  :(

---

### Post by Mikelevel on 2004-10-21
Hi , :D 
The solution is that...

In console :

```
sudo apt-get update &amp;&amp; apt-get install fglrx-driver linux-restricted-modules-2.6.8.1-3-386
``` 

and then reload system or 

```
modproble fglrx
```

and change driver in xfree config 

```
sudo sed -i -e 's/&quot;ati&quot;/&quot;fglrx&quot;/' /etc/X11/XF86Config-4
```

This works if you have the original kernel image. If you have a 686/k7/PPro/Celeron/PII/PIII/PIV image you must choose the correct linux-restricted-modules for your image.

This is the oficial doc: 

[http://wiki.ubuntu.com/BinaryDriverHowto](http://wiki.ubuntu.com/BinaryDriverHowto)

If you have a personal kernel , compiled with your own options , you must read this.... 

[http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html)

P.D: Sorry my english , its so bad  :oops:[/code]

---

### Post by HungSquirrel on 2004-10-21
Actually, your English is great.  Where are you from and what is your native language?  I didn't know you weren't a native speaker until you said your English was bad.  ;)

---

### Post by Mikelevel on 2004-10-21
Thanks!  :D Im spanish

---

### Post by HungSquirrel on 2004-10-21
Entonces perdona mi castellano horrible.   :wink:

---

### Post by Vulc on 2004-10-21
good guide

---

### Post by FreDeas on 2006-06-11
Hi,

I also have a serious problem in installing the drivers for ati. I'm completely new with linux and I would be grateful if sb could help me..

I've spent allmost all the day trying to make it work and studying everything from help files to forum articles on the web, but it doesn't. First of all I'm not sure I fully understand the instructions in the previous answers (I'm a completely newbie..) but I tried them and didn;t worked. Then I followed the instructions I found at ati.com ([https://a248.e.akamai.net/f/674/9206/0/www2)](https://a248.e.akamai.net/f/674/9206/0/www2)). I downloaded the driver, the automatic installation didn't work. When I try to install for specific distributor, after I click on "I agree" it shows a window where I should choose the distributor, I choose Ubuntu, but the "continue" is not shown at the screen, the window is too big and doesn;t fit, and I can't get a higher resolution (it's not supported)...

Anyway, I tried blindly to locate it using the arrows and when I press enter it sents me to a window where nothing happens (!!) The  progress bar doesn' t move and when I use the arrows (because I still can;t see what;s in the lower part) it either aborts the proccess or finds an error. This error "Error: unsupported architecture: 
[Error] Generate Package - error generating package : Ubuntu/6.06". Sometimes it showed an VCD error (or sth like that) and back at the terminal it was a blue screen wHich asked where would I like to locate the drivers or sth...

I'm sorry for my complete ignorance, I a linux user for only few days, but I 've tried everywhere and I can't find a solution. Please if somebody could help I would be grateful..

marinos.

---

### Post by mzdiman3870 on 2007-05-14
Re: Howto install Ati driver?
asd

---

