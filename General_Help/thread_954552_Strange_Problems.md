---
title: "Strange Problems"
date: 2008-10-21
forum: General Help
---

### Post by cangel0612 on 2008-10-21
So here are my problems...

1. When I click on the shutdown button in my toolbar, the toolbar disappears. 

2. My wireless icon on the toolbar no longer shows up and I can't connect to anything, but I checked my hardware drivers and everything looks great. My blue light even comes on the front of my laptop showing that it is being activated. (It usually shows red otherwise) Also, I can't connect to the internet.

3. My brightness icon on the toolbar no longer changes anything.

UPDATE: I get a new warning when running ANYTHING from the command line... GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason: None of the authentication protocols specified are supported and host-based authentication failed. !!!!

HELP!

Thanks

---

### Post by pastalavista on 2008-10-21
reboot in 'recovery mode'--at the prompt, select 'repair broken packages' and 'repair xorg'--then boot normally

---

### Post by cangel0612 on 2008-10-21
Thanks, I tried it but it didn't fix anything for me... but I noticed this...

Another **UPDATE:**

I just noticed that my root folder shows that I have 0 Free Space, which is probably my problem.

I don't know how to fix this, I have a dual boot Vista and Ubuntu and mounted my ext2 drive in Vista and I think it may have locked it in some way.

Is there anyway to fix this inside Ubuntu?

---

### Post by Mariane on 2008-10-21
Where did you get the "repair" command, please? Sounds usefull but my apt-cache search can't find it. 

Mariane

---

### Post by cangel0612 on 2008-10-21
When you boot in recovery mode, there is a "repair" option in the prompts.

---

### Post by pastalavista on 2008-10-21
you can shrink your Windows partiton to allow room to stretch your Ubuntu. To shrink Windows, while you can do it with gparted in Ubuntu, it's best to use Vista's disk management tool (right click My Computer and select 'manage') then boot Ubuntu from the live CD and use gparted to stretch the '/' drive... good luck with all that... you may have to reinstall Ubuntu too if recovery mode didn't fix it..

---

### Post by cangel0612 on 2008-10-21
Well, I don't think I need to resize the partition, it had 10 GB Free as of yesterday and I haven't installed anything on it. Also, I delete things out of Ubuntu like crazy and still 0 Bytes free.

---

### Post by cangel0612 on 2008-10-21
Hopefully the last UPDATE

I checked gparted and it says I have 2GB Free, but when I go into my root folder, it says 0 Bytes Free

I can't even create a folder on the Desktop.

Thanks again...

---

