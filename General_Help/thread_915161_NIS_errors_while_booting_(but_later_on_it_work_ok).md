---
title: "NIS errors while booting (but later on it work ok)"
date: 2008-09-09
forum: General Help
---

### Post by el_baby on 2008-09-09
Hi there...

every time I boot two completely different installs (one is a gnome ubuntu 8.04 installed quite some time ago, the other one is a fresh kubuntu 8.04.1 kde4 remix) I see the following:

```

* Starting NIS services
* binding to YP server...
* ....
* ....
* ....
* ....
* ....
* ....
* ....
* ....
* ....
* .... [fail]
[ OK ]

```


I found a couple of people with the same symptom here in the forums, but they've been always told to disable nis in order to get rid of the problem.

The point is that I USE NIS!! (and nfs... and my user and home are remote)... the funny thing is that at some point during boot, ypbind DOES succeed, cause I am able to use it.

I have the NIS server IP address in /etc/yp.conf

I think that there may be a problem of order during boot.

Any help would be appreciated.

---

### Post by kvtb on 2009-02-21
I think it has to do with network-manager. What happens if you remove network-manager?


Or what happens if you change the startup order of nis in /etc/rc2.d to start after network-manager?
Of move hald to start before nis?

NIS in Ubuntu is already broken for years. Given the current activity on NIS/NetworkManager it will stay broken for the next few years.

---

### Post by Russel_Winder on 2009-04-01
Is there an error report about this anywhere in the system?

(It is unacceptable that this has been broken for ages and nothing is done about it, and I am feeling a period of activism coming on...)

---

### Post by Russel_Winder on 2009-04-03
I have added Bug 354588 for this:

[https://bugs.launchpad.net/ubuntu/+source/nis/+bug/354588](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/354588)

The problem appears to be the start number of NIS compared to Network Manager.  NIS is 18 whereas Network Manager is 28.  By changing NIS to be greater than Network Manager (I changed NIS to 30), everything works without the timeout.

---

### Post by el_baby on 2009-04-03
Thanx Russel,

following your advice, I put nis after network manager (28 ) but before gdm (30)... so it is now happy #29:
```

sudo update-rc.d -f nis remove
sudo update-rc.d  nis start 29 1 2 3 4 5 .

```

Apparently the "thank you" and "solved" tools disappeared from this forums... but your post DID solve my problem and I DO thank you.

---

### Post by Russel_Winder on 2009-04-04
As noted on the error report, this change of number has the effect of speeding up booting massively, but doesn't actually fix the binding failure.  NIS services start up takes a while but succeeds, binding to the server still goes through its 11 attempts then fails but now does it very quickly because of the different state of the network adapter as Network Manager has started.

Thanks for picking up on this and moving it to the stage of sending in a patch for the Ubuntu and Debian guess to take notice of.

---

### Post by 480silverton on 2009-08-29
> **el_baby said:**
> Thanx Russel,

following your advice, I put nis after network manager (28 ) but before gdm (30)... so it is now happy #29:
```

sudo update-rc.d -f nis remove
sudo update-rc.d  nis start 29 1 2 3 4 5 .

```

Apparently the "thank you" and "solved" tools disappeared from this forums... but your post DID solve my problem and I DO thank you.

Will this actually work?

---

### Post by 480silverton on 2009-08-29
> **russel_winder said:**
> 
(it is unacceptable that this has been broken for ages and nothing is done about it, and i am feeling a period of activism coming on...)

amen!

---

### Post by el_baby on 2009-08-29
> **480silverton said:**
> Will this actually work?

Well, it worked for me at least... now I don't recall if I modified something after upgrading to jaunty... I think I did, but I don't remember...

Regards...

---

### Post by 480silverton on 2009-08-31
> **el_baby said:**
> Well, it worked for me at least... now I don't recall if I modified something after upgrading to jaunty... I think I did, but I don't remember...

Regards...


Well I did try that and I found no difference, other then the computer started having troubles mounting the nfs shares.

---

