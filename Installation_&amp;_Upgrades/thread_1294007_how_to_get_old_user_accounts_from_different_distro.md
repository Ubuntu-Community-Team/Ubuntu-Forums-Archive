---
title: "how to get old user accounts from different distro to be active in Ubuntu 8.10"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by ryancw on 2009-10-17
I installed Ubuntu 8.10 into sda4 on my hard drive, a primary partition. sda2, also a primary, contains another linux distro that I was mainly using. I had 6 users, all in a home directory on a different primary partition, sda3, that would mount at /home.

 As I installed Ubuntu, I created a user by the same name as the one I used on the other distro, and same password.  Ubuntu installer also offered to import some settings from all the users into the new installation, and I accepted. I recognized all the user accounts by name, correctly.

The one user I created at installation works fine. It found all my pre-existing data.

In a file manager, I can see that directories exist for each of the other users. However, under System...Administration...UsersAndGroups, the other 5 users are not listed.  And none of them can log in.  When I go to create new users (pointing their homes to their existing homes), I am admonished that those directory paths already exist, and I have to name different paths.

How can I get all my other users properly recognized by Ubuntu, and such that they can access all their existing data?

Thanks.

---

### Post by stlsaint on 2009-10-17
from my understanding when you import those user profiles during install...you import them into the user you created during install. to give more users acess you need to create them individually then give them permissions to the particular folders you have for them...or mount the individual folders to the user's desktop at boot/login.

---

### Post by ryancw on 2009-10-17
Thanks. But that seems to be part of the problem. 

 For example, on the other distro I had been using, there was user1 and user2. They hade home folders /home/user1 and /home/user2.

When I installed Ubuntu, I created user1. That works fine, 

The folder /home/user2 exists. And as long as it does, Ubuntu doesn't let me create user2 with /home/user2 as its home directory.

---

