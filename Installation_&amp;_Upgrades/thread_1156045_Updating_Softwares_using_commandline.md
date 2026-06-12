---
title: "Updating Softwares using commandline"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by sajithkozhikode on 2009-05-11
Hai...

I wish to ask the following question:

[B][COLOR=Blue]Can anyone tell me the command line for updating a software (Eg. Firefox) using apt-get (command line method from Terminal)
[/COLOR][/B]
I have given like this:

**[COLOR=Red]sudo apt-get update firefox[/COLOR]**

But it returns an error.

[COLOR=SeaGreen]So, please help me...[/COLOR]

---

### Post by Peter09 on 2009-05-11
its

```
sudo apt-get install firefox
```

---

### Post by sajithkozhikode on 2009-05-11
[SIZE=4][COLOR=Red][B]Thank you for information...
[/B][/COLOR][/SIZE]
In Fedora, we can use the command:

**[COLOR=Blue]yum update <package name>[/COLOR]**

So, I thought, there will be similar command in Ubuntu...

:):P:o

---

### Post by oldos2er on 2009-05-11
You would run
```
sudo apt-get update && sudo apt-get upgrade firefox
```
 which should do what you want. If you want to upgrade all packages, leave off "firefox".

---

