---
title: "Bumblebee Nvidia GeForce GTX 970"
date: 2016-05-02
forum: Hardware
---

### Post by anon24 on 2016-05-02
I tried to install Bumblebee. After I rebooted, I am unable to get passed the user sign in screen. Help, please!

---

### Post by gnusci on 2016-05-02
Restart and use Alt+F3 to get a terminal, login and remove Bumblebee.

[B]sudo apt-get install ppa-purge
sudo ppa-purge ppa:bumblebee/stable
sudo apt-get purge bumblebee[/B]

---

### Post by anon24 on 2016-05-03
I hit Alt-Ctrl-F1 and that brought up terminal. It asks for my login and pass. When I enter what I know the be correct, it rejects it as if it's wrong.

---

### Post by zer010 on 2016-05-03
You probably mistyped it. Happens to me sometimes. :-P
Try again and report back.

---

### Post by anon24 on 2016-05-03
I have quadruple checked this. I did enter my info correctly.

---

### Post by anon24 on 2016-05-03
So, I decided to do a clean install.

In doing so, I received an error: Executing 'grub-install dev/sda' failed.

---

### Post by gnusci on 2016-05-03
Did you run the LiveCD?

---

