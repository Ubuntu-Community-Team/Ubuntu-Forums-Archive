---
title: "[SOLVED] Switching back to Windows..."
date: 2008-10-29
forum: General Help
---

### Post by Zohso on 2008-10-29
Well, I have been using Ubuntu for over a few months now and decided to make Ubuntu my primary desktop.  I still use Windows for 3 reasons:  1) SolidWorks 2009; 2) ProEngineer Wildfire 4; and 3) Games in general.  

First off, I am a Mechanical Design Engineer for a company manufacturing armor for our military vehicles over in Iraq and the rest of the world.  I use SolidWorks and ProEngineer to do the design work.

I have been able to find excellent alternatives to everything I do, minus Design Engineering and gaming.

I came to the realization that I will always need to dual-boot Windows.  I have contacted the people at Dasault (the owners of SolidWorks) and they have confirmed that they do not see support for Linux in the near future.  They have a very strong relationship with Microsoft.  I also contacted PTC (the owners of ProEngineer) and they have dropped their support for Linux as of last year.  Their reasoning was lack of interest from the engineering community.

I have put a lot of time into Linux and would hate to have to leave the Linux/Unbuntu community; but I think I have no choice.  

So, I will be looking into going with Vista.  Eek!  That means upwards of $1500 for a new system that can handle the hog that is Vista.  Kubuntu 8.1 works flawlessly and is beautiful.  Vista however runs very choppy.  

Someone please give some words of encouragement.  lol  I'm at a loss here.

---

### Post by alienprdkt on 2008-10-29
Could try running your Microsoft OS and needed apps with a virtual machine?

vmware, or virtual box?

