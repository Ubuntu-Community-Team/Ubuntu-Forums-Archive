---
title: "N00b in serious need of help, several problems"
date: 2008-07-13
forum: General Help
---

### Post by Drizzel on 2008-07-13
Hi, I'm a longtime windows user. I'm looking to try out a new os so I installed Ubuntu. I have so many problems I dont know where to start.

First thing that happened was my first install attempt didnt work properly. It got all the way to the end and grub failed to install and ubuntu wouldnt boot. I decided to just run the install disc again. So now its installed, but everytime I tried to log in it would give me the "your session only lasted 10 secs" etc, with no error code.. I did a search and found a post with a similar problem. I logged in under some terminal session and typed "Sudo rm -R /var/cache/apt/archives"

After that I can now log in and at least get online for some help. However this firefox version is out of date and the update option is grayed out. I tried going to firefox.com and downloading the newest version, but now I'm getting hit with another error. "Not enough room on the disk to save /tmp/R9Yl5_BV.tar.part" Wahhh?? I so dont know what to do. I didnt realize installing and using Ubuntu would be so difficult. 

Should I just reinstall ubuntu again and choose different partition options? I'm on dualboot btw. I have been searching the forum for the last 24 hrs trying to figure things out myself, but I'm just getting more and more confused.

My install dvd is Ubuntu 8.04 LTS DVD (i386) from tuxdistro.com if that matters. I had to do the text install as the regular "install ubuntu" would just lockup and fail everytime at a certain point. Sorry for the long post, Please someone help a n00b in need.

---

### Post by mikewhatever on 2008-07-13
In order to update Firefox, just start System>Admin>Update Manager. Be ready for quite a bunch of updates, firefox among them.

Now, about the disk space problem, if there is really no enough, you'll need to enlarge Ubuntu's partition before you install anything. Can you post the output of the following command from Applications>Accessories>Terminal:
> df -h

As a side note, Ubuntu is not a free version of Windows. If you don't want to learn, there is no point in trying it.

---

### Post by Drizzel on 2008-07-13
Hi, thanks so much for replying :)


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda10            2.1G  2.0G     0 100% /
varrun                109M  108K  109M   1% /var/run
varlock               109M     0  109M   0% /var/lock
udev                  109M   76K  109M   1% /dev
devshm                109M   12K  109M   1% /dev/shm
lrm                   109M   38M   72M  35% /lib/modules/2.6.24-16-generic/volatile
overflow              1.0M   80K  944K   8% /tmp
gvfs-fuse-daemon      2.1G  2.0G     0 100% /home/josh/.gvfs

---

### Post by echo314 on 2008-07-13
If you could provide some info regarding how much diskspace you gave the ubuntu partitions and how you set them up it would be helpful. For example, did you just use the automatic options, or did you manually set up sizes.

To update firefox (or most any other application), you use the package manager in ubuntu. Explanation later. Fix your diskspace problem first, then go to a terminal or console, and run "sudo apt-get update" then "sudo apt-get upgrade" and it will update most of the software running on your system, including firefox. Since you have a new install, this first upgrade could take a LONG time. Dont worry though, subsequent upgrades will not take nearly as long.

btw, what version of ubuntu did you install?

Hang in there. I dual booted myself for some months before I finally switched over. Yes, it did take some work for me to get the hang of it, but this forum community was VERY helpful and I can say i would not be using Linux exclusively if it were not for this very helpful community. Go experiment, research, try and follow these instructions, and report back.

EDIT: didn't read the rest of your post, my bad

---

### Post by AnLGP on 2008-07-13
If i'm reading that right there's not a whole lot of space on your hard drive?

---

### Post by falcon61102 on 2008-07-13
You install it to a flash drive or USB device?

---

### Post by Drizzel on 2008-07-13
I have an 80gb hdd. I set xp to use like 30gb and Ubuntu to use the rest. I dont know what is going on. I did manual partitioning, but It was all so different I dont remember exactly what I did. When I go to places/computer I see 2.2GB media, 3.2GB media, 31.5GB media, and 39.9GB media. Have I done something wrong?

---

### Post by falcon61102 on 2008-07-13
It looks like you may have installed Ubuntu onto that 2.2gig media... which is fixable.  I think you should fix your partitions before trying to install any updates, cause you don't have room.

You have your live CD handy?

---

### Post by Drizzel on 2008-07-13
Yes I have that DVD i mentioned earlier.

---

