---
title: "Console boot WITH all options."
date: 2008-11-20
forum: General Help
---

### Post by dznn on 2008-11-20
Hi,

I'v been searching and reading all day long, I broke my system twice and fixed it twice so I came here for help... I know one can find alot about this subject on the net but maybe it's just too much to make sense.

**What I want to achieve:**
I want my system to boot into a shell instead of a xserv & co but I want it to have the same functionallity of an emulated terminal ( you know, when you press ctrl-alt-F* where F7 is default your graphical one... ). So I want my network connection to be up and ready to use the mighty internet :) I would still have to be able to switch terminals with CTRL-ALT-F* and start gnome with startx or start the service manualy ( /etc/init.d/gdm start ). And have colors in my terminal ( I think this is called ncurse library? I mean, it's due the use of ncurse. ) I don't mean colors like an xterm started from gnome, transparant and stuff.. I mean like old DOS colors :)

**What I'v tried & the problems I occured:**
First of all I downloaded sysv-rc-conf to make my 'own' runlevel, I chose 3 and edited it to only start the services I want it too ( no gdm no xserv no bluetooth... ) Then I had to find a way to set the default runlevel too number 3 so I searched and found that I had to edit the /etc/init.d/rc-default file, I know a little about bash scripting so I changed the else's from 2 to 3 and prayed it worked. ( I first used a default script i found on the net but my system refused to boot then so I tryed it myself ) But:
[U][COLOR="Red"]- There is no internet connection...
=> I tought 'i disabled a service to much and so I edited my runlevel to be exactly the same as the default ( 2 ) execpt gdm and xserv.
- Still no network connections made when I reboot..[/COLOR][/U].

Hardware: eeepc 901

**Extra questions: **
- I first tried to use grub to give me a chose between runlevels by adding the runlevel number behind the kernelboot options but this didn't work... Can this be done and if so, how?
- When I startx from the runlevel 3 a message on my desktop says i have to reload a panel or something but it doesnt work whenI click reload, I noticed my shutdown panel is gone... Can't get it to work.
- Will I consume less power from the battery when I'm in runlevel 3... Without gdm or xserv &...?


I hope someone here can help me because I really want this... 
If it has to be done on an completly other way, fine, I'd just want it to work, to achieve the effect I described. ( I want to keep runlevel 2 so just changing runlevel 2 isn't an option.. And I'd like grub to give me a choise...)

Thx in advance.

---

### Post by dznn on 2008-11-20
Anyone? ... Is this the right subforum?

---

### Post by dznn on 2008-11-21
Anyone?

---

### Post by dznn on 2008-11-21
[SIZE="1"][CENTER]bump[/CENTER][/SIZE]

---

### Post by dznn on 2008-11-22
What forum should I post this?

---

### Post by KeyserSoze93 on 2008-11-22
Were you really that concerned about which forum you posted in, or were you just keeping your topic hot?

```
sudo update-rc.d -f gdm remove
```

---

### Post by dznn on 2008-11-22
> **KeyserSoze93 said:**
> Were you really that concerned about which forum you posted in, or were you just keeping your topic hot?

```
sudo update-rc.d -f gdm remove
```

I tought I might get a faster answer in the right forum... And it kept my topic hot :p

But if you read my post you'd see I know how to remove gdm... So unless your method leaves networkmanager or something else with same functionallity intact it's not what I'm looking for.

Thx for you response.

---

