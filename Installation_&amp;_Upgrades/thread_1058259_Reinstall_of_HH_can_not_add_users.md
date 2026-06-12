---
title: "Reinstall of HH can not add users"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by Tom Atkins on 2009-02-02
I reinstalled HH and did not format the seperate home directory. Now I can't add the other users I get an error message that the home directory already exists. What is the work around

---

### Post by lykwydchykyn on 2009-02-02
Typically that error is just a warning, and it creates the users just fine.  Are the users not being created?

What tool are you using to create users?

---

### Post by Tom Atkins on 2009-02-02
The users are not being created. I am using the users and groups app under the system administration in ubuntu

---

### Post by lykwydchykyn on 2009-02-02
Sorry, I'm not familiar with that tool, maybe someone else knows if there's a setting to use an existing home dir.

Otherwise, you can use the "adduser" command at the CLI and it should ignore the existance of the home directory.
```

sudo adduser someusername

```

The thing to remember is that file permissions are stored using the UID (user id number), not the actual user name.  So if you create users in a different order, you'll need to reset the permissions on their folder, like so:

```

sudo chown -R someusername:users /home/someusername

```

---

