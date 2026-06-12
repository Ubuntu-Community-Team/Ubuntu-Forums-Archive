---
title: "webcam issue (including how-to for asus laptop webcam)"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by mazy haze on 2007-09-26
yesterday i managed to install my webcam (integrated in my notebook asus z92t - defacto the same as asus a6) on feisty using the syntec driver. just worked perfectly:

here is what i did:
```

wget http://belnet.dl.sourceforge.net/sourceforge/syntekdriver/stk11xx-1.1.0.tar.gz
tar -xzvf stk11xx-1.1.0.tar.gz
cd stk11xx-1.1.0/
wget http://bookeldor-net.info/merdier/Makefile-syntekdriver
make -f Makefile-syntekdriver
sudo make -f Makefile-syntekdriver install
sudo modprobe stk11xx

```

worked perfectly well. then i updated my system (new linux headers) and went to sleep... and today it's not working any longer. i removed everything (first i just tried sudo make -f Makefile-syntekdriver clean, then i removed everything by myself and started over again). i even tried the svn version ([https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver](https://syntekdriver.svn.sourceforge.net/svnroot/syntekdriver/trunk/driver)) but i always get the same error:
```
$ sudo modprobe stk11xx
FATAL: Error inserting stk11xx (/lib/modules/2.6.20-16-generic/kernel/drivers/usb/media/stk11xx.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

and here is what dmesg says:
```
$ dmesg | grep stk11xx
[ 2767.095049] stk11xx: disagrees about version of symbol video_devdata
[ 2767.095057] stk11xx: Unknown symbol video_devdata
[ 2767.095284] stk11xx: disagrees about version of symbol video_unregister_device
[ 2767.095287] stk11xx: Unknown symbol video_unregister_device
[ 2767.095379] stk11xx: disagrees about version of symbol video_device_alloc
[ 2767.095382] stk11xx: Unknown symbol video_device_alloc
[ 2767.095427] stk11xx: disagrees about version of symbol video_register_device
[ 2767.095430] stk11xx: Unknown symbol video_register_device
[ 2767.095565] stk11xx: disagrees about version of symbol video_device_release
[ 2767.095567] stk11xx: Unknown symbol video_device_release
```

the only thing i found on the web was that discussion: [http://forum.ubuntu-fr.org/viewtopic.php?pid=889392](http://forum.ubuntu-fr.org/viewtopic.php?pid=889392)
however, i don't speak frensh, but as far as i get it they don't have any solution, neither.

anyone got any idea?

---

### Post by PereX on 2007-09-27
Hello! I'm using 2.6.20-16-generic kernel with ubuntu 7.04, and using your how-to my webcam on my asus laptops finally rocks!!! thanks!!!

I don't know if it's important, but I download the driver from sourceforge web:

[http://sourceforge.net/project/showfiles.php?group_id=178178&package_id=205527](http://sourceforge.net/project/showfiles.php?group_id=178178&package_id=205527)

and not from :

wget [http://belnet.dl.sourceforge.net/sourceforge/syntekdriver/stk11xx-1.1.0.tar.gz](http://belnet.dl.sourceforge.net/sourceforge/syntekdriver/stk11xx-1.1.0.tar.gz)

try it... 

I notice that the image was inverted, not like a mirror, but "top-down". This fix it:

sudo rmmod stk11xx
sudo modprobe stk11xx vflip=1

---

### Post by c4no1 on 2007-10-05
hello.this is my first post.to the problem, i've already installed the driver but the image is upside-down.i already use -> modprobe stk11xx vflip=1 but still can't get the image right. i read somewhere about editing line 63 changing from vflip=-1 to vflip=1 but still can't get the image right.next i tried modprobe stk11xx hflip=0 vflip=1 but still can't get the image right.any help please? Thanks in advance

Regards

---

### Post by mazy haze on 2007-10-09
you have to remove the module before loading it again:
```
sudo rmmod stk11xx
sudo modprobe stk11xx vflip=1
```

---

### Post by c4no1 on 2007-10-10
i've already remove it by using rmmod.but still the problem occur. I guess i'll try to go through the driver again.Or maybe a fresh install.. :-k

---

### Post by scabras on 2007-10-23
I am trying to install the stk11xx-1.1.0 for the Webcam (ASUS A6JE) but when I start camorama I got the message:

Could not connect video device (/dev/video0). Please check connection.

It sounds that no /dev/video0 has been created when the module is loaded.
Any help?
Thank Stefano

---

### Post by BillG55 on 2007-10-27
I got this working, but the picture is only in blue colors. What is wrong?

---

### Post by armandas on 2007-11-09
> **BillG55 said:**
> I got this working, but the picture is only in blue colors. What is wrong?

Try adding "Color Correction" filter. This helped for me.

P.S. Thanks for a how-to, mazy haze :)

---