vmware:
[http://vmware.com/](http://vmware.com/)
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

virtualbox (which I like to use):

[http://www.virtualbox.org/](http://www.virtualbox.org/)
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by Portmanteaufu on 2008-10-29
I have a number of friends that have set up Windows XP in a virtual machine in order to continue using one or two pieces of software that they couldn't leave behind for work reasons. All of them have reported that it runs very smoothly -- maybe it's something to consider? Unfortunately, I'm not that well-versed on the topic.

Is there someone more knowledgeable about the subject that could offer their perspective?

---

### Post by roger_1960 on 2008-10-29
Hi

Have you tested these apps with WINE or crossover? May not work, but worth checking..

---

### Post by bodhi.zazen on 2008-10-29
As long as you are needing to run proprietary applications written for a proprietary OS you will be dependent on that proprietary OS. 

The crux of the issue is that there remain a few niche applications for which there is not yet a viable opensource option. This list includes such things as voice recognition and profession specific applications such as doctors/nurse/health care, lawyers, I would venture CAD, and accounting.

You might want to look into running Vista in VMWare or Virtualbox, although you will still need to purchase the various licenses.

---

### Post by alienprdkt on 2008-10-29
> **roger_1960 said:**
> Hi

Have you tested these apps with WINE or crossover? May not work, but worth checking..

Also note that some apps have errors during install with wine. 
I have been able to fix this by copying the application from the Program Files directory with the windows file system and pasting it to the Program Files directory within WINE. Then install runs with no errors (well it worked for Ableton Live).

---

### Post by zoomy942 on 2008-10-29
As an admin of an entire company I will give you advice.

First, MS Windows is like a security blanket to most people.  They feel this unexplainable need to use it, when - outside of 3D design (and games), you can accomplsh everything you need with a Linux platform.

For example, we use several systems here that are 100% NOT Linux compatible  but that does not stop me.  I use Sun VirtualBox and have those 2 or 3 apps loaded in there and it works perfectly.  You can even press CTRL F and have it in full screen mode and you would never know it was a guest OS inside Linux.  Even moreso, if you somehow manage to break Windows (virus, DLL file, anything....) inside the VM, you can simply reload the VM from an image and you are done!  No reloading windows and all your apps.

Trust me when i say this... you are not forced to use Windows - MS wants you to think that.  Cage up Windows in a Virtual Machine where it belongs.  I have been running my company, and providing support for a while now, with a 100% Linux (Ubuntu desktop and Xubuntu Tablet PC) with Windows in a VM and I havent had any troubles or ran into any times i was unable to support my users.

---

### Post by 73ckn797 on 2008-10-29
Ditto on VirtualBox to run Windows. I have to for one website used for my work and for another program that cannot run through Wine.

"Shane, Shane, don't go"!!:)

---

### Post by Zohso on 2008-10-29
> **zoomy942 said:**
> As an admin of an entire company I will give you advice.

First, MS Windows is like a security blanket to most people.  They feel this unexplainable need to use it, when - outside of 3D design (and games), you can accomplsh everything you need with a Linux platform.

For example, we use several systems here that are 100% NOT Linux compatible  but that does not stop me.  I use Sun VirtualBox and have those 2 or 3 apps loaded in there and it works perfectly.  You can even press CTRL F and have it in full screen mode and you would never know it was a guest OS inside Linux.  Even moreso, if you somehow manage to break Windows (virus, DLL file, anything....) inside the VM, you can simply reload the VM from an image and you are done!  No reloading windows and all your apps.

Trust me when i say this... you are not forced to use Windows - MS wants you to think that.  Cage up Windows in a Virtual Machine where it belongs.  I have been running my company, and providing support for a while now, with a 100% Linux (Ubuntu desktop and Xubuntu Tablet PC) with Windows in a VM and I havent had any troubles or ran into any times i was unable to support my users.

First off, do I need a "Legal" copy of windows?  Does a virtual machine act like a computer that I would essentially install windows on?

If this is the case, this is my reasoning behind just simply going with Windows:
If I am going to be purchasing a full licensed copy of MS Vista, then I might as well go ahead and make the switch completely.  The initial benefit I seen with Linux is it's Freedom mentality.  But if I'm still tied to MS, then I'm not totally free.  

I basically want to go one way or the other - obviously I'd rather that way be Linux; but you get my point.

---

### Post by zoomy942 on 2008-10-29
> **Zohso said:**
> First off, do I need a "Legal" copy of windows?  Does a virtual machine act like a computer that I would essentially install windows on?

If this is the case, this is my reasoning behind just simply going with Windows:
If I am going to be purchasing a full licensed copy of MS Vista, then I might as well go ahead and make the switch completely.  The initial benefit I seen with Linux is it's Freedom mentality.  But if I'm still tied to MS, then I'm not totally free.  

I basically want to go one way or the other - obviously I'd rather that way be Linux; but you get my point.

The legality if your Windows install is up to you - can't get into that here for fear of getting in trouble.

That being said, I understand what you mean about not being totally free; however I don't completely agree.

To me, being free means being in control, dictating what my PC does and deciding how I want to use it.  Windows will not allow this.  You must do things a certain way, and you must follow their guidelines.  With Linux, I can install, adjust and change just about anything I want.  

Outside of that, install Windows, but don't forget to install the mandatory virus scanning and mandatory spyware and be watchful for exploits and rootkits.  Since I have switched to Linux and use Windows in a VM, I can compute 100% fearlessly becasue I know I will not become part of a botnet and I dont care about "the latest virus panic." 

The benefits of Linux are vast once you think of it outside of Freedon only.  To me, in my small bubble, wrapping Windows in a VM, and having it not affect anything if it gets broken, it truely powerful.  No longer am I at the mercy of MS and it's way of working..  I merely use Windows as a tool to accomplish a few tasks, then Linux does everything else I need.

---

### Post by Zohso on 2008-10-29
> **zoomy942 said:**
> The legality if your Windows install is up to you - can't get into that here for fear of getting in trouble.

That being said, I understand what you mean about not being totally free; however I don't completely agree.

To me, being free means being in control, dictating what my PC does and deciding how I want to use it.  Windows will not allow this.  You must do things a certain way, and you must follow their guidelines.  With Linux, I can install, adjust and change just about anything I want.  

Outside of that, install Windows, but don't forget to install the mandatory virus scanning and mandatory spyware and be watchful for exploits and rootkits.  Since I have switched to Linux and use Windows in a VM, I can compute 100% fearlessly becasue I know I will not become part of a botnet and I dont care about "the latest virus panic." 

The benefits of Linux are vast once you think of it outside of Freedon only.  To me, in my small bubble, wrapping Windows in a VM, and having it not affect anything if it gets broken, it truely powerful.  No longer am I at the mercy of MS and it's way of working..  I merely use Windows as a tool to accomplish a few tasks, then Linux does everything else I need.

Wow, well put, thank you. I didn't really look at it that way. Also, thank you to everyone else who basicly responded with the same solution, I just didn't get it until now.

I will research VM and VirtualBox. I will update everyone as to my findings - if nothing, for the engineering community. I have been searching, and it appears that engineer Linux users are sparse, if at all.  Atleast from my experience.

Again, thanks to all; and I will update as I go. =D>

---

### Post by zoomy942 on 2008-10-29
> **Zohso said:**
> Wow, well put, thank you. I didn't really look at it that way. Also, thank you to everyone else who basicly responded with the same solution, I just didn't get it until now.

I will research VM and VirtualBox. I will update everyone as to my findings - if nothing, for the engineering community. I have been searching, and it appears that engineer Linux users are sparse, if at all.  Atleast from my experience.

Again, thanks to all; and I will update as I go. =D>


Thanks my friend.

As for VMWare vs VirtualBox; they accomplish the exact same thing so it comes down to feature set.  I prefer VirtualBox A) becasue it is completely free and B) has a smaller footprint than VMWare.  Also, it just seems "cleaner" if that makes any sense.

