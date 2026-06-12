---
title: "location of linux kernal source code"
date: 2005-11-20
forum: General Help
---

### Post by javatrumpet on 2005-11-20
Hi,

I'm installing the linux VPN client provided by the IT department at my school, and the install routine asks for the location of the linux kernal source code in order to correctly build the VPN.  Where would this be?  I'm using Breezy Badger.

---

### Post by ecobuntu on 2005-11-20
hmm...well it's usually in /usr/src/linux*
Where linux is the name of the kernel.  I don't have my source installed so I can't tell you exactly where it is.  But try something like that first.

---

### Post by ratsalad on 2005-11-20
First you will need to install the kernel source for the kernel you're using. 

example:

$ uname -r
2.6.12-9-k7

$ sudo apt-get install linux-source-2.6.12

now if my memory serves me right, this just puts a tar.bz2 archieve in /usr/src ...  so now you have to unpack it.

$ cd /usr/src
$ sudo tar -xjvf linux-source-2.6.12.tar.bz2
$ sudo ln -s linux-source-2.6.12 linux

---

