---
title: "ubuntu 9.4"
date: 2009-04-18
forum: Hardware
---

### Post by penn2014 on 2009-04-18
how to i become a user on ubuntu 9.4

or how do i log onto a ubuntu acount if i have not yet created one

---

### Post by Carl Hamlin on 2009-04-18
> **penn2014 said:**
> how to i become a user on ubuntu 9.4

or how do i log onto a ubuntu acount if i have not yet created one

Hiya, penn2014. I'm not quite sure what you're asking. Can you clarify a little, please? What are you trying to do, specifically?

---

### Post by penn2014 on 2009-04-18
i recently installed ubuntu 8.10 but it was recently updated to 9.4 and i never set up an account how do i set one up so that i can log in

thanks alot

---

### Post by riza hylviu on 2009-04-18
you don't need to set an account to switch/upgrade to ubuntu 9.04
here is described how to upgrade from ubuntu 8.10 or older
[http://www.zepy.net/archives/ubuntu-904-jaunty-jackalope-alpha.html](http://www.zepy.net/archives/ubuntu-904-jaunty-jackalope-alpha.html)
but is better to make a clean install, you can download the iso from the ubuntu website

---

### Post by penn2014 on 2009-04-18
i was recently using the ubuntu 8.10... when i turned on ubuntu today it automatically upgraded to 9.4... once ubuntu loaded completly it asked for me to enter a user name and password... but i did not set up one yet... need advise... can anyone help me?

---

### Post by riza hylviu on 2009-04-18
i think the old one will work

---

### Post by riza hylviu on 2009-04-18
When you first install ubuntu it will ask you a user name and a password, you mean that you didnt enter one?

---

### Post by penn2014 on 2009-04-18
1

---

### Post by penn2014 on 2009-04-18
no it did not ask me to enter a user name

---

### Post by Chemical Imbalance on 2009-04-18
When you install Ubuntu, you usually enter a login name and password to use.  This should still work when you update to Jaunty.  Once you update to Jaunty you cannot roll back the updates to get an Intrepid install again.  If you don't want Jaunty anymore, you will have to backup and reinstall Intrepid.

---

### Post by riza hylviu on 2009-04-18
i found this tutorial about downgrading but it is not safe enough and complicated to me....[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)
it will be better if you reinstall ubuntu 8.10.
Is something not working in ubuntu 9.04?

---

### Post by Carl Hamlin on 2009-04-18
> **penn2014 said:**
> i was recently using the ubuntu 8.10... when i turned on ubuntu today it automatically upgraded to 9.4... once ubuntu loaded completly it asked for me to enter a user name and password... but i did not set up one yet... need advise... can anyone help me?

Have you tried the same username/password combination that you were using in 8.10?

---

### Post by tirage on 2009-04-28
PROBABLY YOU WOULD ENTER A WRONG **username** (as I did it myself) ...! However you can check it easily to see whether it was wrong or not!!!
 
Start your computer and from the boot menu, select ***recovery mode***, which is usually the second boot option. 
 
After you select ***recovery mode*** and wait for all the boot-up processes to finish, you'll be presented with a few options. In this case, you want the ***Drop to root shell prompt*** option so press the down arrow to get to that option, and then press **Enter **to select it. (*The root account is the ultimate administrator and can do anything to the Ubuntu installation (including erase it), so please be careful with what commands you enter in the root terminal.)*
 
Once you're at the root shell prompt, if you have forgotten your username as well, type 
ls /home (**ls** = LS in small capitals) 
 
Hit Enter
 
After that you should see at least a username or a list of the usernames. 
 
* _ * _ * _ * _ * _ * _ * _ *
 
If you do not remember your password, perhaps it would be best to reset your password while you are there...
 
To reset the passwords of a username, type 
 
passwd ***username **(for instance "passwd john")*
You'll then be prompted for a new password. When you type the password you will get **no visual response acknowledging your typing**. Your password is still being accepted. Just type the password and hit *Enter* when you're done. You'll be prompted to retype the password. Do so and hit *Enter* again. 
 
Now the password should be reset, type: 
EXIT
 
AFTER THAT YOU WOULD GET RETURNED TO THE **recovery menu**. 
 
Select ***resume normal boot***, and use Ubuntu as you normally would .... only this time you actually know the correct username and password
.....
 
:popcorn:
 
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

