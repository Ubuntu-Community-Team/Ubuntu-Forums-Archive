---
title: "Lexmark Z816 (Ubuntu x64)"
date: 2010-03-22
forum: Hardware
---

### Post by Brotherbrat13 on 2010-03-22
I have tried for the last week to get my printer, the Lexmark Z816, to work on ubuntu with no luck. 

I have been following this (Probably out-dated) Guide: [http://sites.google.com/site/virtus92/lexmarkz810series(z815z816)](http://sites.google.com/site/virtus92/lexmarkz810series(z815z816))

I have problems converting the .RPM package to .deb with alien. It spits out this.

```
justin@justin-desktop:~$ sudo alien -d/home/justin/Desktop/z810llpddk-2.0-3.i386.rpm
error: incorrect format: unknown tag
Warning: Skipping conversion of scripts in package z810llpddk: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
mkdir: cannot create directory `z810llpddk-2.0': File exists
unable to mkdir z810llpddk-2.0:  at /usr/share/perl5/Alien/Package.pm line 257.
```

The one thing that I have noticed is that even if I can convert the RPM package to .deb, will it error saying that it is the wrong architecture type since I have a 64 bit OS?

Any help would be appreciated.

---

### Post by gordintoronto on 2010-03-22
When I followed your link to the Guide, I got "page not found."

Perhaps the alien command should have a space between "-d" and the file path.

Lexmark is notorious for being the most difficult brand of printer to use in Linux.

---

### Post by flyfishingphil on 2010-04-06
Using Ubunto 32 (ver 9.10) and tried the directions too. Can't get anywhere with the install. Plugged in printer and it offers to install but once done the printer sits idle and does nothing. Looked on the foomatic gui and the printer config and both have "no z810 series drivers found". If I find anything that works I'll add it in.

---

