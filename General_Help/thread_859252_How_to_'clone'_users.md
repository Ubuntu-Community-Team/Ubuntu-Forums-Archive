---
title: "How to 'clone' users"
date: 2008-07-14
forum: General Help
---

### Post by wemersonrv on 2008-07-14
Hi, 

When I create a new user and login using his account, sudo can not run ok, because the system says that the root password is invalid!

I've like to know how to 'clone' a user, making the new user be exactly same as the original, both in permissions, credentials and personal preferences.

In time: Forgive my poor english, I'm brazilian and I don't know english very well! :oops:

Thanks

---

### Post by cmnorton on 2008-07-14
If you want accounts to have similar environments, modify /etc/skel/.bashrc and/or /etc/skel/.profile respectively.

As to cloning passwords, you'll have to cut and paste entries in /etc/shadow. Make sure you make backup copies of everything, /etc/passwd and /etc/shadow.

---

### Post by wemersonrv on 2008-07-14
> **cmnorton said:**
> If you want accounts to have similar environments, modify /etc/skel/.bashrc and/or /etc/skel/.profile respectively.

I don't unterstand, sorry! :(

> **cmnorton said:**
> As to cloning passwords, you'll have to cut and paste entries in /etc/shadow. Make sure you make backup copies of everything, /etc/passwd and /etc/shadow.

I need to create different accounts, and every account with his specific password, but with similar environments and privileges.

Every account that i've created, has his password; but only the default user runs sudo ok. The other users, when runs sudo and type the password, does not works...

---

### Post by koenn on 2008-07-14
> **wemersonrv said:**
> I don't unterstand, sorry! :(



I need to create different accounts, and every account with his specific password, but with similar environments and privileges.

Every account that i've created, has his password; but only the default user runs sudo ok. The other users, when runs sudo and type the password, does not works...

only users that are in the admin group have sudo rights. 
So you should add those users to that group.

This is NOT a good idea. Each of these users will have unlimited power over the system. Are you sure that's what you want ?

---

### Post by cmnorton on 2008-07-14
> **wemersonrv said:**
> I don't unterstand, sorry! :(



I need to create different accounts, and every account with his specific password, but with similar environments and privileges.

Every account that i've created, has his password; but only the default user runs sudo ok. The other users, when runs sudo and type the password, does not works...

Before I answer, I agree with [koenn]("http://ubuntuforums.org/member.php?u=192752")'s post, I want to concur that you do not want everyone to have admin rights. Something can and will go wrong.

On most but not all Linux systems, passwords are no longer stored in /etc/passwd. They are stored in /etc/shadow encrypted.

If you have user fred, and you create user ethyl and you want user ethyl to have user fred's password,, you would have to substitute fred's password (second field after fred:) into ethyl's password field.

I often will exchange /etc/shadow on a new system for a known /etc/shadow on a system I am building to save retyping passwords, but there is more work than that to clone a system, including getting all the user's and group's ids correct. 

Editing /etc/shadow is at your own risk, is fast, and also dangerous.

---

### Post by wemersonrv on 2008-07-14
cmnorton,

Each user will have his password, I will not change that.

What I need is that all users have the same characteristics (environment, permissions, etc.) of the main user, not the root...

I have a couple of VMware Virtual Machines running in user hormonal, when i run the virtual machines in the users hormonal2 or hormonal3, the disc and the other resources of the VM does not have permissions to be runned with this users. I need to make this users to have full access to my Virtual Machines.

---

### Post by koenn on 2008-07-14
> **wemersonrv said:**
> 
What I need is that all users have the same characteristics (environment, permissions, etc.) of the main user, not the root...

I have a couple of VMware Virtual Machines running in user hormonal, when i run the virtual machines in the users hormonal2 or hormonal3, the disc and the other resources of the VM does not have permissions to be runned with this users. I need to make this users to have full access to my Virtual Machines.

if a user can do sudo on an ubuntu system, he ***is*** root, unless you do extensive tweaking of the sudoers file

if you user needs access to VM guests, you do that by setting the required permissions on the vm files. 
if a user needs access to the resources of a vm guest, you do that by setting the required permissions in the OS of the virtual machine. 

plainly allowing everybody to do sudo is probably the worst possible solution.

---

