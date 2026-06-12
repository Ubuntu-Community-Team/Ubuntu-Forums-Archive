---
title: "Dial up serial modem with Ubuntu 12.04"
date: 2012-09-21
forum: Hardware
---

### Post by contributor on 2012-09-21
Hi guys, I want to to configure an external dial up serial modem within Ubuntu 12.04. But, I don't how to do that. Can anyone please me? 

Thank you
Contributor

---

### Post by grahammechanical on 2012-09-21
You already have a utility installed for doing that. It is text based, which means that you do not get a graphical user interface. You use tab, space and the arrow keys to move around in it.

Just open the terminal and type in the command:

```
sudo pppconfig
```

You will need to enter your password. Do not expect to see it printed out on the screen. Just press Enter afterward.

You can also check out gnome-ppp in the Software Centre

And then there is this link:

[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")

See the heading Alternative way 2

Regards.

---

### Post by contributor on 2012-09-22
Thank you Grahammechanical for the response. I am doing it now. :)

---

