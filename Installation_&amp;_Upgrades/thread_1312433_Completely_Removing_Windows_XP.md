---
title: "Completely Removing Windows XP"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by ukapolog on 2009-11-03
I now have Ubuntu 9.10 on an old computer which I had given up on at one time. Under Ubuntu it flies!
Since this is an old computer without huge resources can I now more or less eradicate Windows XP SP3 from my system without affecting Ubuntu?

---

### Post by sliketymo on 2009-11-03
More!LOL. Of course you can.Xp is probably in the first place on your hard disk.Just imagine the speed if Ubuntu is in the first slot ?Something to consider.

---

### Post by coffeecat on 2009-11-03
> **ukapolog said:**
> Since this is an old computer without huge resources can I now more or less eradicate Windows XP SP3 from my system without affecting Ubuntu?

Oh yes, indeed! As the previous poster said, Windows is almost certainly on the first partition which you can access read/write from the Places menu. The simplest thing would be to simply delete all the Windows files and use the partition for data storage. Ubuntu can read/write NTFS reliably, so you don't even have to reformat. That will, of course, leave Windows as an option on your grub menu, but that should be fairly easily sorted.

If you want the Windows partition mounted on bootup it's a simple matter to add an entry to the file /etc/fstab and then you won't have to go to the Places menu each time.

Why not post the terminal output of:

```
sudo fdisk -l
```

... to give us the partition layout.

---

### Post by ukapolog on 2009-11-03
Okay, thanks for the info!
But now I need more detailed info on getting rid of Win XP without wrecking my system.
Where is the first place to go to start deleting? Won't Windows prevent me from deleting it's own vital files?
 
ukapolog

---

### Post by sliketymo on 2009-11-03
Do that from Ubuntu,not from windows,Just boot up Ubuntu,mount the ntfs partition,and go to work.Before you do that,you may want to have a quick look at grub 2 operation,just incase.

---

### Post by coffeecat on 2009-11-03
> **ukapolog said:**
> Where is the first place to go to start deleting?

Boot up Ubuntu, go to the main Places menu, mount your Windows C: partition and delete away.

> **ukapolog said:**
> Won't Windows prevent me from deleting it's own vital files?

If you're in Ubuntu, Windows won't be running and Ubuntu will just see a bunch of folders and files. Windows won't be able to do anything about. In fact all the Windows system files will be completely at the mercy of Ubuntu.

Which is as things should be. :twisted:

---

### Post by ukapolog on 2009-11-03
Hmmm! This older computer has xubuntu 9.10 and does not give me the access to do this at all. I have spent half an hour checking out the various possibilities.

My newer computer (running Ubuntu) certainly does give me such an option but not this older one. It really does not seem to open any doorways into Windows at all. Win XP is still there  for sure but I cannot get into any of it's system from here.

---

### Post by coffeecat on 2009-11-03
Hmmmm indeed. When you said Ubuntu 9.10 we assumed you meant Ubuntu, not Xubuntu. Explanation: Ubuntu uses the Gnome desktop. Xubuntu uses the lighter Xfce desktop - which is somewhat different. The one reason I gave up in disgust with Xfce (which shows so much else promise) is that I could find no easy GUI way of mounting internal partitions. Which is what you've just discovered.

I'll do a bit of digging around later, but in the meantime, open up a terminal (sorry - have no idea where you'll find that in the Xubuntu menus), and post the output of:

