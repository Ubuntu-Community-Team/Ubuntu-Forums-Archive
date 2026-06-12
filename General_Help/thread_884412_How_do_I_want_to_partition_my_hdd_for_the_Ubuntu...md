---
title: "How do I want to partition my hdd for the Ubuntu..."
date: 2008-08-09
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-09
Alright I was getting ready to do the partition, but didnt know what to categorize the partition as...

ext3
ext2
xfs
fat16
fat32

etc etc

Which one do I use and why?

Do I select the "Guided" or do I do it "manually"?

It seems I have the following partitions already done...

/dev/sda1 ntfs - says it is 40k but only used 17400

/dev/sda5 swap said this is 3306 and has used 0

what does all of that stand for and mean?

Someone suggested before that I make a swap partition... apparently this was automatically done for me when I partitioned out windows?

---

### Post by Taxman415a on 2008-08-09
Since you're new, you probably just want to go with ext3, that is the standard linux filesystem and works very well. Guided might work for you, it depends on how much space you want for windows and how much for Ubuntu and what the guided option returns. Select it and see, since it doesn't commit changes until a later step. I always use manual since I already have a number of partitions on a couple drives so I need to select the right one and I'm used to manual partitioning.

How large is your HD and how much space do you want for each?
It's a little surprising you have that sda5 swap partition, what did you see that in?

---

### Post by sandysandy on 2008-08-09
i would suggest u read some tutorials on the subject.

also BACKUP important data.

here are a few links

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

NTFS is for windows.

ext3 - linux



regards

---

### Post by PsychedelicWonders on 2008-08-09
> **Taxman415a said:**
> Since you're new, you probably just want to go with ext3, that is the standard linux filesystem and works very well. Guided might work for you, it depends on how much space you want for windows and how much for Ubuntu and what the guided option returns. Select it and see, since it doesn't commit changes until a later step. I always use manual since I already have a number of partitions on a couple drives so I need to select the right one and I'm used to manual partitioning.

What makes ext3 so much easier the way it runs?

> How large is your HD and how much space do you want for each?
It's a little surprising you have that sda5 swap partition, what did you see that in?

its a 80g hdd.  im doing roughly 37k each.

the swap partition was right under the ntfs

is that a good or a bad thing?

should I leave that swap partition, or should i delete it and make a new one?

what exactly does /dev/sda5 stand for?

like what exactly are the numerical values of the / and the letters and numbers?

---

### Post by sandysandy on 2008-08-09
ur hard disk can be partioned

sda1 is first partition (0,0)

sda5 is fifth partition (0.4)

read this

