---
title: "permission to write and change file in File System"
date: 2008-07-12
forum: General Help
---

### Post by masoud23 on 2008-07-12
Hi

I wonder if it is a way to get permission to write and change file in File System for a Administrator permanently. to use Localhost and do other programming i have to be able to save and change file there from different programs like a Codeeditor(Bluefish)?

---

### Post by dexter.deepak on 2008-07-12
can you be a bit more clear in what you want ?

---

### Post by Tomatz on 2008-07-12
> **masoud23 said:**
> Hi

I wonder if it is a way to get permission to write and change file in File System for a Administrator permanently. to use Localhost and do other programming i have to be able to save and change file there from different programs like a Codeeditor(Bluefish)?

You could just run the program you are using as root. Open a terminal and type the following (obviously replace "APP-NAME" with the app you want to use):

```
gksu APP-NAME
```

Hope that helps ;)

---

### Post by masoud23 on 2008-07-12
I want to be able to crate, save download files in and to my File System. right now i get permission denide all the time.

---

### Post by Tomatz on 2008-07-12
> **masoud23 said:**
> I want to be able to crate, save download files in and to my File System. right now i get permission denide all the time.

You need to root permisions to do this. To open a root file manager do this in a terminal:

```
gksu nautilus
```


Its what makes Linux/UNIX so secure and it's NOT to be turned off.

---

### Post by masoud23 on 2008-07-12
Yes! tanks now I can use FileZilla for downloading. But I have to do this every time i start a progam don't I. Is there a way to grand permission permanently?

---

### Post by dexter.deepak on 2008-07-12
its a real bad habit to get a 100% write/execute access over the entire filesystem. ...especially if you are connected to a network, because if you can write "anywhere" , a traitor may also corrupt your filesystem.

so its better to use your ~ to save/modify files.
 if you are in a real need, you can start your app,like this-
gksu firefox 
 but in that case "you" will not be "you" and the files you create will automatically be having "root" permissions, and you will be able to access those files only as root, via sudo.

---

### Post by Tomatz on 2008-07-12
> **masoud23 said:**
> Yes! tanks now I can use FileZilla for downloading. But I have to do this every time i start a progam don't I. Is there a way to grand permission permanently?

R-click on the **applications menu**, click **edit menus**, find filezilla, double click on the filezilla menu entry then put **gksu** in front of the **command**.

RUNNING FILEZILLA AS ROOT COULD BE POTENTIALLY DANGEROUS!!!

Where are the files you are trying to access on your system anyway? Maybe i can help better if you can explain better.

---

### Post by coffeecat on 2008-07-12
> **masoud23 said:**
> I want to be able to crate, save download files in and to my File System. right now i get permission denide all the time.

I think you're missing the whole point of security and permissions in Linux. This sounds like you're still thinking in Windows ways. Don't worry, we all do it. :) It takes time.

Your home folder is where **everything** you download should go. Create special folders for whatever you want. Then if you need to copy files into system folders, you use sudo or whatever method you need to obtain administrator privileges and do so. Ditto for creating config files and suchlike In fact I can't think of a single instance where I would want to save downloaded files directly into system folders. Can you give examples of what you are trying to do?

---

### Post by Raikiri on 2010-10-22
Sorry for reviving an old thread but I need a solution.

You all say that running filezilla gksu is dangerous but what are the alternatives?  I need to download and upload files to my server and I cannot do it unless in root mode.  Now I see that you also have to open these files in root mode to do anything with them?

Are there any workarounds?

---

### Post by endotherm on 2010-10-22
> **Raikiri said:**
> Sorry for reviving an old thread but I need a solution.

You all say that running filezilla gksu is dangerous but what are the alternatives?  I need to download and upload files to my server and I cannot do it unless in root mode.  Now I see that you also have to open these files in root mode to do anything with them?

Are there any workarounds?

well, the point is, that you should never (or very rarely) be writing to / from a normal user account. a user should save everything in their home directory or on a data drive that has been configured for them. in short, the problem is what you are trying to do, not how you are trying to do it, so the only workarounds are to look for ways to get the things you want, without writing to system areas of the filesystem. 

Many times, when a dev wants an app to save data they create a user account and home directory for the app itself. then they save all their stuff there. 

you can also create a "upload" folder in root, and set yourself as owner, and grant yourself rwx on it. then you can upload to it, and on the server side, decide where the file has to go.

---

### Post by 3rdalbum on 2010-10-22
> **Raikiri said:**
> Sorry for reviving an old thread but I need a solution.

You all say that running filezilla gksu is dangerous but what are the alternatives?  I need to download and upload files to my server and I cannot do it unless in root mode.  Now I see that you also have to open these files in root mode to do anything with them?

You should not need root permission to upload files to an FTP server. If the files are owned by root then you won't be able to read them with your normal user account, but then those files should NOT be owned by root (they are owned by root because you improperly used root permissions - it doesn't help if you have to keep running all programs as root to deal with these files).

Solution? Run the file browser as root, and use it to change the ownership of the files back to your user account. Alternatively, use the 'chown' command which does the same thing. **In future, create your files as your user account and then copy them to privileged locations using a root file browser.**

---

### Post by marcusjames on 2010-10-22
this is ridiculous............for a local apache server all u need do is set the file permissions in htdocs as they should be........there is an extension to nautilus which gives admin access to folders for these purposes......

---

