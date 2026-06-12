---
title: "How do i take ownership of my files"
date: 2008-08-07
forum: General Help
---

### Post by zachoeser on 2008-08-07
I am trying to delete and move files but it will not let me because i do not "own" them and it will not give me the option to take ownership of them. all the boxes  are greyed out and i cant change anything. how do i make it so i have ownership of all items in the filesystem thanks alot!

---

### Post by fmartinez on 2008-08-07
the chown command is perfect for your situation. 
If the file is owned by someone else. ex: 
fileA owned by user "a" and group "a" lets change the owner to owner "b"

sudo chown b:b /path/to/fileA

hope this helps. 
ps. you see the manual for chown for more infomation. 

man chown

---

### Post by jkid on 2008-08-07
right click on the file and go to properties>permision and it should be there,......

---

### Post by zachoeser on 2008-08-07
it is there, but it is greyed out and will not let me click anything

---

### Post by iaculallad on 2008-08-07
> **zachoeser said:**
> I am trying to delete and move files but it will not let me because i do not "own" them and it will not give me the option to take ownership of them. all the boxes  are greyed out and i cant change anything. how do i make it so i have ownership of all items in the filesystem thanks alot!

Originally, the root owns almost all of the items in your filesystem hierarchy. And the reason for that is security. You can delete and move this item by using either:

To copy to other location:

```
sudo cp /source_location/filename.txt /destination_source/filename.txt
sudo -r /source_location/foldername /destination_location/
```

To delete an item or folder:

```
sudo rm /source_location/filename.ext
sudo rm -rf /home/your_user_name/Some_Folders
```

Or simply:

```
gksudo nautilus
```

could do both moving and deleting. Just be careful.

---

### Post by zachoeser on 2008-08-07
its not owned by anyone else though. i am the only user on the computer..... it just says i dont own the files in the filesystem

---

### Post by loligager on 2008-08-07
dude there are 2 ways of doing it!!!
first is the easy and not advised way [cous u could mess thing up]
do a Alt F2 and type in "gksudo nautilus" without quotes

the next way requires the terminal
do a chmod on it
I am sure ppl can help u with that cous i forgot
hehe Have fun

---

### Post by zachoeser on 2008-08-07
it says it will not let me remove the folder because it is a directory, how do i fix that

---

### Post by iaculallad on 2008-08-07
> **zachoeser said:**
> it says it will not let me remove the folder because it is a directory, how do i fix that

Doing it on the terminal:

```
sudo rm -rf /directory/directory_folder_you_want_to_remove
```

---

### Post by zachoeser on 2008-08-07
Solved, Thanks Alot

---

### Post by samoyed on 2009-11-10
Thanks a lot Iam alsonew to linux , I was also trying to delete a folder but it was not allowing to do so , in the properties also it was showing some user like #500 , anyway its now solved .

regards

---

### Post by scouser73 on 2009-11-10
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your  folder/file/drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your folder/file/drive.

---

### Post by samoyed on 2009-11-21
Thanks, scouser73 ,

regarding more information regarding ownership

regards

---

