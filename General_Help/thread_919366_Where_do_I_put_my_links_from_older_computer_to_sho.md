---
title: "Where do I put my links from older computer to show up in my new favorites in Opera?"
date: 2008-09-13
forum: General Help
---

### Post by PsychedelicWonders on 2008-09-13
Alright I copied all of my old favorites and links from my old computer and currently have them on a usb drive.

Does anyone know what folder exactly they go in in Opera so that they will show up under my favorites tab in Opera?

---

### Post by Whiffle on 2008-09-13
I'd just import them, 

Bookmarks > Manage Bookmarks > File > Import Opera Bookmarks

then just browse to the ones you backed up.

---

### Post by PsychedelicWonders on 2008-09-13
alright here is the thing, I have hundreds of links and they are all in different files.

So I need to be able to import all of the folders I made to save the links in when I was using Internet Explorer.

I tried to do it your way, and when I tried to import and I opened a folder, there wasnt anything to import.

Regardless, that doesnt seem to allow me to do them all at once, which is what I need to do otherwise it will take me 10 years to do them one by one.

I dragged and dropped them to a usb drive, then dragged and dropped them onto my Ubuntu desktop and they all seemed to save in a .url

Perhaps Opera cant regonnize that file type?

But how can I import my entire folder of specialty folders I have created over the years?

---

### Post by Whiffle on 2008-09-13
On my copy there is one to do Internet Explorer favorites, I'd try that.  Beyond that, I'm not sure, haven't used IE in quite some time.

---

### Post by PsychedelicWonders on 2008-09-13
Alright I see where you meant and the links now at least show up, but now I need to import an entire folder of links, just not individual ones.

So how do I do this?

There is a "Lock" icon on the shortcut on my desktop.

Is that going to affect things?

---

### Post by PsychedelicWonders on 2008-09-14
anyone have any idea?

---

### Post by Whiffle on 2008-09-14
Yeah the lock icon shows that you don't have permissions to look at that file as a non-root user.  You should be able to change that by doing:

```

sudo chown -R <yourusername>:<yourusername> /path/to/folder/on/your/desktop

```

in my case it would be


sudo chown -R andy:andy /home/andy/Desktop/folder

---

### Post by PsychedelicWonders on 2008-09-14
It seems I have been able to import them into Opera, so that is good.

But I dont like this lock feature.

If I run that code, will that just work for this particular time, or will that forever change my settings to allow me to be root-user? (which is what I want, but I thought I've already done this?)

---

### Post by Whiffle on 2008-09-14
That will just change the permissions for that one file/directory, so that they can be read by the regular user.  Chances are when you copied them over the permissions got written down as owned by root, so you couldn't access them as a regular user.  


As far as running as root all the time, don't do it.  Once you get used to dealing with permissions its like they're not even there, and you'll be better off for it.

---

### Post by PsychedelicWonders on 2008-09-14
Alright, well all of my links seemed to have imported properly into Opera, so I suppose Opera makes me root in order to import them?

I'm good for life now?

I can delete my the icon on my desktop and dont need to unlock it?

---

### Post by PsychedelicWonders on 2008-09-14
alright, seems I need to make myself root in order to delete this file now, I've tried this....

psychedelicwonders@JohnnyScience:~$ sudo chown -R johnnyscience:johnnyscience /home/psychedelicwonders/Desktop/favorites
[sudo] password for psychedelicwonders: 
chown: invalid user: `johnnyscience:johnnyscience'
psychedelicwonders@JohnnyScience:~$ sudo chown -R johnnyscience:johnnyscience /home/psychedelicwonders/Desktop/favorites
chown: invalid user: `johnnyscience:johnnyscience'
psychedelicwonders@JohnnyScience:~$ sudo chown -R psychedelicwonders:psychedelicwonders /home/psychedelicwonders/Desktop/favorites
chown: cannot access `/home/psychedelicwonders/Desktop/favorites': No such file or directory
psychedelicwonders@JohnnyScience:~$ 


still not getting it to work?

What could I be doing wrong?  I think I have two types of names registered for Ubuntu, Psychedelicwonders & Johnny Science, but I dont know which one is which.

I know I log into Ubuntu with Psychedelicwonders

?

---

### Post by PsychedelicWonders on 2008-09-14
It seems I have a lock on the icon on my desktop, and also a lock on my USB drive, not allowing me to delete any of them.

We are working on getting the desktop icon cleared up, but will the icon on my usb drive allow me to delete it once I run this code in the terminal?

---

### Post by Whiffle on 2008-09-15
it should be
```

sudo chown -R psychedelicwonders:psychedelicwonders ~/Desktop/favorites

```

could you post the output of :
```

ls -l ~/Desktop

```

---

### Post by PsychedelicWonders on 2008-09-15
> **Whiffle said:**
> it should be
```

sudo chown -R psychedelicwonders:psychedelicwonders ~/Desktop/favorites

```

could you post the output of :
```

ls -l ~/Desktop

```


Do you want me to run -1 ~/desktop first?

Once I run the other code, it will make me the root user for that favorites file and allow me to delete it, but how will i make myself the root user for the same original file that is still stuck on my USB drive with a lock on it?

---

### Post by Elfy on 2008-09-16
If you want to just delete the file(s) from the desktop

```
sudo rm -r ~/Desktop/nameoffolder
```

To do the same on the usb change the path to suit

```
sudo rm -r /path/to/usb/and/file/location
```

So you are aware the l is a L not a 1 in  > ls -l ~/Desktop

---

### Post by PsychedelicWonders on 2008-09-16
psychedelicwonders@JohnnyScience:~$ sudo rm -r ~/Desktop/favorites
[sudo] password for psychedelicwonders: 
rm: cannot remove `/home/psychedelicwonders/Desktop/favorites': No such file or directory
psychedelicwonders@JohnnyScience:~$ 


Whats wrong?

---

### Post by Elfy on 2008-09-16
Is the file/directory actually there? Run ```
ls -l ~/Desktop
``` please

---

