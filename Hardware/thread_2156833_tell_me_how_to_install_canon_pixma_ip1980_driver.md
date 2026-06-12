---
title: "tell me how to install canon pixma ip1980 driver"
date: 2013-06-23
forum: Hardware
---

### Post by pasire on 2013-06-23
i will go mad ,i use distribuntion ubuntu-12.04 amd64 ,so i can't install deb packages downloaded from canon website ,because it is for 32-bit system ,but how can i compile this source package into deb package ,there is the address:
[http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP1900.aspx?DLtcmuri=tcm:14-738712&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/printers/InkJet/PIXMA_iP_series/PIXMA_iP1900.aspx?DLtcmuri=tcm:14-738712&page=1&type=download)

---

### Post by dino99 on 2013-06-23
[http://askubuntu.com/questions/280279/why-my-ubuntu-12-10-cant-recognize-canon-ip1980](http://askubuntu.com/questions/280279/why-my-ubuntu-12-10-cant-recognize-canon-ip1980)
[http://ubuntu4share.blogspot.fr/2011/03/how-to-install-printer-driver-canon.html](http://ubuntu4share.blogspot.fr/2011/03/how-to-install-printer-driver-canon.html)

and an old one to show you how to compile:
[http://mfirmanshah.wordpress.com/2009/06/22/install-printer-canon-pixma-ip1980-in-ubuntu-jaunty-jackalope/](http://mfirmanshah.wordpress.com/2009/06/22/install-printer-canon-pixma-ip1980-in-ubuntu-jaunty-jackalope/)

---

### Post by pasire on 2013-06-23
you offer me a broken link

---

### Post by pdc on 2013-06-24
if you 

1) create some symbolic links to tell your 64bit system where to find things on the Canon drivers

and 

2) install the drivers, we hope the printer will work

1) symbolic links: copy and paste the red commands into a terminal; using the top line of the terminal

> [COLOR="#FF0000"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

and 

> [COLOR="#FF0000"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]

2) Install drivers

go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100159003.html) and download the COMMON package [COLOR="#008000"]cnijfilter-common_3.00-1_i386.deb[/COLOR]

and go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100159101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100159101.html) and download the ip1980 package [COLOR="#008000"]cnijfilter-ip1900series_3.00-1_i386.deb[/COLOR]

then in a terminal,

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-common_3.00-1_i386.deb[/COLOR]

> [COLOR="#FF0000"]sudo dpkg -i cnijfilter-ip1900series_3.00-1_i386.deb[/COLOR]

if the install baulks on the 386 if you insert the command --force-all so it would be > sudo dpkg --force-all -i cnijfilter-common_3.00-1_i386.deb

let us know how you get along

---

