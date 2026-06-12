---
title: "Verlihub motd"
date: 2008-07-18
forum: General Help
---

### Post by gogles on 2008-07-18
I have just setup verlihub on my ubuntu desktop box and i have run into a problem with changing the motd. I have followed the manual's instructions to modify the motd file in the config directory but after doing so the motd remains the same as it was before. I have searched the entire system finding 2 motd files under verlihub directories and changed them but the motd remains the same. Appreciate any help with this problem.

here is a link to the manual's page on configurarion

[http://www.verlihub-project.org/doku.php?id=configuring_your_hub](http://www.verlihub-project.org/doku.php?id=configuring_your_hub)

"The message of the day will be shown to every member joining the hub. All that needs to be done is a text file needs to be saved as 'motd' in the configuration directory (in this guide /etc/verlihub/motd) and verlihub will automatically use it. Verlihub allows you to show extra motd's based on user class."

When joining my hub there is an existing motd that must be being read from a file. I have found to 2 files that contain the motd text being displayed in my hub. motd is not listed as a database configuration variable (hub config uses MySQL database). Is it possible i have not found the right motd file using system search? there is a folder i cannot access because of permissions. How would i access this directory? In the directory's properties it lists the owner as 'mysql – MySQL Server'. (I am new to linux)

---

### Post by Flytagger on 2009-08-31
> **gogles said:**
> I have just setup verlihub on my ubuntu desktop box and i have run into a problem with changing the motd. I have followed the manual's instructions to modify the motd file in the config directory but after doing so the motd remains the same as it was before. I have searched the entire system finding 2 motd files under verlihub directories and changed them but the motd remains the same. Appreciate any help with this problem.

here is a link to the manual's page on configurarion

[http://www.verlihub-project.org/doku.php?id=configuring_your_hub](http://www.verlihub-project.org/doku.php?id=configuring_your_hub)

"The message of the day will be shown to every member joining the hub. All that needs to be done is a text file needs to be saved as 'motd' in the configuration directory (in this guide /etc/verlihub/motd) and verlihub will automatically use it. Verlihub allows you to show extra motd's based on user class."

When joining my hub there is an existing motd that must be being read from a file. I have found to 2 files that contain the motd text being displayed in my hub. motd is not listed as a database configuration variable (hub config uses MySQL database). Is it possible i have not found the right motd file using system search? there is a folder i cannot access because of permissions. How would i access this directory? In the directory's properties it lists the owner as 'mysql – MySQL Server'. (I am new to linux)


** Try configuring it directly from the hub. !modtrigger +motd -d "text"-f 20 -c 0 -C 10**

---

