---
title: "Can't Access Root"
date: 2008-07-29
forum: General Help
---

### Post by Killtodie on 2008-07-29
Im trying to forcefully mount a bad HD and it says only root can do it, so I use "su root" and it asks for password, I use the correct password and it says authentication failed....

---

### Post by gjoellee on 2008-07-29
try use ```
su -
``` instead. Also if you haven't set the root password you should go to System->Administration->Users and Groups, and click on root, then click unlock and click on root again, click on preferences and then set password by hand and to the su - command...

---

### Post by coffeecat on 2008-07-29
You can't use su (or su -) in Ubuntu. Use sudo. See:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

... for a full explanation.

---

### Post by Killtodie on 2008-07-29
so how do I get root access so I can run ```
mount -t ntfs-3g /dev/sdb2/media/disk -o force
```

---

### Post by coffeecat on 2008-07-29
> **Killtodie said:**
> so how do I get root access so I can run ```
mount -t ntfs-3g /dev/sdb2/media/disk -o force
```

```
sudo mount -t ntfs-3g /dev/sdb2/media/disk -o force
```

But **please** read that link. You'll get nowhere in Ubuntu if you don't.

---

### Post by LaRoza on 2008-07-29
See this thread: [http://ubuntuforums.org/showthread.php?t=870137](http://ubuntuforums.org/showthread.php?t=870137)

---

### Post by jnw222 on 2008-07-29
sudo [command without these brackets]
is the same thing as  logging into root (or su)

---

### Post by jimv on 2008-07-29
> **coffeecat said:**
> You can't use su (or su -) in Ubuntu. Use sudo. See:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

... for a full explanation.

su works fine in Ubuntu.  Just not for root, because root has no password.

---

### Post by coffeecat on 2008-07-30
> **jimv said:**
> su works fine in Ubuntu.  Just not for root, because root has no password.

I'm aware of that. Check the thread title - my comment was in the context of accessing root privileges. You cannot su (or su -) to **root** in a default installation of Ubuntu. I posted the  RootSudo link, trying to point the OP to the Ubuntu way because the previous poster had described how to give the root account a usable password. It is a matter of debate whether this is a good idea, of course.

**Edit**: actually, root does have a password, but it's a random one allocated at installation. Try 'su' without a username in a default install. You get prompted for a password because the system is looking for the root password it knows about but no one in the known Universe does. That's why you get an incorrect password (or whatever) message whatever you put in, unless you do what gjoellee suggested first.

By the way - I'm not trying to nitpick here. Were you? :p :wink: Just trying to clarify things for the OP.

---

