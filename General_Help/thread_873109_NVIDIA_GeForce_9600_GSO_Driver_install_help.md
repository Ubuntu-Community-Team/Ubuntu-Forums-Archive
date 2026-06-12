---
title: "NVIDIA GeForce 9600 GSO Driver install help"
date: 2008-07-28
forum: General Help
---

### Post by hotrod6657 on 2008-07-28
I finished building my first computer a week ago and finally got all my operating systems installed and I need a little help on the Ubuntu front.

Like the title says i have a GeForce 9600 GSO card.  I can't enable desktop effects so I'm assuming it's because i don't have the proper drivers installed.

NVIDIA's website has Linux 64 bit drivers for the card but i can't quite get them installed.  Here's a link to the driver:  [http://www.nvidia.co.uk/object/linux_display_amd64_173.14.05_uk.html]("http://www.nvidia.co.uk/object/linux_display_amd64_173.14.05_uk.html")

It downloads fine, i move it to my home directory, exit X and type the command to execute it.

It does a little, asks me to accept the license agreement (which i do), and then tells me there is no precompiled kernel interface found matching my kernel.

It asks if I would like the installer to attempt to download a kernel interface, so i say yes.  Then it says no interface was found meaning the installer will need to compile a kernel interface for my kernel.

I say ok

then i get an ERROR:  you do not appear to have libc header files installed on your system.  Please install your distribution's libc development package.

I have a feeling that this will be a simple thing to install from the packet manager, but i just don't know what to look for.  Any help?


Okay, that's what i was going to post, but before i did i managed to find this thread:

[http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-install-an-nvidia-driver-600920/]("http://www.linuxquestions.org/questions/linux-newbie-8/how-do-i-install-an-nvidia-driver-600920/")

Which answered my question in the second to last post.

simply needed to **sudo aptitude install build-essential**

installed that, exited X again, ran the installer and everything is good.  Visual effects work, i get the NVIDIA logo in login, everything is cool.  (way easier than what i had to do on my old ATI mobility card lol)

I just figured i would post my question and my answer in the same post incase anyone else was having similar problems.

That driver covers the following cards:

    *  Quadro FX 3600M
    * GeForce 9800 GX2
    * GeForce 9800 GTX
    * GeForce 9600 GT
    * GeForce 9600 GSO
    * GeForce 9600 GS
    * GeForce 9500M GS
    * GeForce 8400
    * GeForce 8400 GS
and there are other drivers on NVIDIA's website that should cover almost everything.

long live Ubuntu!

hotrod

---

### Post by gtrtx on 2008-07-28
You need to install the linux kernel headers. You can find these in synaptic or at a terminal:


sudo apt-get install linux-kernel-headers


Another option is to install envy from the repos and let it do all the work....

sudo apt-get install envyng-core envyng-gtk

Envy will install the latest nvidia drivers for your card.

---

### Post by hotrod6657 on 2008-07-28
scratch that, everything is not alright...  It was fine until i rebooted the computer and was then told i was running in low graphics mode.  I'm working on figuring it out, but i'm not sure what to really do.

Any suggestions?  If i figure it out i'll post another reply.

---

### Post by gtrtx on 2008-07-28
oh crud....my bad. I only read a part of your first post. 

I would really try the envy route. I had problems installing the driver from nvidia and Envy did for me without issue. 

I have a different card however, the 8600 GT.

The 9x being as new as they are do seem to have issues from what I've gathered. 

Another thing that I've noticed is that the Nvidia website only offers 173.14.05 whereas Envy installs 173.14.09...which is newer.

