---
title: "Harddrive became corrupted during install"
date: 2008-08-31
forum: General Help
---

### Post by Allus on 2008-08-31
This night started with me in winxp. I have a dual harddrive with Kubuntu on the slave drive.  Suddenly, winxp gave me the BSOD. I tried to reboot but it would not load up. So, I booted up to Kubuntu and found I was still able to access the winxp disc. 

That's when I did the dumb thing. I decided to go ahead and install the version of Ubuntu on the slave drive. (Mainly because I wanted to see if I could install Propellerhead's Reason on the new edition of Ubuntu using WINE, I saw a YouTube video where someone did.)

I've done Ubuntu and Kubuntu installs before and never had a problem. So, I loaded it up and selected to have it use the entire slave harddrive, erasing what I had on there before.  But the software went into a loop: It acted like it was reformatting the drive, but then came back to the screen where it gave you the formatting choices. After doing that a second and third time I selected a different option. But it again came back to the previous screen. 

So, I decided to reboot. But now the disc image wouldn't even load. Instead I get a bunch of messages like, Buffer ID errors and things like:

ata2.01: status { Drdy Error}
          error { UNC }
         exception mask

This is just a bit of what each line would say they were moving on the screen to fast to jot down what it actually said in it's entirety.

and the lines just went on and on until I started hitting a bunch of keys to make the system reboot.

But everytime I rebooted the same thing would happen. I could not load the cd.

I finally unplugged the computer and took the harddrive out, (this is the slave drive, I already had the master out). Without a harddrive I'm able to run the cd. But, I have no harddrive to install the OS onto.

Anyone have any ideas?

Thanks.

---

### Post by Allus on 2008-08-31
Well, let me run down some of what I've done. first I decided to put both of my hardrives back in my machine. Then I tried to run Ubuntu from the CD and I returned to getting the same screen junk as I did before:

183.536988] ata3.01 BMDMA stat 0x44
183.768396] cmd c8/ 00:04:c3:14:2e:f9 tag 0 dma 2048 i
316.856243] ata3.01 status: { DRDY ERR }
316.857634] ata3.01 error: { UNC }
316.896523] ata3.01 exception Emask 0x00 SAct 0x0 Err 0x0 action 0x0
316.956428] ata3.01 BMDMA stat 0x44

...

stuff like that.

So, then I took the slave drive out of the machine and then with only the master drive, (winxp drive), in I was able to load the livecd.

I really think what I did was corrupted Grub. 

At this point I am able to load winxp again. But, I can only load the ubuntu livecd with the slave drive out. I've been looking for ways to repair GRUB.

With the slave drive out and Ubuntu loaded from the live cd, I've used a terminal to try this:

sudo grub
find /boot/grub/stage1
root(hd?, ?)
setup(hd?)
quit

However, it cannot find a stage1. I have also been told to us chkdsk /f   on the xp and I have it scheduled to do that the next system startup.  But, I do not really know what I'm to expect from that. 

I've also tried this:

[http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

this is done with the livecd, but it does not find a hda. The windows harddrive does show up as mounted as Disk_One or something like that. I can access it through Ubuntu when the livecd is run.

So, my main problem now I guess is how to get that slave drive back into the system so I can install Ubuntu on it.

Any help appreciated.

Thanks.

---

### Post by Allus on 2008-09-01
Just a last word as to a solution. I found a post somewhere from someone who was getting similar messages on their screen. It seems we had entirely different problems, but were getting the same messages. But, he said it took about 10 minutes for the system to boot.  

So, I made my troublesome drive the master drive and took out the other master. Then I tried to run the livecd. Again, I began getting those messages, but I just let them run. After about 10 minutes, the live-cd booted up. 

Now, I was back to the live-cd getting stuck on step 4 again. However, I made my selection and went to bed. This morning, it asked me for my formattig preferences and some other info and it appears that the cd is actually doing an installation.  Very slow though.

The weekend has really burned me out on experimentation though, so since XP is back up and running, I doubt that I'll try to install Reason on Ubuntu.

---

