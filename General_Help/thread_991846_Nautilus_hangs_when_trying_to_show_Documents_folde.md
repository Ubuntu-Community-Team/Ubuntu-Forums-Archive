---
title: "Nautilus hangs when trying to show Documents folder"
date: 2008-11-24
forum: General Help
---

### Post by cornellg on 2008-11-24
Hi there,

I've run into a problem with my filebrowser (Nautilus 2.22.5.1). I made a new floder inside my Documents folder and dragged a single file into it. Nautilus choked somehow. I had to force quit it and after restarting it, it now hangs everytime I try to view the contents of the Documents folder. It doesn't show any contents and the window fades to grey immediately.

Renaming from the Documents folder got it to show the contents once, but it choked as soon as I clicked the new folder. This trick only worked once.

I'm running ubuntu 8.04, but I can remember encoutering this problem on 7.04 als well. I then used a terminal to move the contents of the faulty folder to another folder and as far as I can remember, that worked. 

Can anybody tell me what the problem is and how to slove it? 

Thanks,
Cornell

---

### Post by drs305 on 2008-11-24
There have been a few problems recently in which nautilus tries to open a folder/file with the incorrect app. Normally it is associated with trying to access the folder/file via Places.

The solution to that problem may work in this case to, redirecting nautilus to open a folder with the appropriate application. Try opening nautilus, right click on any folder, select "Open with other application" and select "file browser".  Then see if your folder opens normally.

If that doesn't work, open a terminal and try to see the contents of the 'documents' folder. I deleted mine as soon as I installed Intrepid, so I am not sure of the exact capitalization of the folder, but make the appropriate changes, run the following and note any errors:
```

ls ~/Desktop/Documents # ensure the name and capitalization are correct in this line.

```

---

### Post by cornellg on 2008-11-24
> 
The solution to that problem may work in this case to, redirecting nautilus to open a folder with the appropriate application. Try opening nautilus, right click on any folder, select "Open with other application" and select "file browser". Then see if your folder opens normally.

That didn't work. But I did forget to mention that I can navigate the folders normally using a terminal - no problem there.

---

### Post by kuxpac383 on 2008-11-30
I'm having the same problem, except with my pictures folder.  I tried the same solution that was given, but like you it didn't work.  Anyone have anything else to add?

---

### Post by drs305 on 2008-11-30
Try this variation: Right click on the Home folder, Open with OR Open with other application, Open Folder.

---

### Post by Connyank on 2008-12-01
while sifting through the forum, would seem that this is the only solution posed, least so far.  But the symptoms are getting closer to mine - nautilus locking up.  I originally though it was with folders containing a large number of files but seems that isn't necessary.
I'm a noob but I feel this is nvidia related - am on page 89 of 95 pages on my search results (going backwards).
whew
jg

---

### Post by cornellg on 2008-12-01
I seem to have solved my problem, but in a less than satisfactory way. First it got worse - my home folder itself started to lock up after I tried to create a new folder in it and drag and drop a few items there. That is seriously annoying, because if you force quit Nautilus it automaticaly opens a new browser window which of course just gets right as stuck as the first one.

Anyway, in the past I've had some weird problems with Gimp due to a partition being almost full, so I moved a large folder (more than 10 GB) to another partition and Nautilus started working again. Moved it back and it choked, moved it away again and everything worked fine. 

Now the annoying part about this is that my home folder had about 10 GB free before getting stuck and the trash was empty, so no disk space being used up by hidden files. It doesn't make any sense to me, I guess now I can use Nautilus but I have to live in fear of having less than 30 GB free disk space...

By the way, just before it started working again, Nautilus showed me this error message:
> Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

Hope this helps someone.

---

### Post by Blancmange on 2010-06-25
I'm having this problem too, with Nautilus 2.22.51 on Ubuntu 8.04. Nautilus hangs as soon as I navigate to /home/blancmange/Photos/SCA/. The parent and subdirectories work fine.

It's not a bug I can report, since I can't expect the programmers to have a SCA folder filled with other folders which are in turn filled with images of people hitting each other with sticks and being awfully polite about it, and there's a stupid number of similar bug reports about it that are going nowhere.

I've now pretty much given up on reporting Linux bugs, it's always a years-long fight with the brittle ego of some programmers that consumes far more time and effort than the badly written code did.

---

