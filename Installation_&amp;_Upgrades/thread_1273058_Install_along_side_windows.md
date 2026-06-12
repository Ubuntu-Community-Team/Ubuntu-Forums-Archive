---
title: "Install along side windows"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by Kennethfaria on 2009-09-23
Hey, haven't been here for a while but i recently got a new laptop and need help on how to properly setup the HDD.

Its a 320GB thats going to need to run Windows 7 64 and Ubuntu 9.04 32.

Ill be using Ubuntu 70% and windows only for things requiring AutoCad and similar applications.  What i want to be able to do is seamlessly integrate my windows files and ubuntu files so that that i dont have to go hunting around for free space.

I was thinking, 

Windows 7 = 50GB
Ubuntu = 50GB
the rest would be a universal space where Win7 and Ubuntu would both go FIRST to save documents.

Is this possible? Or is it best the have WIndows 7 installed first, then have a millions Links in Ubuntu? 

And what is an appropriate size for each installation.

I realize that there are probably a million other threads asking the same time, so if you guys get direct me to those that would be great.

Thanks in advance!

---

### Post by mikewhatever on 2009-09-23
What you want is possible, but you lost me with 'a millions Links in Ubuntu'. The sizes you suggested are reasonable. What else do you want to know?

---

### Post by QIII on 2009-09-23
The "million links" thing boggled me, too.

Just a question...

Why run 32 bit Jaunty on a 64 bit machine?  Just asking.

---

### Post by jammen33 on 2009-09-23
One thing you could do is to make the third partition as ntfs and have windows7 mount it to \users\username
and in linux have it mount to /home/username
it would be a little tricky but then all of your document folders like music and pics will be in both

---

### Post by Kennethfaria on 2009-09-23
Why 32 bit on 64?  I don't have the 64 disk haha.  But i suppose i can get it if I will make a significant difference.

The links part:

When you right click a folder you can click, Make link. Its basically a shortcut right?  Anyway, I'd plan on just having a link to my documents/music etc. so whenever i have to save something I'd go back to my windows partition rather than the ubuntu one, just to save things.  But this would include mounting that driver every start up and in previous experiences (on my t42) sometimes mounting did not work 100% of the time so I'm not sure about the reliability of this "method"

Thanks!

---

### Post by gadolinio on 2009-09-24
First of all: sorry for the length of this post, but i think it can help you.
    [LEFT][/LEFT]
    [LEFT]&#65279;Regarding the always-having-to-mount-the-partition issue: install disk-manager. I think it can be found in synaptic, or [http://packages.ubuntu.com/intrepid/disk-manager](http://packages.ubuntu.com/intrepid/disk-manager) (intrepid package; don't know if will work in jaunty). Or [http://disk-manager.softonic.com/linux](http://disk-manager.softonic.com/linux). Otherwise google it and you'll find their website.[/LEFT]
    You can set the partitions to be automatically mounted at startup, so you'll never need to do it manually every time you turn the pc on. I've been using it for some months, and NEVER had any problem. It's like in windows, where you don't know what "having to mount a partition" means.
    
    I did what you want once, experimentally (cause i seem to like having things copied in many places, so i have different folders in different HDs for win and ubuntu). In windows, you can set your users folder ("my documents") to be in another partition, that would be the one for data storage (must be ntfs as far as I know, or windows won't see it). Right click the MyDocuments icon, click Properties, and navigate the tabs... in one of them you'll see the current path of the folder (C:\documents and settings\user\my documents or stg like that). Put the path of the folder you should have previously created for this purpose in the storage partition. Check that when you save something in MyDocuments-my music-etc, it is actually inside the new folder.
    Then boot with ubuntu, and go to system--administration--users and groups. Click "unlock", enter your password when you're asked for it. You can now create a new user or edit the current one. I dod the second thing, as i was just experimenting. You could do the same in order not to risk anything (and you keep the first user, just in case... you can still move all the documents to the new one and you won't waste disk space). So suppose you add a user; go to the "advanced" tab. There you can set that user's personal folder to the one you created when in windows. As it will be in an ntfs partition, which is not the system partition, i think you'll need to have it always mounted from startup (when i did this i already had disk-manager taking care of detecting partitions automatically).
    Well, i think that's it. 
    
    Now, observations:
    ·desktop: this folder is called the same in windows and in ubuntu, so when you place a file in one desktop, it will be there when you boot the other OS.
    
    ·documents folder: in windows it is called "MY documents", while in ubuntu just "documents", so by default you'll have 2. But you can obviously delete one of them. If you delete the win one, do the thing you did before to tell windows the path for "my documents" and set it to be "documents" created by ubuntu. If you delete the one of ubuntu, just make a new bookmark to MyDocuments in the file navigator and use that. Or you might well create a new one called "lalala" and make both of them use it.
    
    ·ubuntu applications and settings: your user's configurations are stored in the folders whose name start with a dot, and those will be in tat same folder used from windows. As this could be somewhat annoying, i'd make a sub-folder to be used as "my documents", so that when you enter there, you have ubuntu's "dot" folders some levels up in the tree and they don't bother. In ubuntu use a bookmark for that too.
    
    Well i hope i haven't bored you, or at least you find this useful (if both, better XD )
    Reply for any questions!

---

### Post by Kennethfaria on 2009-09-24
Thanks for that, I might just have to look more into it.

Another thing i thought of was doing running either windows 7 or XP in VMWare or whichever is best at running virtual OS's.  

My laptop specs:
P8400
GeForce 9800M GTS
4 GB DDR2

Do you guys think AutoCAD 2010 will work in VMWare?

I really want to stay inside Ubuntu and just run Windows for stuff that i can't get working on Ubuntu.

---

