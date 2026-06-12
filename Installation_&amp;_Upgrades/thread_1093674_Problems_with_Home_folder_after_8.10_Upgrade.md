---
title: "Problems with Home folder after 8.10 Upgrade"
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by Misaru-Meep on 2009-03-11
I apologize if there is something similiar to this elsewhere, though I did search. I decided this might have a greater chance of being seen and answered if it was a thread rather than on someone else's (for those who have seen this question on the other thread I posted to).  Ever since I've upgraded from Hardy Heron, my Home folder is inaccessible from the "Places" menu. I can reach it by going into Computer and whatnot, but it says it cannot open that folder (and the bookmarks leading straight to 'Documents', 'Pictures' etc) with the message:

[B]Could not open location 'file:///home/lizz'
Failed to execute child process "/media/KLAUSIE/Floola-linux/ffmpeg/Floola" (No such file or directory)[/B]

"Klausie" is my iPod. Soon after this, I started getting a message whenever I logged into Ubuntu saying: 

**User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned my user and not writeable by other users.**

I assume these are related? I'd greatly appreciate any help! 3:

**I'm still pretty new to Ubuntu, though I have gotten my foot through the door with some things. Please be kind--I'm a beginner who'd love to learn.**


*(If it is a little hard to understand, I mean that clicking on "Home Folder" from the "Places" menu brings that first message. If I want to get into the folder, or anything inside of it, I must go through Computer.)*

***I have successfully gotten rid of the **message** about me having priviledges to open my home folder, but I still have the other problem, about not being able to open it in general, or any of it's subfolders, from the "Places" menu***

---

### Post by FakeOutdoorsman on 2009-03-11
Perhaps this excellent tutorial will help:

[Solving .dmrc and $HOME Permission Errors](http://ubuntuforums.org/showthread.php?t=976610)

---

### Post by Misaru-Meep on 2009-03-12
Thank you very much for that page. I did try those commands, but I still had the same problem, and it told me access was still denied to those files, in the terminal. Haha. I posted the problem there, though. Thanks.

---

### Post by drs305 on 2009-03-12
> **Misaru-Meep said:**
> Thank you very much for that page. I did try those commands, but I still had the same problem, and it told me access was still denied to those files, in the terminal. Haha. I posted the problem there, though. Thanks.

I wrote the .dmrc tutorial referenced above. I am not sure I understand your problem. Are you saying that if you click on your home folder (at the top of the Places menu) you can't see any of the files/folders in the left pane? If the "*it*" is your home folder itself, the following may help. If the "*it*" refers to your iPod, it won't.

One problem may be permissions of some of the files/folders in your *home*. The commands in the tutorial for solving the .dmrc permissions were written to affect as few files as possible. You may have noticed that the commands did not use the "-R" (recursive) option, which would change ownership and permissions of all files and subfolders/files. 

Normally everything in your own home folder and below is owned by you and you shouldn't have a problem using the "-R" switch. If you are sure you want to change everything to belong to you in your home folder, you can run this command. [COLOR="DarkRed"]Just make sure to either copy the command or type it exactly. If you run a -R command with sudo and mistype the target you can mess up your install to the point of having to reinstall the system.[/COLOR] The second command sets up permissions. You can change the number to suit your wishes. 755 gives you read-write-execute and your group and others read-execute.

```

sudo chown -R lizz:lizz /home/lizz 
chmod -R 755 /home/lizz  

```

---

### Post by Misaru-Meep on 2009-03-12
My problem is that when I click on "places" "Home Folder" is there, but when I click on it, I get the "Klausie Message"

But that folder it's talking about, only exists when I attach my iPod. I get the same message whether or not I have my iPod attached. The directions you gave me, I *think* solved the other message showing up. But I just did it again, and got this:

lizz@lizz-laptop:~$ sudo chown -R lizz:lizz /home/lizz
[sudo] password for lizz: 
chown: cannot access `/home/lizz/.gvfs': Permission denied

I'm not sure what to do from here. Thank you for trying to help, so far, though. I appreciate it greatly! :)

---

### Post by drs305 on 2009-03-13
As bodhi.zazen said in the other thread, the .gvfs error message is normal.

I don't know if your problem is specific to the iPod setup or a general nautilus one. There were bug reports filed at one point for nautilus regarding a similar issue. Try opening nautilus, right click on any folder, select "Properties", "Open with", and select "open folder".

If that doesn't solve it, try variations discussed in posts 6 and 7 in this thread:
[http://ubuntuforums.org/showthread.php?t=969158#6]("http://ubuntuforums.org/showthread.php?t=969158#6")

---

### Post by Misaru-Meep on 2009-03-13
Wow--I feel pretty silly. Haha. Thanks for your help. When I upgraded, it only left "Floola" as a source for opening folders. I went and added "open folder" and made it set to that and now it's solved. 

Thank you SO much for your help!

---

