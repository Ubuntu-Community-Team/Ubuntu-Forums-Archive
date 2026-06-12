---
title: "Sharing files over network"
date: 2008-08-09
forum: General Help
---

### Post by ubockto on 2008-08-09
with windows vista x64, how to do it, please

---

### Post by iaculallad on 2008-08-09
> **ubockto said:**
> with windows vista x64, how to do it, please

Try to read this previous [thread]("http://ubuntuforums.org/showthread.php?t=847837&highlight=smbfs") on how to share between windows and Ubuntu.

Be sure to install smbfs:

```
sudo apt-get install smbfs
```

---

### Post by ubockto on 2008-08-09
i have already installed that, its asking for my username and password, but it wont allow access, i have used nautilus to get the shared partition to be recognised, but it wont still allow access

---

### Post by iaculallad on 2008-08-09
> **ubockto said:**
> i have already installed that, its asking for my username and password, but it wont allow access, i have used nautilus to get the shared partition to be recognised, but it wont still allow access

Username and Password must be equivalent to your credentials in vista.

---

### Post by ubockto on 2008-08-09
i dont have a password for my vista installation, never needed it

---

### Post by iaculallad on 2008-08-09
> **ubockto said:**
> i dont have a password for my vista installation, never needed it

Try leaving the password field as blank:
```

sudo mount -t smbfs //192.168.1.100/share_folder_name /home/myshared -o username=your_windows_username,password="",uid=Your_Ubuntu_UserID,gid=Your_Ubuntu_GroupID
```

Note: I just don't know if vista allows its users to have blank password. I don't have a hands on experience on that OS version anyway.

---

### Post by ubockto on 2008-08-09
it doesnt ask me for a password, but only when i try to access ubuntu over the network, though i do have one for the ubuntu installation

---

