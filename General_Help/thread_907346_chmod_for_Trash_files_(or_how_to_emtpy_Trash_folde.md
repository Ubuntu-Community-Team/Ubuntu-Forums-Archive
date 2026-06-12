---
title: "chmod for Trash files (or how to emtpy Trash folder)"
date: 2008-09-01
forum: General Help
---

### Post by Bolda on 2008-09-01
Hi:

I'm a Linux beginner who only always tries to find what I need when I need it (in Ubuntu 8.04, Hardy Heron). I think I've encountered a problem which beats me:

I'm unable to delete some folders and files in my Trash folder since the folders' Access Files parameter is set to Access Files (as opposed to Create and Delete Files) and the files' Access parameter is set to Read-only) as opposed to Read and Write; within Properties / Permissions.

I've tried (sudo) chown, chmod and rm (~/.local/share/Trash/) without success. I haven't been able to find anything that would help, but I did find some talk on the Web about this being a known bug.

Can someone help?

Bolda

---

### Post by Irony on 2008-09-01
In terminal type;

```
gksudo nautilus
```

Then navigate to;

```
~/.local/share/Trash
```

Then delete the files and info folders in it - yes they will regenerate when you dump something else in trash. Remember to close the root nautilus program 'cos you are working as root and don't want to accidently delete something else.

---

### Post by Bolda on 2008-09-04
Hi Irony,

Thanks a lot for your help. I think that your remark about Trash contents regeneration was of most importance for me to understand what was going on.

I got rid of the files in Trash although I'm not sure exactly what finally resulted in success.

Much obliged...

Bolda

---

### Post by Jagen on 2008-10-04
Thanks as well, apparently the location of the trash folder has moved since earlier distributions.

---

### Post by groovomata on 2008-10-09
Thanks for that. I couldn't find out how to navigate to the trash using sudo nautilus.

---

### Post by elbel86 on 2008-10-17
I had some files sitting in there for months and i just couldn't find the trash folder from root nautilus.  Thanks

---

