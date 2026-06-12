---
title: "Microtek scanner - I found something but I dont know what to do with it"
date: 2009-01-25
forum: Hardware
---

### Post by webmiester on 2009-01-25
Hi, Im not an advanced user of linux...

I was trying to get my microtek 3800 flatbed scanned to work on Ubuntu 8.10.  I plugged it in via usb but it doesnt detect it.

So I looked around and found that something from this sane project might work:

I found 

[http://www.sane-project.org/man/sane-sm3600.5.html](http://www.sane-project.org/man/sane-sm3600.5.html)     and
[http://www.sane-project.org/man/sane-sm3840.5.html](http://www.sane-project.org/man/sane-sm3840.5.html)

Im willing to give the drivers here a shot but I dont know what to do with the information on the website.

How do I make the info on these websites useful?  What commands should I use to install them?

Can I uninstall any of them after installation if it doesnt work?

Thank you so much.

---

### Post by teaker1s on 2009-02-19
have you got the latest sane /xsane installed? 
From what I read they basically say it works but has no user setup parameters.

---

### Post by webmiester on 2009-02-20
> **teaker1s said:**
> have you got the latest sane /xsane installed? 
From what I read they basically say it works but has no user setup parameters.

How will I know if I have the latest version?  I think I do, there are no updates pertaining to it so far.

When I plug it in, xsane would simply give an error.  Ill retry it so I can post the error here.

Thanks so much

---

### Post by teaker1s on 2009-02-20
[http://www.sane-project.org/]("http://www.sane-project.org/")

will have later version than ubuntu repositories and has Documentation.

Also you post no details of error, it could be an easy issue to sort if you can post more information please

---

### Post by geraldm on 2009-02-20
webmeister:

xsane --version

---

### Post by webmiester on 2009-02-21
> **geraldm said:**
> webmeister:

xsane --version

 E-mail: [email]Oliver.Rauch@xsane.org[/email]
  package xsane-0.995
  compiled with GTK-2.13.3
  with color management function
  with GIMP support, compiled with GIMP-2.4.6
  XSane output formats: jpeg, pdf(compr.), png, pnm, ps(compr.), tiff, txt

Here's the error when I load Xsane:

Failed to open device 'v4:/dev/video0': Invalid argument

Ive visited the the xsane site... it says a lot about having "source codes"... how do I make these so called "source codes" and other data on the website useful?  Im so sorry, Im really not a programmer.

---

### Post by webmiester on 2009-02-21
Oh what the heck!  The site you guys gave me has in its chart that my scanner model really isnt supported.  I guess it really wont work.,  Thanks so much though.

---

