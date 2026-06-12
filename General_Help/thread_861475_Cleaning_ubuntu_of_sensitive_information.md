---
title: "Cleaning ubuntu of sensitive information"
date: 2008-07-16
forum: General Help
---

### Post by Old Pink on 2008-07-16
Hi there,

Planning to pass a Ubuntu laptop on to someone else, wondering how I can clean it of all sensitive information? I'm planning on creating another user account, and completely removing my old one and any trace of it. 

Is there anything more than this that needs to be done? I'm guessing not considering I've never browsed the internet in sudo or anything? 

- Matt

---

### Post by aysiu on 2008-07-16
There is a utility called *shred* that allows you to securely delete files (instead of just taking away the pointers to them), but I'm not sure it works on files that have already been deleted.

When you "delete" a file, the file is still there, but the space it uses up is marked as available. I guess one way to do it might be to fill up your entire hard drive with non-sensitive information and then delete that.

*shred* is a little better, because it can write 0s multiple times over the file. If that's not good enough, you can look into degaussing.

---

### Post by Old Pink on 2008-07-16
So if I *shred *my /home/name directory?

---

### Post by coffeecat on 2008-07-16
You can 'shred' a complete partition or a complete drive. See man shred. I'm fairly sure that shred comes with a default install so you could boot up from a live Ubuntu CD and do 
```
sudo shred /dev/sda
```- that's if the CD detects the hard drive as sda.

