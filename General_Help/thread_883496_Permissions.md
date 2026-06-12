---
title: "Permissions"
date: 2008-08-08
forum: General Help
---

### Post by Justin Case on 2008-08-08
I recently installed Hardy. I transferred all my backup data from my old system from a cd to the new system.  There are a couple folders that I decided I didn't want. I was able to delete them, but they won't delete from the Trash bin. When I try to delete I get this message: There was an error deleting 2PayZeroInHeatingBills.aspx.html.   Under More Details I get this:  Error removing file: Permission denied.

So I open the permissions in the folder, but it won't let me change permissions. I get this message: Sorry, couldn't change the permissions of Energy Efficiency: Operation not supported by backend

How do I get rid of these folders?  Why can't I change permissions? I can on just about every other folder or file. 

Any insight would be great.

Thanks.

---

### Post by the_hardy_kid on 2008-08-08
Go to terminal and put in
```
gksu nautilus
```
then put in "trash:///" (without quotes, of course) and delete them like that.

---

### Post by iaculallad on 2008-08-08
Or using your terminal:

```
sudo rm -rf /home/your_user_name/.local/share/Trash/*
```

---

### Post by Justin Case on 2008-08-08
Well that didn't work guys. I tried both ways.  Here is the terminal output:


justin@CentralCommand:~$ gksu nautilus trash:/// 
Initializing nautilus-share extension 

** (nautilus:7438): WARNING **: Unable to add monitor: Operation not supported 
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS 
--- Hash table keys for warning below: 
--> trash:/// 

(nautilus:7438): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above) 

(nautilus:7438): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time 
seahorse nautilus module shutdown 
justin@CentralCommand:~$ 


Then I tried the other way, and I get this:

justin@CentralCommand:~$ sudo rm -rf /home/your_user_name/.local/share/Trash/* 
justin@CentralCommand:~$ 

There are folders within folders.  I cannot change the permissions on any of them. 

Nothing seems to be working. Any other ideas?

Much appreciated.  Thanks

Justin

---

### Post by sisco311 on 2008-08-08
```
sudo rm -rf /home/***your_user_name***/.local/share/Trash/*
```Did you replace ***your_user_name*** with your login name?

or try:[FONT=monospace]
[/FONT]```
sudo rm -rf ***~***/.local/share/Trash/*
```

---

### Post by Justin Case on 2008-08-08
I tried it this way as well:

justin@CentralCommand:~$ gksu nautilus 
Initializing nautilus-share extension 
trash:/// 

The root file browser came up but the Empty Trash option was grayed out. Deleting manually with the mouse didn't work either. 

Justin

---

### Post by sisco311 on 2008-08-08
> **Justin Case said:**
> I tried it this way as well:

justin@CentralCommand:~$ gksu nautilus 
Initializing nautilus-share extension 
trash:/// 

The root file browser came up but the Empty Trash option was grayed out. Deleting manually with the mouse didn't work either. 

Justin
it's grayed out becouse the root's trash is empty.
open nautilus in the user's trash:
```
gksu nautilus  ***~***/.local/share/Trash/
```

---

### Post by Justin Case on 2008-08-08
Sisco311, no justin is my user name.  BUT, it worked. I tried the first way you suggested, didn't see anything really happen in the terminal, but I didn't even check the trash.  Then I tried the second way, same thing, nothing seemed to happen.  But when I looked in the trash, the folders were gone.  One of those ways worked.

Thanks a lot Sisco311.  Thanks to everybody else also, all your suggestions were helpful.  These forums are great.

Justin

---

### Post by sisco311 on 2008-08-08
the rm command doesn't 
produce any output when the -f (force) flag is set.

to mark this thread as solved go to the Thread Tools
and select the appropriate option.

---

