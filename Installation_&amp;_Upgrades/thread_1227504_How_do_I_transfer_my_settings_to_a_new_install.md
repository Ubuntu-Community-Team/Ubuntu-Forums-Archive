---
title: "How do I transfer my settings to a new install"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by davegk on 2009-07-30
I'm getting a new laptop delivered tomorrow and will replace HD with two new ones I just bought (need to keep the original [Vista] HD in case of warranty issue during the first year). I currently have a dual-boot laptop, with 9.04 & XP Pro - for about a month or so now, since I decided to switch to Linux. I shall not need to dual boot anymore, so the new laptop will only have ubuntu on it with CorelDRAW and Acrobat Pro in VirtualBox. 

I have customised my desktop with Cairo-Dock, Compiz etc, added some repositories and have my printers, scanner and Wacom tablet working perfectly. To be honest, I really do not want to go through all that again: it would be nice just to copy the settings and, ideally, programs to the new HD and start enjoying it :D  I shall have no problem transferring Thunderbird with all the stuff (done that once already), but the rest is far from clear to me :(

I have searched ubuntu forums and googled and googled and googled, but all I can see are various instructions as to how to clone the entire drive or partition - obviously not suitable in this case (different hadrware and no need for dual boot)...

Any help is greatly appreciated, especially with step-by-step [as in dummy] instructions!

Cheers,
Dave

---

### Post by merlinus on 2009-07-30
Most of your configurations and such reside in hidden directories in /home/user.  You can copy them via nautilus, and remember to choose Show Hidden Files (Ctrl+H).  These directories begin with a dot (.).

As for the apps themselves, other than the ones included on the ubuntu live cd you will have to install them again, but the configurations will be maintained.  Same with drivers for your peripherals, althoug someone may be able to suggest a way to save these.

---

### Post by davegk on 2009-07-30
Thanks,

So when I copy these, and then install the apps, they will assume the "old" settings etc? That's great! (unless I misunderstood something :() Same with themes and current custom theme in particular - all in /home/user? I do know about hidden files. 
Is it really that simple?

---

### Post by merlinus on 2009-07-30
It worked for me on my new machine.  As always, YMMV.

---

### Post by running_rabbit07 on 2009-07-30
If you install and run the program APTonCD you can make an install disk that will have all updates and some of your installed programs. Then after you reinstall you put the disk in and it will offer to open synaptic and let you install the updates and programs. Much faster than waiting on the network connection to download.

Also if you don't have one you may want to add a /home partition while reinstalling. I don't know much about all the other types of /stuff partitions but I am sure that they would help save programs during future reinstalls.

---

### Post by realzippy on 2009-07-30
maybe "remastersys" would be a solution for you.If your /home
is not too large so that the resulting image fits on DVD its
the perfect backup.

[http://klikit.pbworks.com/Remastersys+FAQ](http://klikit.pbworks.com/Remastersys+FAQ)

---

### Post by davegk on 2009-07-31
__Thanks, running_rabbit07 & realzippy, I'll certainly try APTonCD and remastersys.
As far as a separate partition for /home - I do want to do that, but don't remember been given the choice during install. How do I invoke this option?

Also all my old documents are still on an ntfs partition and on external backup drive, also ntfs. Is there anything special I need to do, when I copy them onto a ext3 (permissions, etc, etc)? It's a single user setup. I'm planning to re-format external drive to etx3 after that, although the laptop wil have 1TB internally, so external 320GB will not be of much use anymore :)

---

### Post by running_rabbit07 on 2009-07-31
> **davegk said:**
> Thanks, running_rabbit07 & realzippy, I'll certainly try APTonCD and remastersys.
As far as a separate partition for /home - I do want to do that, but don't remember been given the choice during install. How do I invoke this option?

Also all my old documents are still on an ntfs partition and on external backup drive, also ntfs. Is there anything special I need to do, when I copy them onto a ext3 (permissions, etc, etc)? It's a single user setup. I'm planning to re-format external drive to etx3 after that, although the laptop wil have 1TB internally, so external 320GB will not be of much use anymore :)

When you get to the partitioner setup during install you have to select partition manually and then you just make a small 10-15 Gig Partition for the / and the rest of the drive for /home. The /home will have all of your settings and all files that you normally save to Home folders. Then if you have to reinstall late all that stuff will still be there afterwards. 

