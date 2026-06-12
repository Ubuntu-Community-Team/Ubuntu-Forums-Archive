---
title: "Problem Re-installing Windows 7"
date: 2009-05-30
forum: Installation &amp; Upgrades
---

### Post by Caesar Jaunty on 2009-05-30
Hello fellow members.

I recently tested out Linux Ubuntu 9.04. After a length of time evaluating Ubuntu I've found out that I was not yet ready for it. I wanted to switch back to Windows 7. During the installation of Windows 7. On the part where it asks where to install. It says I cannot install on the HDD because it is not formatted in NTFS. 

I wouldn't kno where to begin to get my HDD back to NTFS format. 

I am also VERY new to Linux. 

Please if somebody could help me get Windows 7 back on my system I would greatly appreciate it. TYVM

---

### Post by coffeecat on 2009-05-30
The problem is that you have (probably) two partitions there, one formatted ext3 for the Ubuntu root partition and a smaller swap partition, and neither filesystem is recognised by the Windows installer - although I am surprised that it doesn't offer to reformat the ext3 one. Anyway, you can use the Ubuntu live CD to delete both partitions and create an NTFS one.

Boot up with your Ubuntu 9.04 live CD and go to System > Administration > Partition Editor. First you need to unmount the swap partition which the live CD will have mounted already. Highlight the swap partition and in the Partition menu, select swapoff. You may have to click 'Apply' - I can't remember. Now highlight each partition in turn and click on delete. Now click on 'Apply' and both will be deleted.

You will now see one line showing 'unallocated' for the whole drive. Highlight this, click on 'New' and in the dialogue window that opens, select 'primary' for partition type and 'NTFS' for filesystem. You can also select a partition label if you want. Click on 'Apply' and when that's finished you are done. Shut down, boot up from the Windows 7 disc and you should be OK from there on.

If you want two NTFS partitions so that one is E:\ or whatever, you can do that easily in Gparted. When you get to the dialogue window for the first partition, simply select the size of partition you want. Then you select the remaining unallocated space for the second partition.

Good luck!

**Edit:** another thought. Are you sure that the Windows 7 installer disc doesn't have a partitioner? When I installed W7, I had already set up a NTFS partition so I didn't have to use this, but I'm sure that before you get to the install step, there's an option to partition up your disc. It won't like what it finds, but it should be able to create a new NTFS partition. There certainly was a partitioner on the Vista install disc, and the W7 one isn't that much different.

Anyway, if there isn't or you can't find it, using the Ubuntu live CD is the answer.

---

### Post by Caesar Jaunty on 2009-05-30
I appreciate the quick respose. And I concur that GParted will definately do the job. I just popped the cd in and restarted. Right clicked on my drive and ticked format to NTFS. This wiped the whole drive as it was restarting I popped the Win7 disc in and Bam. Windows 7 in less than 15 minutes.

Linux Ubuntu by far has the Best graphical interface I've yet to see.. But I hate the way it revolves itself around DOS [Terminal].. Linux makes programs so hard to install.. I gotta add repos and software sources then type 5-6 entries into the terminal just to get to the installer.

If only u could put an executable file on the desktop and install it. But then I guess they would just call it windows then lol.. I just hate the fact that I have to google everytime I want to install a program..

Maybe in the future when I get a new computer.. I can use this one to learn linux.. But at the moment, I think I will stick with Windows 7 as my primary.

---

### Post by Mark Phelps on 2009-05-30
While it's great that you were able to get tech support for Windows 7 on the "Ubuntu forums", in future, you should consider going to the Windows seven forums for help.  Their address is linked below:

