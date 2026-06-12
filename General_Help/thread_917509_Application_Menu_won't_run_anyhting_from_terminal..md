---
title: "Application Menu won't run anyhting from terminal."
date: 2008-09-12
forum: General Help
---

### Post by Bobv2 on 2008-09-12
I just put Ubuntu back in and I ran into a rather... aggravating problem. Whenever I tell it to run any file, valid or not, in console, it says " there was an error creating the child process for this terminal". And quits. All my installed application rely on running through this method to gain root privileges, so I have to run everything manually. But I want to have a menu. Fixes?

---

### Post by cariboo on 2008-09-12
Every program in the menus should run as a regular user except for the some of the programs in System-->Administration if you need to run a program as root you can edit the launcher in the menu like this:

```
gksu <command>
```

You will be asked to enter your user password. 

Be warned that running programs as root can lead to security problems.

Jim

---

### Post by Bobv2 on 2008-09-12
I added that to it. It asks for the password, then nothing happens.

---