[http://www.nvnews.net/vbulletin/showthread.php?t=114873](http://www.nvnews.net/vbulletin/showthread.php?t=114873)

while it doesn't mention the issues you are experiencing it stands to reason that perhaps even a new driver would better support your newer card.

---

### Post by hotrod6657 on 2008-07-28
gtrtx:  Thanks for the advice.  Next time i have to do this i will give that a shot!

Luckly this page:  [http://ubuntuforums.org/archive/index.php/t-763236.html]("http://ubuntuforums.org/archive/index.php/t-763236.html")
Seems to have done the trick.  I followed its steps and the only thing different than what i had done before was entering this:  "nano /etc/default/linux-restricted-modules-common."  And adding "nv" to the DISABLED_MODULES entry.

I've restarted the system a few times and it seems to be working so far.  No low graphics mode or anything like that and desktop effects are once again enabled.

If it breaks this time I'll be using the other suggestion in this thread.

It is weird that envy would install newer drivers than the NVIDIA site... I wonder if they're more of a beta or something.

Would there be a relatively risk free way of going from the NVIDIA driver I'm using to the one envy uses?

---

### Post by knightcoder on 2008-07-28
Linux drivers are mostly made by developers themselves, not the manufacturer.

---

### Post by hotrod6657 on 2008-07-28
right, i've gathered that.  And given that i have a fairly new card i'm not sprised that issues exist.  It is nice of NVIDIA to at least offer drivers.  

Okay, installed all my updates and restarted and got the same low-graphics mode stuff... envy here i come.

I hope that goes smoothly

---

### Post by gtrtx on 2008-07-28
Well,

I don't know why they haven't updated the website to the latest driver. Best that I can tell, the Envy driver isn't beta. 

I'll keep my fingers crossed that it works for you.

---

### Post by hotrod6657 on 2008-07-28
haha, yeah, who knows.  Thanks for the keeping your fingers crossed.  It wouldn't be so bad if it just didn't work when i installed the other driver, but it's the fact that it works for a while and then stops that gets annoying.  I'm glad that reinstalling Ubuntu is a pretty simple task.

I should be giving envy a shot in a few minuets so i'll post results afterwards.

(i'll do my updates before installing it this time too)

---

### Post by knightcoder on 2008-07-28
Good luck man! And don't forget to pray :)

---

### Post by hotrod6657 on 2008-07-28
haha, yeah, it couldn't hurt.  I know that getting this done on my thinkpad too forever the first time.  That's ATI, this is NVIDIA but same sort of thing.  Once i got it working the first time it was a piece of cake to do again, it's just getting that first one done.

I see on envy's site that this should work for ATI cards too...  I may be playing with Ubuntu on my laptop again soon too...

---

### Post by hotrod6657 on 2008-07-28
i hesitate to say this but i think it worked...  I had to manually select the driver from envy's GUI since it couldn't automatically detect mine (likely because of how new it is) but after doing that and running the installer it restarted and everything seems to be okay.

I enabled advanced effects and restarted again and still seems okay.  I'm a little hesitant to start adding programs and files to this right now incase i loose it again, but I'll just keep it simple and keep some backups.

@gtrtx -  Thanks again for turning me on to envy.  That was way easier than the other method and it appears to have actually worked lol.

If it breaks down again i'll be sure to post haha.

hotrod

---

### Post by gtrtx on 2008-07-28
Cool....

I hope it stays working for you.  Your card will be better supported in time. 

I've been using Nvidia cards with linux for over 10 years now. Sometimes support for newer cards can start out a bit rocky, but it usually levels out.  Usually I stay about 8-16 months behind the newest technology(mostly cuz I can't afford the stuff when it's first released) and it helps me to keep system running that's well supported under linux. 

Anywho, lets hope it keeps chuggin along for ya and if you need help with anything else just hollar!

take care,

tx

---

### Post by hotrod6657 on 2008-07-29
Thanks a lot, i really appreciate that!  I've just accepted that this is how it is the Linux and new cards.  The fact that everything is free and there are communities like this around more than makes up for that fact.

This is my first NVIDIA card (i've had a few desktops with on board NVIDIA graphics) and so far so good!

like i said, I messed with this sort of stuff with my ATI card in my laptop so neither brand seems to have the market cornered in terms of linux compatibility.  (though i have heard that NVIDIA is typically better supported.

Thanks again!

hotrod

---

