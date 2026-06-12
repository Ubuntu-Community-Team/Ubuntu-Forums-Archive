---
title: "Bluetooth Mouse/Keyboard at startup"
date: 2007-06-30
forum: Hardware &amp; Laptops
---

### Post by coreybox on 2007-06-30
Hey guys,

I'm having some problems with getting an active bluetooth keyboard and mouse at startup with Ubuntu.

By reading the Ubuntu page (found [here]("https://help.ubuntu.com/community/BluetoothSetup") ) i have been able to get them to connect.  Problem is, when following those directions for connect at startup, they never connect at startup.

As it is now, when my system reboots, i have to open terminal and type in:

sudo /etc/init.d/bluez-utils restart 
hidd --search

By typing that, both the keyboard and mouse are found and work perfectly.  Once I restart though, i can not log in with the keyboard.... i have to repeat those steps over again.

Is there anything missing from that page, or maybe something else i need to do for my system?

thanks,
Corey

---

### Post by coreybox on 2007-06-30
Also, i have just noticed, the connection is lost when the machine goes to sleep

thanks
corey

---

### Post by IntuitiveNipple on 2007-06-30
Use this forum post - it worked perfectly for me:

[ Bluetooth Mouse in Fiesty Fawn](http://ubuntuforums.org/showthread.php?t=468467)

---

### Post by coreybox on 2007-06-30
Thanks for the link, sadly this does not fix my problem.

```

HIDD_ENABLED=1
HIDD_OPTIONS="--connect 00:14:51:CD:75:A3  --connect 00:0A:95:50:CB:6C --server"

```

That is what I edited in my /etc/default/bluez-utils file.   I've also added hidp to my /etc/modules file.

Any ideas?

EDIT: I also notice that the file /etc/init.d/bluez-utils has similar lines as the above file.  Should they both be configured the same?

---

### Post by Jooky1138 on 2007-08-23
Coreybox,

I have been having a similar problem, and so has the poster in this tread:
[http://ubuntuforums.org/showthread.php?t=488902&highlight=bluetooth+mouse+restart](http://ubuntuforums.org/showthread.php?t=488902&highlight=bluetooth+mouse+restart)

If you have made any progress with your issue could you post it?

Thanks
Jooky

---

### Post by Jooky1138 on 2007-08-23
Oops wrong link :)
[http://ubuntuforums.org/showthread.php?t=529774](http://ubuntuforums.org/showthread.php?t=529774)

---

