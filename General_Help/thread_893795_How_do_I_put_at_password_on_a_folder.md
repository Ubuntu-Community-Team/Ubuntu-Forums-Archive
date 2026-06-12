---
title: "How do I put at password on a folder?"
date: 2008-08-18
forum: General Help
---

### Post by jprice19 on 2008-08-18
Is it possible to lock a folder and to put a password on it? Like if I wanted to lock the documents folder or music folder or something. Thanks

---

### Post by dje on 2008-08-18
please don't [double post]("http://ubuntuforums.org/showthread.php?t=893776")

does [this thread]("http://ubuntuforums.org/showthread.php?t=449219") help? or perhaps try a google search?

dje

---

### Post by Elfy on 2008-08-18
Go straight to this thread which is where dje's leads [http://ubuntuforums.org/showthread.php?t=410513](http://ubuntuforums.org/showthread.php?t=410513)

It would work for a documnet folder using permissions as bodhi_zazen shows,but I don't think it would be useful for a music folder as I assume that anything you wanted to run music with would need root rights.

---

### Post by IvoLucien on 2008-08-18
Generally speaking you'd use chmod to set the permissions for the folder and its contents.

Setting file permissions using chmod allows you to restrict access based on the user's login. Are you trying to set a password that restricts access to other users? Or do you want the password to apply even to the same user account? (for example, if more than one person is using the same account)

---

