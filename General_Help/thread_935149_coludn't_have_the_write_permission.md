---
title: "coludn't have the write permission"
date: 2008-10-01
forum: General Help
---

### Post by Joseph82 on 2008-10-01
Hi

I have installed lampp (for php development) on my system. It is installed to the following path:

/opt/lampp/


When I tried by creating a sample file in the root directory of this package (/opt/lampp/htdocs), it returns the following error:


Could not save the file /opt/lampp/htdocs/test.php.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


Please guide me to solve this issue. 

I have logged to the system with a user and changed to root from terminal , to run this package.

Is there any way to assign the whole permission to this user always, so I can get all permissions.. 



Also, can someone here who can guide me to install Quanta ?


Thank You,
Joseph.

---

### Post by Julius1988 on 2008-10-01
Try "chmod -R 755 foldername" to change permission of the directory and everything inside it.

---

### Post by Joseph82 on 2008-10-01
> **Julius1988 said:**
> Try "chmod -R 755 foldername" to change permission of the directory and everything inside it.



Yes, that worked!

Thank you for your help. 



Could you please help me in installing Quanta ? I have downloaded it from the location:

[http://sourceforge.net/project/showfiles.php?group_id=4113](http://sourceforge.net/project/showfiles.php?group_id=4113)

Thank You,
An. Joseph

---

