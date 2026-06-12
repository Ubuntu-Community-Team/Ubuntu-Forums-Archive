---
title: "xsane and epson scanner"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by varla on 2005-07-07
Hi 
I am trying to use an Epson Perfection 3170 photo with xsane and I get:
no device available.
I have found no specific documentation on how to make this scanner work with ubuntu. Can anyone help me in any way?
I have no idea where to start with this. It is the first device I have used with ubuntu that is not exactly working as soon as it is pluged in.

thanks

V.

---

### Post by hagen on 2005-07-08
Hi,

I use a different epson scanner, but I've had similar problems.
I'm not sure if your scanner is supported. It is not listed under

[http://www.sane-project.org/sane-backends.html](http://www.sane-project.org/sane-backends.html).

Did you install the epson iscan package from

[http://www.avasys.jp/english/linux_e/index.html](http://www.avasys.jp/english/linux_e/index.html)   ?

If your scanner is supported it might not work for other reasons (for example "right settings"):

Did you run the epson scanner as normal user with general group settings?

I mean: 

Did you create a group scanner? 
Did you add your user to that group?

After I've created the "scanner" group, I added the user to that group. My scanner started to work then when I run xsane.

Hope that helps

Hagen

---

