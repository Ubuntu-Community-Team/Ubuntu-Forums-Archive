---
title: "New to Ubuntu: Installation Questions"
date: 2009-03-14
forum: Installation &amp; Upgrades
---

### Post by Captain Camaro on 2009-03-14
I'm getting ready to install Ubuntu, and so far I've only been to the dialogue box pops up during the partition settings that says, "Are you sure you wish to resize this drive?  This cannot be undone."  I hate that sentence when it's on a computer.  My wife and I have always been intimidated by computers and I've only just recently started to learn what they are and how they work.  She does not care.  I have to get this install right or she will never trust me on the computer again.

I have a laptop with an 80 Gig HD that has 46 Gigs free.  I also have a 500 Gig external HD which I have transferred all media to, and made a backup of everything I think is important for both our profiles.  I defragged and compressed everything left on the windows side, and I guess I'm good to go on installation.  I'm at a complete loss, though, at what exactly to do as far as partitioning.  Should I just let Ubuntu do the automatic partitioning, allowing for the remaining 46 Gigs to be for Ubuntu?  Can this partitioning really "not be undone?"

Thanks for all your help folks and I look forward to hearing from you all.

Jared Allen

---

### Post by Admiral Yi on 2009-03-14
Hello,
First off, if your worried about partitioning, why not try installing with wubi. Boot into windows and put the ubuntu cd in the drive. When it starts there will be a popup. Click 'install inside windows' and follow the instructions from there. This will be the same as a normal install, only a bit slower and without the 'suspend' option.

If you really want to install normally, use the default option when it reaches the 'prepare disk space window' and you will be ok. This will reduce the size of windows and create space for Ubuntu. I suggest just going with the defaults, they are generally pretty good. If you want to eliminate windows, then pick the 'guuided-use entire disk' option. This will completely erase windows.

Hope I have been helpful, and good luck with your new (for new read 'better' ;)) OS.

EDIT
Sorry, I forgot to mention. If you use Wubi, you can remove Ubuntu by going to the add/remove programs menu and just deleting it. The 'this cannot be undone' message is not entirely correct. If you erase all the partitions, then yes, it cannot be undone. You would have to reinstall. But if you go with the defaults it will be a lot easier to put it all bac how it was.

---

### Post by infinitejones on 2009-03-14
I'm going to make the assumption that you're wanting to install Ubuntu on the 46GB partition and leave everything on the other partition (eg. your Windows setup) completely untouched, so you can boot into either.

In the case, you'll need to select the option to manually partition. Don't let Ubuntu do it automatically, because yes, it will assume you want to wipe everything and start again. (It's always been slightly annoying that there isn't an option to "Leave Windows partitions as they are" or something like that).

Anyway - a good place for tutorials for this is this website - [www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

Have a good read through - there are screenshots and everything - it's a little out of date, in that it's still talking about Ubuntu 8.04 but nothing significant has changed since then.

I made extensive use of the tutorials on this site when I was starting out with Ubuntu and it's great - nice and simple, no crazy jargon, lots of screenshots.

It's always easiest if you can maybe get hold of a second PC or laptop to keep the website open on while you're following the instructions - maybe just print it out instead or something, if you can.

Good luck, and come back if you need more help...

---

### Post by Captain Camaro on 2009-03-14
Thanks a lot for the quick replies.  I am reading through the psychocats install guide now.  I will let you know how everything works out and if I have any other questions.

Jared Allen

---

### Post by Captain Camaro on 2009-03-14
Okay, so I read the install guide, and I think I understand it somewhat, at least enough to install and get started.

I resized the partition that will be created so for now, I will have 50% of the HD for each OS.  Hopefully later I will erase windows and just have Ubuntu.

But the one thing I do not understand is, am I essentially scarring my internal HD by creating a partition?  Is this process reversible in case all goes haywire?  And I still don't completely understand why the installation needs to "resize" Windows?  Isn't there enough space for both OS to reside in their original state?  Thanks so much for all your help folks!

Jared Allen

---

### Post by infinitejones on 2009-03-14
> **Captain Camaro said:**
> Am I essentially scarring my internal HD by creating a partition?

Well, you're not physically damaging the drive, you're changing the way the data is stored on it - basically, the location and/or the order of the data on the drive. However, in my experience, the more changes you make to partitions, the higher the chance something will go wrong that will cause you problems. It wouldn't be a high chance, but it would be higher than if you left everything alone.

> **Captain Camaro said:**
> And I still don't completely understand why the installation needs to "resize" Windows?

Neither do I. I don't think you should have to... 46GB for Ubuntu and 34GB for Windows should be more than enough for both. Although it does depend on how much media you backed up on your USB drive, if you want to put that back on your main hard drive sooner or later.

I'm fairly sure you should be able to set up the partitions as you need them without resizing them. What options is the installer giving you?

---

### Post by angel25 on 2009-03-14
Hi....i want a help in ubuntu....
i installed uduntu.....
now when i start my computer.....
i get 4 options
1)ubuntu
2)ubuntu (recovery mode)
3)ubuntu memtest+98
4)windows xp