[http://www.tldp.org/HOWTO/Flash-Memory-HOWTO/basics.html](http://www.tldp.org/HOWTO/Flash-Memory-HOWTO/basics.html)

for SWAP read this

[http://www.linux.com/feature/121916](http://www.linux.com/feature/121916)

regards

---

### Post by PsychedelicWonders on 2008-08-09
alright going off of that website, they said this...

Your memory stick will be considered as a USB mass storage device posing as a removable SCSI disk (sd)

But why is a hard drive being recognized as a usb sd disk?

so when they are on the same device, and you have multiple partitions, what gives them a numerical value like 0,0 or 0,4?

I techincally only have 2 partitions on my hdd, so why is it considering the swap #5? (or 4 for that matter, what is it 1 less in value?)

---

### Post by PsychedelicWonders on 2008-08-09
that one link said ext2 is the best for linux... but you said ext3.. what is the difference and which one should i use?

---

### Post by sandysandy on 2008-08-09
(0,0) means first hard disk, first partition. sda1
(0,1) means first hard disk, second partition.sda2

(1,0) means second hard disk, first partition.sdb1
(1,1) means second hard disk, second partition.sdb2

and so on

regards

---

### Post by Taxman415a on 2008-08-09
> **PsychedelicWonders said:**
> What makes ext3 so much easier the way it runs?

It's not necessarily so much easier, it's that it's the standard, most common filesystem for linux, so it's very compatible, and therefore the best choice if you don't have a specific well known reason to choose something different. You can read up on it at Wikipedia if you like.

> its a 80g hdd.  im doing roughly 37k each.

the swap partition was right under the ntfs

is that a good or a bad thing?

should I leave that swap partition, or should i delete it and make a new one?
Probably just leave it, though the size you reported is odd. You're switching back and forth between k and g so it's hard to tell.

> what exactly does /dev/sda5 stand for?

like what exactly are the numerical values of the / and the letters and numbers?

/dev stands for the device tree and sd stands for a scsi disc and a is the first hard drive then 5 is the fifth partition on it. Google for linux device naming, linux partition naming, or linux hard drive naming or something like that if you want to learn more or if we weren't clear.

---

### Post by PsychedelicWonders on 2008-08-09
ahh i got it i think.

and when you referenced 0,1 1,0 etc, those numbers are swapped out for letters from time to time in such examples like sda1 = sd0,0 from your chart?

thanks.

so should i do ext2 or ext3?

---

### Post by PsychedelicWonders on 2008-08-09
you're switching back and forth between k and g so it's hard to tell.


What is k & g?  and when do i switch back and forth between them?

thanks for the explanation, i understand how the disks are labeled now, thanks.

---

### Post by sandysandy on 2008-08-09
for ubuntu i am using ext3.

see these links

[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)

[http://en.wikipedia.org/wiki/Ext2](http://en.wikipedia.org/wiki/Ext2)

regards

---

### Post by Taxman415a on 2008-08-09
Wow, lots of questions. Keep reading and you'll keep learning. Here's another to read. It's the manual page for the sd driver. It explains the numbering and why it is both for hard drives and USB, etc. [http://swoolley.org/man.cgi/4/sd](http://swoolley.org/man.cgi/4/sd) On a running Ubuntu system you can just type man sd from a terminal to get that.

Oh, and you definitely want ext3 not ext2. You'll see that if you read up on it.

As for the switching k and g, I was referring to this line, but I think you did it in others
its a 80g hdd. im doing roughly 37k each.

also the k in this was confusing:
/dev/sda1 ntfs - says it is 40k but only used 17400

---

### Post by PsychedelicWonders on 2008-08-09
hmm.  seems ext3 makes the most sense if its just like 2 but with a better back up after power failure basically.

thanks.

---

### Post by PsychedelicWonders on 2008-08-09
alright, now do I want this partition to be "the begining or the end"?

What mount point do I want?

I was getting a root error message, so I am going to assume it was looking for a mount point correct?

I had it blank.

---

### Post by PsychedelicWonders on 2008-08-09
help, im tired and falling asleep...

---

### Post by sandysandy on 2008-08-09
> **PsychedelicWonders said:**
> 

What mount point do I want?


I had it blank.

mount point [COLOR="Red"]/[/COLOR] for root.

regards

---

### Post by PsychedelicWonders on 2008-08-09
what about the beginning or end?

does it matter?

---

### Post by mikjp on 2008-08-09
> **PsychedelicWonders said:**
> that one link said ext2 is the best for linux... but you said ext3.. what is the difference and which one should i use?

ext3 adds journaling to ext2. This means in practice that the system can better recover from things like power failures or accidental crashes. Use ext3.

You should make three partitions:

/swap 
/ 
/home

where /swap is 1-1,5 * RAM, / might be 5-10 GB and the rest of the free space for /home. Use ext3 for / and /home.
         

greetings,

mikko

---

### Post by sandysandy on 2008-08-09
> **mikjp said:**
> 

where /[COLOR="Red"]swap[/COLOR] is 1-1,5 * RAM, / [COLOR="Red"]might be 5-10 GB [/COLOR]and the rest of the free space for /home. Use ext3 for / and /home.
         

greetings,

mikko

SWAP of 5-10 gb may be an overkill. :)

regards

---

### Post by mikjp on 2008-08-09
> **sandysandy said:**
> SWAP of 5-10 gb may be an overkill. :)

regards

Certainly, but I wrote 5-10 GB for /, not for swap.

mikko

---

### Post by PsychedelicWonders on 2008-08-09
> **mikjp said:**
> ext3 adds journaling to ext2. This means in practice that the system can better recover from things like power failures or accidental crashes. Use ext3.

You should make three partitions:

/swap 
/ 
/home

where /swap is 1-1,5 * RAM, / might be 5-10 GB and the rest of the free space for /home. Use ext3 for / and /home.
         

greetings,

mikko

So i want to make 3 partitions in addition to my ntfs?

There is already a swap partition of 3306, but I'm not sure what numerical value it has, does it matter?

When I partition for ubuntu, it prompts me for a choice of dubbing it "Beginning or end"... which one do I choose?

---

