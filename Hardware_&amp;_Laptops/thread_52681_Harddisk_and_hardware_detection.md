---
title: "Harddisk and hardware detection"
date: 2005-07-28
forum: Hardware &amp; Laptops
---

### Post by bootsman on 2005-07-28
Today I decided to remove Windows and install Ubuntu. I've been trying out alot of new things and I've ran into two problems I can't figure out.

I've got 2 harddisks and on hda I've installed Ubuntu and on hdb I've got an NTFS partition with all my data files. Is there a way to access that?

My second problem is the fact that there are so many 'Unknown' devices in my Device Manager. Most of the things I've used today work normally, such as my keyboard, mouse, sound, network, etc. But still I find it odd. Is there anything I can do about it or should I just leave it the way it is?

---

### Post by dave9191 on 2005-07-28
Hey, 

First place to look for stuff is ubuntuguide.org, and check the wiki. 

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

and below that is how to make it mount automatically. Just use /dev/hdb1 instead of hda :)

As for ther hardware, if it all works then leave it as it is. If a piece of hardware doesnt work, then look up if there is a solution for it. 

Dave

---

### Post by Sam on 2005-07-28
I have exactly the same in my device manager. But if you open the nodes, there are the good elements.

---

### Post by bootsman on 2005-07-29
[QUOTE=dave9191]Hey, 

First place to look for stuff is ubuntuguide.org, and check the wiki. 

[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

and below that is how to make it mount automatically. Just use /dev/hdb1 instead of hda :)

As for ther hardware, if it all works then leave it as it is. If a piece of hardware doesnt work, then look up if there is a solution for it. 

Dave[/QUOTE]
 Thanks alot. It worked nicely. As for the Device Manager. When I open the nodes most are good elements, but not all of them.

---

