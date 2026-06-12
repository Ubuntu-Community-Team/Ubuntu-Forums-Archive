---
title: "folder to automount and sync"
date: 2008-11-21
forum: General Help
---

### Post by Kain000 on 2008-11-21
Hey everyone, 

I'm wondering how I would enable a folder on my laptop to have an "identical twin" on my desktop and when my laptop comes online while my desktop is on, or visa versa they would sync and resolve any differences. 

I wright alot of c++ text files for school and when at home I like to use my larger screen, however it's a pain to manualy merge the files, and then again back to the laptop for school the next day.     

I sorta understand how the fstab folder in /etc/ works to mount partitions and drives, I have it set up to mount a NFS share from my desktop and another from my server when it boots up, 

Would this be set up the same way, but somehow told to sinc and resolve any differences when found?

thanks everyone
-sean

---

### Post by ponkarthik on 2008-11-21
Have you tried Dropbox ?

I use Dropbox for the very purpose. Syncs folders ( though limited to Dropbox and its subfolders) without any intervention and files are accessible from an online too. 

[www.getdropbox.com](www.getdropbox.com)

---

### Post by rubberglove on 2008-11-21
> **Kain000 said:**
> Hey everyone, 

I'm wondering how I would enable a folder on my laptop to have an "identical twin" on my desktop and when my laptop comes online while my desktop is on, or visa versa they would sync and resolve any differences. 

I wright alot of c++ text files for school and when at home I like to use my larger screen, however it's a pain to manualy merge the files, and then again back to the laptop for school the next day.     

I sorta understand how the fstab folder in /etc/ works to mount partitions and drives, I have it set up to mount a NFS share from my desktop and another from my server when it boots up, 

Would this be set up the same way, but somehow told to sinc and resolve any differences when found?

thanks everyone
-sean

It sounds like you might want to consider using a revision control system like svn (subversion) or git for that purpose instead. Those tools were designed to do more-or-less what you are describing, and would have a ton of other benefits as well.

If you're not familiar with svn or revision control in general, it can be a bit confusing to understand at first, but can really be worth the effort (especially if are ever working on a software project with a team of people).

---

### Post by Kain000 on 2008-11-23
thanks both of you for your help.

---

