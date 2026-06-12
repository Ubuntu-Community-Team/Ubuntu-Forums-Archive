---
title: "Installing Ubuntu with /home as seperate partition"
date: 2009-07-14
forum: Installation &amp; Upgrades
---

### Post by TrustyLiebowitz on 2009-07-14
Hey gang. 
My first time here so here it goes. 

I decided to try out Ubuntu on a spare drive in an xp machine and liked it. 

I didn't want to bother trying to partition the windows drive so I used a completely separate drive. Which worked fine for the test but now I want to go for a more permanent install. 

A little back story here before my question. 

I tried to make a disk with poweriso which somehow made my cd writer quit writing data although music is still fine. So I called it names and moved on. 

I had an old 20 gig I had layin around an since my windows drive is sata and I only have one ide slave drive, I had an ide left open. I decided to test Ubuntu on the 20 gig slave.

I formatted the 20 gig with Easus partition master 4.0 which I found free on tucows.
I gave it an ntfs formatted partition because when I used fat32 ubuntu installer kept hanging when it was trying to create a swap file. An answer I got form digging in this forum thank you :)   

Since a live CD was impossible do to the fried cd burner, I copied the iso to a new directory my windows drive and unpacked it. I then copied the iso file into the same directory as the unpacked files with wubi.exe and ran WUBI which then installed from that iso and all was good. I rebooted to Ubuntu, the installer ran perfectly, The OS was fruitful and multiplied.  I did a thank you dance for the Gods of Ubuntu and they seemed happy. 

I tested it out. I love it and windows is now free to perform a public display of affection with my hind quarters. 

So after reading many posts here, I notice that everyone is saying I should put the /home on it's own partition.   It looks like a great idea to me cuz after downloading every plugin under the sun, that 20 gig went bye bye pretty fast. 

So I uninstalled Ubuntu from the 20 gig. I formatted my old windows slave 160 gig and I am going to reinstall Ubuntu onto the larger drive now. 

So here is my question:
Since I do not have a live CD, how do I set up the new install of Ubuntu with a separate partition for /home?  Can I use both the 20 gig and 160 gig drives for Ubuntu? Should one be /home and the other everything else? 

I am open to all suggestions as long as they work and do not involve small animals or voodoo rituals. 
 

Thanks 
DAve

---

### Post by earthpigg on 2009-07-14
> **TrustyLiebowitz said:**
> 
So here is my question:
Since I do not have a live CD, how do I set up the new install of Ubuntu with a separate partition for /home?  Can I use both the 20 gig and 160 gig drives for Ubuntu? Should one be /home and the other everything else? 

I am open to all suggestions as long as they work and do not involve small animals or voodoo rituals. 
 

Thanks 
DAve

you have a thumb drive laying around, i assume? system -> administration -> create USB startup disk. 

change your BIOS so it'll boot from USB, boot from the thumb drive, install from there.

> Can I use both the 20 gig and 160 gig drives for Ubuntu? Should one be /home and the other everything else? 

you certainly can, but that just means that *either one* breaking will break your install and be a headache to fix. especially since that 20gig is probably pretty old.

if i had that exact hardware, here is what i would do:

140 gig partition for /home, 2 gig for swap, 18 gig for /.
use the 20 gig internal to back up whatever 20 gigs of data is most important to me.... 

...or, if you aren't *absolutely completely 100% sure* you are done with windows, put windows XP on it for the odd occasion that a piece of windows-only software comes along that you absolutely *_must_* play with/use/work with. if you install windows XP on the 20 gig _**first**_, and then install ubuntu on the 160, it *should* pick up on the winxp install and add add it to the boot menu. if it doesn't, make a thread here and we will sort you out.




as for how to set up a separate /home partition:

boot from thumb drive, install, manually edit partitions, delete all partitions*, create a new 2 gig swap partition, create a new 18 gig ext3/4** partition with the 'mount point' of /, create an ext3/4 partition that takes up the rest of the space with the 'mount point' of /home. hit 'next' or 'apply' or whatever it says, and you are done.

if you think you will need more than 18-20 gigs for your / partition, go for it.... i have 35, and that is insane overkill. i am presently using 5.2 gigs of my / partition, and i have all sorts of software i never use installed: my applications -> games menu takes several seconds to scroll allllllll the way from top to bottom, i have four different full featured web browsers installed, etc.



*i say to simply delete all partitions because resizing takes forever. if you really want to, go ahead and resize. 



**you will not need to run defrag on an ext3 or ext4 partition until after about a *decade* of regular use -- if then. there are other reasons to use ext3/4, or basically *any* of the options you see in the partitioner.... but absolutely none to use fat32 or ntfs on anything other than a thumb drive that you expect to plug into a windows box.

---

### Post by earthpigg on 2009-07-14
also, has anyone mentioned to you the easy-to-establish performance boost available to those using / partitions smaller than 25 gb on a fresh install? you start by making a vodoo doll of a squirrel, and then dipping the squirrel your doll was modeled after in mercury....

---

### Post by TrustyLiebowitz on 2009-07-14
OK that sounds logical about the 20 gig. 

I would trash xp completely and gain yet another 160 gig if it were not for the fact that I create and edit youtube videos.Mostly with a webcam.  I also communicate a lot on yahoo messenger.  Once I find a way to do those two things in Ubuntu, windoze is in the trash. 

New questions:

1. On the thumb drive, do I just put the iso on it or the unpackaged stuff as well? 
2. What should I use to create these partitions? I do not remember seeing an option during the wubi  
    install which would allow me to do that. 

3. I see I can ad gknome partition manager in the ad/remove programs area. Would that help me in 
    any way?

