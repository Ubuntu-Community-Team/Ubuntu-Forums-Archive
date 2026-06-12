---
title: "Can't find network card after install"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by pjhsv on 2006-06-04
Hi guys...I was wondering if someone could help me.  I downloaded Kubuntu 6.06, burnt the CD, booted the live disc on my laptop and all worked good.  When I installed it though, it can't find my PCMCIA network card anymore??  dmesg has an entry "cs: unable to map card memory!"   I don't have any entries at all relating to PCMCIA stuff when I use lspci ...i have no idea what the problem is...any help?

The strange thing is, when running with the live CD, it works fine.  It's only after a reboot that it wont work. (however, as I don't run a DHCP server, I have to manually add the IP settings for the live CD to work with the network card)

Also, if it's of any relevance,  /etc/pcmcia/ is empty.  Is that correct?  or should there be configuration files in there? (I don't have any other PCMCIA devices connected to the laptop, just the Xircom Realport network card).

Thanks guys.

Paul

---

### Post by colgate on 2006-06-06
I get the same problem with Xubuntu 6.06 on a old PIII Toshiba.
I think that it's a bug of the installer....

help needed here!

Bye

Federico

---

### Post by colgate on 2006-06-06
I resolved this issue installing "pcmcia-cs" even if it shouldn't be the solution because it is usefull just to older kernels....but it works!

bye

Federico

---

### Post by anti-dan on 2006-06-15
I had this problem (pcmciautils not recognising my card) and fixed it without needing to manually start pcmcia-cs's cardmgr every time.

It seems to be down to pcmciautils not being legacy compatible, so to fix it you've got to get the pcmcia-cs tarball from [http://sourceforge.net/project/showfiles.php?group_id=2405](http://sourceforge.net/project/showfiles.php?group_id=2405) then look in your /var/logs/syslog to find what firmware file it's not able to find (mine was PCMLM28.cis - your mileage may vary). Once you know what to do, copy the **.dat** version of that file from the tarball's ./etc/cis/ to /lib/firmware/ and rename it to **.cis** (I don't know why you need to do this bit, but you do :)). Then run /etc/init.c/pcmciautils restart and it should all work.

So, to sum up:

```
wget http://belnet.dl.sourceforge.net/sourceforge/pcmcia-cs/pcmcia-cs-3.2.8.tar.gz
tar zxvf pcmcia-cs-3.2.8.tar.gz
tail -f /var/log/syslog
#Take your card out and reinsert it here, note the .cis file required
sudo cp ./pcmcia-cs-3.2.3/etc/cis/XXXXXX.dat /lib/firmware/
#Replace XXXXXX with the name of the file you need
sudo mv /lib/firmware/XXXXXX.dat /lib/firmware/XXXXXX.cis
#Stop cardmgr just in case they conflict, this should work with /etc/init.d/pcmcia-cs stop but it complains about the kernel version
killall cardmgr
/etc/init.d/pcmciautils restart

```

*Hopefully* this will load the firmware for your pcmcia card and it will work without relying on deprecated software. It did for me running an ancient (1998!) Sony Vaio N505X celeron 333.

Cheers!

---

