---
title: "Unable to add existing Users after upgrade"
date: 2008-11-22
forum: General Help
---

### Post by ali_bongos_dad on 2008-11-22
In the past when I've upgraded to the latest edition of Ubuntu I've added any existing users by entering the user name, real name, password etc. into the Users and Groups dialogue boxes and all worked fine.

However with upgrading to Hardy when I do the same an error flags up saying "Home Directory Already Exists - Please enter a different home directory path" and I've been unable to re-instate the users.

Can anyone tell me how to add these users?

---

### Post by geirha on 2008-11-22
Use adduser in a terminal. It should reuse the homedir if it exists.
```
sudo adduser *username*
```

Don't know whether it's a new feature or a bug in the users-admin gui. In my opinion it should allow you to create users with existing homedirs.

EDIT: Not seeing any bug reports on it at launchpad: [https://bugs.launchpad.net/gst/+bugs?field.tag=users-admin](https://bugs.launchpad.net/gst/+bugs?field.tag=users-admin)
Feel free to make a bug report.

---

### Post by ali_bongos_dad on 2008-11-22
> **geirha said:**
> Use adduser in a terminal. It should reuse the homedir if it exists.
```
sudo adduser *username*
```

Don't know whether it's a new feature or a bug in the users-admin gui. In my opinion it should allow you to create users with existing homedirs.

EDIT: Not seeing any bug reports on it at launchpad: [https://bugs.launchpad.net/gst/+bugs?field.tag=users-admin](https://bugs.launchpad.net/gst/+bugs?field.tag=users-admin)
Feel free to make a bug report.

That worked!

Thank you very much, my Wife and daughters  can now access their accounts and so you have saved me from a lot of grief!

---

### Post by petri on 2008-12-25
Thanks geirha this har been a real pain... :popcorn:

---