### Post by balaknair on 2008-07-13
Hello Drizzel
It looks as though you installed Ubuntu on a 2 GB partition, and apparently, you've run out of space. You'll need to either resize the partition(I'd advise at least 8GB, though I'd prefer to install Ubuntu on a 6GB / partition and a seperate /home partition of 10 to 20 GB) or reinstall Ubuntu, this time allocating more disk space to Ubuntu. 2 GB is the bare minimum, and I wouldn't recommend it.
Check these links before proceeding
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
and
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

How much capacity does your hard drive have? Depending on how much free space you can scrounge from the Windows installation, I'd suggest you allocate as much space as possible to Ubuntu, and then you can install fs-driver(details and link in the page link above) in Windows so you can access all files from both Windows and Ubuntu. But at least 8GB for Ubuntu(without a seperate /home partition) should give you a functional Ubuntu installation.

---

### Post by falcon61102 on 2008-07-13
There is a program on there called GParted and it will allow you to resize and move your partitions around.  You need to be really careful because you hit the wrong one and you will erase everything.

Do you know which partition WinXp is on?  Once you determine that, write that down so you don't forget and accidently delete it.

Run the following code in your terminal and post the results so that we can help you rearrange things as necessary:
```
sudo fdisk -l
```

If anyone sees where I'm going with this and knows an easier way... let's here it.

---

### Post by Drizzel on 2008-07-13
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20572056

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825        9729    47431912+   f  W95 Ext'd (LBA)
/dev/sda5            3825        4218     3164773+   7  HPFS/NTFS
/dev/sda6            4219        9072    38989723+   b  W95 FAT32
/dev/sda7            9649        9729      650601   82  Linux swap / Solaris
/dev/sda8            9361        9627     2144646   83  Linux
/dev/sda9            9628        9648      168651   82  Linux swap / Solaris
/dev/sda10           9073        9339     2144646   83  Linux
/dev/sda11           9340        9360      168651   82  Linux swap / Solaris


Also when I was doing the partitioning It gave me an option to select something like 20%, 30% etc. I typed in max. I dont know how I ended up installing it like this.

---

### Post by balaknair on 2008-07-13
Oops
my bad

OK, since it's a new install, I'd suggest you read the pages I linked above, then using the Live CD reinstall Ubuntu, formatting and partitioning manually. Make sure that the partition you allot "/" has at least 6 GB spcae(5-10GB), and a /Home partition of 10-20GB(or more if you can spare the space).
It's safer than repartitioning with gParted IMO given the confusion you've been through just now.

"/dev/sda7 9649 9729 650601 82 Linux swap / Solaris
/dev/sda8 9361 9627 2144646 83 Linux
/dev/sda9 9628 9648 168651 82 Linux swap / Solaris
/dev/sda10 9073 9339 2144646 83 Linux
/dev/sda11 9340 9360 168651 82 Linux swap / Solaris"

These are the partitions you need to format from the LiveCD, then create 3 new partitions- 
"/"- 5-10GB
'Swap"- 512 to 2GB(a good measure is your RAM X 2)
"/home"- 10- 30GB or all the remaining space- it's up to you.

---

### Post by falcon61102 on 2008-07-13
Ok... you may not have to reinstall... give me a min to look at your partition table.  Do you have any other operating systems besides XP and Ubuntu installed?

---

### Post by Drizzel on 2008-07-13
Ok I'll try that then. Hopefully I'll get it right this time. Thanks sooooo much for your help guys! I really appreciate it. I'll report back after the installation.  

:popcorn:


Edit: Oh a new reply. Ok I'll wait. All I have installed is xp pro and ubuntu.

---

### Post by falcon61102 on 2008-07-13
Did you creat those W95 partitions that are listed.  Depending on whats on those partitions, if anything, you could delete most of those partitions and then resize sda10 which holds your Ubuntu system to use the free space from those other ones.

---

### Post by balaknair on 2008-07-13
> **Drizzel said:**
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20572056

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3825        9729    47431912+   f  W95 Ext'd (LBA)
/dev/sda5            3825        4218     3164773+   7  HPFS/NTFS
/dev/sda6            4219        9072    38989723+   b  W95 FAT32
/dev/sda7            9649        9729      650601   82  Linux swap / Solaris
/dev/sda8            9361        9627     2144646   83  Linux
/dev/sda9            9628        9648      168651   82  Linux swap / Solaris
/dev/sda10           9073        9339     2144646   83  Linux
/dev/sda11           9340        9360      168651   82  Linux swap / Solaris


Also when I was doing the partitioning It gave me an option to select something like 20%, 30% etc. I typed in max. I dont know how I ended up installing it like this.

I guess it installed in the minimum space instead.

---

