---
title: "Can not add/remove"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by andrewrw66 on 2009-07-01
I am trying to remove some applications and make room, when doing so, i get this error:

"This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

Any assistance would be great. I dont want to re install as i am new to the Linux world

---

### Post by tvtech on 2009-07-01
silly question have you opened a terminal and done the following? 

```
username@localhost:~$sudo apt-get update
```
```
username@localhost:~$sudo apt-get install -f
```


also do the following while in a terminal

```
username@localhost:~$gedit /etc/apt/sources.list
```

look through the file and make sure nothing looks glaringly wrong.  like random strings of text or incomplete urls
If they are wrong.... you may have to search how to fix them.

you can edit the file by entering the following in a terminal
```
username@localhost:~$sudo gedit /etc/apt/sources.list
```

---

### Post by Geoff918 on 2009-07-01
The above poster sounds correct. What it looks like happened is that updates failed to install fully / properly before. So you would need to go to a terminal window (Applications -> Accessories -> Terminal) in GNOME (if running Ubuntu you have GNOME). The issue those two commands he gave you, after the first sudo...command it will prompt you for your password. That first command will update the software database on your local system. The second command will fix anything that didn't install nicely.

---

### Post by andrewrw66 on 2009-07-01
Geoff after seeing the GET9, i see the following: 0% [Waiting for headers] [Waiting for headers]

---

### Post by Sef on 2009-07-02
Easy way to fix broken packages:

System > Administration > Synaptic Package Manager > Edit > Fix Broken Packages

---