I suggest you use the verbose flag. A shred of a whole disc (I've done it :( ) takes hours. It's a bit unnerving seeing nothing happening in the terminal.

An alternative would be [Darik's Boot and Nuke]("http://dban.sourceforge.net/"). Very effective but again you'll need the patience of Job.

---

### Post by aysiu on 2008-07-16
> **coffeecat said:**
> You can 'shred' a complete partition or a complete drive. I didn't know that. Thanks for the info.

*man* pages make no sense to me. If Old Pink had already deleted the /home/*username* directory, would there be a way to shred only the empty space and not the rest of the partition?

---

### Post by Old Pink on 2008-07-16
I haven't deleted the home directory yet, I'll shred that... but shredding the empty space sounds good, is that possible?

---

### Post by coffeecat on 2008-07-16
> **aysiu said:**
> *man* pages make no sense to me.

Are they meant to make sense? :)

Actually, I just looked at the man page for shred and it makes no mention of drives and partitions, just files. But, yes you can. 

  Also, the instruction for iterations is unclear. The default is 25 (:shock: that **is** secure). If you want to change it to 5, say, the syntax is:

shred -n 5 *file/partition*

or

shred --iterations=5 *file/partition*

...and don't forget to add the verbose flag. :)

---

### Post by coffeecat on 2008-07-16
> **Old Pink said:**
> but shredding the empty space sounds good, is that possible?

Yes. Just shred the whole drive. Then you can reformat the drive. A shredded drive comes up as all unallocated in a partitioner.

I seem to remember that, for some reason, it wouldn't shred folders. One file, sets of files, a whole partition, a whole disc, but not a folder. Odd

---

### Post by Old Pink on 2008-07-16
I don't really want to re-install here, folks. Just shred my data off.

---

### Post by coffeecat on 2008-07-16
> **Old Pink said:**
> I don't really want to re-install here, folks. Just shred my data off.

Oh sure. I was just pointing out what the next owner will be confronted with.

Good luck.

---

### Post by aysiu on 2008-07-16
> **coffeecat said:**
> Oh sure. I was just pointing out what the next owner will be confronted with.

Good luck.
I don't think Old Pink wants the new owner to reinstall either, though.

The ideal scenario is to create a new user and then shred the old user while keeping the installation intact, if I'm understanding this support request correctly.

---

### Post by SSVegito888 on 2008-07-16
Why don't you just wipe the entire hrad drive with DBAN from sourceforge.net.

Use one of the high security options on DBAN though.  I don't think the latest stable version is available as binary download yet, so just compile it or use the beta DBAN or a slightly older version which come as source or Binary.

Also, I don't think the older versions have USB support but I think the newer ones, including "Stable" do have USB Support.

BOOT WITH FLOPPY OR CD (Which Ever one you Dowloaded)

If you use Linux it is easier to download the ISO to create CD.


PS: My 80GB Hard Drive takes about 24 Hours to wipe using Gutmann Method (One of the High Security Methods). Another high security method is PRNG Stream. If you use this method MAKE SURE YOU SET THE ROUNDS to 8 OR HIGHER, SO THAT IT WILL BE SECURE.




After tthe steps above, just reinstall Ubuntu.

---

### Post by coffeecat on 2008-07-16
> **aysiu said:**
> The ideal scenario is to create a new user and then shred the old user while keeping the installation intact, if I'm understanding this support request correctly.

Yes, that would be more complicated. Particularly with shred's unwillingness to shred folders - at least when I tried a few months ago.

---

### Post by Old Pink on 2008-07-16
> **aysiu said:**
> I don't think Old Pink wants the new owner to reinstall either, though.

The ideal scenario is to create a new user and then shred the old user while keeping the installation intact, if I'm understanding this support request correctly.

Exactly, that's what I've ended up doing. 

> **coffeecat said:**
> Yes, that would be more complicated. Particularly with shred's unwillingness to shred folders - at least when I tried a few months ago.

Unsure why shred is so against folders, but it was in my situation too. Resorted to > sudo su
shred -fv /home/name/* && shred -fv home/name/*/* && shred /home/name/*/*/* && shred -fv /home/name/.*/* and so on, worked pretty well from what I could see. 

Thanks guys. Sucks a bit to see there isn't a tool to do this for you.

---

### Post by Habbit on 2008-07-16
Shred does not work on directories because it writes over its arguments. Directories cannot be opened with fopen or whatever shred uses.
Next time, instead of resorting to the * */* */*/* .*/* etc. trick, you can do the following: ```
/home/user# find . -type f | xargs shred -u
```Or even:```
/home/user# find . -type f -execdir shred -u {} +
```
and then recursively remove the user dir with rm -rf /home/user. You must be careful not to have any mountpoints/hardlinks inside your user dir that can lead shred/rm to kill other parts of the filesystems. In particular, network shares are mounted in ~/.gvfs, so make sure all are disconnected before starting the process.

---

### Post by SSVegito888 on 2008-07-17
I also have a question that falls into this catagory.

Is there a GUI for ANY Shredding Utility for Ubuntu that uses secure algorithms such as DoD or Gutmann?


Thanks,

SSVegito888

---

### Post by bilijoe on 2008-07-17
> **aysiu said:**
> If that's not good enough, you can look into degaussing. [COLOR=Red]You do NOT want to degauss a hard drive, unless you never plan to use it again.[/COLOR]   :-s

Agencies like the FBI and CIA used to use this technique before they discarded a hard drive, to prevent sensitive material from falling into the hands of the garbage man.  They used it because it is quick and effective.  Problem is, there is one side of one physical disk within the hard drive, that contains "positioning data".  This data provides markers used to position the heads, and without this data, the drive has no way to know where to position the comb that carries the physical heads, when a read or write request comes in.  

Degaussing wipes EVERYTHING off the HDD, including this positioning data, and the data returned by the drive when it receives an "identify yourself" request from the OS  (this is how the OS knows if it is dealing with an IDE, SCSI, ATA, SATA, CD, DVD etc., and how it knows its dimensions, i.e., number of cylinders, heads, and sectors, of the device, as well as other identifying information).  :(

Believe me, this was my career, before I retired.  At one time, not that long ago, I knew as much about hard drive technology as anybody, and served as a consultant to governments, intelligence agencies and military organizations around the world.  I had nothing to do with the technology used to actually record what is essentially DC data (ones and zeros are represented by two different DC voltages) on a medium (magnetic emulsion) that can only record a continuously changing signal (i.e. AC).  That is an entire field unto itself.  But in all other aspects of Hard Drive technology, I was an acknowledged World Class expert*.  So when I tell you [COLOR=Red]DO NOT DEGAUSS A HARD DRIVE, if you EVER expect to use it again[/COLOR], you can take it to the bank. 

*[COLOR=SeaGreen]Definition: expert; an "ex" is a has-been, a "spurt" is a drip under pressure.[/COLOR]

---

### Post by bilijoe on 2008-07-17
> **coffeecat said:**
> Also, the instruction for iterations is unclear. The default is 25 (:shock: that **is** secure). If you want to change it to 5, say, the syntax is:

shred -n 5 *file/partition*

or

shred --iterations=5 *file/partition*

...and don't forget to add the verbose flag. :) Actually, 8 (the Government standard) is truly overkill; 3 is really all it takes unless it is the CIA or NRO that you are worried about, then I'd go with the default (25).  In reality, I almost always used just one, primarily because of the amazingly long time involved, and, because, knowing all the technologies available (and I do mean _all_ the technologies available, to governments, intelligence agencies, the military, foreign governments, etc.), I know that a single overwrite is actually sufficient, though the government's standard for the highest level of security, is 8 overwrites (with different data patterns for each pass.  This is truly nearly ridiculous overkill, and takes an unimaginable amount of time, even on a small Hard Drive.  In a previous post, SSVegito888 mentioned that an 8 pass, Gutmann Method wipe of his 80Gb HDD took about 24 hours.  Consider the time it would take to wipe 250Gb, or more.  Again, unless you have a valid reason for being *really paranoid*, I'd settle for a single pass. However many you choose, at least it is a process that can safely be left unattended.

Gutman, PRING, and DOD are technically more aggressive than "shred", however, again, unless it's the government that's going after your data, and it's a very high profile case, shred is all you really need.  (DOD, by the way, denotes the method developed by the Department of Defense.)  Recovering overwritten data, after even one overwrite, is a *very* expensive, and time, and resource consuming endeavor.  Shred, at 3 passes, is really totally effective.  You'll probably hear horror stories to the contrary, but as one whose career was dedicated to just this kind of stuff, I can tell you, they are all fiction.  

As I said, even knowing all the available technologies for recovering overwritten data, the only time I ever personally used more than one pass was when the data involved was truly sensitive (as in involving National Security issues), and was someone else's data (like the Government's).  

Identity thieves, and the like, simply do not have available the technology, the equipment, or the time to read through even one overwrite, nor do "curious" Computer Science, or Physics College students.  Even Bill Gates, with all his resources, would be hard pressed to come up with the wherewithal to read overwritten data.  

Simply delete it, and, in less than a day, I can find you 1000 High School students who can read it, in the blink of an eye.  Overwrite it, even only once, and it's gone, gone, gone.

[COLOR=DarkOrange][COLOR=Red]IMPORTANT NOTE: Be sure to see Habbit's earlier post regarding the special case posed by directories![/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black]
If you want a brute force product, designed specifically for this purpose, check out Darik's Boot and Nuke, at[/COLOR][/COLOR][COLOR=DarkOrange][COLOR=Black][COLOR=Blue] [/COLOR][/COLOR][/COLOR][[COLOR=Blue]http://dban.sourceforge.net/[/COLOR]]("http://dban.sourceforge.net/")[COLOR=DarkOrange][COLOR=Black], also mentioned in [/COLOR][/COLOR]SSVegito888's earlier post.

---

### Post by coffeecat on 2008-07-17
**bilijoe**, those last two posts are the most interesting (and useful) things I have read on this forum for a long time. I am truly grateful, and in response I have clicked the 'thanks' button for **both** posts. :)

> **bilijoe said:**
> [COLOR=SeaGreen]Definition: expert; an "ex" is a has-been, a "spurt" is a drip under pressure.[/COLOR]

Excellent! :lol:

---

