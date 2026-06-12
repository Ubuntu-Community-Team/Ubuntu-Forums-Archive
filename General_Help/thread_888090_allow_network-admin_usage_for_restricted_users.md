---
title: "allow network-admin usage for restricted users"
date: 2008-08-12
forum: General Help
---

### Post by colbster on 2008-08-12
Hi there! I'm having an issue with policykit in hardy and the way things work now. I have two users on my system, an administrator and a restricted user. I want the restricted user to be able to use "System>Administration>Network" or network-admin, but none of the other system administration tools. I dont know how to do this with policykit, as it lumps all of them together. Before we had it so the sudoers file gave access to network-admin, and we had a xauth thing setup, but this doesn't work now. Any help is appreciated thanks!

---

### Post by cariboo on 2008-08-12
I don't know if this will help, but if you go to System-->Administration-->Users and Groups, unlock it using your password, click on the user then click properties in the properties window click the user privileges tab and check connect to wireless and ethernet networks. This makes your user a member of the netdev group.

To check what groups your user is a member of:

```
groups <user>
```

Jim

---

### Post by ouro on 2008-08-20
I have the same problem but I've not found the "connect to wireless and ethernet networks" option on "user privileges" tab. Are you sure this option is avaliable on hardy??.

---

### Post by colbster on 2008-08-25
The restricted user can access the network fine, but not use the network-admin tool. adding them to the netdev group doesn't solve this unfortunately.

---

