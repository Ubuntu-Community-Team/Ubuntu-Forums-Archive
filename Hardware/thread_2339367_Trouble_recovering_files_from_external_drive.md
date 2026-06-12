---
title: "Trouble recovering files from external drive"
date: 2016-10-07
forum: Hardware
---

### Post by schnumbles on 2016-10-07
Howdy all! I have an external drive that I used as a backup drive for my no longer functional mac.
I'd like to access these files however I am unable to move the files or alter them. I always get the following error:

 > The folder “Documents” cannot be handled because you do not have permissions to read it.


I have tried using root nautilus and I have also tried changing ownership in terminal but still have the same issue. Any help would be greatly appreciated.

---

### Post by colmax on 2016-10-08
Maybe make the folder "documents" shared
Hey Welcome to the Ubuntu world :)

---

### Post by schnumbles on 2016-10-10
Figured it out! I had accidentally changed the ownership of all the folders to root. So I used the command line to change them back to me.

[http://askubuntu.com/questions/6723/change-folder-permissions-and-ownership](http://askubuntu.com/questions/6723/change-folder-permissions-and-ownership)

---

