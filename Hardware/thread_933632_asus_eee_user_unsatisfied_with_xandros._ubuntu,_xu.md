---
title: "asus eee user unsatisfied with xandros. ubuntu, xubuntu, eeebuntu or something else?"
date: 2008-09-29
forum: Hardware
---

### Post by (chubbstar) on 2008-09-29
so ive been using the default xandros install on my Asus eee 901 for a few days now and i find it quite limiting for the most part. 

so basically i would just like some knowledgable linux/eee pc users to share their experience and insights in dealing with other linux distros on the eee. 

im primarily concerned with:
-having the longest possible battery life.
-having as much out-of-box hardware detection and compatibility as possible (less terminal the better).
-minimizing read/write on the SSD to improve seek/write times and minimize any possibly long term damage from overuse. 
-wifi MUST work. no exceptions.
-i would like to have compiz fusion available to have fun with as well (despite the likely battery drain)  

from what i understand theres a variety of options available to me. from the following list, which distro would best suit the concerns i have above?

-[Ubuntu Notebook Remix]("http://www.canonical.com/projects/ubuntu/nbr") 
-Ubuntu
-[Ubuntu eee (eeebuntu)]("http://www.ubuntu-eee.com/wiki/index.php5?title=Get_Ubuntu_Eee")
-[eeeXubuntu]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:home")
-Xubuntu
-Puppy Linux
-gOS
etc etc etc...

also, how essential would installing [this kernel]("http://array.org/ubuntu/setup901.html") from array be for each distro? 

thanks!

---

### Post by michaelkahl on 2008-09-29
I'm using Ubuntu Eee with netbook remix GUI.  I'm very satisfied.  I just made sure to use ext2 file system and have no swap since I have an SSD in my 900.  This reduces disk activity, as well as setting noatime in the fsatab for all your partitions.  
Wireless and wired worked out-of-the-box.  I haven't tested webcam, but so far I'm good on all other fronts.
I have wine installed with steam, so far so good.  I've installed HL, but not HL2 from steam.  HL runs very smooth.  I have not installed compiz, but thats only because I'm using netbook remix and I don't feel that it needs or benefits from it.  You can install xfce, kde, or configure gnome w/o netbook remix.  From what I gather it's as easy as installing compiz from the repos and setting up as you like.
I tried eeexubuntu a couple of months ago on a 2g surf.  It was light and fast, but wireless didn't work at that time.  Hopefully thats resolved now.  
I've also hear other users give very positive remarks to DebianEee.  Good luck and I hope you enjoy that 901.

---

### Post by (chubbstar) on 2008-09-30
> **michaelkahl said:**
> I just made sure to use ext2 file system and have no swap since I have an SSD in my 900.
How does one go about doing this?
 > **michaelkahl said:**
> 
Wireless and wired worked out-of-the-box.  
my wireless doesnt work outa the box. in fact with ubuntu eee pressing fn+f2 (wireless activation) causes the os to hang/freeze. wired works though. so im gonna try some things at [array.org]("http://www.array.org/ubuntu/setup.html"). 
> **michaelkahl said:**
> 
I haven't tested webcam, but so far I'm good on all other fronts.

webcam and mic work outa box.

---

### Post by michaelkahl on 2008-09-30
How-to setup ext2 file system:  
During installation I do a manual partition setup.  I setup "/" with 10gb as ext2 filesystem and setup a "/home" with 6gb of space and as ext2 file system.  The system will warn that no swap partition was setup, but thats ok.  We don't want swap on SSD.

As for setting up noatime, simeply edit the fstab:

sudo gedit /etc/fstab

For each partition you will see an entry that says "relatime" change this to "noatime", save your settings and exit.

I'm not sure why your wireless didn't work.  I downloaded the .iso just a couple days ago, and the version I got was solid with my 900.  Also I never have to hit fn+f2.  I did with Xandros and Ubuntu a couple of times to check the impact on battery life and I noted a couple of things.  
1.  Fn+F2 always told me wireless was off, but if I gave it a few seconds it would turn back on with no message telling me it was on.
2.  Even if I turned wireless off, rebooting would turn it back on.  I'm guessing that this is because my wireless controller is turned on in the bios.
Another thought, you are running a 901, I'm not sure if the 900 and 901 use the same wireless controller or not.  If they do then you should be fine, if not then you may need to wait on support unless someone has a fix documented out there.
Good luck I hope some of that is helpful.

---

