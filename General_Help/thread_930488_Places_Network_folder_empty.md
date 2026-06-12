---
title: "Places Network folder empty"
date: 2008-09-26
forum: General Help
---

### Post by gimmejimmy on 2008-09-26
Hello, I've just recently installed Ubuntu for the first time.  I've gotten sharing between my XP and Ubuntu machines working.  I mounted the XP share to /mnt/black and all the files show up there when I use the file browser.  But when I click on Places->Network->Windows Network->HOME the BLACK folder isn't there.  Only the GRAY folder (share on Ubuntu machine) shows up.  Yesterday the problem was different, the BLACK folder was present but empty.  In both cases the folder was properly mounted because I could browse, open, and modify files in /mnt/black.  How do I fix this?  Thanks.

PS - How do you mark a thread as solved?

---

### Post by Bucky Ball on 2008-09-26
Thread Tools, top right.

In Ubuntu: right click the share folder (grey); Sharing Options
In Windoze: right click the share folder /partition (black); Sharing

Make sure they are in the same domain:

HOME (or whatever you like)

Hope this works. :)

---

### Post by gimmejimmy on 2008-09-26
Thanks for the reply.  The XP workgroup is HOME and I checked smb.conf and the workgroup is also HOME.  Could it be a upper/lowercase issue?  I know Windows isn't case sensitive so it should work.
Now it's back to yesterday's behavior where the "Windows shares on black" folder is visible but empty.  Again browsing to /mnt/black works perfectly.

---

### Post by Bucky Ball on 2008-09-26
What is actually supposed to be in the black folder? And yes, I would make the workgroup name exactly the same on both machines, including case.

---

### Post by gimmejimmy on 2008-09-26
Well, shouldn´t the contents of /mnt/black and Windows Network/HOME/BLACK be the same?  The GRAY folder contains the same files as the Ubuntu share so shouldn´t BLACK contain the Windows share files?

---

### Post by gimmejimmy on 2008-09-28
Help?

---

### Post by Bucky Ball on 2008-09-29
> **gimmejimmy said:**
> Well, shouldn´t the contents of /mnt/black and Windows Network/HOME/BLACK be the same?  The GRAY folder contains the same files as the Ubuntu share so shouldn´t BLACK contain the Windows share files?

I think I follow you, so that sounds right. Did you try setting up the share by right clicking and using 'sharing options' on the folders you want to share or you actually made mount points for them by the looks? The easiest way to do it, if this is what you are attempting, is that route. No need to create mount points and your Ubuntu folder should show up as a samba share on your Windoze box. You have put a file in the shared folder/partition on the Windoze box and it doesn't show up in the 'black' folder? Odd, as Windoze shared folders/partitions should mount automatically in Ubuntu. Or am I not getting this either; are you talking about two computers or the windoze partition on the same computer (which should show up with no manual mounting or sharing anyhow)?

---

