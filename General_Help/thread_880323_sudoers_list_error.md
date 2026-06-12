---
title: "sudoers list error"
date: 2008-08-04
forum: General Help
---

### Post by lil_niles on 2008-08-04
I was just trying to get rtorrent to run at startup on my little server at home when all of a sudden my admin account is no longer on the sudoers list. I just get the error stating i'm not on the sudoers list and that a report has been sent. I can then check my mail and see the report that i tried to sudo something... becuase i'm the admin.

I don't know how this happened; the last thing i'd done is added the line "rtorrent" to a file (that i just forgot the name of) that apparantly runs rtorrent as root on startup. 

I'm betting i will just have to delete my server and start over again... sometimes i hate ubuntu's lack of recovery from things like this. thanks for any help

---

### Post by mb_webguy on 2008-08-04
If you select "recovery mode" in the GRUB menu, it will boot you into a command line as root.  Then you can add your admin account back into the group.

You can add a user to a group with the command "useradd -G group-name username".

---

### Post by Oldsoldier2003 on 2008-08-04
> **lil_niles said:**
> I was just trying to get rtorrent to run at startup on my little server at home when all of a sudden my admin account is no longer on the sudoers list. I just get the error stating i'm not on the sudoers list and that a report has been sent. I can then check my mail and see the report that i tried to sudo something... becuase i'm the admin.

I don't know how this happened; the last thing i'd done is added the line "rtorrent" to a file (that i just forgot the name of) that apparantly runs rtorrent as root on startup. 

I'm betting i will just have to delete my server and start over again... sometimes i hate ubuntu's lack of recovery from things like this. thanks for any help

just reboot and select recovery mode then add your user back to the admin group.

```
usermod -aG admin <your_user_name>
```

---

