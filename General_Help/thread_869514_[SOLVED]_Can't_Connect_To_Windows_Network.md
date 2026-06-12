---
title: "[SOLVED] Can't Connect To Windows Network"
date: 2008-07-24
forum: General Help
---

### Post by ShinHadoken on 2008-07-24
Ok, running Hardy here, and all of a sudden, I can't access shared folders and files on Windows networks. I go to Places > Network, and I get this:

[IMG]http://i118.photobucket.com/albums/o120/ShinHadoken/Network-FileBrowser.png[/IMG]

But when I go into "Windows Network",it shows up empty. Any ideas? Do I need to reinstall Samba? Or is it a network thing that I can't control?

Thanks in advance for the help!

SH

---

### Post by ajmorris on 2008-07-24
hi there,
what version of windows is the machine running that you are trying to access? If it is vista, the version of samba that has properly working support for vista, is only in beta. Also, if you know the ip address of the machine in question, or the 'computer name', you can put smb://<ip address> in the Navigation bar of your nautilus to access the shared files. If this doesnt work, you could try opening up a terminal, and entering in:
```
smbclient -U <username> \\\\<ip address>\\<share name>
``` to see what error you get.
 
AJ

---

### Post by cariboo on 2008-07-24
Can you ping the other computers on your network?

Jim

---

### Post by ShinHadoken on 2008-07-24
Yes, I can. I'm sorry, I meant to mention that. I can ping other network computers.

---

### Post by geeth on 2008-07-24
I have this same issue on both my Hardy machines.

What I have done, is set them up as bookmarks through

Places >Connect to Server
Select windows share and enter the ip address
tick the bookmark box and name it
Then under Places click on the name in bookmars and you should get the share open.

Thats how I have worked around it, but for an actual fix I'm not to sure, I have had this issue for about 3 weeks after an update.

---

### Post by ShinHadoken on 2008-07-25
Ok, thanks, I'll try that, and if anyone from the Canonical & Ubuntu staff is reading this, please send out a patch!

SH

---

### Post by bholliday72 on 2008-07-25
Yes, in windows, i mapped them as network drives under my MSHOME network.  I had no problems with accessing the shared files or any other network issue, for that matter.  Of course, I had my network set up before installing ubuntu.

---

### Post by ShinHadoken on 2008-07-27
> **geeth said:**
> I have this same issue on both my Hardy machines.

What I have done, is set them up as bookmarks through

Places >Connect to Server
Select windows share and enter the ip address
tick the bookmark box and name it
Then under Places click on the name in bookmars and you should get the share open.

Thats how I have worked around it, but for an actual fix I'm not to sure, I have had this issue for about 3 weeks after an update.
Thanks again to Geeth, for providing me with a workaround. It works, so I can share files. However, I still can't print. I reported this on Launchpad, so maybe we'll get results. Anyone, Ubuntu Dev or other wise, who has an answer, please post it here! I would be very thankful! =D

SH

---

### Post by haydemon on 2008-07-30
> **bholliday72 said:**
> Yes, in windows, i mapped them as network drives under my MSHOME network.  I had no problems with accessing the shared files or any other network issue, for that matter.  Of course, I had my network set up before installing ubuntu.
I'm having the same problem, can't see any of my files on the Windows network. How do I do the qyoted thing above?

---

### Post by ShinHadoken on 2008-07-30
> **geeth said:**
> I have this same issue on both my Hardy machines.
 
What I have done, is set them up as bookmarks through
 
Places >Connect to Server
Select windows share and enter the ip address
tick the bookmark box and name it
Then under Places click on the name in bookmars and you should get the share open.
 
Thats how I have worked around it, but for an actual fix I'm not to sure, I have had this issue for about 3 weeks after an update.
Here's what I did Haydemon, and I can access shared files just fine.
 
**NOTE: IF ANY OF YOU ARE HAVING THE SAME PROBLEM (WHICH SOME OF YOU OBVIOUSLY ARE) PLEASE GO TO [LAUNCHPAD.NET]("http://www.launchpad.net/") AND REPORT THIS BUG!!! I HAVE ALREADY STARTED A BUG REPORT, SO IF YOU WOULD FIND IT, AND BASICALLY SAY YOU'VE BEEN HAVING THE SAME PROBLEM, IT MIGHT GET THIS FIXED FASTER!!! THANK YOU VERY MUCH, UBUNTU COMMUNITY!**
 
Seriously, thank you for your help so far, and your help to come!
 
SH

---

### Post by haydemon on 2008-08-01
> **ShinHadoken said:**
> Here's what I did Haydemon, and I can access shared files just fine.
 
Tried it, didn't work. Still an empty shell. I'll add to the bug report. Thanks anyway. (BTW, the only work-around--if one can call it that--that I've done was to copy all my files from the network into a flash drive and use them that way. Not the best solution, but a solution after all. :()

---

### Post by ShinHadoken on 2008-08-01
The first time I did it, I had an empty shell too. But I went back to it later (probably after a reboot), and it worked.

---

