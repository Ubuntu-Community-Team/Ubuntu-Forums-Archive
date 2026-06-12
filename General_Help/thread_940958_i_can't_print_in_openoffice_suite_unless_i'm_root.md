---
title: "i can't print in openoffice suite unless i'm root"
date: 2008-10-07
forum: General Help
---

### Post by badfish69 on 2008-10-07
The title pretty much says it all. It worked until a few days ago, now I have to open the application through terminal as root to be able to print. That's for all of them, writer, presentation, or spreadsheet.

---

### Post by Seedsta on 2008-10-07
Have you installed any updates in the last few days, any new programs?  are you running selinux?  does the system give you any warnings when you try to print as a user?  have you changed any of your user account settings?

Can you print out of other applications, or from terminal as a user?

---

### Post by badfish69 on 2008-10-07
[http://localhost:631/admin/log/error_log](http://localhost:631/admin/log/error_log)

```

E [07/Oct/2008:15:59:57 -0500] [Job 49] No pages found!
E [07/Oct/2008:15:59:58 -0500] [Job 50] No pages found!
E [07/Oct/2008:16:00:06 -0500] [Job 51] No pages found!

```

---

### Post by badfish69 on 2008-10-07
> **Seedsta said:**
> Have you installed any updates in the last few days, any new programs?  are you running selinux?  does the system give you any warnings when you try to print as a user?  have you changed any of your user account settings?

Can you print out of other applications, or from terminal as a user?

I removed myself from administrator group, no sudo priveleges. I su root everything that needs it. I'm running ubuntu hardy. It gives me no warnings, it acts normal and adds a a line to my cups error log. Even when I put myself back in the admin group and restart, the same thing happens, and I have to sudo open oowriter to print. Every other program on my comp prints fine as user. Other than that I recently added a network printer in another city, but that only gets used when I go home for a weekend.

on a possibly related note, xsane still works fine as user.

---

### Post by Seedsta on 2008-10-08
Essentially, the spool/que is getting the job, but it is empty, that is what the cups error log is telling you.  Unfortunately I am not near a linux box right now, but there should be an option under printing for the page range you want printed, make sure that current, or all pages is selected.  Since you are able to print out of other programs with the user it should be an open office glitch or setting.
This did not start occurring when you removed your usr's su rights did it?  
I am not familiar with where oowriter is stored, but if it is in a systems directory (which it most likely is) and this started occurring when you removed your su rights, then that is the problem, you are going to have to either reassign your self as a su, or you are going to have to explicitly give your user rights to oowriter.  
I will look at it more for you when I am in front of an Ubuntu box with Open Office.
Hope that helps some in the mean time.
-Seedsta

---

### Post by badfish69 on 2008-10-08
I've already tried reassigning my su rights. Even with su rights, I still have to sudo oowriter in the terminal to be able to print. Explicitly giving my user rights to oowriter would be the ideal fix.

---

### Post by Seedsta on 2008-10-09
Indeed, so this did happen when you took su rights from your user account.  I will look into writing you some instructions on that later, in the mean time, if you are printing a lot, you may want to script the su oowriter commands you have been having to use, it will at least make it a bit faster, if not still just as annoying.

---

### Post by Seedsta on 2008-10-09
better yet, here is a really good online tutorial on how to change file permissions.

[http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&cdn=compute&tm=105&f=00&su=p284.9.336.ip_p504.1.336.ip_&tt=2&bt=0&bts=0&zu=https%3A//wiki.ubuntu.com/FilePermissions](http://linux.about.com/gi/dynamic/offsite.htm?zi=1/XJ&sdn=linux&cdn=compute&tm=105&f=00&su=p284.9.336.ip_p504.1.336.ip_&tt=2&bt=0&bts=0&zu=https%3A//wiki.ubuntu.com/FilePermissions)

I would suggest creating some dummy files and toying with them until you get the hang of it.
NOTE: You are going to need to sudo root to change the permissions on oowriter!!!  You are also going to need to know what group your usr account is part of, and I would not suggest making it part of "other," that could cause 'OTHER' problems.

Good luck to you, hope that does the trick, if not, post back and we will go from there.

---

### Post by badfish69 on 2008-10-09
I made a little progress, but it's far from resolved. After removing myself from the "admin" group, I didn't add myself to any other groups. So I went in, added myself to the group "users," and rebooted. Now, the print command works in open office. Except I get a blank sheet. And now it's doing it in gedit and everything else too. If I remove myself from the group "users" it goes back to the way it was.

---

### Post by badfish69 on 2008-10-09
> **Seedsta said:**
> Indeed, so this did happen when you took su rights from your user account.  I will look into writing you some instructions on that later, in the mean time, if you are printing a lot, you may want to script the su oowriter commands you have been having to use, it will at least make it a bit faster, if not still just as annoying.

I don't know anything about scripting. I've been having to 
```

su root
oowriter
```

after that, the print button works normally. i don't think it's a permissions issue, as unsaved documents created with my user account do the same thing.

---

### Post by Seedsta on 2008-10-09
it has to do with the permissions to oowriter, not the file you create or save!!!  You need to add your user to the permissions for oowriter, which means your user needs to be a part of a group.  you can create a new group or add your self to the users group as you did before, you can also assign rights per-user.  Once you are a part of the group, use the afformentioned tutorial to add the group you are a part of to the oowriter file, or simply add just your user to the oowriter file, and give that group or user execute rights.

What is happening is that oowriter is not able to open when you send a job because your user does not have rights to execute the file oowriter, but when you open it with root, it is now open and thus usable by Open Office under your user name.  

I am trying to give you a distilled explanation, but it is kind of hard for me, it took me a really really long time to start understanding this stuff and get good at using, so please do not feel bad or get frustrated, just tell me what you do not understand.

P.S.  scripts are very helpful for frequently used command sequences, if you use the same command sequence a whole lot you can type "script <filename>" and proceed to type the commands as normal, when you are done you type exit, and the script ends and saves to a file named what ever you called it in the directory you where in when you started it.  You can also just type the commands in a text editor and save them that way.

If you are not familiar with [www.google.com/linux](www.google.com/linux) you should become so, that search engine comes up with only linux related stuff, so if you type scripting in, or file permissions it is going to give you only stuff for linux... it is very helpful.

-let me know if you need further direction
Seedsta

---

### Post by badfish69 on 2008-10-31
Damndest thing. I never did anything to it, and now it started working again.

---

