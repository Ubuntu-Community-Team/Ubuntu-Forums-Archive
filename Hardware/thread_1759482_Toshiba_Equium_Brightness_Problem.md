---
title: "Toshiba Equium Brightness Problem"
date: 2011-05-15
forum: Hardware
---

### Post by rpmmatt on 2011-05-15
Hi guys,
I have Ubuntu 10.04 LTS installed on my Toshiba Equium Laptop. I can't adjust the brightness using the Fn key+F6/F7.

I have tried using the "sudo setpci -s 00:02.1 F4.B=xx" command in terminal to manually set brightness  but it doesn't change anything or even bring up an error.

I would like to rebind brightness up and down to a new manual shortcut like I have already done with my volume, but i have no idea what command to set to make a manual shortcut work.

Please help, not being unable to chage brightness is very frustrating.

---

### Post by rpmmatt on 2011-05-16
Bump...


Anyone?

---

### Post by quantumrex on 2011-05-25
I had some luck with this. I have the same problem with a Toshiba Satellite T135. 

bright() { sudo setpci -s 00:02.0 F4.B="$@"; }

is the line from my .bashrc file. After opening a new terminal, just type bright X, X between 0 and 100.

I mention this because mine uses 02.0, as opposed to 02.1, as yours does. I tried 02,1 with mine, and it failed, so try 02.0 with yours... I dunno if this will help, but it does work for me. 

Tested in 10.10 and 11.04.

---

