---
title: "Strange permissions issue w/external hd"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by osdesk on 2007-05-10
I have a Western Digital external 160 gig hard drive which works perfectly (out of the box) w/Fiesty Fawn.  

However,  the issue I'm having is when I'm creating/editing files with desktop apps such as BlueFish....the files created/edited are getting permissions set by the system and when I upload them via ftp I have to reset the permissions for viewers of my sites to see them and not get the "you're not authorised to view this page" error message.

With all that said, finally my question: Is there a way that I can tell Ubuntu to not set permissions on files that are being created in an external hd?  A command in terminal or something?   (I'm still very new to Ubuntu).  Thank you in advance for any assistance.  

Have a great day.  :biggrin:

---

### Post by kidders on 2007-05-11
Hi there,

I'm afraid the answer to your question is no. Ownership and permissions are fundamental to all modern filesystems, and the Linux operating system itself. Having said that, there are two things worth noting:

[LIST=1]
[*]Not all filesystem support ownership/permissions. FAT filesystems are good examples. Even so, Linux cannot function without being given some idea of who should be entitled to do what, so "fake" permissions are invented and enforced for the duration of a single mount (even though they are not actually stored anywhere).
[*]Certain filesystems have support for "ignoring" permissions stored on the filesystems themselves, allowing them to be treated more or less as though they had no permissions support at all. Having said that, the idea of a file somehow having "no permissions" has no meaning.
[/LIST]

Something you *do* have control of is what a newly created file's default ownership & permissions *are* ... quite detailed control, in fact. You may be interested in tweaking these. One basic example of how to perform simple manipulations is called a "umask".

Of specific interest in the case of removable devices is the way in which file ownership is stored. On virtually all filesystems, a file's owners are physically stored as numbers of some sort.
[LIST]
[*]In Linux, these are typically in the 1000-2000 range, although they can be pretty much any relatively small positive integer.
[*]On MacOS, UIDs are most often nearer 500.
[*]On Windows, they are usually far longer beasts (ie _U_UIDs) ... which has certain advantages.
[/LIST]
The reason I mention this is that who user 1075, for instance, happens to be (assuming he even exists) is platform-dependent, so if you create a file using one PC (where your UID is 1075), you won't necessarily be able to access it using a second PC (where your UID might be 1001). Worse still, user 1075 might be you on one machine, and your little sister on another one, leading to an apparent transfer of ownership of your files!

It's worth mentioning that, for the mostpart, the main reason Linux users (particularly former Windows junkies) encounter problems accessing files is the difference in the default policy in place on both platforms. While Windows likes to err on the side of not irritating people, Linux's default position is that nobody has access to anything at all, unless a specific instruction exists that forces it to do otherwise. I don't suppose there is any question about which is better ... but that doesn't make it any less annoying, when you're not accustomed to it!

Anyhow, sorry for rambling ... I hope that little summary is of some help. Essentially, I'm not quite sure what aspect of permissions management is causing your problem (or where it might be), so I figured I'd cover all the bases hehe!

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by osdesk on 2007-05-13
Thank you very much for the detailed response...it has been very helpful in understanding what might be going on with this.

I did find a "quick fix" solution...a 1 gig storage stick.  I simply need something to work from Linux to Windows and have a quick way to access the files I created on Windows, accessing them later on Ubuntu.  The "storage stick" has saved me hours of work having to reset permissions everytime I want to upload a file via FTP that was created on one OS or another.

Again, thank you very much for your thorough response.

---

### Post by kidders on 2007-05-13
Curiously enough, there's no real difference between USB sticks and internal hard disks. If you can master permissions management with one, you can do it with the other. :-)

---

### Post by osdesk on 2007-05-13
> **kidders said:**
> Curiously enough, there's no real difference between USB sticks and internal hard disks. If you can master permissions management with one, you can do it with the other. :-)

Hmmm.  Strangely enough, I just plugged the Flash Drive in (From SanDisk) and started saving and editing files, moved back and forth from Windows to Linux and didn't have to do any permissions settings.

---

### Post by kidders on 2007-05-13
Yep. Depending on what you want, default permissions control configurations can be quite suitable. :-) You only have to fiddle around when they're not quite what you're looking for.

---

