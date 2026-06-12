---
title: "Kubuntu 8.10 just switched to Unbuntu ??"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by Pepse3 on 2009-03-16
This is really weird I installed Kubuntu 8.10 Friday night and Sunday night I went to Add/Remove software and added a bunch of stuff.  That all went good until I went back on about an hour ago and added some wallpaper.  I went to my other Hard Drive that has Kubuntu 8.04 to send my bookmarks folder across the 2 hard drives via Storage Media and came back to what should be KUBUNTU 8.10 and it's UBUNTU 2.24.1  What the heck is going on?  Is *Buntu 8.10 that messed up?

Later.  Pepse.

---

### Post by taurus on 2009-03-16
What do you mean Ubuntu 2.24.1?  I assume you mean Gnome version.  What was "a bunch of stuff" that you added from Add/Remove?

---

### Post by Pepse3 on 2009-03-16
Yeah, Ubuntu as in the Gnome interface, ugly brown desktop screwed up task bar.  The list goes on.  But that's not why were here.

  As for what I added?  Well, let's put it this way.  It would probably take me about 30 minutes to list everything I added.  Serious, I start at the top "Accessabilty" and all the way down to whatever is at the bottom.  I've been doing this kind of installing since I've been a Linux user; 8 years.

  I get the feeling I should start over?  Re-install Kubuntu 8.10?

Later. Pepse.

---

### Post by taurus on 2009-03-16
Perhaps you added some stuff that required Gnome!  Again, if you have a happy clicking finger, then you would install more stuff then you really need.

---

### Post by Pepse3 on 2009-03-16
"Happy Finger", true but I do have a need for everything I add.  Yeah, there is a lot but I really do use the stuff I add.

Pepse.

---

### Post by taurus on 2009-03-16
When it is downloading the apps that you want, you can expand the window and see exactly what are the files that are being downloaded.  Then, you would know whether you also install some Gnome stuff on your KDE.

---

### Post by Pepse3 on 2009-03-16
Okay, I will see what might have caused that screw up.  Funny thing though, I'm sure in the past I've added some Gnome stuff but, it didn't affect Kubuntu.  So, apparently I added something different than I ever did before.  Possibly when I was trying to figure out what would give me the "Storage Media" part.  Since that isn't included with default apps anymore.

  I will let you know a little later what I found out.

Pepse.

---

### Post by Pepse3 on 2009-03-17
Well I went to applications-->add/remove and looked at "installed" programs and it didn't show me anything that I thought was unusual to what I usually install.  So, I went to Synaptic Package Manager and scrolled down to Ubuntu apps and there are 5 items checked that I "think" can be removed that might be the problem causing Gnome to be my desktop when it should be KDE.  The programs are:  Ubuntu-keyring  Ubuntu-minimal  Ubuntu-standard  Ubuntu-system-service and ucf.  Opinion?

Later. Pepse.

---

### Post by Pepse3 on 2009-03-17
Problem solved.  I finally got rid of Gnome 2.xx.x .  Basically went to synaptic package manager and started through the alphabet until I got to Gnome packages and deleted what didn't look normal for my KDE system and it worked:popcorn:.

  Now all I gotta do is figure out how to get the Storage Media or whatever it might be called so I can access my other 2 hard drives.  I see Gnome 2.xx.x has it.

Later.  Pepse.

---

### Post by taurus on 2009-03-17
If you want to access the other two harddrives (or partitions), can you just add two entries in /etc/fstab so they would be mounted automatically each time you boot?

---

### Post by Drellir on 2009-03-18
Sorry I jump into this where do you add two entries in /etc/fstab ??? I'm a bit confused as a newbie :-/

Drellir

---

### Post by Pepse3 on 2009-03-18
I probably could but then it also means the KDE people forgot that little item that they had in KDE 3.5.x, and yet the Gnome people remembered.  

  Now that I said that I can say "if I add the entries in /etc/fstab" are you saying that I will need to go to a command line to access the other hard drives?  Or do you mean when I boot the computer?  If so, that is Not necessary as GRUB shows me and I am able to boot to any hard drive.

Later. Pepse.

---

### Post by markbuntu on 2009-03-18
You could have just used change session at the login screen to get to the KDE desktop. That's what I do.

---

### Post by Pepse3 on 2009-03-23
True, but I have it set to bypass the login screen.  

  And after about a week of Kubuntu 8.10 I am rather disappointed with KDE 4.x  But I recall somewhere, either here or in the Kubuntu Forums something on changing KDE 4.x back to KDE 3.x.x and keeping the *Buntu 8.10 kernel and such.  So, chances are I am not alone in this assesment.

Later.  Pepse.

---