If you need any VirtualBox help, let me know.

---

### Post by Zohso on 2008-10-29
[I]--Replying to zoom942--
"If you need any VirtualBox help, let me know."[/I]

I will, again, thank you. 

I just got excited once again. Almost like the day I made the decision to leave Windows.

---

### Post by Dragonbite on 2008-10-29
Where I work, we use virtual machines for our development environment (IIS Server).  It is made identical to our production environment so we can build and test things out before we push them into production. These virtual machines are running on an openSUSE server.

While the tools I use are Microsoft Windows based (Visual Studio, Adobe Acrobat, etc.) the concept of having the dev environment run in a virtual machine on a linux box should theoretically run on my laptop for the non-cross platform tools and use Linux variants whenever possible (office files, ms exchange, etc.).

Then again, I just got CrossOver yesterday so I am going to try my apps out on that and find out if that would work better than virtualizing.

---

### Post by zoomy942 on 2008-10-29
> **Dragonbite said:**
> Where I work, we use virtual machines for our development environment (IIS Server).  It is made identical to our production environment so we can build and test things out before we push them into production. These virtual machines are running on an openSUSE server.

While the tools I use are Microsoft Windows based (Visual Studio, Adobe Acrobat, etc.) the concept of having the dev environment run in a virtual machine on a linux box should theoretically run on my laptop for the non-cross platform tools and use Linux variants whenever possible (office files, ms exchange, etc.).

Then again, I just got CrossOver yesterday so I am going to try my apps out on that and find out if that would work better than virtualizing.


I have Crossover as well.  All in all, it works very very well.  MS Office 2007 is still a little temperamental, so save your work alot.  As for other applications, I have had zero troubles, which is pretty amazing to be honest.

---