### Post by gimmejimmy on 2008-09-30
Hi, there are two separate computers.  I've setup shared folders on each of them.  There is actually no problem opening/modifying files or folders within those shares.  From the Windows PC My Network Places shows "Shared on gray server (Samba)" and that is working perfectly.
> You have put a file in the shared folder/partition on the Windoze box and it doesn't show up in the 'black' folder? Odd, as Windoze shared folders/partitions should mount automatically in Ubuntu.
I followed this guide [https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") to mount the Windows shared folder.
On the Ubuntu PC if I click on Places then Network then Black it is empty.  However, I can access the files through /mnt/black.
Do you mean I should remove the line I added to fstab since Ubuntu will mount the share automatically anyway?  Thanks again.

PS - I could forget about the whole thing and just use /mnt/black but I'd like to understand the behavior and I'm a bit bothered why it's not working the way I think it should.

---

### Post by Bucky Ball on 2008-09-30
> **gimmejimmy said:**
> 
On the Ubuntu PC if I click on Places then Network then Black it is empty.  However, I can access the files through /mnt/black.



I wonder if you're auto-mounting a partition called 'black' that has nothing to do with the network. It would show up but yes, it would be empty.

> **gimmejimmy said:**
> 

Do you mean I should remove the line I added to fstab since Ubuntu will mount the share automatically anyway?  Thanks again.



When you go Places->Network, does it not have 'Windows Network' in there? Your 'black' folder should be in there. If not, that is odd because the ability to access your windoze box, and thus this function, should have installed with Hardy (smbfs).  :-k

Try this page:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

The smbfs client package is what I was thinking might be more appropriate, unless you really want to have the windoze folder mounted when you boot ubuntu (even when the windoze box is not on). If you went the other way, the windoze box would run as the server (which it is doing now) and ubuntu box the client (doesn't need the server software). At the moment, sounds like you are trying to create two servers and that may require a different approach, perhaps.

---

### Post by gimmejimmy on 2008-09-30
> When you go Places->Network, does it not have 'Windows Network' in there? Your 'black' folder should be in there.
Reading your post I had a breakthrough!  I realized the PC name is also "black".  So I typed in "smb://black/black" at the address bar and it worked!  Now, the question is, how do I get it to automatically show the black folder when I'm at "smb://black", it would be a pain to have to type it in at the address bar every time.

---

### Post by Bucky Ball on 2008-10-01
> **gimmejimmy said:**
> Reading your post I had a breakthrough!  I realized the PC name is also "black".  So I typed in "smb://black/black" at the address bar and it worked!  Now, the question is, how do I get it to automatically show the black folder when I'm at "smb://black", it would be a pain to have to type it in at the address bar every time.

Yep, /black/black sounds about right. Not sure of the correct command for fstab off the top of my head, but maybe just add another /black to the end of the line you set up for auto-mounting it. Maybe go back and check out the link you posted originally relating to this one more time, but it sounds like you are pretty close. As I say, if you get it showing up in ...

Places->Network->Windows Network->Black(windozebox)->black(windozeshare) 

...that might suit you. Not sure why you want this folder to show up when you boot ubuntu, even when the windoze machine is not on, but guess you have your reasons. :)

I would strongly advise you change the names of your shared folders to something like 'blackshare' 'greyshare' to avoid any more confusion. Then you know exactly what is showing up where.

---

### Post by gimmejimmy on 2008-10-01
I think I finally know how to solve this.  A recap:
1.  I have two PCs named Black and Gray.  Black is running XP while Gray is running Ubuntu.
2.  On the computer ¨Black¨ there is a shared folder also named ¨Black¨.
3.  I put a line in fstab to mount this folder to /mnt/black.
4.  There is no problem accessing the folder and its contents by browsing to /mnt/black.
5.  However, when I browse the network Windows Network->Home->Black the shared folder does not show up unless I type it in the address bar.

I believe this is because the login credentials on the two PCs are different.  If I create a new user on the Ubuntu PC with credentials that match a user on the XP PC the shared folder should show up on the network without me having to type it in.  Here´s the problem:  trying to create a new user then clicking Unlock and typing in my password returns
> Could not authenticate.  An unexpected error has occurred.
This is Windows-like behavior!

---

### Post by Bucky Ball on 2008-10-01
The security is for the machine the shared folder is coming from. Have you typed in your Ubuntu credentials (user, password etc) on Windoze? Login details don't matter, domain does.But you would be there I guess. System->Admin->Network->General. Make sure domain is 'home' or whatever you have on *both* computers. Maybe old news but worth a shot. Creating a new user I don't think is going to make any difference. 

But then, your grey folder wouldn't be showing up on the windoze box if it wasn't in the domain and figuring how to not have to type in the address in Windoze is a Windoze question which I can't answer off hand. Sorry. :(

Are you typing smb://grey/grey to get there by the way?

Last time I ran shares the security details for the Ubuntu share when accessed from windoze were always necessary. I also had no matching IDs on both machines.

---

### Post by gimmejimmy on 2008-10-03
> But then, your grey folder wouldn't be showing up on the windoze box if it wasn't in the domain and figuring how to not have to type in the address in Windoze is a Windoze question which I can't answer off hand. Sorry.
Actually, I'm trying to figure out how to not have to type the address in Ubuntu.  :D
Thanks for the patience.  You were right, creating a new user (the GUI for that is still broken haven't figured it out) on Ubuntu didn't help, though I'm pretty sure that's the trick that worked back when the Ubuntu machine was still running WinME (ugh).

---

### Post by Bucky Ball on 2008-10-04
> **gimmejimmy said:**
> Actually, I'm trying to figure out how to not have to type the address in Ubuntu.  :D
  (ugh).


What i mean. The windoze shares should be showing already! Doh!

---

