---
title: "hp 1105 tablet"
date: 2010-01-08
forum: Hardware
---

### Post by onlycoder on 2010-01-08
hi
i have a hp smart touch tx2-1105 tablet...
in windows both touch and pen was wroking...
i suse 11.1 only pen was working...
now i installed ubuntu 9.10 64 but pen and touch not working.
i installed all pachages related to wacom and tablet with synaptic but no change!
when the pen touches the screen these rows adds to daemon.log:

```
Jan  3 23:49:20 mohamad-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/pan0, iface: pan0)
Jan  3 23:49:20 mohamad-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/pan0, iface: pan0): no ifupdown configuration found.
Jan  3 23:49:20 mohamad-laptop NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/pan0: couldn't determine device driver; ignoring... 
```plz help me.

---

### Post by Favux on 2010-01-08
Hi onlycoder,

Welcome to Ubuntu forums!

Please see the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

Hope this helps.

---

### Post by onlycoder on 2010-01-08
> **Favux said:**
> Hi onlycoder,

Welcome to Ubuntu forums!

Please see the [N-trig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

Hope this helps.

The link was a grate help...

I work whole day and finally it's working!!

mercy for your help.

now i can easily remove my windows with out any consideration!

---

### Post by Favux on 2010-01-08
Hi onlycoder,

Good!  Nice work.

---

### Post by onlycoder on 2010-01-08
i can't solve the auto rotation and I'm working on it....

there are 2 more problems... 

[LIST]
[*]the right click button on the pen does not working
[*]when the pen is near the screen or on it, the touch should be off and on again when the pen is over, this is because when you are using the pen, your hand is on the screen too.
[/LIST]

---

### Post by Favux on 2010-01-08
Hi onlycoder,

> i can't solve the auto rotation and I'm working on it....

How is that going?  Need help?

>     * the right click button on the pen does not working
    * when the pen is near the screen or on it, the touch should be off and on again when the pen is over, this is because when you are using the pen, your hand is on the screen too.

You are in Karmic (9.10).  Which N-trig firmware do you have?  Vista, Win7 rc, or Win7?  Which hid-ntrig.ko version are you using?

---

### Post by onlycoder on 2010-01-09
Hi,
i give up in this matter!
auto rotation not working...
i do the steps many times but there is no change.
 
my n-trig is hid-ntrig-2.6.31-16-generic (as same as my kernel??)

about the N-trig firmware... how can i find it out?

---

### Post by Favux on 2010-01-09
Hi onlycoder,

> auto rotation not working...
i do the steps many times but there is no change.

Are you using the ATI proprietary driver "fglrx"?  If so did you do the ati config command at the bottom of the Rotation HOW TO?  In lsmod do you see hp-wmi?
> about the N-trig firmware... how can i find it out? 
In Windows it should be in Device Manager.  Which Windows do/or have you installed?  Vista, Win7rc, or Win7?

---

### Post by onlycoder on 2010-01-09
i test hp-wmi in my tests, but not working...
I'll test again today.

the original os on this tablet was windows vista 32 home premium... bud i remove that and installed 7 x64. it was functioning the same as vista.

---

### Post by Favux on 2010-01-09
Sounds like maybe Win7 firmware.  The 2.184 firmware from HP.  As the HOW To mentions things don't work quite right with it.  If you compiled the hid-ntrig.ko using 'ntrig-v6.tar.bz2', you have Ayuthia's .ko for Win7 firmware.  He's working on it, as are some others.  He's posted an update for it but I think it breaks suspend/resume.

---

### Post by onlycoder on 2010-01-09
oh ok,

mercy for your help... 
i installed basket and ms-office 2007 in my Ubuntu, i completely removed my windows! I'm free free for ever!

---

### Post by Favux on 2010-01-09
Hi onlycoder,

Wow!

You might want to check out CellWriter, Xournal, and EasyStroke.


If you want to look at another effort by Ayuthia using linuxwacom 0.8.5-8 see [post #432]("http://ubuntuforums.org/showpost.php?p=8574003&postcount=432").

Petition to N-trig for linux support:  [http://www.ipetitions.com/petition/ntrig-on-linux/](http://www.ipetitions.com/petition/ntrig-on-linux/)

---

