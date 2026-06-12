---
title: "New to Linux need server installation help."
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by CombatGod on 2006-01-13
Hi I am new to linux. I was hoping to use Ubuntu to run my website. So I installed the server version. Is there a way to run a GUI on the server version? I was hoping to be able to edit and update the site on the server itself.

Also, can anybody list some resources I can use to help me set up my website. I've worked with setting up a website in a windows envirnment but never linux.

---

### Post by Xumbi on 2006-01-13
As far as getting a GUI, I would try running:

```

sudo apt-get install xserver-xorg

```

That should install Xorg at least.  I can't remember all the packages you would need to install the gnome desktop, but I'm sure someone else will...

As far as getting help to setup your website, I recommend this guide:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

Especially this page:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5)

which covers Apache.  The guide is aimed at internet service providers, but it has a lot of information that will probably help you.

---

### Post by hillbilly on 2006-01-13
you can install the desktop with

 > sudo apt-get install ubuntu-desktop

---

### Post by CombatGod on 2006-01-13
[QUOTE=Xumbi]As far as getting a GUI, I would try running:

```

sudo apt-get install xserver-xorg

```

That should install Xorg at least.  I can't remember all the packages you would need to install the gnome desktop, but I'm sure someone else will...

As far as getting help to setup your website, I recommend this guide:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10](http://www.howtoforge.com/perfect_setup_ubuntu_5.10)

Especially this page:

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p5)

which covers Apache.  The guide is aimed at internet service providers, but it has a lot of information that will probably help you.[/QUOTE]

The website is great thanks. However, now I'm having a problem with the permissions. When I try to access /etc/network/interfaces as the root user it spits out a Permission Denied error.

Any suggestions? I honestly have no idea what I'm doing :P

---

### Post by hillbilly on 2006-01-13
are you sure you are root ? (you can use "id" to verify)

The check the permissions of /etc/network/interfaces ! If the permissions dont allow root, then use chmod to set the proper permissions. And you would have to use "chmod" as user root.

---

### Post by CombatGod on 2006-01-13
well my command promt looks something like this
root@server:/home/loginname#

I followed the direction form the howto link exactly. 
the ID command spits out the following:
uid=0(root) gid=0(root) groups=0(root)

the command I'm trying to run is:
/etc/network/interfaces

that's spitting out the Permissions Denied

---

### Post by hillbilly on 2006-01-13
what is the output of ls -l /etc/network/interfaces. Make sure that it is an executable file.

---

### Post by CombatGod on 2006-01-13
[QUOTE=hillbilly]what is the output of ls -l /etc/network/interfaces. Make sure that it is an executable file.[/QUOTE]

well I get the following error:

bash: -l: command not found

---

### Post by curtis on 2006-01-13
You cannot directly run the text file.
Try:
```

nano /etc/network/interfaces

```
As root of course.
Also, you do not want it to be executable.
All you need it to be is readable and writable by root and maybe some other system accounts.

---

### Post by CombatGod on 2006-01-13
I'm sorry. The directions are not very clear.

[http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3](http://www.howtoforge.com/perfect_setup_ubuntu_5.10_p3)

All it says is to edit: /etc/network/interfaces
I thought I just had to run the command:
/etc/network/interfaces

However, I realized I had to use NANO to edit this.
Hopefully my assumption is correct :P

---

