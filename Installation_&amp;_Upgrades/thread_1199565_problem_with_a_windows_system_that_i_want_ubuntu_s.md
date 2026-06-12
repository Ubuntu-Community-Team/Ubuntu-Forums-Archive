---
title: "problem with a windows system that i want ubuntu system on"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by 10ghost on 2009-06-29
I want to install ubuntu on a friends system but when i right clicked on my computer and on the drop down menu i clicked manage it gave me this[IMG]/media/BATUNDE/error.jpg[/IMG] error

How wld i solve this problem?
The msg is windows cannot access the specified device,path or file. You may not appropriate permission to access the file

---

### Post by 10ghost on 2009-06-29
I really need the solution to the problem so i can add one person to the number of linux users.
pls readers i need a solution badly

---

### Post by presence1960 on 2009-06-29
you can't add a Linux user from within Windows. Boot into Linux and go to System > Administratopn > Users and Groups. You can add a user from there.

---

### Post by 10ghost on 2009-06-29
sorry presence1960
d problem is not adding a new user.
it is about partitioning/shrinking the system so that i can create space for linux installation .
hope dis wld help bcos ineed to get the dialogue so i can get to disk management option and then shrink the device.

---

### Post by abn91c on 2009-06-29
is it windows vista or XP?
if its vista you may want to scan the disk for errors, viruses and defrag first. for XP you better off using a third party disk manager
Also the windows user need to have **administrator** rights

---

### Post by 10ghost on 2009-06-29
ok
it is actually a windows vista.
I wld do as u hv said and see wat it d problem is.
but does any one know another solution to dis ?

---

### Post by raymondh on 2009-06-29
As you may know (and if so, I apologize for trivializing this)


BACK-UP first your friends' personal files.

1.  Defrag the Vista partition
2.  Use Vista's disk management tool to resize-down the vista partition.  I have found it less troublesome to use Vista's own tools to work on Vista.

From there, you can use gparted to create your partition preferences (extended, separate /home, /var, /user ...etc) or.... just use the installer from the liveCD.

NOTE : Try the liveCD first and see how it reacts to your friends system specs'.  Proceed from that experience as to whether you install or choose another version.

Good luck.

---

### Post by 10ghost on 2009-06-29
The real issue is that i cant get to disk management
Is There another means of getting to disk management apart from through manage menuitem when one  right clicks on my computer and select the menu item manage.

---

### Post by raymondh on 2009-06-29
> **10ghost said:**
> The real issue is that i cant get to disk management
Is There another means of getting to disk management apart from through manage menuitem when one  right clicks on my computer and select the menu item manage.

you cannot access disk management thru this method?

start > control panel > system maintenance > administrative tools ... which will open computer management > on left pane, expand storage > disk management

See this link

[http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/](http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/)

Do you have administrative rights?

---

### Post by 10ghost on 2009-06-29
thanx a million i really appreciate.
But try the means i told u . You wld see that it is possible to go thru that means except your system gives the error i had.
Thank u ubuntu forum

---

### Post by 10ghost on 2009-06-30
> **raymondhenson said:**
> you cannot access disk management thru this method?

start > control panel > system maintenance > administrative tools ... which will open computer management > on left pane, expand storage > disk management

See this link

[http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/](http://www.windowsreference.com/windows-vista/how-to-use-disk-management-in-vista/)

Do you have administrative rights?

Administrative right! i taught  had but based on the error it gave me it seems i dont have it  again. The error was what i stated first in the first msg i posted.
I decided to do what i was advice to  yesterday which was to go through the control panel but it gave me the same error again.

I tried using vista help but i realised that one item in the administative tool was missing which was the local security policy which i felt would help me solve the problem of administrative right.
How do you think i can solve this now?
This is one of the reasons why my friend wants to leave windows.

---

### Post by presence1960 on 2009-06-30
Does your friend have a legitimate, genuine version of Windows? Or is it a pirated copy? If it is genuine just insert the DVD and try the repair function. If it is a recovery DVD and/or partition recover the machine back to it's original state then start over by shrinking Vista. First of course back up all your friends data. If that doesn't fix it just wipe Windows off the drive by installing Ubuntu on the whole disk. At the Prepare disk space window of Ubuntu's installation process choose "use entire disk". You can always reinstall Windows later if need be.

---

### Post by 10ghost on 2009-06-30
it is a genuine one but it came installed on his laptop.
Actually we are just troubleshooting it to see the outcome so if we see such a problem again and the person does not want to wipe the vista off we would be able to resolve it.
He would do the back up  hopefully today.
thanx  a lot.

---

### Post by presence1960 on 2009-06-30
> **10ghost said:**
> it is a genuine one but it came installed on his laptop.
Actually we are just troubleshooting it to see the outcome so if we see such a problem again and the person does not want to wipe the vista off we would be able to resolve it.
He would do the back up  hopefully today.
thanx  a lot.

then he should have a hidden recovery partition which can be accessed by pressing a key at boot. refer to your friends documentation that came with the lappie or go to the manufacturer's website to find the user manual and see which key needs to be pressed to start recovery process. **_Make sure all data you don't want to lose it backed up to an external media as this will wipe the entire disk and restore to factory specs!_** Then you can start over by defragging Vista. I would defrag again because some of the worst fragmentation I have ever seen is after a windows install. After defragging shrink Vista's partition with it's disk management tool. Then install Ubuntu.

P.S. first I would try this. Go to control panel> Taskbar Settings. Go to start menu and scroll down to the bottom. There is an option to have system administration tools (i believe that's what it is called) show up on the start menu and all programs. see if this gives yo access before the recovery option.

---

### Post by uberdonkey5 on 2009-06-30
sorry if this is a naive response or maybe I have misunderstood...

...why are you using vista to resize the partition? I use dual boot, but just installed vista (and defragment if you have been using it before ubuntu installation) and then started computer up with ubuntu installation disk, which automatically permitted correct partitioning.

If you have ubuntu already and want to add a user, you go into ubuntu to do this.

---

### Post by presence1960 on 2009-06-30
> **uberdonkey5 said:**
> sorry if this is a naive response or maybe I have misunderstood...

...why are you using vista to resize the partition? I use dual boot, but just installed vista (and defragment if you have been using it before ubuntu installation) and then started computer up with ubuntu installation disk, which automatically permitted correct partitioning.

If you have ubuntu already and want to add a user, you go into ubuntu to do this.

the reason is that experience shows that some but not all of the time Vista freaks out if a third party partitioning tool is used to resize Vista. The result has been an unusable Vista.

---

### Post by presence1960 on 2009-06-30
OK, I rebooted into windows 7. here is where you go. Control panel > Taskbar & Start Menu > Start menu > Customize. Scroll down to the bottom and there should be an entry to add System Administration to All programs and Start menu. Try that and see if you can access disk management that way. If not you may be stuck recovering the lappie and starting from scratch.

---

