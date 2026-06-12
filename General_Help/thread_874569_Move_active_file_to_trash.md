---
title: "Move active file to trash"
date: 2008-07-30
forum: General Help
---

### Post by janberk on 2008-07-30
Hi!

I wonder if I could create a command in Compiz that would move the active file to trash. 

For example, while reading a PDF file, I would love a shortcut like <Super>+D to move this file to trash without browsing back to the original position of the file using nautilus.

I know it looks like a bit dangerous when mis-used, danger of deleting binary files for example, but I think it would be very useful with careful use.

Thanks for any help,
Jan

EDIT: The situation is better described here:
[http://brainstorm.ubuntu.com/idea/11699/](http://brainstorm.ubuntu.com/idea/11699/)
.

---

### Post by diaa on 2008-07-30
As far as I know this is not possible currently, shortcuts, unless global, are handled by the application and I haven't seen anything like this, except in image viewers for example(gThumb), to implement it properly this particular shortcuts should be handled by the Desktop Environment and when it is pressed the DE should query the foreground application about the currently open file and then it can move it to trash and close the application.

I'm not sure how useful this is but generally I suggest posting it at [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by janberk on 2008-07-30
I usually deal with hudereds of PDF files in a day, most of them badly named. So it's usually very time consuming to find the active file in Nautilus to delete, usually I search the name.

Well, some image viewers do this job, I know, so I guess this should be possible for other applications also. What was in my mind was to create a command and associate it globally to a shortcut. 

I don't know the command to display the path of the file currently run by active window, say it is %activepathname, so a global shortcut running command "rm %activepathname" would simply do the job, but I slowly realize that it might not be that simple.

But instead, a global script appended to the right-click context menu might also work. When the window header is right clicked, options like "Move to Trash", "Move to Desktop" etc. might activate the relevant script. (Moreover, this commands can be appended to theme managers as buttons, like "minimize window", "close window".)

But either way a distinction is compulsory, regarding for which applications should these commands can be used. For example it's OK for Evince to have these commands when the window header is right-clicked, but for Firefox or Pidgin, this is completely unnecessary. Also there should be another distinction, as not to remove the binary file of the application that is running the file but the file itself.

Don't know really, I'm far from being an expert on Linux, Ubuntu or OSs in general, but I hope these might be some inspiration for knowledgeable people. I'll try [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/) also, thanks.

---

### Post by diaa on 2008-07-30
> **janberk said:**
> I usually deal with hudereds of PDF files in a day, most of them badly named. So it's usually very time consuming to find the active file in Nautilus to delete, usually I search the name.

Well, some image viewers do this job, I know, so I guess this should be possible for other applications also. What was in my mind was to create a command and associate it globally to a shortcut. 


It is possible but not needed by many and this is why it's not done, in this case I think that you need something custom since your need is only related to PDFs

are these PDF files usually in the same directory?
What about a delete dialog right after you close each one asking you whether to delete it or not?

---

### Post by hugmenot on 2008-07-30
There is no way for the window manager to determine what the "active file" is. There is an active window, but what is an "active file"? This concept sounds ill-defined.

Your best bet is to petition the Evince developers to add a "delete" function.
File an enhancement request at bugzilla.gnome.org.

---

### Post by janberk on 2008-07-30
> **diaa said:**
> 
are these PDF files usually in the same directory?
What about a delete dialog right after you close each one asking you whether to delete it or not?

No, they're not in the same folder necessarily. Although your suggestion looks like a nice solution, I think it would greatly reduce usability. I can foresee the frustration caused by clicking "NO" each time when there's no need for deletion.

---

### Post by diaa on 2008-07-30
> **janberk said:**
> No, they're not in the same folder necessarily. Although your suggestion looks like a nice solution, I think it would greatly reduce usability. I can foresee the frustration caused by clicking "NO" each time when there's no need for deletion.

This will be a special script that you run, it won't happen everytime you open a PDF.
so for example this will be a script that you run on a folder, the script will view all the PDFs in this folder(and probably its subfolders) in succession and will show a question dialog after each asking if you want to delete the previous file.

---

### Post by janberk on 2008-07-30
> **hugmenot said:**
> There is no way for the window manager to determine what the "active file" is. There is an active window, but what is an "active file"? This concept sounds ill-defined.

Well, I suspected that. But to give a clarification, active file is the current file displayed by the active window.

---

### Post by diaa on 2008-07-30
> **janberk said:**
> Well, I suspected that. But to give a clarification, active file is the current file displayed by the active window.

Actually it's possible theoretically but it requires modifying both the desktop environment and all the applications, which is practically very hard to do.

---

### Post by janberk on 2008-07-30
> **diaa said:**
> This will be a special script that you run, it won't happen everytime you open a PDF.
so for example this will be a script that you run on a folder, the script will view all the PDFs in this folder(and probably its subfolders) in succession and will show a question dialog after each asking if you want to delete the previous file.

Well I see. But this wouldn't be useful in my case. 

I deal with scientific articles. While reading a main article, I download the articles referenced by this article and see if they are useful. At some moment in the middle of the day, my desktop becomes full of badly named and mostly unuseful articles, most of which are still open. So, each time I need to delete an article, I map the usability of the article with its name and search for it on the desktop and delete it. This really slows down the pace. Or I don't know if I'm a spoiled guy :)!?

---

### Post by diaa on 2008-07-30
> **janberk said:**
> Well I see. But this wouldn't be useful in my case. 

I deal with scientific articles. While reading a main article, I download the articles referenced by this article and see if they are useful. At some moment in the middle of the day, my desktop becomes full of badly named and mostly unuseful articles, most of which are still open. So, each time I need to delete an article, I map the usability of the article with its name and search for it on the desktop and delete it. This really slows down the pace. Or I don't know if I'm a spoiled guy :)!?

well this is a very special case, I don't know how to help further, sorry.
Try to find a PDF viewer that allows deleting the currently open file.

---

### Post by janberk on 2008-08-01
Ubuntu Brainstorm link:

[http://brainstorm.ubuntu.com/idea/11699/](http://brainstorm.ubuntu.com/idea/11699/)

---

