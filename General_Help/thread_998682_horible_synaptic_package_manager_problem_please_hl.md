---
title: "horible synaptic package manager problem please hlep"
date: 2008-12-01
forum: General Help
---

### Post by zayl on 2008-12-01
I was messing around trying to install wine and now when i try to access the synaptic  package manager I get this error

'E:Type '--2008-11-30' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list, E:The list of sources could not be read.'

Does anybody know how to fix this please help I am new to ubuntu

---

### Post by jpmontalbo on 2008-12-01
Hi there. Can you run this command for me and paste the output.

```
cat /etc/apt/sources.list.d/winehq.list
```

It looks like theres a syntax error in line one of that list.

---

### Post by 3rdalbum on 2008-12-01
It looks like you've used a HOWTO for installing the latest version of WINE straight from the WINE developers. This HOWTO has used the "wget" command to add a new repository to your Apt sources, and Wget has not been able to fetch the file it needs, therefore dumping an error message into your apt sources. This error message confuses the Apt system and so it stops working temporarily.

You can fix the problem by deleting the file that the HOWTO tutorial created. You actually posted the filesystem location of it in your first post in the thread, so once you delete that and reload the package list (sudo apt-get update), you'll be fine. You can try the Wine HOWTO again at a later date.

---

### Post by zayl on 2008-12-01
3rdalbum thank you for the help, unfortunately when I go to delete the file it tells i do not have permission, how ever I am loged in as the administrator do you know what I should do?

also to jpmontalbo thank you for your help and here is the results of the command

alex@alex-desktop:~$ cat /etc/apt/sources.list.d/winehq.list
--2008-11-30 23:57:49--  [http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list](http://wine.budgetdedicated.com/apt/sources.list.d/intrepid.list)
Resolving wine.budgetdedicated.com... 81.171.111.184, 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 190 [text/plain]
Saving to: `intrepid.list.2'

     0K                                                       100% 20.9M=0s

2008-11-30 23:57:49 (20.9 MB/s) - `intrepid.list.2' saved [190/190]

---

### Post by zayl on 2008-12-01
I was able to use the rm command to remove the file, thanks for all the help!

---