### Post by Drizzel on 2008-07-13
I really dont remember creating anything. It was all so confusing and I had so many problems. The main thing I remember doing was typing "max" when it asked how big the partition should be and then it took over and did its thing. I dont know how I ended up with all these small partitions.

---

### Post by falcon61102 on 2008-07-13
Ok... well, as long as you don't touch the first one, WinXp should be fine.  So whether you want to reinstall and your the partitioner there or try to resize and move what you've got is up to you.

---

### Post by Drizzel on 2008-07-13
hmmm I guess I'll just go for a reinstall since I cant download anything I wouldnt be able to get gparted anyway. I'll report back soon. Thanks again! Cant wait to get Ubuntu up and running so I can start having fun with it.

---

### Post by falcon61102 on 2008-07-13
For future reference, gparted is installed on the live cd... it's in the menu.  Good luck.

---

### Post by balaknair on 2008-07-13
OK let's see, you said you have WinXP on 30 GB
 that's here
/dev/sda1 * 1 3824 30716248+ 7 HPFS/NTFS

That's your primary partition
The rest of your drive is basically one extended partition with 47 GB
/dev/sda2 3825 9729 47431912+ f W95 Ext'd (LBA)

and some smaller partitions(the rest of it).

If as you said you have allocated 30GB for XP and the rest for Ubuntu, I guess that means you have nothing Windows related on the remaining space. So you can go ahead and remove the large 47 GB partition, and create new partitions to install Ubuntu.

The reason I'd advise installing anew is that it's simpler to just create new partitions and install to it, you get a cleaner partition table, you can create a seperate /home partition, which is easier if you want to back up or if you want to upgrad. Plus it's almost the same amount of work. And the Grub tavles are also created anew, with less chance of error.

Beyond that, it's your call.

 All the best. : )

---

### Post by Taxman415a on 2008-07-13
I agree with balaknair. Verify that you don't have anything important on all those other small partitions and if not, then delete them and go with a larger one that uses up all the 47 GB remaing or so that Windows isn't using. It's not likely that the Ubuntu installer created all those small paritions, but if you really didn't know what you were doing it's possible you did.

---

### Post by Drizzel on 2008-07-14
Success! I must have been on mars last night when I was trying to do the partitioning. It was cake. I just deleted all those partitions except the xp one and everything went smooth. Thanks for your help and suggestions guys. You all deserve medals for all the help you provide on these forums! :) 

Only thing I'm kinda curious about is when I did the update manager it pulled like 212 updates, but 42 failed. Now when I run the update manager it downloads the 42 updates that failed, but doesnt install em. It just says system is up to date. Is that normal?

---

### Post by mikewhatever on 2008-07-14
Can you post the exact error message you get. Congratulations on successful install.

---

### Post by Drizzel on 2008-07-14
It just acts like it is updating, the little download box that pops up with the progress bar and it says downloading 1,2,3,4.. of 42. "Then it says reading state information" and after that it just goes back to the update manager. It says "Your system is up to date" "The package information was last updated less than an hr ago".. I have run the updater several times trying to get it to install the 42 updates, but it wont.


Also, I hate to ask as I'm feeling so clueless right now, but.. You know how in windows you can push win+E and windows explorer comes up? Is there anything similar in Ubuntu? I cant figure out how to access my files. :oops:

---

### Post by Drizzel on 2008-07-14
Anyone know of a nice N00b guide to Ubuntu? Something like showing people who are used to windows how to do common tasks in Ubuntu.. Keyboard shortcuts, exploring files and directories like when using windows explorer, useful terminal commands etc. I found a n00b guide somewhere here on the forums yesterday, but lost the bookmark. I think it was in someones sig.

I'm loving Ubuntu, a feeling of freedom has come over me. Its so much better than windows imho.

---

### Post by balaknair on 2008-07-14
try psychocats- it's a great collection of tutorials and guides put together by aysiu, one of the admins here at ubuntuforums.
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

It certainly helped me on more than one occasion(still refer to it frequently).

---

### Post by balaknair on 2008-07-14
There's more stuff here

