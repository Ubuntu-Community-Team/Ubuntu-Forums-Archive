---
title: "acer aspire 3623 wireless card problem"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by cymoril on 2006-04-26
hello everyone.

i installed kubuntu on my new acer laptop.

this is my wireless card:

Integrated Acer InviLink&#8482; 802.11b/g Wi-Fi CERTIFIED solution supporting Acer SignalUp wireless technology.

i don't know how to make it work.

i loaded the "wireless lan manager ( kwifimanager )" but it wouldn't detect any networks.

some other specs:

celeron m processor 370 1.50 ghz.
mobile intel 910 gml express chipset.
512mb ddr2 ram.

please help!

thanks,
cym.


EDIT:

i did lspci -n to find my card's PCI ID: 14e4:4318 and its corresponding entries on [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

i found some of the broadcom drivers mentioned on that page in my Acer Resource CD. i tried installing them but after doing ndiswrapper -l , this is what i received:

Installed ndis drivers:
bcmwl5  invalid driver!
bcmwl5a invalid driver!
bcmwl5.sys      invalid driver!

: (

cym.

---

### Post by num_one on 2006-05-03
please check the following URL:
[http://midtoad.homelinux.org:9080/frog/user/midtoad/article/2006-03-24/18](http://midtoad.homelinux.org:9080/frog/user/midtoad/article/2006-03-24/18)
He said that he had the same error message and he managed to solve the problem and get the WLAN up.
hope that will help. 
let us know in any case.
good luck :)

---

