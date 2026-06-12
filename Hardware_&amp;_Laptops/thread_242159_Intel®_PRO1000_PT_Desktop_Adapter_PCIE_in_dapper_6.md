---
title: "Intel® PRO/1000 PT Desktop Adapter PCIE in dapper 6.06"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by iduriduridur on 2006-08-23
The existing e1000.ko driver does not work for this card. Search for this file e1000.ko

How to get running.

first install dapper
then login and update the normal Software updates way.

reboot because of the kernel update.

go to synaptic and install

make
linux-headers-2.6.15-26-amd64-generic - do a uname -r to make sure what you are running.
gcc

install

then get a terminal window up and do sudo su to be root.
type:
ln -s /usr/src/linux-headers-2.6.15-26-amd64-generic /usr/src/linux

download intels latest driver for your card. 

[http://downloadfinder.intel.com/scripts-df-external/File_Filter.aspx?Filename=e1000-]("http://downloadfinder.intel.com/scripts-df-external/File_Filter.aspx?Filename=e1000-")

unpack and go to src folder as root

make install. 

Maybe e1000.ko needs to be updated in Edgy /Dapper 6.06.2?

---

### Post by iduriduridur on 2006-08-25
Change:

The existing e1000.ko driver does not work for this card. Search for this file e1000.ko. find it as root and delete the existing file. 


I don't know if it is necessary step, but I did it. :rolleyes:

---

