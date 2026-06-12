---
title: "help needed with terminal customizing"
date: 2008-10-04
forum: General Help
---

### Post by jabbawokie on 2008-10-04
hi there im kind on new to ubuntu and need some help!
does any1 know how to set a program 2 run throgh terminal but without having to go into the directory
thanks

---

### Post by kdcoetzee on 2008-10-04
Alt-F2
Or
in terminal you run the command with a "&" at the back.

If i understand you question correctly.

---

### Post by StooJ on 2008-10-04
I... I think the OP is wanting to add a programme to the PATH so that they don't have to cd to the correct directory before running the programme.

I'm not sure if this is the best way of doing it, but you could alter your .bashrc file to include something like:

```
export PATH=$PATH:*directory_where_your_programme_is*
```

.bashrc is in your home directory.

---

### Post by kdcoetzee on 2008-10-04
That usually works correctly.
if he need to specify the location of all the programs then there is something wrong. 

if it is just one program that needs the location. you can setup an alias in your .bashrc.

```
 alias program_name='/location/program_name' 
```

---

### Post by jabbawokie on 2008-10-05
cool thanks that helps alot

---

