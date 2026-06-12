---
title: "My Hard Drive sometimes working hard in Ubuntu."
date: 2011-12-26
forum: Hardware
---

### Post by khosro on 2011-12-26
Hello,
I have a problem with my Hard Drive in Ubuntu.
Sometimes my Hard Drive is working hard for a long period of time and light of my Hard drive is on("working hard" means that there is a program that have a heavy read/write from Hard Drive).In order to find which program causes my Hard Drive working hard ,i close all programs one by one to find which one causes my Hard Drive working hard but after closing all of my programs(FireFox ,Chrome,Eclipse)my Hard Drive still working and do not stop and light of Hard Drive is still on,in order to stop it, i must restart my laptop.
Is there any program that tell me that which software consumes my Hard Drive?
It is better to say that my Hard Drive is new ,and i bought it a month ago,and i have not the same issue in Windows.

Khosro.

---

### Post by 2F4U on 2011-12-26
I would start by opening a terminal and starting top, or install htop and use that. The advantage of htop is that it allows you to scroll through the list of processes.

---

### Post by khosro on 2011-12-26
Hi 2F4U,
I do not understand how "top" command can help me.
According to [http://linux.about.com/od/commands/l/blcmdl1_top.htm]("http://linux.about.com/od/commands/l/blcmdl1_top.htm"),would you please tell which field description can help me?

Khosro.

---

### Post by hakermania on 2011-12-26
Oh, I always had this awful feeling in MS Windows :/
I would say to open the system monitor manually and see which processes are working hard that time. It's better to avoid command line while having nice GUIs for this :)

---

### Post by khosro on 2012-01-06
Thanks 2F4U and hakermania for your helps.
By running "top" command ,i at last found updatedb.mlocat causes my Hard Drive working hard.
It seems updatedb.mlocat runs randomly.

Khosro.

---

