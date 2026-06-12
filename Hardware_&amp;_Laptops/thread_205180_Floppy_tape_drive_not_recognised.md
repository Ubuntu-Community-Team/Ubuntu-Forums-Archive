---
title: "Floppy tape drive not recognised"
date: 2006-06-28
forum: Hardware &amp; Laptops
---

### Post by BluDragon on 2006-06-28
I have an old Eagle Exabyte TR-3 Travan floppy tape drive that I would like to use to occasionally back up my Dapper Drake installation. After some research, I came across and installed ftape-utils. After the installation, I loaded the zftape driver using modprobe. I then ran the command "ftmt -f /dev/qft0 status" but I got a "Device does not exist" error. What do I need to do to make this dang thing work? I'm ](*,)  right now trying to figure it out.

On a side note: Can anyone tell me why this thing makes the bloody light on the floppy drive stay on whereas in the server I pulled it from I never had that issue? Also, the floppy drive does not seem to be working correctly whereas in the server it did. :-k

---

### Post by BluDragon on 2006-06-28
Doh! #-o Apparently the tape drive and floppy drive don't like being on the same bus. I guess I'll have to go to my favorite local computer store and find a controller card. Not sure how worth it it is, though, as I barely use the floppy drive (only occasionally when I make boot disks). :???:

---

### Post by dhughes on 2007-07-27
Any luck getting it to work?

 I thought I'd try my old Iomega Ditto Easy 800 tape drive, after much searching I came across ftape - so at least there is a driver. I never tried ztape.

 It's connected to the floppy controller so that should be OK it's the way it is supposed to be connected. I tried to install ftape but I got some errors I didn't know about so uninstalled it  using make uninstall (I think it was?). 

 There isn't any mention of ftape in Synaptic either.

 I also found this:
[http://packages.ubuntu.com/warty/utils/ftape-source](http://packages.ubuntu.com/warty/utils/ftape-source) ...but it seems every link to download from fails, the file isn't there.

* [ Ftape download](ftp://sunsite.unc.edu/pub/Linux/kernel/tapes/)
* [ Iomega tape drive manuals and specifications](https://iomega-na-en.custhelp.com/cgi-bin/iomega_na_en.cfg/php/enduser/std_adp.php?p_faqid=14432)

---

