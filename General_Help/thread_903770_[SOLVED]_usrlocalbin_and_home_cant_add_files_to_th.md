---
title: "[SOLVED] usr/local/bin and /home cant add files to them"
date: 2008-08-28
forum: General Help
---

### Post by wolfhunter2142 on 2008-08-28
I am the only user and it says that the permissions are denied. and ideas on what to do. I am new to ubuntu

---

### Post by drs305 on 2008-08-28
> **wolfhunter2142 said:**
> I am the only user and it says that the permissions are denied. and ideas on what to do. I am new to ubuntu

The only places a normal user can normally perform file operations is in his/her home directory - that would be /home/*yourusername* (which is often abbreviated to **~/** )

To perform file operations anywhere else requires you to use administrator privileges - even though you are the only user.

You do this by preceeding the command with "sudo" for terminal operations or "gksudo" for gui-apps or terminal commands which will open a gui app.

So to open nautilus:
```
gksudo nautilus
```

To copy a file to /usr/local/bin:
```
sudo cp filename /usr/local/bin
```

Note: When you type a command with "sudo", you will be asked to enter your password. As you type you will not see any entry. Hit enter once you have typed the password and it will continue.

Here area couple of good guides to help understand permissions:
[FilePermissions]("https://help.ubuntu.com/community/FilePermissions")
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

