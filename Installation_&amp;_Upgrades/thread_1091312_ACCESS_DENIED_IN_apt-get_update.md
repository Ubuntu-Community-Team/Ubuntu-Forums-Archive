---
title: "ACCESS DENIED IN apt-get update"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by newb_nate_08 on 2009-03-09
ok so im trying to do the cube thing and when i do apt-get update after copying deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main universe restricted multiverse into sources list, i copy apt-get update into terminal and get E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory


WTF? I'm logged into administrator user and have all access. i cant get it to work

---

### Post by karlr42 on 2009-03-09
```
**sudo** apt-get update
```
And why Dapper? Are you using Dapper or Hardy or Intrepid?

---

### Post by Neo_The_User on 2009-03-09
He's most likely using Dapper unless he's trying to downgrade :/

Usually when you have Synaptic open and a terminal open both doing repo updates, you get the /var/whatever lock error.

---

### Post by karlr42 on 2009-03-09
That's a different error "unable to gain exclusive lock- is another application using it?". Unable to get a lock because permission is denied on the file is because the invoking user is not root.
It's also quite possible the OP is following an out-of-date guide.

---

### Post by Neo_The_User on 2009-03-09
well he did say he did "apt-get update" not "sudo" so that might be the problem. Yeah it is. I just did it.

```

neo@neo-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

Put sudo before apt-get update. Like this:

```

sudo apt-get update && sudo apt-get dist-upgrade

```

---

