---
title: "how to add a lampp (Apache etc)"
date: 2012-07-25
forum: Hardware
---

### Post by dilbert_one on 2012-07-25
hi just installed lubuntu 

all runs great - now i want to install & configure an apache or lamp
how to proceed!`?

love to hear from you

---

### Post by Cheesemill on 2012-07-25
Just do:
```
sudo apt-get install lamp-server^
```

This will install Apache, MySQL and PHP and set them up for you.

---

### Post by dilbert_one on 2012-07-25
hello and good day dear Cheesmill 

many thanks !

> **Cheesemill said:**
> Just do:
```
sudo apt-get install lamp-server^
```This will install Apache, MySQL and PHP and set them up for you.

great - i will try out this command. 

btw. i come from the opensuse-world - and there i usually get access to the super-user-mode in the terminal by typing the command [B]su 


Well if i do so in lubuntu: 


[/B]i get back the comment: 

password:  - and if i type my password  - well those one that i use for accessing
the system - well if i do so, i get back the comment


su: error with the Authentification (i translated the german phrase into english)

well - what should i do here-  what can i do now!?

sure thing - this is a new thread.Perhaps i should open a new thread with this..
issue. 

love to hear from you 

greetings 
dilbert

---

### Post by Cheesemill on 2012-07-25
The root account is disabled by default in a Ubuntu installation, you can gain temporary access to a root shell by using:
```
sudo -i
```
or by prefixing each command with 'sudo'. For more information:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

