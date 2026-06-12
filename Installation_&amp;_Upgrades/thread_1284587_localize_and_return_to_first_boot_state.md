---
title: "localize and return to first boot state"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by mutrox on 2009-10-06
Hi all, after searching in documentation, google, and forum I don't find any clear reference on how to return to at first boot state of an oem instalation. let me explain.
I want to install some packages and tweak some configurations (basically localize in local language) an equipment with ubuntu jaunty pre-installed and then deliver to the costumer but I don't want to deliver an equipment with a pre-created user/pass so I the last step of this process has to be to erase the user I created and let the costumer set his own user/password on his "first" boot, as I have done.
OEM solution does't fit because I want to use the already installed ubuntu on the device not make a full install again.
There is some one to can point me in the right direction (links, config files implied in the first boot detection... whatever 
even if you consider there is a more accurate place to do this question 
Any hint will be appreciated

---

### Post by rreese6 on 2009-10-07
I have done this many times.
I call the customer and ask them for a user name.
then I make a strong password for them.
I deliver the computer, give then a paper with there username and password.
if you already have a user and password, create the new user and password (with new home directory) then remove your old user and the home directory.

---

### Post by mutrox on 2009-10-07
Yes this is one solution, but I'm searching for a more industrialized/scriptable proccess
But thanks anyway :)

---

