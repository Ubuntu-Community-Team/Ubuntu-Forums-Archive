---
title: "Creating swap partition?"
date: 2008-12-06
forum: Installation &amp; Upgrades
---

### Post by kartal on 2008-12-06
Hi  I am having hard time to find some info on this one. Most of the documents lead me to creating a swap file rather than swap partition.  I hope someone can help me out on this one.

I want to create a swap partition and activate it.

I read the swap file Ubuntu documentation. But I do not want a swap file I want a swap partition. So I created swap partition(stole some space from my existing fat32). It is swap file system and formated. How can I activate it now?


thanks

---

### Post by cdtech on 2008-12-06
You would need to find an empty partition or repartition a disk to add additional swap space.

To create a swap file without repartitioning your hard drive use the dd command. To create an empty 1GB file, type:
```
dd if=/dev/zero of=/swapfile bs=1024 count=1048576
```
/swapfile being the name of the swap file, and the count of 1048576 is the size in kilobytes (i.e. 1GB).

Then prepare the /swapfile:
```
mkswap /swapfile
```
Then mount it using:
```
swapon /swapfile
```
The /etc/fstab entry for a swap file would look like this:
```
/swapfile       none    swap    sw      0       0
```

---

### Post by kartal on 2008-12-06
Cdtech

I already have a swap partition and I do not want to use a swap file :) I am trying to figure out how to activate and use my swap partition.

---

### Post by cdtech on 2008-12-06
> **kartal said:**
> Cdtech

I already have a swap partition and I do not want to use a swap file :) I am trying to figure out how to activate and use my swap partition.

Use the swapon command:
```
swapon -a
```
And add the entry for your "/etc/fstab" file:
```
/dev/sda5 none swap sw 0 0
```

---

### Post by kartal on 2008-12-06
thanks cdtech I will add. It sounds very easy. Only thing is that my fstab file has UUID=some numbers on multiple lines. Does htat mean my swap partition would need such number as well or /dev/sda5 none swap sw 0 0 would be enough? I just do not want to have  surprise at next restart :)

thanks again I was just looking for this.

---

### Post by cdtech on 2008-12-06
I have that backwards. You need the fstab entry then the "swapon -a" command. If you don't have it listed within the "fstab" file then mount the swap using the command:
```
swapon /dev/yourswappartition
```

---

### Post by cdtech on 2008-12-06
The device is fine. If you want to use the block id just use the command:
```
blkid
```
copy and paste into your fstab file.

---

### Post by kartal on 2008-12-06
I just did swapon dev/ line and used "free" command. It seems like it is activated. 

Now this line below in my ftstab will activate the swap partition automatically right I wont need to add swap on everytime or add it somewhere else? Sorry linux is a new thing to me and I am trying to figure out and understand at the same time.

/dev/sda5 none swap sw 0 0

---

### Post by JoesCat on 2008-12-06
Looks like you already have plenty of replies so this is basically redundant.....

take a look at the file: /etc/fstab

If you need more info, you can type in "man fstab" for more help, then press q to quit.

Here is a sample line for swap in the /etc/fstab file:
```
/dev/hda5 swap swap defaults 0 0
```

You will need to use the correct partition where I typed in /dev/hda5 for my example.

Hope this helps.

---

### Post by cdtech on 2008-12-06
> **kartal said:**
> I just did swapon dev/ line and used "free" command. It seems like it is activated. 

Now this line below in my ftstab will activate the swap partition automatically right I wont need to add swap on everytime or add it somewhere else? Sorry linux is a new thing to me and I am trying to figure out and understand at the same time.

/dev/sda5 none swap sw 0 0

Your correct, good luck with your new adventure. ;)

---

### Post by kartal on 2008-12-06
Hey Guys thank you so much. This seems to work fine now. At least "free" command shows me an active swap partition. I cannot really tell if it makes a difference at the moment thou :) 

thanks again

---

### Post by JoesCat on 2008-12-06
Due to your reply of
> I cannot really tell if it makes a difference at the moment thou I think it is best to explain what you really want out of having a swap.

Consider swap a safety net which you will rarely ever use, and preferably not use. swap is cheap insurance if you consider 1G of hard drive is less than 1 dollar.

A lot of software is written assuming there is abundant RAM available, and therefore don't check for failure to aquire enough RAM. This unfortunately is a programming practice that should be avoided, but you'll see many examples on the internet and if you want to help code programs, it's one of the 1st/easiest things to look for and correct.

If you did not have enough RAM AND whatever you were doing all of a sudden could not get more RAM, you would have a problem (I've seen plenty of seg-faults and am glad to have helped fix a few due to this simple miss). This is where having swap saves your day.

What swap does is act as a safety net in case you do run out of RAM by using memory on the hard drive.... and you might not have noticed it with slower computers like 100MHz machines which were more common a few years ago, but you sure will notice it now if you do use swap. You'll notice your hard drive light running a lot and your computer slows down real fast like a ferrari hitting a brick wall because hard drives are slow compared to today's computers.

If you never experienced the slow down, one way is to load up memory intensive applications...let's say GIMP and just begin loading a lot of high definition pictures to take away available RAM until you cross into swap space... when you cross into swap space, you'll know it because your mouse, computer and everything goes sluggishly slow and you need to be patient and let the computer recover in time.
If you know you are low on RAM and seem to experience these slow-downs often, it may be a good idea to get more RAM.

Other operating systems also have swap too such as BSD. Others have hidden files such as Windows or OS/2.

Since you were asking about setting up swap, I'm sure most of the info above is redundant (but it helps other readers reading your thread to come up to speed).

The "slowdown" aspect is really the main reason for replying and I think was worth pointing-out so you know what happens.

---

### Post by cdtech on 2008-12-06
Using swap is the way the Linux kernel handles the virtual memory subsystem thats incorporated into the code.

The only reason there is virtual memory in the first place is that you may not have enough RAM for all the programs running at once, and disk space was cheap. Swap is still tightly integrated into the kernel code and there should be some swap space used for this purpose. The kernel code runs smoother with some swap space.

**UPDATE::.**
Think of the older systems that need swap. You really need the integration of swap within the code for such cases. You also need disk space to hibernate to as well (if you hibernate).

---

### Post by kartal on 2008-12-06
I have 3 gb of ram on my macbook pro. I do not think that I need swap partition for standard operations. The main reason for me was suspending and hibernation modes. Couple sources speculated that hibernation would require swap operations. CdTech I am glad that you clear that up for me as well.

---