According to the webpage that I added, you can make the /home partition before reinstalling which means you can putthe data there and it will be safe during reinstall. More on the /home partition can be found [URL="http://www.psychocats.net/ubuntu/separatehome"]here.
[/URL]

---

### Post by mwillams73 on 2009-08-01
> **running_rabbit07 said:**
> If you install and run the program APTonCD you can make an install disk that will have all updates and some of your installed programs. Then after you reinstall you put the disk in and it will offer to open synaptic and let you install the updates and programs. Much faster than waiting on the network connection to download.

Also if you don't have one you may want to add a /home partition while reinstalling. I don't know much about all the other types of /stuff partitions but I am sure that they would help save programs during future reinstalls.


So how do you actually install them? When I tried it, it opened synaptic i typed in simple ccsm, it came up but when i marked it to be installed it said it couldnt satisfy the dependency, shouldnt have apt on cd put the dependencies on the disk also? I made the apt disk using what was already installed on my system so I know they are working. 

I know im crashing the thread but this is where i found out about apt on cd so i installed it and 5 minutes later i was burning the cd and I was so happy but when i went to use it to install some stuff on a friends computer pretty much everything i tried to install off the disk said that it needed the dependencies. Is it possibly because my friend doesnt have an internet connection? (which is why i was using my apt disk to hook him up) 
If thats the case it doesnt make much sense using it at all if it doesnt also add the programs dependencies along with the programs themselves now does it? I wanted it because ive borked my system so many times that having to redownload everything is a pain ( i have a really slow connection) 
Im starting to think thats this is another case of oops the linux guys did it again, convince some one that this is what you need but dont tell them about the special extra stuff you have to do before it works right. Which by the way is the reason people find linux scary and hard to deal with.

---

### Post by mwillams73 on 2009-08-01
Well I figured out why it needed dependencies, APTonCD does not select them by default( kinda dumb aint it!) I read the docs at their site and you have to select Auto Select dependencies, In order for it to add them to the cd. Again kinda dumb since the programs wont work without them. Also their site didnt even say how to select them, By the way clik on edit and select Auto select dependencies, So sorry if i seem like an *** but sometimes i wonder what the heck people are thinking when it comes to linux.

Lets not make it easier , no lets make it harder and not fully explain even in our docs how to do something that we should have had selected by default in the first place.

And we all wonder why people who come to us from windows world are crying in the corner cause they cant figure out something that should be easy but of course it isnt cause this is linux.

PS im sorry about the way the post sounds but what good is a forum when i have to figure it out on my own anyways?

---

### Post by davegk on 2009-08-01
Thanks, I did the new install now with 35GB / partition and separate /home one. In the end, I had to do most of settings manually, as the new install is 64bit, so most of the apps either different or had additional dependencies etc. I've added APTonCD to my list though - certainly very useful. 

Now, if I can only figure out how to calibrate this laptop's screen, or at least get it to drop contrast a bit, I'll be a happy bunny :)

---

### Post by running_rabbit07 on 2009-08-02
> **mwillams73 said:**
> Well I figured out why it needed dependencies, APTonCD does not select them by default( kinda dumb aint it!) I read the docs at their site and you have to select Auto Select dependencies, In order for it to add them to the cd. Again kinda dumb since the programs wont work without them. Also their site didnt even say how to select them, By the way clik on edit and select Auto select dependencies, So sorry if i seem like an *** but sometimes i wonder what the heck people are thinking when it comes to linux.

Lets not make it easier , no lets make it harder and not fully explain even in our docs how to do something that we should have had selected by default in the first place.

And we all wonder why people who come to us from windows world are crying in the corner cause they cant figure out something that should be easy but of course it isnt cause this is linux.

PS im sorry about the way the post sounds but what good is a forum when i have to figure it out on my own anyways?

Wow, sad to hear it didn't work right for ya. I have only used the APTonCD disk I made once after reinstalling Ubuntu and it made the 180 updates that I had to do upon reinstallation only take about 3-5 minutes instead of the normal 10 minutes because it loaded 99% of the programs from the disk.

Learning Linux is like learning not just to ride a bike but learning how to do pro tricks. It takes a lot of time and practice. The only way to make APTonCD work for more than one system would be to take a system with a lot of hard drive space and install everything from synaptic namely all the lib files.

---