```
sudo fdisk -l
```(That's 'SUDO FDISK -L' but in lower case.)

That will give us your partition layout from which I can give you some terminal commands to mount the Windows partition - or even add a line to /etc/fstab to get it mounted on bootup.

The other option you might think about is to install Gnome on top of Xubuntu. Then you can choose between gnome and Xfce at login. But you need anough RAM. How much RAM do you have?

---

### Post by coffeecat on 2009-11-03
> **coffeecat said:**
> I'll do a bit of digging around later

I found this:

[http://www.dedoimedo.com/computers/automount_ntfs.html](http://www.dedoimedo.com/computers/automount_ntfs.html)

It's a tutorial for setting up a GUI app that edits /etc/fstab for you for NTFS partitions.

I haven't yet found anything to mount partitions on the fly. Which is so easy in Gnome and KDE - just a click and a password. [/rant] :evil:

:wink:

---

### Post by ukapolog on 2009-11-03
Thank you, coffeecat.
 
I appreciate the help.
 
I will look into that a little  later, we are off to lunch now.
But to set the scene a little better for you,
1. Yes, I know where terminal is, no problem on that.
2. Yes, my 2001 computer (which started out on Win ME but got upgraded to XP around 2004), has quite small memory facilities, can't remember how much at present, I am typing this on my newer Vista/Ubuntu computer).
 
Within a week I put Ubuntu to share with Vista (despite what so many say, I love Vista and will certainly keep that) on this 18 month old computer, then I read somewhere (maybe even on this forum??) where somebody wrote that Ubuntu gave new life to a rather pathetic old computer. I was just about to give up on the old one but installed Xubuntu on it (taking around 8 hours) and it has been a great success.
 
If getting rid of XP completely proves too problematic I will just leave it there but I would rather get rid of it.
ukapolog.

---

### Post by coffeecat on 2009-11-03
Enjoy your lunch! :)

To find out how much memory the old computer has, open a terminal and run 'top'. You'll find it under "mem", expressed in kilobytes - or possibly kibibytes. :?

Tbh, if you're running Xfce/Xubuntu OK, that computer might just manage with the heavier gnome environment. Xfce was designed as a lightweight alternative but it's got a bit - um - saggy round the middle in the Ubuntu stable, so Xubuntu needs more RAM than some of the other Xfce distros - or so I understand.

> **ukapolog said:**
> If getting rid of XP completely proves too problematic I will just leave it there but I would rather get rid of it.

It won't be a problem. It looks as though mounting the partition might be a bit more fiddly in Xfce, but we'll get there. I'm confident.

---

### Post by czekon on 2009-11-03
> **sliketymo said:**
> More!LOL. Of course you can.Xp is probably in the first place on your hard disk.Just imagine the speed if Ubuntu is in the first slot ?Something to consider.

hmmm intersting so moving ubuntu to first slot( if thats proper terminology im noob)will affect boot time or work of whole os??


cheers

---

### Post by coutts99 on 2009-11-03
> **coffeecat said:**
> Boot up Ubuntu, go to the main Places menu, mount your Windows C: partition and delete away.

Why would he want to do this? Surely he just wants to delete the partition?

---

### Post by coutts99 on 2009-11-03
> **czekon said:**
> hmmm intersting so moving ubuntu to first slot( if thats proper terminology im noob)will affect boot time or work of whole os??


cheers

No it won't

---

### Post by coffeecat on 2009-11-03
> **coutts99 said:**
> Why would he want to do this? Surely he just wants to delete the partition?

I suggest you read the whole thread. Deleting the partition is one option. Re-using the partition is another.

---

### Post by jamest09 on 2009-11-03
> **coffeecat said:**
> I suggest you read the whole thread. Deleting the partition is one option. Re-using the partition is another.

Why would you want to use a NTFS partition on a system that doesn't have Windows on? That's bad advice.

Surely easier just to make a new ext3/4 partition and be happy.

---

### Post by coutts99 on 2009-11-03
> **coffeecat said:**
> I suggest you read the whole thread. Deleting the partition is one option. Re-using the partition is another.

I did read the whole thread, you don't want an ntfs partition if you haven't got Windows, use something proper. Simples.

---

### Post by coffeecat on 2009-11-03
> **jamest09 said:**
> That's bad advice.

Be so good as not to accuse me of giving bad advice. That is discourteous. You are welcome to list the advantages and disadvantages of both NTFS and ext3 and then letting the OP decide for him/herself. Anything else is presumptious.

---

### Post by coutts99 on 2009-11-03
> **coffeecat said:**
> Be so good as not to accuse me of giving bad advice. That is discourteous. You are welcome to list the advantages and disadvantages of both NTFS and ext3 and then letting the OP decide for him/herself. Anything else is presumptious.

If you are going to delete Windows from your system, mounting the drive, deleting the files, and then continuing to use NTFS is just not the done thing, it is bad advice, face it.

---

### Post by ukapolog on 2009-11-03
I checked out the ntfs thing, downloaded it and checked out the Dedoimedo page (quote above), unfortunately on my Xubuntu you can only check external files not internal ones so I got nowhere.
 
So it looks like I will have to live with Win Xp still being present even if I don't use it. But can I just go into Win XP and delete some pretty big files to make more space?? Or would the system stop me from the Windows end (I presume it would) and would it be pretty meaningless?
 
ukapolog

---