Keyboard shortcuts
[http://ubuntuforums.org/showthread.php?t=50794](http://ubuntuforums.org/showthread.php?t=50794)

More shortcuts
[http://ubuntu-tutorials.com/2007/02/20/shortcut-keys-you-might-not-know-about/](http://ubuntu-tutorials.com/2007/02/20/shortcut-keys-you-might-not-know-about/)

You can also customise keyboard shortcuts
System Menu> Preferences> Keyboard Shortcuts

---

### Post by balaknair on 2008-07-14
And regarding the updates, try this(can't say for sure if it'll work)
Open Synaptic(System menu> Administration> Synaptic Package Manager), select 'upgradable packages' and check the version you have installed to see if it's the newest version. You can also look at properties to see if there are any dependencies. 

If you have an older version and it's upgradable try updating each package individually and see if it returns an error. You can also "Force Version" or mark for complete reinstallation by right clicking on it.

 Hope this is helpful
All the best.

---

### Post by Drizzel on 2008-07-14
Well I opened Synaptic, but didnt see 'upgradable packages' anywhere. I'm not sure what dependencies are so I'm a bit timid to do anything. I dont want to mess anything up, its all running so nice. 

In Synaptic on the left menu where it says 'All' should I check all the boxes and do something? It just says mark for installation when I try to click the boxes. Man.. I have so much to learn. I wasted too much time with windows.. Should have made the switch years ago. Thanks for the links you provided, they were exactly what I was looking for. :)

---

### Post by balaknair on 2008-07-14
Sorry about the delay, at work here.

Yep those links helped me quite a lot when I switched to Ubuntu. That's the best feature in Ubuntu- it's got a great community. 

In Synaptic, on the left hand pane, there ought to be an option which says upgradable packages along with All and Installed packages etc(I'm on a Windows box right now, so this is mostly from memory, the descriptions may vary slightly). If it isn't there, you can still find the packages by using the search tool(on the toolbar on top) if you know the name(or part of the name or description) of the package. Installed packages have the little box next to them turned green. Upgradable packages have a green check box with a tiny yellow star in the corner.
Checking the blank boxes(apps not installed on your computer) marks the packages for installation(a little curved arrow appears in the box).
As an example, use the search box to find Firefox, which is most likely installed. You'll see the green box there. If you right click on it, you'll get the list of options- properties, install, reinstall, uninstall etc.

So now you can try to find the individual packages and either reinstall or force version for each. Just don't delete or uninstall anything if you don't know what it does(especially lib files).

I'll check Synaptic when I get home and give it another shot.
All the best.

---

### Post by Drizzel on 2008-07-14
Well the thing is I dont know what its failing to update. When the box pops up during the update and starts downloading 42 updates it happens so fast I cant read what its trying to update. All I see is a progress bar for just a second. I click show details, but by the time it shows the details of what its trying to update the process is over and the box disappears. No error codes or anything. Frustrating really. If I knew what it was not updating I could just do it manually(which I shouldnt have to). I'm at a loss right now and I'm just not sure if this is for me. Seems the most simple of tasks are so much trouble to do.

---

### Post by balaknair on 2008-07-14
When you open update manager, doesn't it show a list of updates available?
Something like in the image attached.

Try using the Terminal(Applications>Accessories>Terminal), you'll get a list of available packages you can then copy the text and save it in a text file.

sudo apt-get update
sudo apt-get upgrade

When asked for your password, just type it in and hit enter(you won't see the little asterisks appearing when you type in the password- that's normal).

---

### Post by Drizzel on 2008-07-15
> **balaknair said:**
> When you open update manager, doesn't it show a list of updates available?


It doesnt show a list. I open the update manager and click check and then it pops up saying downloading 42 updates. It never installs them. Here's a screen shot. But like I said before I've tried clicking details to see what it is trying to download, but theres just not enough time. It all happens so fast I could barely take the screenshot. Also I did those commands you posted, but it didnt update anything or list anything. Thanks for all your help. I dont know what to do about this.

---

### Post by balaknair on 2008-07-15
I'm afraid I'm out of ideas. 
The only sure fix I can think of is reinstalling(I'm a bit trigger happy about reinstalls, used to break and reinstall Windows all the time in the past when I was in college, at least twice a year, and did the same for Ubuntu when I started out a year back, I'd play with system settings and stuff in both OSes till they broke and if I couldn't think of a way to fix it, just reinstall). Unless you've got a lot of data there or you've configured the settings quite a bit, it would seem like an easy option to me. I'm a bit lazy with things like that, preferring to start over rather than clean up the mess I make.

However in your case, I suggest you start a new thread, with a mention of the problem in the title- 'updates won't install'- or something like that. This will probably help you get assistance more than just something like 'I'm in trouble' 'help' or 'urgent'. 
I'm really sorry not to be of more help here. I hope you're able to fix this problem soon. All the best.

PS: If I do find something that might help, I'll get in touch and send you a PM.

---

### Post by Drizzel on 2008-07-16
Thanks for all your help balaknair! I did a reinstall earlier today and still have the same issue. I'm thinking about finding an app to record all my activity so I can make a little vid to show exactly what is happening. 

Take care :)

---

