---
title: "Enviroment paths?"
date: 2008-07-23
forum: General Help
---

### Post by mech7 on 2008-07-23
How can i set enviroment pahts... for exmaple i have php and mysql.. and i want the available everywhere in CLI not just from the direct file...

In windows i can change the enviroment paths... but how does it work in debian :confused:

---

### Post by phidia on 2008-07-23
See this [guide]("http://www.slackbook.org/html/shell-bash.html").
The general command follows this form: > export PATH=$PATH:/some/new/directory


---

### Post by mech7 on 2008-07-26
ah it works... but only for the script.. when i open the shell again its gone :(

---

### Post by ghostdog74 on 2008-07-26
you should change it in your profile.

---

### Post by mech7 on 2008-07-27
I found it... in ubuntu its called bahsrc... in the page i found on internet the name was little different :D

---

### Post by dexter.deepak on 2008-07-27
you cam either add it in the .bashrc or on the .profile file.

the only advantage that you get if you edit the .profile file, is that you can use that environment variable on ssh/remote logins too !!

---

### Post by mech7 on 2008-07-27
> **dexter.deepak said:**
> you cam either add it in the .bashrc or on the .profile file.

the only advantage that you get if you edit the .profile file, is that you can use that environment variable on ssh/remote logins too !!

Ah thx that is good to know... does root has this file too? As i need to change something on debian server too... also how about more then one path can i jut put them all under each other?

---

### Post by dexter.deepak on 2008-07-27
yes, the root has it ..
what do you mean by setting multiple paths ?
you can simply put as many values for a single PATH variable like this:
PATH=path_A:path_B:.
and so on.

---

### Post by mech7 on 2008-07-27
> **dexter.deepak said:**
> yes, the root has it ..
what do you mean by setting multiple paths ?
you can simply put as many values for a single PATH variable like this:
PATH=path_A:path_B:.
and so on.

Ah ok yes that is what i meant.. i was not sure if i needed to set PATH= Again so the : is the seperator :)

---