### Post by starcannon on 2008-10-29
Wish I had words of encouragement for you :(
But dual booting seems like your best option for now.

I will say I'm a bit amazed that the engineering community showed a lack of interest in Linux, would have thought most engineers would be loving it. Anyway, perhaps you can have your cake and eat it too, boot windows for the job, and Ubuntu for your personal life?

GL and sorry to here your in a no win situation with the software that pays the bills.

---

### Post by zoomy942 on 2008-10-29
> **starcannon said:**
> Wish I had words of encouragement for you :(
But dual booting seems like your best option for now.

I will say I'm a bit amazed that the engineering community showed a lack of interest in Linux, would have thought most engineers would be loving it. Anyway, perhaps you can have your cake and eat it too, boot windows for the job, and Ubuntu for your personal life?

GL and sorry to here your in a no win situation with the software that pays the bills.

Unless, of course, his aplications work in a VM environment... then there is no reason to dual boot.

---

### Post by starcannon on 2008-10-29
> **zoomy942 said:**
> Unless, of course, his aplications work in a VM environment... then there is no reason to dual boot.
He listed several that require 3D acceleration, I have not had much personal success with VM's doing a good job ad 3D; however, I hear that Apple may be fixing that in the not so distant future with *Opengs *I think it was, sorry forgot the details, and couldn't come up with the link to the article :(

---

### Post by zoomy942 on 2008-10-29
> **starcannon said:**
> He listed several that require 3D acceleration, I have not had much personal success with VM's doing a good job ad 3D; however, I hear that Apple may be fixing that in the not so distant future with *Opengs *I think it was, sorry forgot the details, and couldn't come up with the link to the article :(

Good call.  I have tested VMware recently, and version 6.5 supports 3D accel in the VM; which is pretty slick (and it's about time).

---

### Post by Zohso on 2008-10-29
> **starcannon said:**
> He listed several that require 3D acceleration, I have not had much personal success with VM's doing a good job ad 3D; however, I hear that Apple may be fixing that in the not so distant future with *Opengs *I think it was, sorry forgot the details, and couldn't come up with the link to the article :(

Both SolidWorks and ProE utilize the latest OpenGL formats.  And since Linux, correct me if I'm wrong, uses OpenGL aswell, there SHOULDN'T be a problem... right?

---

### Post by neighborlee on 2008-10-29
> **Zohso said:**
> Both SolidWorks and ProE utilize the latest OpenGL formats.  And since Linux, correct me if I'm wrong, uses OpenGL aswell, there SHOULDN'T be a problem... right?

Last I knew ( Post I read on nvidia forum, from a NVidia rep ), it was not possible to run 3d apps inside a VM so I'd be very careful and research that exhaustively before committing yourself :)

Running inside a VM is also going to cost you a bit in terms of OS sluggishness, but maybe the app you would be running ( assuming 3d will even work, and if you have a nvidia card no matter about vmware, it might be moot ) would behave 'ok' regardless,- all things to consider. On the point about containing a virus..no matter that Vista is running inside a VM, if you get hit by a virus, it is going to be able to do damage TO vista/your data possibly.

cheers
nl

---

### Post by KeyserSoze93 on 2008-10-29
> **neighborlee said:**
> Last I knew ( Post I read on nvidia forum, from a NVidia rep ), it was not possible to run 3d apps inside a VM so I'd be very careful and research that exhaustively before committing yourself :)

Running inside a VM is also going to cost you a bit in terms of OS sluggishness, but maybe the app you would be running ( assuming 3d will even work, and if you have a nvidia card no matter about vmware, it might be moot ) would behave 'ok' regardless,- all things to consider. On the point about containing a virus..no matter that Vista is running inside a VM, if you get hit by a virus, it is going to be able to do damage TO vista/your data possibly.

cheers
nl

What I do with my virtual machines to is install them and the create a duplicate of the fresh install. Then, if the OS goes down for any reason, I can just roll back to the fresh image.

---

### Post by zoomy942 on 2008-10-29
> **neighborlee said:**
> Last I knew ( Post I read on nvidia forum, from a NVidia rep ), it was not possible to run 3d apps inside a VM so I'd be very careful and research that exhaustively before committing yourself :)

Running inside a VM is also going to cost you a bit in terms of OS sluggishness, but maybe the app you would be running ( assuming 3d will even work, and if you have a nvidia card no matter about vmware, it might be moot ) would behave 'ok' regardless,- all things to consider. On the point about containing a virus..no matter that Vista is running inside a VM, if you get hit by a virus, it is going to be able to do damage TO vista/your data possibly.

cheers
nl


Again - 3D with VMware 6.5 is possible.

And yes - the OS has the potential to be sluggish, but on my Tablet PC with its 1.2 Dual Core my VM Windows XP runs fine.  If your system hardware is more powerful (everyone's is compared to my tablet..lol) you will be fine.

And yes, if Vista get a virus it's toast, VM or not.  But, my questions would be, why surf the web/do email in your VM vista and chance getting a virus - when you can do those things in Linux and not worry?  Go into Vista for your appz you need then get out.

---

### Post by jenkinbr on 2008-10-29
> **neighborlee said:**
> Last I knew ( Post I read on nvidia forum, from a NVidia rep ), it was not possible to run 3d apps inside a VM so I'd be very careful and research that exhaustively before committing yourself :)

Running inside a VM is also going to cost you a bit in terms of OS sluggishness, but maybe the app you would be running ( assuming 3d will even work, and if you have a nvidia card no matter about vmware, it might be moot ) would behave 'ok' regardless,- all things to consider. On the point about containing a virus..no matter that Vista is running inside a VM, if you get hit by a virus, it is going to be able to do damage TO vista/your data possibly.

cheers
nl

No experience with VMWare, but if you don't need networking resources, I would just disable networking for that VM alltogether.  (This can be done from within Windows, or possibly from VMWare itself.)

---

### Post by Zohso on 2008-10-30
Okay, I installed VirtualBox last night.  I must say, I'm extremely impressed with it's user-experience.  It guided a noob (me) right through everything.  I put my legal copy of windows in the drive and installed it inside the VirtualBox.

I set it to use 10gb with 1gb of RAM.  I'll probably have to play around with it a bit to find that sweet-spot for what I do, but I now have windows on my system.

Now, I need to install SolidWorks and see just how it will/will not work.

I'll keep you all posted...

---

### Post by zoomy942 on 2008-11-01
excellent!

I reinstalled Ubuntu and VB last night as well.  I got Windows all set with all the updates and it works great.  I am helping a friend of mine switch to Linux too, so if you need help with VB, let me know.

---

### Post by Dragonbite on 2008-11-01
All of this talk about virtualization is getting me thinking of putting Virtual Box on my desktop computer (when I get it set up) and throw Windows on it. Maybe a 2nd vb for a server for testing/developing.

Of course, first I need to up my RAM.. everything has 512 MB but the server/desktop/laptop can handle 4/2/2 GB (ea. respectively)

---

### Post by Zohso on 2008-11-01
Well... here's the latest update of my prolem.

Success!!!

I was able to successfully, and way too easily I felt, install the VirtualBox on my Ubuntu 8.1 system - right from the repositories.  it guided me through everything and was extremely painless.

I popped my windows XP disc in the drive, it immediately started installing windows inside the 'box.  I installed all the service packs and updates as needed... and done.

The final test, and the ultimate reason for the Virtualization to begin with, was to install SolidWorks (a 3d parametric CAD system) on my machine.

It installed without any errors whatsoever.  nice and smooth. I restarted the 'box and loaded up SolidWorks perfectly.

I just finished my first design a little while ago.  While it is a little slower than what I was used to, it's not overwhelmingly noticable. and yes, the 3d functionality works flawlessly.  it was actually pretty smooth, and solidworks is traditionally a resource hog.

thank you to everyone. this was an overall great experience. and Windows is back in a cage where it belongs.  lol

---

### Post by zoomy942 on 2008-11-01
> **Zohso said:**
> Well... here's the latest update of my prolem.

Success!!!

I was able to successfully, and way too easily I felt, install the VirtualBox on my Ubuntu 8.1 system - right from the repositories.  it guided me through everything and was extremely painless.

I popped my windows XP disc in the drive, it immediately started installing windows inside the 'box.  I installed all the service packs and updates as needed... and done.

The final test, and the ultimate reason for the Virtualization to begin with, was to install SolidWorks (a 3d parametric CAD system) on my machine.

It installed without any errors whatsoever.  nice and smooth. I restarted the 'box and loaded up SolidWorks perfectly.

I just finished my first design a little while ago.  While it is a little slower than what I was used to, it's not overwhelmingly noticable. and yes, the 3d functionality works flawlessly.  it was actually pretty smooth, and solidworks is traditionally a resource hog.

thank you to everyone. this was an overall great experience. and Windows is back in a cage where it belongs.  lol


Excellent to hear!!  There is nothing more pleasing than a SMOOTH transition to linux.  Sure, anyone can change over, but for it to go smoothly is the best kind of news.

I'm glad your program worked as you needed it to, and I agree that Virtual Box is simple and elegant, where VMWare may be more feature rich (depends on who you ask) but is more resource hungry.

I finished getting a friend of mine, who is a senior Microsoft consultant, switched over to Ubuntu 8.10 with VM's for Windows.  She loves it also, and her setup was very smooth.  I stayed on Pidgin all day to walk her through everything and make sure nothing scarey happened.  

2 success stories in one day!  Yahoo!

---

### Post by Dragonbite on 2008-11-02
> **Zohso said:**
> Well... here's the latest update of my prolem.

Success!!!

I was able to successfully, and way too easily I felt, install the VirtualBox on my Ubuntu 8.1 system - right from the repositories.  it guided me through everything and was extremely painless.

I popped my windows XP disc in the drive, it immediately started installing windows inside the 'box.  I installed all the service packs and updates as needed... and done.

The final test, and the ultimate reason for the Virtualization to begin with, was to install SolidWorks (a 3d parametric CAD system) on my machine.

It installed without any errors whatsoever.  nice and smooth. I restarted the 'box and loaded up SolidWorks perfectly.

I just finished my first design a little while ago.  While it is a little slower than what I was used to, it's not overwhelmingly noticable. and yes, the 3d functionality works flawlessly.  it was actually pretty smooth, and solidworks is traditionally a resource hog.

thank you to everyone. this was an overall great experience. and Windows is back in a cage where it belongs.  lol

Woo Hoo!  Congratz!

---

### Post by Taras.M.K on 2008-11-21
Your experience is really great to me :)
It helps me to move smoothly to linux. This solution is really valuable!

Also I'd like to know little more about 3D performance:
> **Zohso said:**
> I just finished my first design a little while ago.  While it is a little slower than what I was used to, it's not overwhelmingly noticable. and yes, the 3d functionality works flawlessly.  it was actually pretty smooth, and solidworks is traditionally a resource hog.
As I've caught it works quite well? Elder versions of SW had some options in preferences, so one could see whether it uses OpenGL, can you check it (well, I do not know what's about SW2009)? Did you work with assemblies, what about graphic performance with several scores of parts? What about ProE, does it run well too (at least from 3D performance side)?

---

### Post by Zohso on 2008-12-03
> **Taras.M.K said:**
> Your experience is really great to me :)
It helps me to move smoothly to linux. This solution is really valuable!

Also I'd like to know little more about 3D performance:

As I've caught it works quite well? Elder versions of SW had some options in preferences, so one could see whether it uses OpenGL, can you check it (well, I do not know what's about SW2009)? Did you work with assemblies, what about graphic performance with several scores of parts? What about ProE, does it run well too (at least from 3D performance side)?
I did turn off all of the fancy features in SolidWorks.  Since my card is not an OpenGL card, I had to run SolidWorks in software mode, and that does take a toll on performance - no hardware acceleration.

And while I did create some very basic assemblies, I wasn't able to try it out in a full blown environment like I do at work.  So yes, assemblies and drawings worked okay, but to what extent I am still unsure.

I hope THIS helps you.

---

### Post by Taras.M.K on 2008-12-18
Thanks, it gives to me better understanding what I can expect.

For those of us who's interested in it: new VirtualBox 2.1 includes OpenGl support! :)

---

### Post by swiftwood on 2008-12-30
Hello,

New to the forum, lots of useful information here!

After running WindozeXP for several years, I'm happily to be back on Linix.
I used to run in year ago, back when it was on several floppy disks, for those that remember those!

Like you I'm also running SolidWorks, which is why I've kept running Windoze in the 1st place.

I installed Ubuntu in dual-boot mode, so I can bring it back up for SolidWorks, but of course that means rebooting.

I took you tip an installed VirtualBox, but I haven't installed WindowsXP yet.

I had a harddisk failure a while back, I had also lost my system disks.
So, I had a new harddrive and system installed at CircuitCity a while back.

This left me with a running system, but no install disks for VirtualBox.

Can I access the install that's still on the harddrive like I do with Wine?

This would be great since I wouldn't need to take up more disk space.

Thanks

---

### Post by doughorne on 2008-12-31
I'm an Ubuntu newbie (love it), but I don't run anything heavy duty like you guys do.  Having said that,  this thread sure has made me want to go home and tinker around with Virtualbox, so that I might have access to some of the Windoze apps that I don't see any Linux equivalent for.  Awesome info.

---

