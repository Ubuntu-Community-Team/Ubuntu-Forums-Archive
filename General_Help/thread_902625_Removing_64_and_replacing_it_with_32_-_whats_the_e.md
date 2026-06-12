---
title: "Removing 64 and replacing it with 32 - whats the easiest way?"
date: 2008-08-27
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-27
Alright, the simple fact that java doesnt work in 64 and my dock seems to be always screwed up, I'm not willing to deal with this any more.

What should I do to go about removing 64 completely and adding 32?

---

### Post by arch0njw on 2008-08-27
Are you talking about java from the command line, or the browser plugin?

I have gotten around the java plugin not working by following the instructions for installing "firefox32".  It doesn't yield a terribly sexy Firefox, but has worked for what I need it to do.

---

### Post by habtool on 2008-08-27
If you running the x64 Ubuntu and now want to go back to x32, then download the X32 livecd or alternative x32 and install from scratch.

I have also run the x64 version, but found very little advantage as i dont have more than 4G ram.

Personally I dont think the extra inconvinience is yet worth the little problems that arise from using the x64 version.

Hopefully more proprietary software will going FOSS or release X64 version, then life will be easier.

(Even FOSS projects like Flock dont released X64 versions, AFAIK)

---

### Post by PsychedelicWonders on 2008-08-27
Do I format this partition before putting 32 back on?

I am going to lose any data currently on this partition right?

So I dont need to remove 64 first?  32 will automatically do it for me?

---

### Post by tamoneya on 2008-08-27
yes for all 4 questions.

---

### Post by PsychedelicWonders on 2008-08-27
haha thanks.  you gotta quadruple check stuff when it comes to data.

---

### Post by jayson.rowe on 2008-08-27
Just make sure when you re-install you create a seperate /home partition so you won't lose your data next time you need to reload, or if you want to do a fresh install of a future release w/o upgrading.

---

### Post by rcrcomputing on 2008-08-27
One more suggestion, put your home on another hard drive.

---

### Post by PsychedelicWonders on 2008-08-27
youre saying to go 

places>home folder - and then drag that onto another hdd?

Will this save all of my settings and changes I've done to 64 and transfer them over to 32?

---

### Post by rcrcomputing on 2008-08-28
> **PsychedelicWonders said:**
> youre saying to go 

places>home folder - and then drag that onto another hdd?

Will this save all of my settings and changes I've done to 64 and transfer them over to 32?

I am assuming 2 things here. 
1) The config files for the 64bit and 32bit versions of the programs are the same.  ???  I'm unsure.
2) Your refering to personal settings and not program settings that might be in /etc/???   or /var/  

What it won't save is, programs you may have installed. 

what it will save are documents you've written, program USER settings, etc..

I'd use cp -a or better yet, here's an rsync example for you: It should get the archive bit's for you.

rsync -av /home/ /media/other_hard_drive/home/

When you get the new system up and running, you can reverse this. Like this. 

rsync -av /media/other_hard_drive/home/ /home/

The wording of your questions is making me nervous. Do you have another hard drive we can backup the whole machine to?

---

### Post by Sef on 2008-08-28
> Alright, the simple fact that java doesnt work in 64

OpenJDK works on 64-bit.   It's available from Add/Remove.    Click on my link for more information.

---

### Post by PsychedelicWonders on 2008-08-28
> **rcrcomputing said:**
> I am assuming 2 things here. 
1) The config files for the 64bit and 32bit versions of the programs are the same.  ???  I'm unsure.
2) Your refering to personal settings and not program settings that might be in /etc/???   or /var/  

What it won't save is, programs you may have installed. 

what it will save are documents you've written, program USER settings, etc..

I'd use cp -a or better yet, here's an rsync example for you: It should get the archive bit's for you.

rsync -av /home/ /media/other_hard_drive/home/

When you get the new system up and running, you can reverse this. Like this. 

rsync -av /media/other_hard_drive/home/ /home/

The wording of your questions is making me nervous. Do you have another hard drive we can backup the whole machine to?

What is cp -a?  I'm totally new to Ubuntu and Linux.  

I have another hard drive to move all important data too, yes.  It is the one I am trying to re-format in another thread.

Do you have a basic walk through to do what you are talking about?

SEf:

does it run flawlessly?  you are the 1st person to tell me java works in 64.

I seem to have a lot of problems with my AVN Dock though, so I'm wondering perhaps if it would run smoother and properly in 32?

---

### Post by rcrcomputing on 2008-08-28
cp -a (copy -a) and rsync are two differant ways you can copy files to that new hard drive. Both are run from the command-line or "terminal".
example: cp -a /home/* /media/home


Stepping back a bit, let's see where we are.

We've another hard drive we hooked up.
we are formating it to ext3
the machine will now see it as /media/whatever_you_named_it.

Now that all that's done and the hard drive is mounted, open a terminal window. 
Type this in rsync -av /home/ /media/whatever_you_named_it/home/
Notice the space after /home/


A little note here. With rsync source is always first and should almost ALWAYS have the trailing slash. 

When done, you can use your file browser to check it out and see what you've got. As for your settings etc., most are kept in (dot) files like .mozzilla etc. You can see these files if you choose "view hidden files". Or from the command line:
cd /media/whatever_you_named_it/home/
ls -all

---

### Post by tuxxy on 2008-08-28
> **PsychedelicWonders said:**
> Alright, the simple fact that java doesnt work in 64 and my dock seems to be always screwed up, I'm not willing to deal with this any more.

What should I do to go about removing 64 completely and adding 32?

Java works well in 64bit, what dock is this?

---

### Post by PsychedelicWonders on 2008-08-28
> **tuxxy said:**
> Java works well in 64bit, what dock is this?


Is Sef's link for java the best one for 64?

I am running the AVN dock. 

I cant seem to drag and drop icons to it and it seems to disppear after a while.

---

### Post by tuxxy on 2008-08-28
Launch the dock and drag & drop the applications you want on to the dock itself not its managment program.

Yes Sef linked the OpenJDK java which I use on my 64bit systems still, you could however upgrade suns java, I never had the need though

---

### Post by PsychedelicWonders on 2008-08-28
> **tuxxy said:**
> Launch the dock and drag & drop the applications you want on to the dock itself not its managment program.

Yes Sef linked the OpenJDK java which I use on my 64bit systems still, you could however upgrade suns java, I never had the need though


I tried dragging and dropping icons from the desktop and I tried draggin and dropping them right from the main menu.

They wont attach.

They did at one point, but then they would disappear.  Now they just wont stick period.

What is the difference between OpenJDK nad suns java?

Should I just go right for suns java?

Have you had any problems or errors at all?

Is flash and java the same thing, just kinda of different? 

or are they completely separate as far as what they do?

---

### Post by PsychedelicWonders on 2008-08-29
Opera is my browser, is this Sun Java 6 extension going to allow opera to now view all java?

---

### Post by PsychedelicWonders on 2008-08-30
When I follow Sefs 64 java walkthrough, I click on Sun Java 6 link because I want 100% compatability in Ubuntu, and moe specifically in Opera.

But when that walk through opens, it goes into many other subjects and I seem to get lost.

Anyone have an install guide for Sun Java 6?

---

### Post by PsychedelicWonders on 2008-09-01
bump

---

