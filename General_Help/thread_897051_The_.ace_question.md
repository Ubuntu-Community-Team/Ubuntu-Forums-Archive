---
title: "The .ace question"
date: 2008-08-21
forum: General Help
---

### Post by starving030 on 2008-08-21
I can't seem to find a clear answer on how to unpack a .ace file. I tried to download the latest version from winace.com. But I get this message when I go to install it:

[COLOR="Red"]/tmp/linunace25.tgz could not be saved, because you cannot change the contents of that folder.

Change the folder properties and try again, or try saving in a different location.[/COLOR]

I've seen a lot of hangups on this topic but no clear answer. I know there are a lot of knowledgeable folks on here. Can someone possibly put together some type of tutorial on this? 

Thanks guys

---

### Post by DirtDawg on 2008-08-21
Unace is in the repos. If I'm understanding you correctly, you're having a hard time with the unace you downloaded from the official site? Anyways, try
```
sudo apt-get install unace unace-nonfree
``` 
Then you should be able to extract the archive. Maybe by right-clicking, or maybe by opening a terminal and using something like, 'unace /path/to/archive.ace'.

---

### Post by starving030 on 2008-08-21
OK. I used that code and got this:

[COLOR="Red"]ts@dt:~$ sudo apt-get install unace unace-nonfree
[sudo] password for ts: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
unace is already the newest version.
unace-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ts@dt:~$ [/COLOR]

But when I go to open the .ace file I have on my desktop it wants to use "Archive Manager". Which just sits there saying:
[COLOR="Red"]
Reading archive, please wait..[/COLOR]

I waited about two hours and still the same thing. I don't think it's frozen cause the little box still moves back and forth.

---

### Post by DirtDawg on 2008-08-21
Try moving the .ace file to your home folder, then running the following command in a terminal
```
 unace ~/nameofarchive.ace
```
The '~/' bit is shorthand for the home folder. If something is wrong, it should return an error message you can copy/paste here. If nothing happens within, say, five minutes, then post back here (hopefully with an error message).

---

