---
title: "Problem with HD 6370M"
date: 2011-04-03
forum: Hardware
---

### Post by milsy on 2011-04-03
Hello :)

I'm trying to install a proprietary ATI Catalyst  driver (ver. 11.3) on Ubuntu 10.04 (kernel 2.6.32-30-generic). 
But she displayed me after install 
```
aticonfig: No supported adapters detected
```WT*?

I'm install drivers from package with options --buildandinstallpkg.
They are not support? Or i'm stupid?)

---

### Post by milsy on 2011-04-04
I'm install ubuntu 10.10. It works, drivers set.

---

### Post by sandy8925 on 2011-04-04
Please mark as solved.

---

### Post by milsy on 2011-04-07
&#1054;&#1082; :)

---

### Post by yogi1983 on 2011-04-20
hello folks
could we please reopen this thread. the real problem was not solved. the intial problem was with the card and 10.04.   i wish to stay away from 10.10. 
i have tried everything. it looks like evrything is in place then i try to do the aticonfig. and it doesn't see the driver.
ciao

---

### Post by schnelle on 2011-04-23
> **yogi1983 said:**
> hello folks
could we please reopen this thread. the real problem was not solved. the intial problem was with the card and 10.04.   i wish to stay away from 10.10. 
i have tried everything. it looks like evrything is in place then i try to do the aticonfig. and it doesn't see the driver.
ciao

Here you can find step by step guide for installing newest catalyst ( fglrx) driver:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

Cheers

---

### Post by xape on 2011-05-20
Hi,

Do you try the 11.5 driver on Ubuntu 10.10?
I have the same problem, the module works fine but displayed me after install 
```
aticonfig: No supported adapters detected
```.
andrea


> **milsy said:**
> Hello :smile:

I'm trying to install a proprietary ATI Catalyst  driver (ver. 11.3) on Ubuntu 10.04 (kernel 2.6.32-30-generic). 
But she displayed me after install 
```
aticonfig: No supported adapters detected
```WT*?

I'm install drivers from package with options --buildandinstallpkg.
They are not support? Or i'm stupid?)

---

### Post by GreekRockNRoller on 2011-06-15
Hello i run into the same problem with 11.4 too. I have a Asus notebook with this card and on 64bit ubuntu when running aticonf and after successfully installing the packages appears :no supported adapters detected
probably its unsopported by catalyst...

Could anyone give me an idea how to create a basic /etc/X11/xorg.conf file? thx!

anyway i will use this xorg.conf:
```

Section "Device"
 Identifier "ATI radeon 6370M"
 Driver "fglrx"
EndSection

```


if it works i will let you know

---

### Post by GreekRockNRoller on 2011-06-15
So it works!! but now on the right corner i have a watermark with amd logo saying unsupported hardware! anyway i can get rid of this?

Could anyone posts "control" file from etc/ati/ folder when using latest catalyst drivers (11.5) Thanx in advance!!

---

### Post by GreekRockNRoller on 2011-06-15
> **kubug said:**
> x86Daddy's suggestion worked like a charm.

In a terminal type this:

```
nano fixwatermark.sh
```Paste the following into it: 

```
#!/bin/sh
DRIVER=/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so
for x in $(objdump -d $DRIVER|awk '/call/&&/EnableLogo/{print "\\x"$2"\\x"$3"\\x"$4"\\x"$5"\\x"$6}'); do
 sed -i "s/$x/\x90\x90\x90\x90\x90/g" $DRIVER
done 

``````
chmod +x fixwatermark.sh
``````
sudo sh fixwatermark.sh
```Log out and back in. Ta da!
this does the trick !

---

### Post by Yellow Pasque on 2011-06-15
I am wondering if the watermark is gone with Catalyst 11-6..?

---

### Post by GreekRockNRoller on 2011-06-16
> **Temüjin said:**
> I am wondering if the watermark is gone with Catalyst 11-6..?

well when i firstly installed (11.6) it reappeared but then i runned again "sudo sh fixwatermark.sh" and after next loggin its gone.

---

