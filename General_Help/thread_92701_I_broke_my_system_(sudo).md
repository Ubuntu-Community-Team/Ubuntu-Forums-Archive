---
title: "I broke my system (sudo)"
date: 2005-11-20
forum: General Help
---

### Post by B0rsuk on 2005-11-20
Hey

At the moment I'm typing this I can't get sudo or kdesu to work. It says it returns an error.
More specifically, I get
sudo: unable to lookup ubuntu via gethostbyname()

I've been trying to change my hostname recently. I did it by editing the configuration files. Now when I open one of them it seems they somehow reverted to "ubuntu".

Oh, and I tried to add a user via adduser. It worked, sort of, but after logging out my keyboard would esentially freeze. I wouldn't be able to type username/login on graphical login screen.
==========
Is my system effectively broken ? I don't have another machine to mount my disk and edit conf files.
If only reinstal would help, how do I store my current list of installed packages ? Can I write it down somehow ?

Please help !

---

### Post by Haegin on 2005-11-20
If you just need to edit the conf files try a live cd - this will get you into a base ubuntu system from where you can mount the hard drive(s) and change the conf files. I'm not exactly sure of your problem so I can't tell you exactly how to fix it.

Hope this helps

---

### Post by B0rsuk on 2005-11-20
Fixed.
I needed to change my hostname back to "ubuntu"

So-called "recovery mode" automatically logs you in as root.

---

