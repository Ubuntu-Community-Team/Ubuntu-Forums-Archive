---
title: "Lexmark T630 over Samba"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by razialx on 2006-08-18
Hello,
I am having trouble getting a Lexmark T630 to work over Samba. There is no default driver for this model, though I have found a linux driver on Lexmark's website.

I installed the Debian package they have, but the driver does not show up on my driver list for creating a printer. I also tried using Alien on the RPM package, with no effect. There are drivers installed, however I am not finding any .ppd module to manually load. 

I have also tried a default post-script driver, but that does not work. It tells me that the printer is asleep.

Any help would be appreciated, I have read that these lexmarks can give problems. 

Tim
...
Lexmark Driver downloaded from:
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:359:0:0&emeaframe=&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:359:0:0&emeaframe=&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&target=http://downloads.lexmark.com/cgi-perl/downloads.cgi&&req=:::::)

---

### Post by czambran on 2007-03-16
First execute

sudo /usr/local/lexmark/setup.lexprint

Then do

lexprint

---

