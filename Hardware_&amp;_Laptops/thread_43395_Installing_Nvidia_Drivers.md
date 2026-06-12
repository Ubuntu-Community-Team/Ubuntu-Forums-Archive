---
title: "Installing Nvidia Drivers"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by ryanmartini on 2005-06-21
Well I am trying my best to cope with linux, but this is nuts. I am having some severe Root issues. During the instalation I noted my password, every time it asked for a password, I gave it the same password to be safe. Now when i try to install them. In the console it sais must be ran as root. 

Ok thats fine but one problem, I cant login as root because it sais incorrect password. I VERY carefully put the same password for everything. Is there a default password for root ? 

Any help is appretiated. 

 -Ryan

---

### Post by Gezzer on 2005-06-21
if using ubuntu try this

open a terminal
write
sudo passwd root

enter your password
press enter

then give a root password

after u have done that go to the login preference and tick
enable wdm root login

logout then in using
user name = root
enter root password

u should now be in root ...

if using Kubuntu the setup is the same but u will have to change the
rootlogon from false to true in
/etc/kde3/kdm/kdmrc

use a text editor to do so ...

---

### Post by ryanmartini on 2005-06-21
thank you kind sir. 

I will try this ASAP =)

But might I ask why you cant have a root username and password setup during the install ?

---

### Post by Gezzer on 2005-06-21
because ubuntu & kubuntu are setup to use sudo root

google for sudo root & please have a read u will find it most interesting 
a very safe & powerful way of using a linux system


but i too use root but only when all else fails via sudo ...

---

