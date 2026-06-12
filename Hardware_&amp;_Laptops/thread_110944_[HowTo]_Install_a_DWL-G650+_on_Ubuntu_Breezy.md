---
title: "[HowTo] Install a DWL-G650+ on Ubuntu Breezy"
date: 2006-01-01
forum: Hardware &amp; Laptops
---

### Post by ahFeel on 2006-01-01
After searching for few hours how to get my DWL-G650+ pcmcia card working on my pretty Ubuntu Breezy, i finally found and decided to make a little tuto, cause it's really not difficult but a lot of diff&#233;rents pages gives diff&#233;rents solutions, sometimes quite long and hard. Here's mine :

**Step 1**

Natively the card is detected and installed by the system, but the WiFi doesn't work, we'll go on removing the current driver :

First, we'll check that the drivers is installed :

```
$>find /lib/modules/`uname -r` -name "*acx*"
```

You should get :

```

$>find /lib/modules/`uname -r` -name "*acx*"
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/acx
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/acx/acx_pci.ko
```

Then, save them to /root or whatever you want.

```
$>sudo find /lib/modules/`uname -r` -name "*acx*" -exec mv {} /root \;
```

And finally, make and update of the modules d&#233;pendencies :

```
$>depmod -a
```

End of the first step, go on with the new drivers installation.

**Step 2**

You have to download two things :

First one is to get the drivers, you can grab them here :

[ftp://ftp.dlink.co.uk/wireless/dwl-g650+_rev_Bx/dwl-g650+_rev_bx_drv_v204.zip]("ftp://ftp.dlink.co.uk/wireless/dwl-g650+_rev_Bx/dwl-g650+_rev_bx_drv_v204.zip")
( you can also use wget url of course )

Unpack them :

```
$>unzip dwl-g650+_rev_bx_drv_v204.zip
```

ok, then the second thing : we'll get ndiswrapper, it allows to install Windows Wifi Drivers under linux ! ;)

```
$>sudo apt-get install ndiswrapper-utils
```

now, we just have to give ndiswrapper the right .inf file..

```
$>ndiswrapper -i /path/of/drivers/GPLUS.inf
```

and reboot !

I hope this tuto will work for you, that's the way i did and it works perfect now :)

--
ahFeel - [email]ahfeel@unixaumonde.com[/email]

---

### Post by funkydan2 on 2006-01-01
Thanks,

However, in what way does WiFi not work?  My card connects perfectly fine to my WEP enabled access point, though WPA is not supported.

---

### Post by ahFeel on 2006-01-01
Well, the card was found, iwconfig wlan0 seemed to work, but NOTHING came out with networks scanning ( iwlist scan ).. and now it works great. ^^

---

### Post by zambizzi on 2006-01-01
I'm in the same situation only I have a plain 'ol DWL-G650 (no +)....would it work the same way?  Where would I find the drivers?

---

### Post by wh0rd on 2006-01-01
It's funny that the WEP security worked under Ubuntu 5.04 and doesn't seem to work on Breezy. It only works without any security setup.

---

### Post by ahFeel on 2006-01-01
zambizzi, i DO think it would work exactly the same way, here's the URL of your drivers, hope you'll success with them :)

[ftp://ftp.dlink.co.uk/wireless/dwl-g650_rev_Bx/dwl-g650_rev_b_drv_superG_v248.zip]("ftp://ftp.dlink.co.uk/wireless/dwl-g650_rev_Bx/dwl-g650_rev_b_drv_superG_v248.zip")

Tell us if it worked ! we could make a more general thread :)

---

