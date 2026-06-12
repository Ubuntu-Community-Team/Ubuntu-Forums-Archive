---
title: "Wireless Not Working?????"
date: 2008-07-18
forum: Hardware
---

### Post by cjb89chris on 2008-07-18
Hi,
This is my first time ever using Linux and I could use some help please :)
Erm... First of all I don't know how to install my wireless card. I have a Dell Inspiron 1501. 

Also I want to install flash player, I did get some help with this on another forum but they were giving me over complicated answers with all kinds of commands and something called terminal.

Thanks in advance for your help-(Keep it as simple as you can because I am (as I said) completely new to Linux).

---

### Post by phidia on 2008-07-18
If the Network applet from System>Admin>Network doesn't show your wireless card-you can try network manager also-then you probably will have to open a terminal and type/enter commands. It's not that hard. From Applications>Acessories>Terminal when that opens put this in there: > sudo lshw -C network You will be asked for your password, when you enter that you should see your network card listed.

---

