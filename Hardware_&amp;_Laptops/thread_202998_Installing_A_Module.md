---
title: "Installing A Module"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by jgordon510 on 2006-06-24
I'm trying to install the fpi2002 kernel module (v0.5): [http://groundstate.ca/files/fpi2002-0.5.tar.gz](http://groundstate.ca/files/fpi2002-0.5.tar.gz) 

..which will allow the pen on my tablet pc to work, but when I try to make it I get:

I get:
2.6.15-25-386

Which makes me think that I need to run the 2.6 version of the Makefile.
If I do, it tells me:
make -C /lib/modules/2.6.15-25-386/build
SUBDIRS=/home/jeffrey/Desktop/fpi2002-0.5 modules
make: *** /lib/modules/2.6.15-25-386/build: No such file or directory.
Stop.
make: *** [fpi2002.ko] Error 2

Somebody on a non-ubuntu forum told me I need to install a kernel source, but I've tried to do that and I can't figure it out.  Can someone help?

---

### Post by woedend on 2006-06-25
do you have build-essential and the headers?  if not try downloading the headers.
sudo apt-get install build-essential
sudo apt-get install linux-headers-2.6.15-25-386


 then try just doing a make install.  so, you could untar the file in a directory such as /home/yourname/fpi
then open a terminal, do :

cd /home/yourname/fpi
sudo make install

if it finishes, then try
sudo modprobe fpi2002

let me know if i'm on the wrong track here or if you get this figured out.

---

### Post by angel12 on 2006-08-14
that doesnt work, im in the same boat. with the same driver. but this isnt the only driver thats giving me problems, my desktop's wifi card drivers are doing the same thing in dapper.

---

