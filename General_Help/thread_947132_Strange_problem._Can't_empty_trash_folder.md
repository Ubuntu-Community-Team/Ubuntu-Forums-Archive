---
title: "Strange problem. Can't empty trash folder"
date: 2008-10-14
forum: General Help
---

### Post by kokkus on 2008-10-14
I try to empty my trash but the files comes back.
I even tried to delete the files as root.
What is the reason and how can I empty the trash folder?

Thanks in advance

---

### Post by Washer on 2008-10-14
right click on the files & select delete. What error does it give?

---

### Post by kokkus on 2008-10-14
None error. It deletes and comes back.

---

### Post by bigbrovar on 2008-10-14
first open terminal **Application/Accessories/Terminal** and run this command ```
gkdu nautilus
``` this would open the nautilus file manager in root mode from there 
- go to your home folder
- from the view menubar select **show hidden files** (this would show you all the hidden files on your system i.e files whose name start with a dot 
- now navigate to **.local/share/trash**

[IMG]http://farm4.static.flickr.com/3058/2941041832_930c21688b_o_d.jpg[/IMG]

-who would see 2 folders **files** and **info**
-open the file folder and delete everything there do the same to the info folder

The reason why u had the problem was because u sent something that had root permission to the trash meaning only a root user can delete it. anyway u have just deleted it now ( i hope) so problem solved (i guess)

---

