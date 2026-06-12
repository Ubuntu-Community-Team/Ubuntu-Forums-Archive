---
title: "root password"
date: 2005-11-05
forum: General Help
---

### Post by eyebrowman92 on 2005-11-05
whats the code for the terminal to change the root password. i forgot.

---

### Post by Dr. Nick on 2005-11-05
try > sudo passwd root since Ubuntu doesnt use the root account,  but instead sudo, I am not sure how this will work, I believe it works for regular user accounts though

---

### Post by trigg on 2005-11-05
[QUOTE=Dr. Nick]try  since Ubuntu doesnt use the root account,  but instead sudo, I am not sure how this will work, I believe it works for regular user accounts though[/QUOTE]


it does - and if you want to disable the root account again, type this:

```

sudo passwd -l root

```

---

### Post by eyebrowman92 on 2005-11-10
alright i got it. all i needed was the code to set the root password. thanks again.

---

### Post by alibanet on 2005-12-06
I have this problem:

After ubuntu installation I created root account as described in the forum
and I was able to log in the system as root.
Since few days (perhaps an update?) if I use the command "su root" the 
bash tell me:
"mimmo@hugo-home:/etc$ su root
Password:
su: Authentication failure
Spiacente."

*Of course I use the right root password.*

So I tryed to set a new root password:
"mimmo@hugo-home:/etc$ sudo passwd -l root
Password:
Password cambiata.
mimmo@hugo-home:/etc$ sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully"

But this don't fixed the problem and every time
I try to do "su root" the answer is:
"su: Authentication failure
Spiacente.":confused: 

Can anybody help me, please?
Tnx

---

