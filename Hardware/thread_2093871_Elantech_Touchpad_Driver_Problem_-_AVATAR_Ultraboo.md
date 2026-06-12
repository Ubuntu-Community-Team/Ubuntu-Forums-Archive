---
title: "Elantech Touchpad Driver Problem - AVATAR Ultrabook"
date: 2012-12-12
forum: Hardware
---

### Post by spine5 on 2012-12-12
Hello, I have an AVATAR ultrabook, this model: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834686004](http://www.newegg.com/Product/Product.aspx?Item=N82E16834686004)

They're a relatively little-known brand and I can't even find any instances of someone purchasing a product of theirs and installing any kind of Linux distribution on it.

I am running Xubuntu 12.10, on the latest kernel available (3.5.0-19).

It uses an Elantech Touchpad. However, I am unable to use two finger scrolling or any other kind of multitouch feature. There is no "Touchpad" option under the Xubuntu Mouse and Touchpad setting. gpointing-device-settings also has no touchpad options.

Output from various commands:

```
$ synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

```

```
$ xinput list
...
PS/2 Elantech Touchpad         id=12 [slave pointer(2)]

```

```
$ dmesg | grep 'elantech'
...
elantech: assuming hardware version 4 (with firmware version 0x361f00)
elantech: elantech_send_cmd query 0x02 failed.
elantech: failed to query capabilities.
(repeated many times)

```

I've seen lots of other people having issues with Elantech touchpads, but their issues all seemed to have been resolved with kernel patches tailored to their laptop model.

Does anyone have any advice for me? Experimental drivers or kernel modules to try, or something?

Thanks.

---

### Post by falseteeth on 2012-12-16
Also having this exact same problem. Identical model and output.

Any suggestions?

---

### Post by spine5 on 2012-12-16
Bump.

---

### Post by falseteeth on 2012-12-19
Still having this issue.

---

### Post by spine5 on 2013-01-04
Bump.

---

### Post by fiddlefan31 on 2013-09-29
Having the same issue as well - same output messages. This thread has been sitting around a while... Any luck with it yet?

---

### Post by saurosii on 2014-09-10
Hi,

I'm late but if it can help others.

I have a Avatar  AVIU-145A6 that have a Elantech and I had the same issue:

dmesg | grep 'elantech'
...
elantech: assuming hardware version 4 (with firmware version 0x361f00)
elantech: elantech_send_cmd query 0x02 failed.
elantech: failed to query capabilities.
(repeated many times)
I can't say it will works for everyone but here my workaround that solve my issue.

Add the parameter ***i8042.nomux=1*** in your kernel boot commande line.

If your are using GRUB2, it could be add in the */boot/grub/grub.cfg* file (dont forget to do a *sudo update-gru*b) 

ex.: *[COLOR=#333333][FONT=Ubuntu]**GRUB_CMDLINE_LINUX_DEFAULT=**[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]"quiet splash, [/FONT][/COLOR] i8042.nomux=1[COLOR=#333333][FONT=Ubuntu]"[/FONT][/COLOR]*

Here is the explanation I found:

The kernel (3.13.x for me) use the i8042 chips that are capable of multiplexing data coming from multiple pointing devices. The traditional PS/2 interface only provides for one keyboard and one mouse; modern laptops often have a two or more of a touchpad, a trackstick and an external PS/2 plug. Some controllers follow the active PS/2 multiplexing specification, which permit up to 4 devices; the data sent by each device carries an indication of which device it comes from.


The Linux driver tries to find out whether the i8042 controller supports multiplexing, but sometimes guessing wrongly. With the i8042.nomux=1 parameter, the driver does not try to detect whether the controller supports multiplexing and assumes that it doesn't. With the i8042.reset parameter, the driver resets the controller when starting, which may be useful to disable multiplexing mode if the controller does support it but in a buggy way.

---

