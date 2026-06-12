---
title: "[SOLVED] how do i make hard drive permissions open to all?"
date: 2008-08-27
forum: General Help
---

### Post by jmate24 on 2008-08-27
i have read links and posts but none of them clearly explain how to make hard drive and ext3 filesystem permissions open to all (linux)computers and make it permanent.

i am using Ubuntu 8.04 Hardy and have a 1TB USB drive formatted ext3. and i would like to be able to read and write from any Ubuntu including variants.

thanks for the help.

---

### Post by tramir on 2008-08-27
Ext3 systems should be readable by any linux/unix variant. As long as you're logged in as the same user, things should work. Can you explain a bit better what you mean by "accessible by all linux computers"? You can always share a drive in a network - is this what you want?

---

### Post by jmate24 on 2008-08-28
the permissions. i need to be able to write to it from any variant with out using the command line to set it each time i plug in the drive.

---

### Post by PGScooter on 2008-08-28
ah, you mean "permissions open to all (linux) USERS". I haven't had to do change anything for my drives, but there's probably something you need to do in fstab or mtab.

---

### Post by JermainWijnhard on 2008-08-28
Have you tried setting all the permissions to 777? As in chmod 777 [filename].
It worked for me :p But you need to be root / owner to do it though. Also im a bit of a beginner so you might want to do man chmod before taking my advice :(

---

### Post by tramir on 2008-08-28
This should work: plug the hard disk in the computer that you used to format it. It should open a Nautilus window. Select all the files and  folders, right click and choose "properties". Go to the "Permissions" tab and change the permissions for "group" and "others" to "Create and delete files" (folder) and "Read and write" (files). Click OK. Now you can unplug the drive and your files should be accessible by any user on any computer. Let us know if it worked.

---

### Post by jmate24 on 2008-08-28
here's what i tried: i went and searched my former posts and found a website [http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Windows_with_Dapper_Desktop") and used the information to mount the hard drive to give access and to auto mount at boot and rebooted. then i opened the terminal and typed ```
$ sudo gedit /etc/fstab
```(entered my password) and deleted the lines that i created for that hard drive and clicked save. then i rebooted and logged in and opened a terminal and typed ```
$ sudo nautilus
```(entered my password) and navigated to /media and deleted the folder i created as the mount point for that drive. next i rebooted and logged in again and remounted my external drive and then i opened it up and right-clicked on an empty space and selected Properties. then in the permisions tab i made sure that my user name was preceded by both **Owner** and **Group**. then i made sure that just below the **Others** that says 'Access Files' I changed that to 'Create and delete files'. then i closed it and now i can write from any Ubuntu variant. i just have to have the same username and password that my administrator (my account) has.

---

