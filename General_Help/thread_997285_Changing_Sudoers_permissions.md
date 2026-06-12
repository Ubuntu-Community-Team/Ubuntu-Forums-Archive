---
title: "Changing Sudoers permissions"
date: 2008-11-29
forum: General Help
---

### Post by eldila2 on 2008-11-29
I created a new group called partialadmin. I want the users to pretty much have complete root access. However, I want to make sure that they don't have permission to edit particular files.

Is there a way to do this? If there isn't a way, what can I do to give them as much permission as possible without giving them access to particular files.

Please include the changes that I need to make in visudo and any file permission changes that may be needed.

---

### Post by markharding557 on 2008-11-29
you can use users and groups in system>administration in the menu.
i am puzzled by your reference to root access since ubuntu in its default state does not have a root account.

---

### Post by eldila2 on 2008-11-29
I don't mean that they can log in as root.

For example, the group has the following sudo access:

%partialadmin ALL=(ALL) ALL

This allows them to have access to everything when using sudo. However, I don't want them to have access to particular files.

Alternatively, if you set the sudo access to:

%partialadmin ALL=(accounts) ALL

The user doesn't have access to all configuration files (ie. /etc/network/interfaces). However, I want them to have access to some of these configuration files.

---

