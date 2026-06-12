---
title: "Sudo(Ubuntu)"
date: 2008-07-13
forum: General Help
---

### Post by pvalley1967 on 2008-07-13
Hi all


I have HH installed and cant get sudo going

I type sudo apt-get install k3b I type the password and it says Sorry? what gives

yes I changes the root password to match the administrators password with no luck?

Paul

:(

---

### Post by drs305 on 2008-07-13
If you enter the following command do you see an entry "admin" ?
```
groups
```

Also, if you run the following command you should see "127.0.0.1 localhost" in the first line and in the second line "127.0.1.1 *computername*"  with nothing attached to the end of it ( yourcomputername is ok, yourcomputername.somethingelse probably not).
```
cat /etc/hosts
```

---

### Post by CatKiller on 2008-07-13
The password you give for sudo is your normal user password.

More information here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lisati on 2008-07-13
When you type your password at the terminal, don't worry if it doesn't show - this is a security precaution. Just use the same password as your usual logon.

---

### Post by pvalley1967 on 2008-07-13
> **CatKiller said:**
> The password you give for sudo is your normal user password.

More information here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I've tried both root and normal user

---

### Post by coffeecat on 2008-07-13
> **pvalley1967 said:**
> I type sudo apt-get install k3b I type the password and it says Sorry? what gives

I've never seen a Linux terminal apologise before. Do you mean you get the word 'sorry' as a message? Can you try 'sudo apt-get install k3b' again and copy and paste **everything** that's in the terminal into a post. It'll help everyone see exactly what's happening.

> **pvalley1967 said:**
> yes I changes the root password to match the administrators password with no luck?

How did you do that? It's important to know what you did to see what may have gone wrong.

By the way, I know this won't help with your terminal problem, but have you tried installing k3b with Synaptic? Will it accept your password?

---

### Post by pvalley1967 on 2008-07-14
as per request 


pvalley@DippieTheHippie:~$ sudo apt-get install k3b
[sudo] password for pvalley: 
Sorry, try again.
[sudo] password for pvalley: 
Sorry, try again.
[sudo] password for pvalley: 
pvalley is not in the sudoers file.  This incident will be reported.
pvalley@DippieTheHippie:~$ 

the last one I tried was my normal password the first two are using the administrator password

---

### Post by YaroMan86 on 2008-07-14
You need to make pvalley an administrator.

---

### Post by aysiu on 2008-07-14
You're not in the sudoers file, so you can't invoke *sudo*.

Try this:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by pvalley1967 on 2008-07-14
ok will try administrator first:cool:

---

### Post by mali2297 on 2008-07-14
> **coffeecat said:**
> I've never seen a Linux terminal apologise before. Do you mean you get the word 'sorry' as a message?
From the sudoers man page:
```

badpass_message Message that is displayed if a user enters an incorrect
                password.  The default is Sorry, try again. unless
                insults are enabled.

```
If your terminal never apologizes, perhaps it uses *insults* instead?

---

### Post by pvalley1967 on 2008-07-14
well I guess I am going to give up at this point and just su and or just switch fron regular user account to the administrators account thanks for all the help


Paul

---

### Post by aysiu on 2008-07-14
> **pvalley1967 said:**
> well I guess I am going to give up at this point and just su and or just switch fron regular user account to the administrators account thanks for all the help


Paul
Check out the link in post #9.

---

