---
title: "Samba in 8.10"
date: 2008-11-20
forum: General Help
---

### Post by ToadofSteel on 2008-11-20
Okay so I installed 8.10 on one of my machines (did a clean install over a previous 8.04). In the 8.04 machine, I had a bunch of Samba shares set up. Anyway, in the Samba package I used, the Samba Daemons could be started with /etc/init.d/samba start, but the command isn't there in 8.10 (which had samba packaged with the OS from what I can tell) I need to know where the command is located now...

---

### Post by pennacook on 2008-11-20
does dpkg show that samba is installed?
```
dpkg --list samba
```

---

### Post by ToadofSteel on 2008-11-20
> **pennacook said:**
> does dpkg show that samba is installed?
```
dpkg --list samba
```

Yes it does, although it doesnt list a version number or a description...

---

### Post by pennacook on 2008-11-20
Strange. Does  ```
dpkg -s samba 
``` show 
```
Status: install ok installed
```

---

### Post by ToadofSteel on 2008-11-20
ok yeah it says that its not installed, even though there are config files and what not listed. Oddly enough though, running apt-get install samba didnt work last time, but it works now...

---

