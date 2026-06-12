---
title: "Floppy Automount issues"
date: 2005-04-29
forum: Hardware &amp; Laptops
---

### Post by sancho on 2005-04-29
Hey.  
Here is my problem:

I can mount and unmount floppies from the terminal using 
sudo mount /dev/fd0 /media/floppy 
and 
sudo umount /dev/fd0
without any problems or error messages.   

However if i try to use KDE (kubuntu) to do the same task it does not work properly. 
Konqueror > media:/ > double click Floppy.    
this sucessfully mounts the drive and it can be accessed in konqueror and shows up in mtab. 
however: Konquer>media:/>right click floppy unmount doesn't fully do its job.   
The floppy gets physically unmounted, i hear it tick a way a bit and its entry is gone from mtab, but KDE still thinks it is mounted (the green arrow is still there). No errors related to floppys are shown in /var/log/mesages either.   But since KDE does not think it is unmounted, when i put in a new disk and double click the floppy drive i get either a blank listing of files in konqueror or the listing of files that were on the floppy that i just removed.  In other words since KDE never thought it was unmounted it doesn't even attempt to read/mount the new floppy upon insertion.  

Whats interesting about this, to me anyhow, is that i have tried a USB floppy drive and it works flawlessly.  Also optical drives and pen drives work fine using the same procedures under KDE.  

Any suggestions?  Or anybody having the same problem?

only thing i can think of is a possible problem with HAL,udev,and hotplug.  

PS: The only reason 'do it from command line' is not acceptable is because i am working on a deployment of kubuntu for our end users.  I work in a computer store in a very small (redneck) town and i would like to offer the people here an alternative to using windows.  Some of these people can hardly spell computer (seriously), so simplicity is a necessity.

---

### Post by sancho on 2005-05-02
bump.  

i booted off a Mepis CD and had no problems working with the floppy from the GUI.  Only difference i saw was that mepis was using kde 3.3 and the Kubuntu box i'm playing with is using KDE 3.4.  If i remember right that came about from an upgrade.   I'm going to try a fresh install of Kubutu and see what happens.   I'm also going to try an install of Ubuntu to see if its just a KDE problem in general.  

Has anybody had similar problems?  Or is this a known bug/missing feature?  
I honestly don't know, i haven't used a floppy in years.  This is my actual first time using a floppy in linux.  Never saw a point, but now i have learn so my customers will be happy.   

Also, while digging through the forums i saw somebody post something about a gnome vfs mtools application of some sort.  Something like a floppy deamon that would allow people to use a floppy in linux in a similar way that they do in windows.  No mounting/unmounting to worry about.  Anybody have a link to that project? I can't remember what its called, and i can't find it in the forums again.  If you ever have messed with that thing tell me how it went for you.

---

### Post by sancho on 2005-05-02
alright.  guess i was wrong.  The default install of Kubuntu comes with KDE 3.4.   The update i was thinking of was just kdelibs.   Either way though, i can not get a default install of kubuntu to work with standard floppies properly from the GUI. 

I'm going to try a few other things and then install ubuntu to see if its just a KDE problem.

---

### Post by sancho on 2005-05-02
Ok just tested it with Ubuntu and it works fine.   

All this testing was on the same machine, so i know its not a hardware problem.  

I guess it must be a problem with KDE 3.4 and dbus or something.   

Any suggestions would be greatly appreciated.

---

### Post by Lovejoy on 2005-05-06
Hey Sancho,

I'm having exactly the same problem! I'm also from a redneck town and spell computur that way. I installed Kubuntu because I like kde, but that may change. Anyway, I tried to use a knoppix cd (which uses kde) I have to get the work done, and guess what it had the same problems. I don't know what the answer is, but for the time being I'll go into shell and mount and unmount as you said you did. Thanks!

Lovejoy

---

### Post by sancho on 2005-05-09
Found a work around.  

I learned something new the other day, KDE 3.4 (and older versions i belive) support mtools directly.  I guess its like the saying goes, you learn something new everyday, i was never aware KDE worked with mtools in that way.  I guess i never cared about floppies so i never learned about them under linux.  

Anyhow here is what i did.  

Kynaptic > install mtools.  
Then in konqueror you can access your floppy without mounting/unmounting it using "floppy:/" in the address bar.  

Then to make it simpler for the end user i created an icon "Link to URL" by right clicking on the desktop and putting the URL as "floppy:/".     Now our users can work with floppies fine if they use the icon on the desktop.  However if they use the 'storage media' under konqueror it will still get messed up.  

Next problem:  making floppies easy to work with under Open Office.  Any suggestions?

---

