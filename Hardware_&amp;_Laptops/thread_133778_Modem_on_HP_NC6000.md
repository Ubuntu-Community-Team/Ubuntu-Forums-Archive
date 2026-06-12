---
title: "Modem on HP NC6000"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by Zarek on 2006-02-20
Hello,

I've just installed Ubuntu 5.10 on my laptop HP NC6000 and got a problem with the internal modem Agere System AC'97. It doesn't work with ppcconfig and pon I tried so many times! I started searching the web and have found that I must install special drivers called slmodem.

I booted Windows and downloaded slmodem-2.9.9.tar.gz

Than booted Ubuntu and unpacked this file to my home directory.

Than I run

apt-get install make
apt-get install gcc

And after that:

make install

But Ubuntu showed my lots of pages with errors in .h and .c files and couldn't compile them.

Please give me advice what to do? I use Linux only several days and spent two days tryed to solve the problem with the modem but with no results :( 

Thanks in advance.

---

### Post by hollowhead on 2006-02-22
Zarek,

One possilbility is the following, [http://ubuntuforums.org/showthread.php?t=91596&highlight=hollowhead](http://ubuntuforums.org/showthread.php?t=91596&highlight=hollowhead).  To get anything to complile in breezy you seem to have to "downgrade" gcc to 3.4.4, download the debs concerned (link on page) to a folder then dpkg -i *deb, then follow the instructions at the bottom of this page to set the default gcc to 3.4.4 although it will still report 4.02 with gcc -v.  Then try recompiling slmodem.  

I have the same modem in my HP laptop and I'm unsure of how to proceed.  Some people say all you need to do is install slmodem and reboot others say you need the linux headers and other stuff.  If this works for you then please contact me through the private message system or post here with instructions!  Hollowhead

---

