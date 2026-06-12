---
title: "Help needed with Thunderbird Backup"
date: 2008-10-19
forum: General Help
---

### Post by smaranya on 2008-10-19
Hello,

I recently started to use Ubuntu as my only operating system . i am very happy with it but having one issues with my emails .

I have multiple email accounts configured in Thunderbird ( in my previous os : windows xp ), having more than 2k emails .

Now as I am using only Ubuntu , i need those emails to be set in Thunderbird ( in Ubuntu )

So my question has two parts , as follows :

1. How to have a backup of all emails and settings from Thunderbird-windows   

2. how to that  can be restored in Thunderbird ( Ubuntu )

and also is there any facility available if I can have periodic backups of my email from Thunderbird .

Thanking you in Advance for all of your help.

Regards

---

### Post by jimv on 2008-10-19
Quite a few articles on how to migrate Thunderbird from XP to Ubuntu:

[http://www.google.com/search?q=migrating+thunderbird+xp+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=migrating+thunderbird+xp+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

For the backup, all you really need to do is grab a copy of **/home/you/.thunderbird** on Ubuntu, and **C:/Documents and Settings/You/Application Data/Thunderbird** in Windows.  All of the files you need are in there.

---

### Post by Altay_H on 2008-10-19
You can see where Thunderbird stores your emails by going to Tools > Account Settings > Local Folders > Local Directory. You should be able to copy the contents of this folder from your XP computer to your linux computer. Similarly, to see where your Linux Thunderbird stores your emails, you'll need to go to Edit > Account Settings > Local Folders > Local Directory.

---

### Post by smaranya on 2008-10-19
Thanks for your advice , will give it a try ....

regards

---

### Post by cariboo on 2008-10-19
I've been using the same thunderbird folder since I started using thunderbird. If you haven't setup thunderbird yet, you can just copy the windows folder and continue using it. Thunderbird's folder is hidden so to access it. Open Nuatilus (Places-->Hiome Foler) and press Ctrl-h to reveal hidden files and folders the folder you are looking for is ~/.mozilla-thunderbird.

I just backup the whole ~/.mozilla-thunderbird to my server using rsync. Have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=639979](http://ubuntuforums.org/showthread.php?t=639979)

Jim

---

