---
title: "acl's question"
date: 2008-09-03
forum: General Help
---

### Post by boblemur on 2008-09-03
hey all,

im trying to let my uni server have a dedicated space on it.

```
~/shared/assignment1


```

so that people in my group for the assignment we are doing are able to access the files but others arnt.

being a student, i obviously dont have sudo (although it would be awsome)
so i cant make a unix group  for us and make that the owner of the file.

i wanted to set this up using acl's

```
setfacl -Rm user:group_member1:rwx assignment1
```

however it says "Operation not supported" because the filesystem is not mounted with the acl option.

so i cant mount..."only root can do that"

is there a way i can mount a tmpfs inside my home folder? without needing to be root?

or is there another way to do this that i have overlooked

```
chmod o+rwx 
```

IS NOT ALLOWED, its against uni policy to have read access granted to others for any assignment work

thankyou for any help in advance

---

### Post by kpatz on 2008-09-03
Do the users in your assignment group belong to a common group, that you could chgrp the directory to?

Type **id** at a shell and see what you get for groups assigned.  Maybe have the server's admin set up a group for you?

---