### Post by (chubbstar) on 2008-09-30
Thanks alot. I'm going to reinstall with manual partitioning and get the ext2 concern outta the way.

Upon reading around a bit I've seen alot of problems with wireless being reported on the 901+ and 1000 models. Apparently it IS a different controller. I'm off to try a few things I've found around the nets seeing as the fix at array.org didnt work for me. 

Unfortunately, if I can't find anything that work Ill have to reinstall Xandros.. sigh.. If I have success, I'll document it here.

---

### Post by michaelkahl on 2008-09-30
Good luck, with the new install.
BTW I ditched the netbook-remix and setup xfce.  I like it alot.
I have compiz & emerald theme manager running as well.  Performance is just fine.

---

### Post by (chubbstar) on 2008-09-30
so guess what? i just did that fresh ext2 install with the exact same iso that i used before and wifi works outa box. 

so uh yea. dont know what happened there. thanks again tho!

---

### Post by michaelkahl on 2008-09-30
Woot! that is awesome.  I hope you enjoy it.
:guitar::guitar::guitar:

---

### Post by xadder on 2008-10-01
I'm curious. Why were you dissatisfied with Xandros? I really like Ubuntu and am interested in an Eee PC (901 or 904HD). I'm looking for an easy life too though, and since Xandros has synaptic it sounds as though I can use it much like ubuntu - install what I want. Is that wrong?

---

### Post by michaelkahl on 2008-10-01
I think it comes down to personal preference on GUI customization.  I could be wrong, but thats my take.  Try out Xandros, if you like it stick with it.  I've also heard that many tasks are made more difficult because it's locked down pretty well.  
I only have about 1 hour total experience with it, but I just like having Ubuntu or variants of it on my system.

---

### Post by clarkritz on 2008-10-02
I recently installed Arch Linux on my eee pc 701 surf.  I quite like Arch.  It is not for beginners, though, since almost everything is on the command line, and there is no GUI installer.  But if you like the command line it is very well documented and it works great.  I still have ubuntu on my desktop, but i'm considering switching that as well...

I have everything working now.  The problem I had with eeeXubuntu and eeeUbuntu was that they would break after updates because of the special kernels.  With Arch, it is easier to control what updates do, and it is fairly easy to modify the kernel yourself (I was shocked when I did it with sucess on the first try).  All that said, it took me a weekend to get it all installed properly.  I recommend it highly if you're a command line lover.

---

### Post by michaelkahl on 2008-10-02
I was looking at Arch, but from what I could tell it didn't have support for wireless out of the box.  Was this your experience or did it work for you?
I'd have to put xfce on myself.  To be honest, xfce on Ubuntu Eee is fast on my 900.  I'm liking it more than the netbook remix.  It's just more responsive.  
Glad to hear you are having a positive experience with Arch, I've heard nothing but good things about the distribution overall.

---

### Post by derflooh on 2008-10-02
I have an EEE Pc 1000h with Ubuntu and it rocks!! I just did a clean Ubuntu 8.04.1 install and applyed the kernel from [array.org]("http://array.org/ubuntu/") because its a deb package witch means easy uninstall :) The second thing are the Fn keys. I found [this]("http://www.informatik.uni-bremen.de/~elmurato/EeePC/Ubuntu_ACPI_scripts-EeePC_900A_901_1000.tar.gz") script-package witch did not install automaticaly but did with cp and it made all hotkeys working as esxpected. The third thing was [Network-Manager 0.7]("https://launchpad.net/~network-manager/+archive") witch is also working very fine. Hope this helps anybody :)

---

### Post by michaelkahl on 2008-10-02
Thanks, good to know.

---

### Post by (chubbstar) on 2008-10-16
> **xadder said:**
> I'm curious. Why were you dissatisfied with Xandros?

Preference mainly, both aesthetic and familarity. Plus "advanced" Xandros and the way its Synaptic updates worded annoyed me. 

being able to switch out of the Netbook Remix to the regular Gnome desktop is nice since im familar with it. 

plus i might be a Ubuntu fanboy. not sure yet. =)

also, i hear that ubuntu suspend uses way less battery power than xandros.

---

### Post by michaelkahl on 2008-10-16
I'm glad to hear your still enjoying Ubuntu on it.  Still going strong for me as well.

---

### Post by Artemis3 on 2008-10-17
When i got mine in January, the first thing i did was put eeeXubuntu and its been like that ever since.

