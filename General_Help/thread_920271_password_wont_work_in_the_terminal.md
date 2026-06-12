---
title: "password wont work in the terminal"
date: 2008-09-15
forum: General Help
---

### Post by jammin2222 on 2008-09-15
I have just installed ubuntu 8.04 on my old laptop and the password i use to log in dosent work when i use the "su" command in the terminal. it says Authentication failure.
I can use the password to make changes to my system using the gui but not in the terminal.
 Whats going on?

Many thanks 

Ben

---

### Post by forger on 2008-09-15
Use: ```
sudo command
```
For example:
```
sudo echo "Hello!"
```

If you want to log in as root, use
```
sudo -s
```
or ```
sudo -i
```

---

### Post by iaculallad on 2008-09-15
> **jammin2222 said:**
> I have just installed ubuntu 8.04 on my old laptop and the password i use to log in dosent work when i use the "su" command in the terminal. it says Authentication failure.
I can use the password to make changes to my system using the gui but not in the terminal.
 Whats going on?

Many thanks 

Ben

By default, the su does not work because Root account is disabled. Alternate way of accessing su is to use:

```
sudo su
```

or

```
sudo -i
```

and input your own password.

---

### Post by jammin2222 on 2008-09-15
Thanks ill try that, i was following a video tutorial and it said i had to type su then my password, it worked on the video lol

Much thankings 


Ben

---

### Post by iaculallad on 2008-09-15
> **jammin2222 said:**
> Thanks ill try that, i was following a video tutorial and it said i had to type su then my password, it worked on the video lol

Much thankings 


Ben

For sure they enabled the ROOT account on the video you watched, thus, it worked on their terminal.

---

### Post by jammin2222 on 2008-09-15
thanks for the info, my brain cant take much more of ubuntu i fear. there is too much programming knowledge needed to do the simplest of things for it to become popular IMHO

All im trying to do is install ndiswrapper so i can use my wireless card to connect to the internet, but i have to type so much ******** into the terminal to get it to install and something always goes wrong. WAAAAAAAaaaaaa :confused:

---

### Post by northern lights on 2008-09-15
> **forger said:**
> If you want to log in as root, use
```
sudo -s
```

'sudo -s' enters a root shell with the current shell's environment. This is essentially comparative to running graphical applications with 'sudo'. Unless you're a developer and need to do this to accomplish an otherwise impossible task, you should refrain from either.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

