---
title: "Brand new to linux/ubuntu"
date: 2008-11-29
forum: General Help
---

### Post by rob40001 on 2008-11-29
I have decided to ditch Microsoft for an operating system however I am new to everything regarding ubuntu and only used to the way windows does things.
My question is I am trying to install azureus but I am having difficulty it needs java to run so downloaded jre6u10linux-x64bin to desktop but cant get that to run at all. Just get error message when i double click saying 'could not open'

Sorry for my basic questions can anyone help.

Thank you

---

### Post by taurus on 2008-11-29
An easier way to install java is either with add/remove, synaptic, or from a terminal.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```
When you get to the java licensing screen, press Tab to highlight the <OK> and press Enter to except it.

---

### Post by rob40001 on 2008-11-29
Hi thanks tried the code you suggested but got the message

Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by taurus on 2008-11-29
Sounds like you don't have enough repos enable in /etc/apt/sources.list.  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by rob40001 on 2008-11-29
Thanks for your help seem to have sorted it out using synaptic package manager :)

---

### Post by ugm6hr on 2008-11-29
> **rob40001 said:**
> Thanks for your help seem to have sorted it out using synaptic package manager :)

I assume you have installed Azureus through Synaptic too.

If not - I would recommend it.

---

