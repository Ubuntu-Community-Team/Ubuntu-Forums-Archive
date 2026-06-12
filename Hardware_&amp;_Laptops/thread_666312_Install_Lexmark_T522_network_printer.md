---
title: "Install Lexmark T522 network printer"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Erik. on 2008-01-13
Hi,

I have a Lexmark T522 printer in my network and i want to print on it.

I already found i driver for linux at the lexmark website:
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:298:0:0&searchLang=en&os_group=Debian%20GNU&target=](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:298:0:0&searchLang=en&os_group=Debian%20GNU&target=)


i also found the french website of ubuntu but i can not read it is there an page in english or dutch?
[http://doc.ubuntu-fr.org/materiel/imprimantes_lexmark_toutes](http://doc.ubuntu-fr.org/materiel/imprimantes_lexmark_toutes)
But when i want to add a printer i got an error.

Does someone know how to add the printer to my list so i can make print jobs?

Erik

---

### Post by Erik. on 2008-01-13
I also tried this:
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#head-5255cc8a7649a1b9977bc33497a036723ed15dab](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#head-5255cc8a7649a1b9977bc33497a036723ed15dab)

It says when you have problems whit Creating print queue Lexmark failed
That problem do i have you need to do :

sudo chown username:lp /etc/cups/interfaces
could not get acces to   /etc/cups/interfaces file or map does not exist

How can i slove this problem?

Hope someone could help me

---

### Post by wieman01 on 2008-01-14
I know very little about printers, but why do you not install the DEB file posted on their website? Wouldn't that be the most obvious solution?

---

### Post by Erik. on 2008-01-14
I already installed that file, thats a program...
When i want to add a printer into that program i got that error and you can reslove that problem whit some terminal lines but i got an error when i want to do that:

sudo chown username:lp /etc/cups/interfaces
could not get acces to /etc/cups/interfaces file or map does not exist

i don't have the map interfaces

---

### Post by wieman01 on 2008-01-14
But CUPS is installed by default, isn't it?

What does this yield:
> ls -l /etc/cups/interfaces

---

### Post by Erik. on 2008-01-14
File or map does not exist

Thats the output

i downloaded the dep file and installed it did everything i needed to do

---

