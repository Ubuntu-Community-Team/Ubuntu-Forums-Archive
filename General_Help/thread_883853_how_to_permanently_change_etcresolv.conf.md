---
title: "how to permanently change /etc/resolv.conf"
date: 2008-08-08
forum: General Help
---

### Post by serialbox on 2008-08-08
Hey,

My stupid ISP has recently began using deep packet inspection to redirect invalid DNS requests to their own lame ad-filled search pages.  The only way around this is to use alternate DNS servers.

Ive modified /etc/resolv.conf and entered in the new name servers and they work fine for as long as I dont shut down my laptop.

Once I shut down and restart, /etc/resolv.conf reverts back to its original settings.  can I cause any harm by setting that file to readonly after I change it?

it annoying as hell to have to keep changing it after each reboot.

thanks

---

### Post by kpkeerthi on 2008-08-08
$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
# reboot

**Note:** 208.67.222.222 & 208.67.220.220 are the IPs of [opendns]("http://www.opendns.com"). You may want to change it to desired DNS server IP of your choice.

---

### Post by serialbox on 2008-08-08
> **kpkeerthi said:**
> $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
# reboot

**Note:** 208.67.222.222 & 208.67.220.220 are the IPs of [opendns]("http://www.opendns.com"). You may want to change it to desired DNS server IP of your choice.


Thanks a lot.. Im using 4.2.2.1 and 4.2.2.2 since I cant be bothered with setting up an opendns account to customize their redirection.  was all working great until I switched from windows to linux.

now im confused though.. do I need to add the nameserver lines to resolv.conf as well as modify dhclient.conf? or is it sufficient in just dhclient.conff?

thanks again

---

### Post by ilrudie on 2008-08-08
That is how I would do it on a Linux host.  I, however, have my router overwrite the dns my ISP tries to force on me and pass it out to any dhcp clients that connect to it.  I found this to be a great solution and it saves me a little configuration.  I use dd-wrt on a Linksys WRT45G.

---

### Post by kpkeerthi on 2008-08-09
> **serialbox said:**
> 
now im confused though.. do I need to add the nameserver lines to resolv.conf as well as modify dhclient.conf? or is it sufficient in just dhclient.conff?

thanks again

Just add the lines to dhclient.conf only

---

