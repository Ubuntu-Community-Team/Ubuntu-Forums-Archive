---
title: "Can not enable bluetooth after rfkill"
date: 2010-12-31
forum: Hardware
---

### Post by pedi0022003 on 2010-12-31
Yesterday i used "rfkill block bluetooth" to turn off my Bluetooth device.but after that i could not enable it by using "rfkill unblock bluetooth".
when i click on the applet all i get is a big "Turn On Bluetooth" button that actually does nothing.
when i run "lsusb" in terminal i get :
```

Bus 005 Device 002: ID 0a5c:2145 ***[COLOR="Red"]Broadcom Corp. Bluetooth with Enhanced Data Rate II[/COLOR]***

```
and when i run "rfkill list" i get :
```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
so whats the problem?how can i solve this?
by the way i'm using ubuntu 10.10 on thinkpad sl500c.
thank you.

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
deleted

---

### Post by pedi0022003 on 2010-12-31
i made mistake....how can i delete this posts?!its my internet problem

---

### Post by pedi0022003 on 2010-12-31
still no one?
i am so so sorry about the extra posts

---

### Post by pedi0022003 on 2010-12-31
just found the solution:
remove everything about Bluetooth and install them again!not a very "good" one but it works.i googled almost anything and tried almost everything.
sorry about too many posts again!

---

### Post by liju.g.chacko on 2012-10-06
**_Bluetooth not identified(cannot be enable) on resume with bluetooth blocked before suspend(solved)_**
When the system suspended with bluetooth blocked , on wake up bluetooth was not identified.
 I had used following two command to enable bluetooth 

[LIST]
[*]"killall bluetoothd"
[*]"bluetoothd"
[/LIST]
and that too has to be given after unblocking bluetooth

---

### Post by overdrank on 2012-10-06
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

