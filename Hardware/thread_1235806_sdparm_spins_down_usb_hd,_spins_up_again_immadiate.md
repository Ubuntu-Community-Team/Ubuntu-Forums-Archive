---
title: "sdparm spins down usb hd, spins up again immadiately"
date: 2009-08-09
forum: Hardware
---

### Post by ferencj on 2009-08-09
Hi,

I have an usb-sata outboard harddisk. I only use it once a day, it could sleep the rest of the time. 

sdparm --command=stop /dev/sdc spins down the disk nicely, but it spins up again immediately. 

This sort of defeats the purpose. :( The disk is not mounted, lsof /dev/sdc or lsof /dev/sdc1 or lsof /dev/sdc2 (2 partitions) don't list processes busy with the disk. 

Any help much appreciated!

Cheers,
Ferenc

(immEdiately, of course)

---

### Post by unutbu on 2009-08-09
Perhaps take a look at 

[http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html](http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html)

Which links to a script: [http://github.com/liyan/suspend-usb-device/raw/master/suspend-usb-device](http://github.com/liyan/suspend-usb-device/raw/master/suspend-usb-device)

I have not tried this, so please be careful.

It looks like the script issues 
```

sdparm --command=sync /dev/sdc >/dev/null
```
before
```

sdparm --command=stop /dev/sdc >/dev/null
```
I wonder if that helps.

---

### Post by ferencj on 2009-08-11
Hi,

Thanks for answering. Actually I tried

sdparm --command=sync /dev/sdc 
sdparm --command=stop /dev/sdc


But it didn't make a difference. I will give the script you mentioned a try, it looks promising, especially the unbind command.

cheers,
Ferenc

---

