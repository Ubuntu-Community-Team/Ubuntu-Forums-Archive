---
title: "Change User Name"
date: 2008-11-22
forum: General Help
---

### Post by want-to-believe on 2008-11-22
I installed Ubuntu 8.10 yesterday, I was using 8.04 for awhile. I installed kde desktop and transferred over all my data. I was very happy until I wrecked my user profile "troy". When that happened I did what I would do in Windows, I created a new user profile, "troy2" and copied over my data. I deleted "troy" and now I want to change my user name from "troy2" to "troy" but I can't seem to locate how I can do this. I went to System-Users and Groups, but the user name category is greyed out. I really appreciate any response. Thanks.

---

### Post by drs305 on 2008-11-22
did you try to unlock the Users & Groups? If you weren't successful, the reason is probably because you didn't give troy2 admin powers. You will have to go into the recovery mode from boot and add troy2 to the the 'admin' group. Then reboot, go into Users & Groups and try again. While you are in there, highlight your username, Properties, click on the User Privileges tab, and tick any services you may need. (And do the same for troy1, especially admin powers).

At the recovery mode root prompt:
```
adduser troy2 admin
```

---

### Post by taurus on 2008-11-22
Boot your machine into recovery mode from GRUB menu.  If you don't see GRUB menu when you turn on your machine (instead of the word GRUB), you have three seconds to press ESC to bring up the menu.  Then at the prompt, run

```
cd /home
mv troy2 troy
chown -R troy:troy /home/troy
```
Now, you need to edit /etc/passwd and replace /home/troy2 to /home/troy since there is no troy2 anymore.

```
nano -Bw /etc/passwd
```
Once you have done it, exit with <Ctrl>x and save it with Y.  Then, you also need to edit /etc/group and replace troy2 with troy.

```
nano -Bw /etc/group
```
Now reboot and see if you can log in as troy.

```
shutdown -r now
```

---

### Post by want-to-believe on 2008-11-23
Hey, thanks. troy2 is in the admin  group.

---

### Post by want-to-believe on 2008-11-23
Thanks for the help.

---

