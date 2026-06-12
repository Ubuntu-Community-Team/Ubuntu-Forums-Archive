---
title: "Urgent: unable to access users/groups"
date: 2008-09-09
forum: General Help
---

### Post by budkule on 2008-09-09
Hello all...
I am the user and admin of the system and i am the only user for the system, I was testing users/groups properties
I changed my name to s and said ok in user properties for my username. All permissions and access were given to my earlier username not even to root.
when i tried to access the users/groups under system>Administration i could not. :(
After restarting the system i could login only as s. Now the option users/groups is also not allowed.
How can change it back to my earlier name. Password is the same for user and root.
Please help its urgent

---

### Post by iaculallad on 2008-09-09
Be sure to click on "Unlock" before clicking on the "Properties" button on your Users/Groups menu.

---

### Post by budkule on 2008-09-09
Thanks for the reply.
Now after logging in as s, there is no option for users/groups.
How do i access users/groups menu either as s or as root so that i unlock and use the properties.
Please help its really urgent

---

### Post by Vivaldi Gloria on 2008-09-09
It's well known that your user loses the privileges of the previous username when you change your name. You shouldn't have done that. I suggest you press ESC at the boot and choose recovery to boot into recovery console and try adding your new username to admin group. Read the man pages of the following commands:

```
groups
adduser
usermod
```

Actually first search these forums incase someone already went through the same ordeal.

---

### Post by zvacet on 2008-09-09
Give administrator privileges to your new username.

```
sudo adduser username admin
```

If you can not use sudo boot in **recovery mode** and type above command without **sudo**.

---

### Post by budkule on 2008-09-09
Yeah i should not have done that. I am repenting now thanks a lot for your reply.
:)

---

### Post by budkule on 2008-09-09
Thanks guys for all the help.
Now i am able to access and i have set up user name and the privileges. :KS

---

### Post by Vivaldi Gloria on 2008-09-09
> **budkule said:**
> Thanks guys for all the help.
Now i am able to access and i have set up user name and the privileges. :KS

Good to hear. Have fun.

---

