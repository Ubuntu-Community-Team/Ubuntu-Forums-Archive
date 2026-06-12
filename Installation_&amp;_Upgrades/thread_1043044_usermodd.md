---
title: "usermodd"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by aazmath on 2009-01-18
Hello;)

I have on my machine 8.10 ibex.  

Can somebody tell me how to change user name?

now looks like that:   leszczyk@leszczyk

i want to looks like that   lechu@home  

I tried to usermod -I lechu and dont work.

Help...:(

THX

---

### Post by ibutho on 2009-01-18
To change the username, you would do
```
sudo usermod -l newlogin oldlogin
```
You may have to rename your old home directory so that it matches your new user name. Another option would be to create a new account and then copy your files from the old account to the new account. For the other part, you have to change your hostname using the network-settings tool.

---

### Post by aazmath on 2009-01-18
okk now i got :


Dont have name@leszyk-&!

---