when i click the 1st ubuntu....it stops in username....
even though i login i am unable to go to ubuntu window....
it happens for the 2nd also
it comes to the # sign and when i click ctrl+d it goes to sign in ..... 
can u pls...tell me how can i go to ubuntu window...

---

### Post by Captain Camaro on 2009-03-14
I went ahead and installed Ubuntu with 50% of the HD for each OS.  I think it was something like 34 Gigs each.  Like I said, my end goal is to convince my wife that it's a good idea to remove Windows from the computer altogether.  First, I need to convince myself.  So far, so good.  Everything looks great and now I'll start poking around.  Thanks for all your help, Jones.

The first thing I noticed after install, updates.  268 of them to be exact.  Is it typical to just install all of these updates as trustworthy?  I'm assuming they're all from the community and necessary, it's just a little intimidating I guess.

Thanks again folks.

Jared Allen

---

### Post by Captain Camaro on 2009-03-14
> **angel25 said:**
> Hi....i want a help in ubuntu....
i installed uduntu.....
now when i start my computer.....
i get 4 options
1)ubuntu
2)ubuntu (recovery mode)
3)ubuntu memtest+98
4)windows xp

when i click the 1st ubuntu....it stops in username....
even though i login i am unable to go to ubuntu window....
it happens for the 2nd also
it comes to the # sign and when i click ctrl+d it goes to sign in ..... 
can u pls...tell me how can i go to ubuntu window...

I had this same window when I first restarted the computer after install.  I just left it alone and didn't click anything, and Ubuntu started successfully.  Maybe I was just lucky, but I am also sort of confused on the options during bootup aswell.  I'm sure there is someone here who can provide us with an explanation. :)

Jared Allen

---

### Post by Partyboi2 on 2009-03-14
> **Captain Camaro said:**
>   And I still don't completely understand why the installation needs to "resize" Windows?  Isn't there enough space for both OS to reside in their original state?  Thanks so much for all your help folks!

Jared Allen

You will probably currently find that your windows partition(s) eg c: drive  is using the whole hard drive. Even though you have 46 gigs free that is probably the space free on the Windows partition(s). Windows uses  the ntfs file system where as Ubuntu uses the ext3 file system. So unless you are installing ubuntu inside windows (wubi) you need to shrink down your windows partition so that it is using a smaller amount of the hard drive space which then allows you or the ubuntu installer to create the parititions that Ubuntu requires to install.

---

### Post by angel25 on 2009-03-14
so...u mean that i will have to delete some softwares from the c: to go to my ubuntu desktop....i have a total to 14.5gb free
in my c:

---

### Post by Kevbert on 2009-03-14
Regarding updates. Initially you'll find you need to install loads of updates, but there will be less of these in the future. It's best to install all of these as they are either bug fixes or security updates. Unlike Windows linux is a proactive operating system for security updates as it fixes potential future problems which in theory may cause potential problems and are not due to actual security problems found in the outside world (unlike Windows fixes which may occur after the (virus) problem has occurred and needs to be removed).

---

### Post by angel25 on 2009-03-14
can..some one tell me...how to go to ubuntu window from .......
the $ sign......or # sign......
pls......
i am able to do only commands......

---

### Post by Captain Camaro on 2009-03-14
> **Kevbert said:**
> Regarding updates. Initially you'll find you need to install loads of updates, but there will be less of these in the future. It's best to install all of these as they are either bug fixes or security updates. Unlike Windows linux is a proactive operating system for security updates as it fixes potential future problems which in theory may cause potential problems and are not due to actual security problems found in the outside world (unlike Windows fixes which may occur after the (virus) problem has occurred and needs to be removed).

