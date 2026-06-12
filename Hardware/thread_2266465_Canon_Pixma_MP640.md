---
title: "Canon Pixma MP640"
date: 2015-02-23
forum: Hardware
---

### Post by fkervin on 2015-02-23
Hi all,

I'd like to make my printer work under linux, but unfortunately I cant. The printer is a Canon Pixma MP640 and this is the[ download site]("http://www.canon-europe.com/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MP_series/PIXMA_MP640.aspx?type=download&language=ES&os=Linux")

Since I use a Ubuntu System I've download the last package "Debian Linux Print Drivers" and after unpacking the "MP640_debian_driver_pack.tar" file I have another three compressed file, then unpack the drivers one and I get a folder with an "install.sh" and a folder containing two .deb packages.

I've try yo install using the .sh file I get those dependencies errors:

cnijfilter-mp640series dependens on libatk1.0-0 (>= 1.9.0).
 cnijfilter-mp640series dependens on libcairo2 (>= 1.0.2-2).
 cnijfilter-mp640series dependens on libgtk2.0-0 (>= 2.8.0).
 cnijfilter-mp640series dependens on libpango1.0-0 (>= 1.12.3).
 cnijfilter-mp640seriesdependens on libtiff4.

If I try to manually open the .deb, the first seems to be installed, but second not, "**libfitt4 dependencies not meet**". I've try to install this **libtiff4 using sudo apt-get install** but doesn' works. After a search I see my system has libtiff5 instead, and don'k know hot to solve this.

How can I make this printer work?

Regards

---

### Post by pdc on 2015-02-23
Hi there fkervin

so the printer is a 2009 model; and things change quite a bit in the computer world; so back then, everyone had 32bit drivers and so the Canon debian package is for a 32bit install; 

one can make what are called symbolic links..................as the driver looks in lib whereas it should look in lib64..............if you tell us what you have installed; 

__________________

get libtiff4 from the Debian repository: [ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/](ftp://ftp.us.debian.org/debian/pool/main/t/tiff3/) and go about 14 or 17 down the list to find the 32bit or 64bit version .....................first few on the list are libtiff4-dev you can see ................

.........when you click to download, your software manager programme should offer to install it for you; there is a programme called gdebi installer that may or may not be already on your ubuntu version; many find it very useful as an install handler; and install it on their systems; 

_________________

if you are running 64bit, these symbolic links should hopefully help

```
sudo ln -s /usr/lib /usr/lib64
```

```
sudo ln -s /usr/local/lib /usr/local/lib64
```

..........to set them up, you need to open a terminal; paste each one in separately; line by line

_______----

let us know how you get along

---