Wifi out of the box is something you won't get for a while. The story is a bit boring, but there might be hope now as Atheros released specs in September and the needed changes might eventually land in madwifi, which means it might eventually land in Ubuntu. Although the custom Eee distros usually work with wifi after install, you must careful to NOT upgrade your kernel (packages with the name Linux) unless you are ready to fix your wifi by hand.

I think currently [Ubuntu Eee](http://www.ubuntu-eee.com/) is a good candidate to try.

---

### Post by Flag on 2008-10-17
Hi, Am usuing a 900 for a couple of weeks now. First with the settings as purchased, which was a bit dull, so then I added the 701 repo and installed the desktop, better, but still too limited. Switched to Ununtu standard and guess what... everything works oob even wifi, two things to add only 1) shut down takes ages but can be fixed easily, 2) needed to install gnome-volume-manager for Skype usage.
Boot time is reasonable.
Highly recommended.

---

### Post by Flooq on 2008-10-17
I've just set up my 901 and my short experience with the default Xandros distro was very similar. Everything works as you would expect but by default it is very limited.

It does two things which I don't like. The first thing is that it hides functionality which I expect to find in a modern linux GUI, it seems to be set up with the attitude that if all the common applications are installed then noone should want to change or update them. For my purposes it made more sense to just install a distribution that I was more familiar with (this proved to be very easy, I expected to have to tinker around to get things working with this hardware but that wasn't the case).

The second thing I don't like is that it imitates Microsoft Windows with a faux Windows XP aesthetic and folder naming structure (drive letters and a my documents folder). Years ago this might have made sense but nowadays the average linux distribution isn't harder to use, it's just different. I don't have anything against Windows but if someone wants to use that OS then they can order it with a EEE PC now, the linux versions aren't cheaper so presumably people who buy them aren't looking for a windows clone.

---

### Post by silkstone on 2008-10-17
Flooq - I'm in a similar position with a 901. I really don't like the implementation of Xandros at all. It wouldn't be so bad if the menus were configurable and you could add links to folders etc, but this seems impossible.

I would like to change to Ubuntu which I already use on a desktop PC and a laptop, and I'd be grateful if you could tell me exactly what version you installed and how you did it. Not many people say that everything worked without tinkering!

---

### Post by silkstone on 2008-10-17
Well, I've just made Xandros a lot better by finding a way to edit the menus. Most of the guides on how to do this are *wrong* because Asus has changed the way it uses the simpleui.rc file.

There is now an easy solution. Go to...

[http://www.3eportal.com/index.php?option=com_content&task=view&id=34&Itemid=1](http://www.3eportal.com/index.php?option=com_content&task=view&id=34&Itemid=1)

... and download and install the deb file. (Install the app to the 'Settings' tab, ideally.)

The package contains a graphical editor for simpleui.rc, and also a very neat icon generator. (You still need the basic graphic for the icon.) You can add new programs to any menu tab, and also delete existing one that you don't want.

If your main frustration with Xandros on the eee PC is the fixed menu structure, give this a try!

---

### Post by clay_glenn on 2008-10-17
I have a PC900.  I ran the default Xandros for about three months.  I run Ubuntu 8.04 on my desktop and liked the look and feel of that, so I did a clean install on my PC900, along with the Array.org kernel.  

I noticed that although the wifi worked, it didn't work as well as with Xandros.  What I mean is that the signal strength is not as good.  If I am at the opposite end of my house from where my wifi router is located, I would still get 90+% signal, and receive three or four of my neighbor's wifi signals, under Xandros.  Under Ubuntu I would only get 30% - 40% signal strength on my wifi, and maybe get one weak neighbor sighal.  Occasionally when I would boot up Ubuntu, the wifi wouldn't connect, and would start asking me for a passphrase.  I would shut down and reboot, and it would connect just fine.

Shortly after installing Ubuntu, the speakers died on my PC900.  I could not get ANY sounds from them.  The audio worked fine if I plugged in headphones, but not from the speakers.  After a few weeks of searching for settings, drivers, etc., I capitulated and decided that I would have to send it back to Asus for repairs.  But to do that, I had to reinstall Xandros.

When I got Xandros back on the PC900, the speakers still didn't work, but I recovered solid/strong wifi operation.  It seems that the webcam has a better picture (maybe better resolution) with Xandros also.

Bottom line, when I get my PC900 back from Asus, I'll probably stick with Xandros.  Even though I really do prefer Ubuntu (and I learned a lot about setting up the OS, drivers, etc.), some things just seem to work better on the PC900 with Xandros.  Kinda sucks, but that is my experience.

>>>> Clay >>>>

---

