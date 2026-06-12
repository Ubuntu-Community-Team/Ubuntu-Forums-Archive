---
title: "Error while deleting"
date: 2008-10-19
forum: General Help
---

### Post by accodata on 2008-10-19
Hi
I put some files on my PC from a CD since, then I am getting - I get this message, 
Error while deleting.
Error removing file: Permission denied

I am not sure where I need to change the Permission, I have tried to change the Properties, I go to the Permissions, and change 
Owner
Group
Others
However with the Group and Others Permissions, it won't allow me to change it at all, and won't delete my garbage bin fully.  

I am on Heron 8.04

I know I am thick... but if someone could help I would greatly appreciate!!

Many thanks
Tracey

---

### Post by Sycron on 2008-10-19
If your file is on the Desktop, then do the following:

Open up a terminal (Applications-->Accessories-->Terminal) and type ```
cd Desktop && sudo chmod 777 **name_of_your_file.your_extension**
```

---

### Post by accodata on 2008-10-19
The Documents I am trying to delete is a folder in the Garbage Bin called Documents.

Thank you for your help!!

Tracey

---

### Post by Sycron on 2008-10-19
Just to know with ```
chmod 777
``` command you give to a file(or)folder full read/write access and you are the owner of that file after this command is executed.

---

### Post by accodata on 2008-10-19
Hi I did that

this is what come up in the terminal
need for form,
tracey@tracey-desktop:~$ sudo chmod 777
[sudo] password for tracey: 
chmod: missing operand after `777'
Try `chmod --help' for more information.
tracey@tracey-desktop:~$ 
tracey@tracey-desktop:~$ 


Help!!!
Tracey

---

### Post by Sycron on 2008-10-19
So, you want to change the permissions of a folder, aren't I ?

---

### Post by accodata on 2008-10-19
Hi thank you for your help yes I am trying to change permission of a folder, that is in my garbage bin, that is called documents.

Tracey

---

### Post by Sycron on 2008-10-19
Could you tell me the exactly location of Documents folder ?

if you know the location, open up a terminal and type ```
sudo chmod 777 -R **path/to/your/folder/name_of_the_folder**
```

---

### Post by accodata on 2008-10-19
Hi The folder I am trying to delete is called documents in my garbage bin called documents,
Here is a copy of the code you sent me
tracey@tracey-desktop:~$ sudo chmod 777 -R path/to/folder/documents
[sudo] password for tracey: 
chmod: cannot access `path/to/folder/documents': No such file or directory
tracey@tracey-desktop:~$ 

Thanks

Tracey

---

### Post by Sycron on 2008-10-21
hey, :) replace **path/to/folder/documents** with the exact location of your folder.

---

### Post by Ryadt on 2008-10-21
Try ```
sudo rm -rf ~/.local/share/Trash/Documents
```

---

### Post by accodata on 2008-11-05
That is awesome thank you so much, it worked!!!!!!!!!!

---

