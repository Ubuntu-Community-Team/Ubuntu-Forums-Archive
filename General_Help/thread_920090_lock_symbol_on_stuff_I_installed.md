---
title: "lock symbol on stuff I installed"
date: 2008-09-14
forum: General Help
---

### Post by tuskpc on 2008-09-14
I did not know how to phrase the question right, but I seem to keep getting a lock symbol on "stuff" I put on Ubuntu from backup CD-r's and DVD-R - on both my desktop and laptop.  

Is this something I need to look into or just keep on ignoring...

```

**tuskpc@tuskpc-desktop:~/Videos$ ls -l**
drwxr-xr-x 2 tuskpc tuskpc 4096 2008-09-14 11:07 Google.Lectures
dr-xr-xr-x 2 tuskpc tuskpc 4096 2008-05-02 18:42 poker


**tuskpc@tuskpc-desktop:~/Videos/Google.Lectures$ ls -l**
total 2195872
-r--r--r-- 1 tuskpc tuskpc 195683319 2008-03-20 13:42 7_Habits_For_Effective_Text_Editing_2.0.flv
-r--r--r-- 1 tuskpc tuskpc  79875284 2008-03-19 18:24 DanIngallsObjectOrie.flv
-r--r--r-- 1 tuskpc tuskpc 356660479 2008-03-19 23:54 GabrielRobins-TimeManagementByRandyPauschNovember2007187.wmv
... edit...


**tuskpc@tuskpc-desktop:~/Documents$ ls -l**
-r--r--r-- 1 tuskpc tuskpc 50581341 2008-03-18 15:00 Aho - Compilers - Principles, Techniques, and Tools 2e.pdf
dr-xr-xr-x 2 tuskpc tuskpc     4096 2008-05-02 18:42 Computer.Organization.and.Design.The.Hardware.Software.Interface.3rd.Ed.2004
-rw-r--r-- 1 tuskpc tuskpc   520899 2008-09-12 21:12 II.Foomatic-User.pdf


```

---

### Post by iaculallad on 2008-09-14
You could right-click on the folder and change permission on it's properties.

```
gksudo nautilus
```

Or simply use the Terminal:

```
sudo chown -R $USER:$USER Folder_Location
```

Of course you will replace $USER with your user name. 
The $USER contains the value of currently logged user.

---

### Post by Mister.Vash on 2008-09-14
It is because they are marked as read only.  When the files are written to a cd or dvd, the write bit is removed.  When they are copied back over, they no longer have the write bit. If you aren't going to edit the file, it won't hurt anything unless it bugs you.  If it's something that you are going to edit, like a open office document, then you should change the file permission to include write.

---

### Post by tuskpc on 2008-09-15
I thank both of you for the reply.  I was just checking to make sure it wasn't a sign of something I should check into.

---