---

### Post by earthpigg on 2009-07-14
> **TrustyLiebowitz said:**
> OK that sounds logical about the 20 gig. 

I would trash xp completely and gain yet another 160 gig if it were not for the fact that I create and edit youtube videos.Mostly with a webcam.  I also communicate a lot on yahoo messenger.  Once I find a way to do those two things in Ubuntu, windoze is in the trash. 

New questions:

1. On the thumb drive, do I just put the iso on it or the unpackaged stuff as well? 
2. What should I use to create these partitions? I do not remember seeing an option during the wubi  
    install which would allow me to do that. 

3. I see I can ad gknome partition manager in the ad/remove programs area. Would that help me in 
    any way?

i've never edited video on ubuntu for youtube, but i would encourage you to explore the repos and do some research. the fact that there are approximately twelve billion videos on youtube showing off Ubuntu with compiz and the 3d cube and whatnot means it can't be *that* hard.

as far as yahoo messenger, ubuntu comes with 'pidgin' installed, and another popular IM client that works well with yahoo is Emphany, which is in the repos. if pidgin and emphany from the official repos is giving you trouble connecting to yahoo, get it from [http://www.getdeb.net/](http://www.getdeb.net/) -- they have a newer version than what is in the repos, but still specifically designed to run on ubuntu.

1. im not certain exactly what you are asking, but i am certain that the process of creating a USB Startup Disk is easy as pie. :D try it out, if you would, then please post if you have any questions about it.

2. a wubi install does not create partitions, correct. you will see an option to 'manually partition' during the non-wubi install process. it will look like this:

[IMG]http://farm4.static.flickr.com/3648/3362344673_b2d3cb0f76.jpg[/IMG]

note how the user that took that screen shot has the partitions the size he wants, and the respective 'mount points' set to / and /home. the individual in that example is electing not to create a swap partition. you will want a 3rd partition with the 'type' to be 'swap' instead of ext3 or, in that example, ext4.


3. you can partition ahead of time using gnome partition manager, if you like. it looks close to the same and accomplishes exactly the same as doing it during the install process. note, however, that you cannot partition 'mounted' filesystems... if you are running ubuntu from a given hard drive, you cannot partition that hard drive from within itself. thumb drives and hard drives other than where you presently have ubuntu installed, yup, go for it. since you have ubuntu on that 20 gig partition, you should be able to 'unmount' the 160 gig and do it that way. or, you can do what most people do and run gparted (aka 'gnome partition manager') from the live cd/usb. 

there are 500 ways to skin a cat (or edit partitions) in ubuntu - that is why, on these forums, you will often see people start their answes with 'well, you could....' or 'the easiest way is possibly to....' and very rarely will you see someone say 'this is how you do it, and the only way to do it....'

people migrating from windows are often used to their only being one way to accomplish a given task, and get overwhelmed with all the options available and worried about what difference it makes as to the exact method used.

you now know three easy point-and-click ways to partition your 160 gig hard drive:

1. during the install, select 'manually partition'.
2. run gparted aka 'partition editor' from the live cd.
3. boot as normal from your 20 gig ubuntu hard drive, unmount your 160 gig hard drive, and do it from there.

pick the one you like best, it really does make absolutely _no_ difference.

---

### Post by earthpigg on 2009-07-14
i exaderated about youtube videos. there are 4,960 youtube videos returned when you search for 'compiz ubuntu', slightly less than twelve billion.

my apologies if i misled you.

---

### Post by TrustyLiebowitz on 2009-07-14
Thanks man!
I'll take the next few days and go through everything you suggested. 

As you just pointed out, if there are that many youtube videos on ubuntu out there then I must be able to learn it as easily as I leaned multiple editing systems in windows. 

I solved the yahoo problem already both with pidgin and an online flash versi8on. So I am well on my way to ditching windows for good. 

The idea of using the 20gig as a place to boot an work and partition from is perfect. Not to mention I haven't even tried to burn a CD from Ubuntu yet and I see there is an ap for burning livecds. 

I used to have all sorts of mouse problems in xp which woudl come an go from one reboot to the next and they are completely gone now so I am guessing the cd prolly works now as well. 

 I think I am gonna play around for a bit an then trash windows and do my entire machine over in a few days. 

Thank you for your help!

DAve

---

### Post by earthpigg on 2009-07-14
best of luck

---

### Post by alfu on 2009-10-07
I created 1 primary partition for '/' and 2 ext3 logical partitions on the extended partition, and selected mountpoints '/home' and '/usr' for them during the LiveCD install using the pop-up menu.

Reason being, when I re-install Ubuntu (had to do that once already) I want to keep my user prefs.

The Ubuntu install ignored both the '/home' and '/usr' partitions, placing both '/home' and '/usr' on the '/' partition as folders.  (The item the Filesystem identifies as the 'home' folder has as its Properties/Basic/Location: defined as '/', as does the item named 'usr'. The Volume is 'unknown'.)

In fact, unless I look at these partitions with GPartEd, I can't even tell they are there from the Desktop.

What's THAT all about?!?  :confused:

---

### Post by earthpigg on 2009-10-07
> **alfu said:**
> 
What's THAT all about?!?  :confused:

honestly? it sounds like you didn't double check everything at the manual partitioning portion of the install.

---

### Post by mechro on 2009-10-07
> **alfu said:**
> 
In fact, unless I look at them with GPartEd, I can't even tell they are there from the Desktop.


Er... Correct? You should have a Home icon on your Desktop, but you won't be able to tell whether it's mounted on a separate partitition from the Desktop.

---