[http://www.sevenforums.com/]("http://www.sevenforums.com/")

---

### Post by Caesar Jaunty on 2009-05-30
For your information.. I did go to a Windows 7 forum as well. But why would I ask a Windows user how to format a Linux drive?? 

And who do think think you are anyway Mr. Ubuntu Forum??

How bout you just stick to answering questions and leave the order giving to someone else.

---

### Post by mocoloco on 2009-05-30
> **Caesar Jaunty said:**
> But why would I ask a Windows user how to format a Linux drive?

Because there's no such thing as a "Linux drive", it's just the partition that is for Linux/Unix; the installer should offer to reformat it no matter what. That's what the XP installer does.

Incidentally you're not the only one who noticed this problem. [URL="http://blogs.computerworld.com/installing_windows_7_with_some_linux_help"]Installing Windows 7 with some Linux help
[/URL]

---

### Post by Mark Phelps on 2009-05-30
> **Caesar Jaunty said:**
> For your information.. I did go to a Windows 7 forum as well. But why would I ask a Windows user how to format a Linux drive?? 

Maybe Mr. ATTITUDE, because there is no such thing as a "Linux drive"!  
> 
And who do think think you are anyway Mr. Ubuntu Forum??

Too stupid a question to deserve an answer.
> 
How bout you just stick to answering questions and leave the order giving to someone else.
I wasn't giving any orders; I was providing an alternate forum address where you could find answers to detailed Windows 7 problems -- like how to force it to reformat your "Linux drive".

Excuse me for trying to be helpful.  Next time I see any post from you, I'll be sure NOT to provide any help.

---

### Post by Caesar Jaunty on 2009-05-30
TY for the informative thread mocoloco.. Helps me from looking crazy.

And what I meant by "Linux Drive" was a HDD that was specifically formatted for Linux.. lol When I installed Ubuntu, It turned it into a format other than NTFS. I couldn't even tell you what format it was because I've only used Linux for about 3 days. All I kno is that it certainly wasnt NTFS which is required by Windows.

On the Windows 7 installation process.. when I clicked on the drive. I couldn't format, I couldnt delete.. All it said is there was an error. When I clicked the Learn More link it told me that the HDD needed to be formatted in NTFS and it wasn't. Said it was a format not recognized by Windows.

So first thing I did was go to the Windows 7 forums. all I got was a bunch of responses saying noone was familiar with Linux and couldn't help me. So then I thought why not go to the Ubuntu Forums. And I did.. and I posted. And I got a Very fast response [TY coffeecat] and it worked perfectly.

I am satisfied.


@Mark Phelps

I'm sorry it seemed if I had an attitude.. wasnt my intension. I was very frustrated with Linux and not being able to get back to Windows made it even worse. I took that post as you saying "go back to punk *** Windows then.. and while you at it keep your *** out my Linux forums"


Linux/Windows/Mac doesn't matter to me.. if I can help then I will.

---

### Post by coffeecat on 2009-05-31
> **Caesar Jaunty said:**
> But I hate the way it revolves itself around DOS [Terminal]

No, it doesn't.

> **Caesar Jaunty said:**
> .. Linux makes programs so hard to install..

No, they aren't.

> **Caesar Jaunty said:**
> I gotta add repos and software sources then type 5-6 entries into the terminal just to get to the installer.

No, you don't.

> **Caesar Jaunty said:**
>  If only u could put an executable file on the desktop and install it.

Yes, you can. (Well, strictly not an executable, but the same effect without compromising security.) 

Grasshopper, you have much to learn! :wink:

[Here's a good start on some general points]("http://linux.oneandoneis2.org/LNW.htm").

In the meantime, fyi, you obviously didn't find the Add/Remove utility in the Applications menu. It's nothing like the Windows Add/Remove abomination and for a Windows user it's a revelation. Since the four main repositories (main, restricted, universe, multiverse) are enabled by default, this will cater for >95% of your software needs - seriously. And it's about the most user-friendly and easy to use GUI app I've ever come across. And that's from someone who uses a Mac as well. :)

---

### Post by Jestersage on 2009-05-31
And if you know the name of the software package, just go to synaptic, click on it, and it will throw in all the nice dependency. Not as good looking as YaST, but does it job far better and simpler.

---

### Post by Mark Phelps on 2009-05-31
> **Caesar Jaunty said:**
> I'm sorry it seemed if I had an attitude.. wasnt my intension. 

OK, rereading my post, it came off stronger than I had intended. I didn't mean it to be insulting; I was only trying to provide an alternative forum that might be able to provide more detailed answers.  And, I'm sorry they didn't treat you well there.

I'm not a Seven expert at all, but I do know that in Vista, you can boot to a command line from the DVD and run a whole bunch of DOS-like commands, including those to format your drive (like used to be done in DOS with fdisk).  I've not tried that in Seven, so I don't have any details to help you.

---

### Post by jhahoneyk on 2009-06-08
> Linux Ubuntu by far has the Best graphical interface I've yet to see.. But I hate the way it revolves itself around DOS [Terminal]..
Not true, the Terminal is just more powerful than the GUI. You use the terminal when there are things the GUI can't perform. In GNU/Linux, when GUI isn't enough, you have the option of a powerful command line, but in Windows, if its not in the GUI, you can't do it. (I've used windows for 8 years, learnt not much, used ubuntu for 1 year, learned a LOT)

