---
title: "User Administrator"
date: 2008-08-10
forum: General Help
---

### Post by focus310 on 2008-08-10
Hello:

I downloaded a zip file which automatically went to my Desktop.

I need to unzip the file into a directory which was created for Oracle.

When I try to do the unzip, I receive an error that I do not have permissions to that directory.

How can I give myself permission to work with that directory?

I then tried to login with the user who is the owner of the folder and the username and password comes as no match.

I went to the terminal window and changed the password for this user to be the same, I tried logging in to Ubuntu, and I still received the username and password do not match.

Can someone help me figure out all this user access/permissions?

Also, when I do a download via Firefox, how can I change the location of the download?  I would like the ability to select the directory where I want the file to go.  

And, when I'm ready to unzip the file, the extraction also doesn't let me choose a directory.  How can I change this?

Thanks for the help.

---

### Post by iaculallad on 2008-08-10
Try to insert the **sudo** command to your "unzip" terminal command or you could just do **gksudo nautilus** in your terminal.

---

### Post by tuxxy on 2008-08-10
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

