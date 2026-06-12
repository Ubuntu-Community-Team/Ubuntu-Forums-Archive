---
title: "change sudo pass to root pass"
date: 2008-08-01
forum: General Help
---

### Post by hoo2 on 2008-08-01
Hello all, I'm new with linux and kubuntu and i try to set up my desktop PC. I have this problem:

I need to change the sudo password to root password, so for sudo i'll have to type the root password and not the user's password. I have already enabled the root account. 
Does anybody know how to disable the user password from the sudoers and enable only the root for that?


Sorry for my English (or something like English)

---

### Post by y-lee on 2008-08-01
> **hoo2 said:**
> I need to change the sudo password to root password, so for sudo i'll have to type the root password and not the user's password. I have already enabled the root account. 
Does anybody know how to disable the user password from the sudoers and enable only the root for that?

Enabling the root account is considered a bad idea in this community. There are plenty of post explaining why so precede with caution if you take that route. Disabling a user password from sudo is easy tho. Take a look at [RootSudo]("https://help.ubuntu.com/community/RootSudo").

Be warned

> If you disable the sudo password for your account, you will seriously compromise the security of your computer. Anyone sitting at your unattended, logged in account will have complete root access, and remote exploits become much easier for malicious crackers.

I am sorry but I can't tell you more for I feel it is against forum policy here and they give infractions and ban people for things like that. So it is unlikely anybody is going to help you any further in this issue. May I ask you why you wish to do this? :confused:


> Sorry for my English (or something like English)

No problem on your english it is not really bad anyway and besides we are used to that.Peace and good luck. :)

---

### Post by Boobek on 2008-08-01
I don't know what are you want,
but if you want to disable 'sudo', you can remove your account from the "admin" group (System-> Administration-> Users and groups click on your account and go to the "options", on the second tab you remove the pipe from left of the "system administration" and click 'ok')
And after: you cant get root access with sudo! you must login as root (for example: "su" or "login root") to gain root access.
ps: sorry for my english..;)

---

### Post by hoo2 on 2008-08-01
> **y-lee said:**
> 

I am sorry but I can't tell you more for I feel it is against forum policy here and they give infractions and ban people for things like that. So it is unlikely anybody is going to help you any further in this issue. May I ask you why you wish to do this? :confused:



The reason is that i don't want the first user to have admin privileges.

I also can not understand how a remote user with root password "abc" can effect my desktop with root password "***"???

If the first user has root powers why do we need the root account????

---

### Post by sonicb00m on 2008-08-01
Just remove the users you dont want from sudo

 nano /etc/sudoers

---

### Post by jocko on 2008-08-02
So you have enabled the root password and want to remove admin rights from the first user? Why would you need to have sudo ask you for root password then?

As the user won't have admin rigths, it will not be able to not use sudo, and as root always have full rights, there is no point to use sudo with the root account.
And you'll break all starters for programs that use sudo or gksudo (synaptic and most other system utilities...). You would have to run all such programs from a root terminal...> **hoo2 said:**
> I also can not understand how a remote user with root password "abc" can effect my desktop with root password "***"???
A hacker that tries to get in to your system will most likely try to log in as root, and will "only" have to crack your root password.
If the root account is not enabled, any attemt to login as root will fail, no matter how many passwords are tried, and the hacker will not be told that the reason it fails is because the root password is disabled, so he will continue trying and failing.
If the hacker knows or guesses you don't have an active root account, he will have to find out *both* your username and password, which is usually harder than just finding out the password.
> **hoo2 said:**
> If the first user has root powers why do we need the root account???? The first user have the right to *temporarily* grant himself root power (using sudo). Any programs that are run with sudo will be run with root privileges, so even if you have sudo, you need to have a root account. You just don't need to have a root password and possibility for an exclusive root login.
But still, using sudo and your normal user password, you can log in as root in a terminal using any of these commands:
```
sudo su
sudo bash
sudo -i
```

---

