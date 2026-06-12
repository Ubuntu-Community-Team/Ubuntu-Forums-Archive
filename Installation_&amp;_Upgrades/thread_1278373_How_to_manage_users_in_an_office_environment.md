---
title: "How to manage users in an office environment"
date: 2009-09-29
forum: Installation &amp; Upgrades
---

### Post by majdi on 2009-09-29
Hi,

Coming for a Fedora background, user management seemed easier to setup for an office environment.

Because Fedora has root and normal user for each Desktop, it makes it easier to control what the user has access to on his Desktop. Ubuntu, has made this more complicated and it seems for security reasons as I have read.

Has anyone setup such an environment where all Desktops are running Ubuntu with an Ubuntu server running as a file and print server. We have a few Windows XP and Vista Desktops that will also need to use the Ubuntu server as a file and print server.

Can anyone help with feedback on this type of setup?

---

### Post by Lars Noodén on 2009-10-01
Can you say more specifically what you miss from Fedora?

If you are looking for a way to prevent users from adding or removing programs or configurations, then one way is to add their user account after the installation is done.  The account added during installation ends up with administrative privileges. 

If there are some activities that the users need root access for, then specific functions can be added to /etc/sudoers on a case by case basis.  Configuration files like /etc/sudoers are nice to manage centrally using SVN, BZR or CVS. 

Radmind might be worth looking into, as well.

---

### Post by majdi on 2009-11-07
Fedora dose this for you during installation.

In your opinion, what would be the best way to manage users in a mixed windows/ubuntu office environment?

---

### Post by majdi on 2009-11-08
So, I don't want the user created by the ubuntu install to be able to change settings on the system. How can I do this? Can I change that user's setting or do I have to create a new user?

---

### Post by Lars Noodén on 2009-11-09
> **majdi said:**
> So, I don't want the user created by the ubuntu install to be able to change settings on the system. How can I do this? Can I change that user's setting or do I have to create a new user?

Do you mean administrative settings or mean have the system locked down as a kiosk.  If the former, take that user out of the groups **admin** and **adm**.  Look at the file /etc/sudoers to see about that.  

However, before you do that, make sure you have another user that is a member of those groups or else you are locked out.

---

### Post by majdi on 2009-11-09
In System>Administrator>Users and Groups

For the user created at the ubuntu install I removed (Administer the system) in User Privileges. 

Now I cant do much with the system. How do I bring back this option for that user?

---

### Post by Lars Noodén on 2009-11-10
> **Lars Noodén said:**
> However, **before you do that, make sure you have another user that is a member of those groups or else you are locked out**.

> **majdi said:**
> 
For the user created at the ubuntu install I removed (Administer the system) in User Privileges. 

Now I cant do much with the system. How do I bring back this option for that user?

Remember, **before** you take away that user's privileges, make sure you have another user that is a member of those groups or else you are **locked out**.

---

### Post by Devi1903 on 2009-11-10
In Karmic you can just set the password for root and then remove the current user from the groups as mentioned before. Then you have root (whose login is now enabled by default) who has administrative privileges and the user without.

If you have already locked yourself out of the system by not taking following the instructions to make sure a user was still in the group, then you can boot from a live cd and edit the file mentioned before adding the user back with administrative privileges.

If you are looking for a central solution for administrating users, then i would recommend adding ldap & samba to your server to do this. However this is a complex installation.

---

### Post by whoop on 2009-11-10
What ubuntu really misses in the office is roaming profile technology. This works in windows and is quite user friendly.
In ubuntu it's technically possible (although I don't think we can cache, aka log in when the server is down), but it is difficult to setup and there is no up-to-date documentation for this.
So, please **vote**:[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

### Post by Devi1903 on 2009-11-10
I use nfs to mount home directories. You are right it does not seem possible to cache so the server goes down and the clients cannot work eather. However i do think that it is a lot faster due to the fact that it does not cache.

This is a bit of a pain to set up. I have done it and it is working like a dream now, but it was a lot of work and the documentation is all very old. Maybe i should put up a new howto?

---

### Post by whoop on 2009-11-10
> **Devi1903 said:**
> I use nfs to mount home directories. You are right it does not seem possible to cache so the server goes down and the clients cannot work eather. However i do think that it is a lot faster due to the fact that it does not cache.

This is a bit of a pain to set up. I have done it and it is working like a dream now, but it was a lot of work and the documentation is all very old. Maybe i should put up a new howto?

Yes, especially if it works for lucid, as this will be the next LTS!!!

---

### Post by lykwydchykyn on 2009-11-10
> **whoop said:**
> Yes, especially if it works for lucid, as this will be the next LTS!!!

Let's be realistic; we're talking about a front-end that doesn't currently exist.  The chances it will be written, tested, and added into Ubuntu within a six-month release cycle is slim to none.

---

