---
title: "configuration error when running any application"
date: 2008-11-17
forum: General Help
---

### Post by evanct on 2008-11-17
Whenever i run any application i get an alert box with this:

```
An error occurred while loading or saving configuration information for [application name]. Some of your configuration settings may not work properly.
```

the output is this message, repeated several times:

```
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
```

the application always works fine, it's just that sometimes previous configuration settings will not be saved and I have to redo them.

---

### Post by cariboo on 2008-11-17
Do the  configuration files in your home directory have the correct ownership/permissions? To check go to Places-->Home Folder and press Ctrl-h this will show the hidden files and directories. THe majority of the files and directories chould be owned by the user and have a permission of 755.

Jim

---