> Linux makes programs so hard to install.. I gotta add repos and software sources then type 5-6 entries into the terminal just to get to the installer.
Nup, mostly, all software is available in Applications>Add/Remove. there is no need to use the terminal. (though I personally use the terminal only because I prefer typing, it saves time)

> If only u could put an executable file on the desktop and install it. But then I guess they would just call it windows then lol.. I just hate the fact that I have to google everytime I want to install a program..
Ok, so everytime you want to install a Windows program, you wink your eyes and tada! the installer comes at the desktop. Its not, right? So, for a windows program, you have to google, download the installer, and then install it. For Ubuntu (for general apps), goto Applications>Add/remove Programs, search the app name, select, click Install, done.

> Maybe in the future when I get a new computer.. I can use this one to learn linux.. But at the moment, I think I will stick with Windows 7 as my primary.
Sure, but just a personal opinion, Windows makes you use the system, GNU/Linux makes you learn the system.
Both are easy. Its just that if you have too many Windows habits, they aren't same in GNU/Linux, and then you complain. If a person never used Windows and always used Ubuntu, he'll say that Windows isn't user friendly (I've checked this on one of my friend).
Anyway, all the best :)

(If you're referring to the complete OS, its called GNU/Linux.)

---

### Post by Caesar Jaunty on 2009-06-15
[B]Wow I didnt kno this post continued this long.. I had the wrong opinion of you guys. I figured I'd check up on this thread and see how many "hate" replies there were for the "windows 7" user.

But after reading them all.. I've found alot of helpful replies..



In response:


I've heard so many great things about linux.. And I'm the type of person that switches OS's quite often between different customized versions of XP, Vista and seven. So I you tubed linux a little bit. Mostly saw Ubuntu. I seen it setup similar to a mac with the dock navigation.

I said to myself right then that I had to have it. When I got it.. I admit I wasnt used to it. But I thought to myself, Ima learn it. So I figured I could just google for a few days as long as I didnt have a problem surfing. After 3 days I was still completely lost. Frustrated.. wanted my 7 back so bad.

I tried installing programs from the Add/Remove.. I tried installing from synaptic.. and I would see them download and install.. But after they were done I would look in the menus and not see them as I would in windows. I wouldnt even kno how to bring up the program to configure preferences and options. 

One in particular was the firewall.. does that run in the background.

Grasshopper Indeed!! lol

Anyways.. I dont wanna write a book here.. I'm still interested in learning linux ubuntu.. Just dont think I could stand being in the dark for months while I'm learning.

Maybe I'll get it reinstalled in a virtual box or use the wubi? installer to dual boot.

None the less I appreciate the responses



[/B]

---

### Post by jhahoneyk on 2009-06-15
> Wow I didnt kno this post continued this long.. I had the wrong opinion of you guys. I figured I'd check up on this thread and see how many "hate" replies there were for the "windows 7" user.

We do not hate any OS, the free software philosophy is "You are the user and you're FREE to choose whatever you want".

> I tried installing programs from the Add/Remove.. I tried installing from synaptic.. and I would see them download and install.. But after they were done I would look in the menus and not see them as I would in windows. I wouldnt even kno how to bring up the program to configure preferences and options. 

One in particular was the firewall.. does that run in the background.

Grasshopper Indeed!! lol

Anyways.. I dont wanna write a book here.. I'm still interested in learning linux ubuntu.. Just dont think I could stand being in the dark for months while I'm learning.

Its nice, and I really appreciate people like you who want to LEARN. And frankly, its only for such people gnu/linux exists.

> Maybe I'll get it reinstalled in a virtual box or use the wubi? installer to dual boot.

1.Virtual Box-
Make sure you have enough RAM running two OSes. Ubuntu would always be < 512 in most cases. Rest whatever 7 wants.
2.Wubi-
Say, if you install ubuntu on D: drive , you won't be able to access D: partition from ubuntu (Wubi limitation). (BTW, this my observation. if someone finds I'm incorrect here, please correct).