Thanks for that, downloading and installing all updates now.
One confusing thing: Is Ubuntu using windows based drivers to use my hardware?  Or are drivers installed on my HD separate from and usable by any OS installed?

One of my biggest inconveniences on my laptop is that my CD/DVD drive will read and burn only DVDs, but nothing on CDs will register.  I've found ways around it, but I'd still like to eventually fix it one day.  I just checked and the problem is the same in Ubuntu as it was in Windows.  This confuses me, because I always thought it was a driver issue, and I always assumed drivers were OS-specific.  I guess I was wrong...

Thanks again folks,
Jared Allen

---

### Post by Admiral Yi on 2009-03-14
Just in case you were wondering, this is the grub boot menu. 

1)ubuntu
2)ubuntu (recovery mode)
3)ubuntu memtest+98
4)windows xp (or vista)

Ubuntu obviously starts normal ubuntu. The recovery boot goes back to a previous version of the kernel. If something goes wrong, try booting from this option to see if the problems still there. Memtest tests your RAM or errors, and the final option will boot you other OS.

Im pretty sure Ubuntu isn't using your Windows drives. I may be wrong (im no expert) but im pretty sure the drivers just come on the Ubuntu CD. Some things don't ahve drivers on the CD and need to be installed manually (graphics card maybe).

---

### Post by angel25 on 2009-03-14
pls...pls...pls.....help me with my ubuntu ....i need to know how to get ubuntu window . my mama told me to click....ctrl+alt+f1...
but nothing happened....
pls....help.....

---

### Post by angel25 on 2009-03-14
[QUOTE=Admiral Yi;6892591]Just in case you were wondering, this is the grub boot menu. 

1)ubuntu
2)ubuntu (recovery mode)
3)ubuntu memtest+98
4)windows xp (or vista)



i used 1st ubuntu and it never ended giving me informations...it went so on......and i had to restart the computer to stop it....
then i went to ubuntu (recovery mode) this helped me to get the # prompt and then the $ prompt....ibut i have restart always inorder to stop ubuntu.....
how do i solve this.....?

---

### Post by Captain Camaro on 2009-03-14
> **Admiral Yi said:**
> Just in case you were wondering, this is the grub boot menu. 

1)ubuntu
2)ubuntu (recovery mode)
3)ubuntu memtest+98
4)windows xp (or vista)

Ubuntu obviously starts normal ubuntu. The recovery boot goes back to a previous version of the kernel. If something goes wrong, try booting from this option to see if the problems still there. Memtest tests your RAM or errors, and the final option will boot you other OS.

Im pretty sure Ubuntu isn't using your Windows drives. I may be wrong (im no expert) but im pretty sure the drivers just come on the Ubuntu CD. Some things don't ahve drivers on the CD and need to be installed manually (graphics card maybe).

So you think that maybe the install disk for Ubuntu has several common hardware drivers available?  Interesting.  Can I view these somewhere inside Ubuntu?  I am completely lost in trying to view system info in this OS thus far.

Also, are there any good FAQs out there for using Evolution Mail?

Thanks Yi,
Jared Allen

---

### Post by carml on 2009-03-14
> **angel25 said:**
> [QUOTE=Admiral Yi;6892591]Just in case you were wondering, this is the grub boot menu. 

1)ubuntu
2)ubuntu (recovery mode)
3)ubuntu memtest+98
4)windows xp (or vista)



i used 1st ubuntu and it never ended giving me informations...it went so on......and i had to restart the computer to stop it....
then i went to ubuntu (recovery mode) this helped me to get the # prompt and then the $ prompt....ibut i have restart always inorder to stop ubuntu.....
how do i solve this.....?
If you choose the 2nd entry,you'll be prompted with some new entry:
recover broken packages;try fo fix x server; go to root;
choose the one with root,then type apt-get install ubuntu-desktop,wait until it finishes and you should be ok.
I don't remember exactly the messages on the entry,but those I wrote should be quite correct. :)

---

### Post by angel25 on 2009-03-14
> **Captain Camaro said:**
> So you think that maybe the install disk for Ubuntu has several common hardware drivers available?  Interesting.  Can I view these somewhere inside Ubuntu?  I am completely lost in trying to view system info in this OS thus far.

Also, are there any good FAQs out there for using Evolution Mail?

Thanks Yi,
Jared Allen

thats simple.....just type mail in your command prompt and you can view your mails

---

