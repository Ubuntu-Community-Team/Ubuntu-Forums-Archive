---
title: "Update screwed me - AGAIN !"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by davidU on 2009-10-06
Just writing to say I am well fed up with this OS, Ubuntu 8.04.   This is the second time that an auto update has killed a machine or made it unworkable, requiring re installation.  Hmmm, maybe it's too much effort and I won't bother, unless someone here has a simple solution that won't take weeks of visits to this forum.    OK, in the first instance, the Update feature didn't know that I didn't have enough disk space for the package files, and quite frankly, how am I supposed to know whether or not   (i) I have enough disc space for all those packages,  (ii) whether I actually need all those packages anyway ?    Needless to say, no more Ubuntu on the family machine now.    Today I just rendered my Toshiba laptop Ubuntuseless before I could start work, by doing the recommended auto update.  I guessed that I didn't have enough disc space for all the packages, so spent an hour, un-ticking those which I guessed (again) I don't actually need. And there were a lot of them.    After attempting and failing to download and install my selected packages, Ubuntu says "Reboot is required", so much for superiority over Windose.  Especially as according to my Ubuntu I now have no propriety drivers in use so as far as I can see, no wireless network card slotted into the PCMCIA card slot on my machine. No Internet connection, but a nice notice telling me I need to update my machine.    All the wireless settings have disappeared and will need to be re-configured, once I find out how to get Ubuntu to see my Wireless Cardbus Adapter again.    Can anyone please help me to get my wireless connection back, and maybe teach me how to use Synaptic without killing the machine.   Regards

---

### Post by TenPlus1 on 2009-10-06
Just before you install the updates it will tell you how many packages are to be installed and how much space is needed...  You can easily check your Filesystem size to see if you have enough room before hitting the accept button...

How big is your filesystem partition ?  You shouldn't run out of space to quickly while updating, so maybe a program called BleachBit will come in handy to clean up your system before doing an update...

[http://bleachbit.sourceforge.net/download/linux](http://bleachbit.sourceforge.net/download/linux)

---

### Post by ajgreeny on 2009-10-06
You have obviously had a bad time with this, and it is impossible to say why without a lot more information about your machine and how you have it set up.  What is the machine in terms of its spec, disk size, ram, wireless card, graphics card, etc etc.  If you are not sure run ```
sudo lshw > spec.txt
``` and attach to us the spec.txt file that will appear in your home folder.

You show that you are using v6.06 Dapper Drake, which I believe is no longer supported, so the first thing to do is probably backup all your data and update to a newer version.  From my experience I would suggest you try a live CD of v9.04, as it is much better than 6.06, certainly it will pick up many more wireless cards than any previous version, and has many other updates of packages that make it worthwhile.  9.10 will be with us in about two weeks time, so you may prefer to await that before you download anything new to try.

Regarding your space problem, try running from a live CD if you can't get your install to connect (or even run) and from that mount you hard disks and post back the output of ```
df -h
```then
```
sudo fdisk -l
``` This will show us what is on your computer, and how everything is set up at the moment.

---

### Post by presence1960 on 2009-10-06
after the first fiasco with updates I would have increased the size of my / partition. It isn't the updater's fault if you don't allow enough space in your / partition for updates. My first impression here without seeing all of the facts is operator error not Ubuntu error.

I know you are upset but you need to think calmly & logically. It isn't Ubuntu's fault if there is not enough space for updates. The updater only searches for available updates, it does not "see" how much space is available for them (just like windows update).

If you want to fix this run the commands suggested. You will probably be able to increase your / partition size.

If you don't want to do that then there is always windows for you. Your choice. Simple. No hate. Just choose.

---

### Post by davidU on 2009-10-11
Thanks everyone for your replies to my posting.    There's a lot here and first I have to admit to "operator error", even though I have a BSc in Info Sys and a decade or so running Windows plus quite a few successful installs of Ubuntu under my belt.  However, Ubuntu fans, there is still some room for improvement, and no doubt, I shall see these when I run a newer distro.  Hopefully this will find my D-Link wireless card easily as it is a few years old now.  

Thank you presence1960:    

Unfortunately my disk space is very restricted as I run a dual boot with Windose XP on the Toshiba Satalite laptop which threw up this issue, with the latest update only, all the others went fine.  I still think there is plenty of room to run into space issues with older hardware, simply because the size of the update was massive, as it included lots of stuff [apps] that I never use, plus a raft of others that I really don't know if they are necessary to the Operating System, or not.  

Thank you ajgreeny:   

for the suggestion to use lshw. Yes an older distro on even older hardware. Toshiba Salalite laptop with 60 Gb HDD shared with Windows XP.  The 30 Gb partition for Ubuntu 6.06 holds next to no personal files as I transfer them to my Windows desktop machine as soon as I finish working on the lappy.  I will take your advice, and I'll back up my personal files on the Windows partition, just in case, as I once lost my Windows instalation as well, after a failed Ubuntu update on a dual booting desktop machine.  

Thank you TenPlus1:  

for your suggestions.  Yes the update package manager did exactly as you said.  From the size of the download indicated, I knew there was not enough disc space on the partition, so I spent about an hour de-selecting as many packages  as I could, mainly using guess work rather than in depth knowledge of the Ubuntu system. Of course I kept all the security packages, and I guess 6.06 would require more than 9.04.  

What I find confusing is the fact that some applications like those handling multimedia files are handled by many different programs.  Surely I don't need four media players ? And do I need C C++ compilers and debuggers if I don't do programming in C C++.  What about MySQL, PHP, Python, etc. I don't use them, why do I need to install them ?  I could go on and if you are being fair, you have to admit that this sounds like the old Windows condition of "bloat ware".  

Even though I have several years experience with Ubuntu, nothing that I have read so far prepared me for having to deal with this situation at boot time, and have to make so many crucial decisions about what is essential and what is additional to the Application Layer, the Network Layer, or the OS.  Hopefully 9.04/9.10 will prove all my worries unfounded and I'll be up and Ubuntuing in no time.  

I can only say that I am happy that I hadn't already made the jump to running my business on Ubuntu only.  How I wish I could, but I have to accept my own failing on this, still so much to learn.  

Regards everyone, thank you all DavidU  

PS if you like music, visit my web site for free stuff, all legal. [www.crackpots.org.uk](www.crackpots.org.uk) 

Sorry folks some times it disappears through IP changes, plus the Apache server is running on Windows 2000 as I haven't been able to get LAMP running without MySQL installing and spoiling am otherwise clean machine.:guitar:

---

