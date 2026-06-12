---
title: "Monodevelop and Mcrypt"
date: 2008-11-27
forum: General Help
---

### Post by digbigbrotherjenson on 2008-11-27
I'm trying to write a simple C# script that adds a user to the system.

The command syntax : cmd <username> <password> <email> <homedirectory>

... 

Now the thing is ... The password can only be added to the system through the useradd unix command ... 
The password in it's turn must be entered encrypted to be stored in the /etc/shadow file ... the encryption of the password must be done using the mcrypt library ...

How can I use make use of this library in Monodevelop ?

---

