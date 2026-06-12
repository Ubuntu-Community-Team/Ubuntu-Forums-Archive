---
title: "How to change /tmp directory? (not in fstab)"
date: 2008-10-12
forum: General Help
---

### Post by kung fu buntu on 2008-10-12
I'm having problems with available disk space so I need to change the location of my /tmp directory.
One of the reasons is that K3B seems to need 4GB of free space to verify the burn operation.


If I had my /tmp in fstab it would be easy, but I don't, so I don't know how can I do it.
I've tried booting as single user and making a link, but I got a "device is busy" error.


Any ideas?
Thanks

---

### Post by bodhi.zazen on 2008-10-12
change the location in what way ?

did you make a new partition ?

Or do you have a new directory ?

If you are using a new directory, use mount --bind

mount --bind /new /tmp

add a line to fstab

```
/new  /tmp  none bind
```

You need to set the proper permissions of /tmp

```
sudo chown root.root /tmp[FONT=monospace]
[/FONT]sudo chmod 1777 /tmp
```

---

### Post by Kissell on 2008-12-26
This fixed mine too!

What I meant to do, was "chmod 770 folder_name -R" to a folder I created at /

What I did (after messing with windows machines all night) was "chmod 770 folder_name *" oops!!!  that changed the folder permissions to all the folders in the root of the OS...  where's my undo button?  

I thought I had changed everything back, but didn't know about the 1777 trick for /tmp.  Gnome wouldn't load up a GUI interface for any user without doing that.  Thanks!  

I learned something today, unfortunately it was about how to set permissions on tmp and not about reading whats typed in / before hitting ENTER.

---

### Post by lakitu on 2011-08-11
i just did the above suggestion, & it nuked my ubuntu. i had to live cd gksu gedit my fstab back to before that line -

it kind of seems to be working, but i'm wondering (in ubuntu 10.10) *what do i need to do to restore from doing the above commands* - did you mean /new instead of /tmp zazen? 

is there anything i need to undo? i undid the fstab line.


please pardon any incorrect etc info AS i have aphasia - sorrys


EDIT: for one my file manager won't open - kind of a big problem.

---