In both cases, performance won't be as good as normal install. But enough to learn, all the best.

---

### Post by Caesar Jaunty on 2009-06-15
If I did decide to run in VirtualBox I would dedicate 1GB to each OS. Which I think I would do because I'd be able to learn linux and still be to instantly switch back to windows to perform tasks without having to reboot.

I just need to find some good video tutorials on using ubuntu.

---

### Post by Mark Phelps on 2009-06-15
Caesar:

If you read my tagline, you saw that I, too, am a "Seven" user, and like so many others here, use a variety of OSs for a variety of reasons.  I also don't "hate" any OSs (or OS users, for that matter).  My philosophy is simple -- use what works best for you.

You're certainly free to try to run Seven using virtualbox, but if you interested in experiencing real-time performance first-hand, that's not the way to do it. Dual-booting is a much better approach, especially since the versions are leaking on a weekly basis and reinstalling the Virtualbox version every week to keep up with the latest and greatest could be a major piece of work.

---

### Post by mocoloco on 2009-06-16
Glad to hear you haven't given up completely. Even if you never use it as your main OS it's always good to have new skills, and for geeks like us (including you) it's fun!
I would recommend a full install rather than using a VM. Besides speed, while booted in to it you're forced to use it instead of just switching out of the VM to do something, but you're hands aren't completely tied; if you need to get something done you don't know how to do you can still reboot back to Windows.  Wubi is a great approach for a "temporary" trial you can easily  remove and re-do, but is nearly as fast as a "real" install.
I would also point out that your plight not just an Ubuntu/Linux thing, it's a learning a new OS thing, after being a poweruser on Windows. If you're not already familiar with Mac OS X you would run in to similar frustrations and confusion since there are things that are approached very differently. I know, because that was me a couple of years ago when I got my first Mac, it was very humbling :). But it's not as hard as you might think, once you learn the major differences you'll get the hang of it.

---

### Post by Caesar Jaunty on 2009-06-16
> You're certainly free to try to run Seven using virtualbox, but if you interested in experiencing real-time performance first-hand, that's not the way to do it. Dual-booting is a much better approach, especially since the versions are leaking on a weekly basis and reinstalling the Virtualbox version every week to keep up with the latest and greatest could be a major piece of work.

I'm actually running Windows 7 RC v7100 as my primary OS. The RTM build has leaked but i'm not too interested in getting every update build out there. I got the RC version and it is stable so far so I will stick with it for now.



> Glad to hear you haven't given up completely. Even if you never use it as your main OS it's always good to have new skills, and for geeks like us (including you) it's fun!
I would recommend a full install rather than using a VM. Besides speed, while booted in to it you're forced to use it instead of just switching out of the VM to do something, but you're hands aren't completely tied; if you need to get something done you don't know how to do you can still reboot back to Windows. Wubi is a great approach for a "temporary" trial you can easily remove and re-do, but is nearly as fast as a "real" install.
I would also point out that your plight not just an Ubuntu/Linux thing, it's a learning a new OS thing, after being a poweruser on Windows. If you're not already familiar with Mac OS X you would run in to similar frustrations and confusion since there are things that are approached very differently.


Yes I havn't given up nor will I. I've seen the capabilities of Linux and I would like to achieve them. I'm just the type of guy that needs hands on training before I can pick stuff up. For example, I've been trying to learn dreamweaver.. I've read at least 20 "basics" text tutorials.. still never understood it. Then I found some HiDef college course video tutorials on YouTube and had my website up and running that very same day.

I currently have Linux Ubuntu 9.04 installed in a VM.. I think I will keep it like that until i figure out the basic functions and navigations.. after that I will try the wubi dual boot and continue with that until I can master the installations and upgrades. Then after I am quite comfortable.. make it my primary operating system.

I said in an earlier post that I jump from OS to OS quite frequently. Maybe it is because I have not yet found an OS that meets my standards. Maybe Ubuntu is my calling. But the basic default interface is quite intimidating. Makes it look like it's not capable of anything compared to windows. Although I kno otherwise. 


I'd like to achieve these sick graphical interfaces that i've been seeing everytime I google Linux. Also have ALL my programs in the dock similar to Mac OSX.

If someone can give me a few encouraging tips or point me in the right direction on howto learn and customize this OS I would greatly appreciate it.

---

