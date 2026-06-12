---
title: "&quot;owner&quot; and changing folder permissions"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by cp1969 on 2007-12-11
In the course of trying to get an Epson cx8400 to work with 7.10, I have come across the problem that I need to copy a file into /usr/share/cups/model

However, I can't, since it tells me I am not the owner.  It lists 'root' as the owner.

How do I copy a file into that folder?  

Thanks.

---

### Post by froy02 on 2007-12-11
Install nautilus-gksu with synaptics.

Open a terminal and type 'gksudo nautilus'.  Nautilus (GUI file browser) will launch with you as a super user. Now  you can copy any file even hidden ones by setting your preference.

---

### Post by eliasz on 2007-12-12
> **cp1969 said:**
> In the course of trying to get an Epson cx8400 to work with 7.10, I have come across the problem that I need to copy a file into /usr/share/cups/model


sudo cp fileYouWanaCopy /usr/share/cups/model

enter your password at prompt

---

### Post by cp1969 on 2007-12-13
edit deleted post

---

### Post by cp1969 on 2007-12-13
Then I realized it might need the .ppd extension, so I did this:

cep@cep-desktop:~$ sudo cp Stylus_CX8400.ppd /usr/shared/cups/model
[sudo] password for cep:
cp: cannot stat `Stylus_CX8400.ppd': No such file or directory
cep@cep-desktop:~$

Still no joy.

??

---

### Post by cp1969 on 2007-12-13
I spotted the error of having a "d" on the end of "share", so tried this:

cep@cep-desktop:~$ gksudo cp Stylus_CX8400.ppd /usr/share/cups/model
cep@cep-desktop:~$ 

Which....seemed to work?  At least no error message!

But when I look in /usr/share/cups/model  alas, there is no file there.

Anybody?

<sound of crickets chirping>

---

### Post by cp1969 on 2007-12-14
Oddly enough, that file IS in the model folder.  Sometimes it shows up; sometimes not.  I think I must have been in root(?) mode or something like that when it was visible.

---

