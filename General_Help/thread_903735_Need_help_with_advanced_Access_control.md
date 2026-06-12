---
title: "Need help with advanced Access control"
date: 2008-08-28
forum: General Help
---

### Post by descentspb on 2008-08-28
I have a samba share, on which everyone connects as guest.

I need this share to behave the following way:
everyone can upload (create) and rename files. But noone can delete anything.

Is there a way I can do that with Linux?

---

### Post by amitkher on 2008-08-28
acl, selinux etc can give you a much fine-grained control but you will have to look at a complicated tutorial to do that. The following can be done easily, your /tmp folder already behaves in a fashion similar to your requirements.

Suppose the directory is /home/descentspb/share. Just do
```

chmod 1777 /home/descentspb/share

```

Now if user1 creates a file, only user1 will be able to remove it. All users can create their own files.

I understand that this is not exactly your requirement. You don't even want the creator to be able to remove a file.

EDIT: note that the owner of /home/descentspb/share can delete all files in it. If you don't want this, make root its owner.
```

sudo chown root /home/descentspb/share
sudo chmod 1777 /home/descentspb/share

```

---

