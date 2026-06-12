---
title: "Canon MP540 Ubuntu 11.04 64-bit"
date: 2011-08-04
forum: Hardware
---

### Post by nmcbs70 on 2011-08-04
Hi,

Im having problems installing Canon PIXMA MP540 in Ubuntu 11.04 64-bit version. The regular canon drivers dont seem to work they report the error: "wrong architecture". Can anyone help me/ give me some instructions how to install? I have some important paper work i need to print.

Thank you
Regards

 Nuno

---

### Post by demonipuch on 2011-08-05
Hello

Follow these instructions :
```
sudo add-apt-repository ppa:michael-gruz/canon
sudo apt-get update
sudo apt-get install cnijfilter-mp540series
```(This will add this [ppa]("https://launchpad.net/%7Emichael-gruz/+archive/canon") to your repository list. It provides many Canon PIXMA drivers for Ubuntu.)

Now go to [http://localhost:631/admin](http://localhost:631/admin) and add your printer.

---

### Post by bluetonic on 2011-09-13
Thx demonipuch. It works like a charm :)

---

### Post by bannesen on 2012-01-08
Thanks a lot for this very useful answer.
It did also work like a charm for me.

---

### Post by melonenbaer on 2012-04-26
Thanks for this ppa. Worked for me, too! :P

---

