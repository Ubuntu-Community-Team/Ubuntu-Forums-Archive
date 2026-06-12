---
title: "Latest/Best ati driver..."
date: 2005-08-22
forum: Hardware &amp; Laptops
---

### Post by floyd27 on 2005-08-22
Hi.
i am STILL trying to get this driver installed..
I just need to know what one to go ahead and try again..

Should i use the ATI driver , or the ubuntu one if so what is the latest?
thanx...
I find there is one thing i dont like..
There is no definitive way to install these drivers.
I brows the site and see 50 different ways ..
This makes it confusing for the newbi..

There should be only 1 guide on how to do it .............

---

### Post by tmilam on 2005-08-22
Try the ubuntu driver first. It's xorg-driver-fglrx

If that doesn't work, at least you can uninstall it ;)  Then you'll want to either post your error message on the forums to see what others did to fix it (do this first) then if that doesn't help you, try the ones from ati.

---

### Post by tmilam on 2005-08-22
Oh, and as far as instructions on installing them go:

```

apt-get install xorg-driver-fglrx

modprobe fglrx

```

If you don't get an error with the modprobe command, it probably worked! Now all you need to do is run fglrxconfig, then /etc/init.d/gdm restart and you should be using ati's driver. If you get an error message saying Fatal: Module not inserted because blah blah....run

```

dmesg | grep fglrx

```

That may give you a clue to search the forums with. 

Installing the driver from ati is a little more involved. Just shout if you need more help.

---

