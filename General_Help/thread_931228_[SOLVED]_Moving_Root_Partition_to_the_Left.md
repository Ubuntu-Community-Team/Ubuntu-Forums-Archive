---
title: "[SOLVED] Moving Root Partition to the Left"
date: 2008-09-27
forum: General Help
---

### Post by merkel04 on 2008-09-27
Hello,

Ive been using ubuntu full time for about a month now, and started getting very low on space.

I decided to take the full plunge and delete my windows partition and add its space into my ubuntu partition.

Unfortunately, my windows partition was the 1st partition, and as far as I can tell, I cannot resize my existing ubuntu partition to the left to use up that unallocated space.

I have tried booting into the live cd and messing around with no luck.

I posted my screen shot of gparted below.

My goal is to add all of the unallocated space shown below, into the ext3 partition shown below, Without completely formatting.

Thanks for any help!
Brian

[img]http://img242.imageshack.us/img242/7875/gpartedtk9.png[/img]

---

### Post by plucky on 2008-09-27
You cannot resize a partition to the left,but you can move the start of the partition to the left using the Live CD.

As it has to move all your data as well,this can take a while,so be patient.

Once the move has been completed,you can then resize the partition.Do each step separately. 


**Or** if you are feeling daring,you could create a separate partition of the unallocated space and move your /home data there.

See this link for [Creating a separate home partition](http://www.psychocats.net/ubuntu/separatehome)


Good Luck

---

### Post by merkel04 on 2008-09-28
Would I use gparted from the live cd to do this? I couldn't find the correct option to do this when I was using the live cd + gparted.

Anymore help would be greatly appreciated.

Thanks again,
Brian

---

### Post by louieb on 2008-09-28
Just a thought. Create a partition at the start of the unused space the same size as your current partition and copy the current partition there. 

once you get it booting to the new partition it will be easy enough to grow it to the right. and much faster than growing it to the left.

And as plucky pointed out you need to run GParted from a Live CD.

My favorite live CD for partition work is  the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")

---

### Post by merkel04 on 2008-10-01
Before I attempt that I just wanna double check...

1.) Boot from the live CD
2.) Create new ext3 Partition
3.) Move the entire file system to the new partition.
    -Is it really as simple as just dragging and dropping the file system into the new mounted partition?

4.) Resize the new partition into the old partition.
5.) Fix grub to boot from the new partition.

Thanks again for all the help

---

### Post by dcstar on 2008-10-01
> **merkel04 said:**
> Before I attempt that I just wanna double check...

1.) Boot from the live CD
2.) Create new ext3 Partition
3.) Move the entire file system to the new partition.
    -Is it really as simple as just dragging and dropping the file system into the new mounted partition?

4.) Resize the new partition into the old partition.
5.) Fix grub to boot from the new partition.

Thanks again for all the help

Do yourself a favour and create a separate /home partition in the free space, then you will have a far more robust system and more than enough space in the original root partition (without having to touch it now).

Do a forum search for detailed instructions.

---

### Post by vanadium on 2008-10-01
I support the suggestion of dcstar to create a separate data partition. the other approaches are more complex to achieve and are only recommended if your know some linux system administration. It can be easier than what dcstar suggests, though. Instead of moving the home partition (also a quite technical operation), you can just move your user data, documents, spreadsheets, pictures, etc. to the new big partition. Most of it can be done just using the graphical tools, from within a normal Ubuntu session. Even when things can be done graphically with a nautilus instance with root privileges ("gksudo nautilus") I will give the commands because that is much easier for me.

1. Creating the partition
1.1 Install gparted if you did not already using Synaptic Package manager.
1.2 Start gparted: Alt+F2, type "gksudo gparted" <enter>.
The advantage of running gparted from a normal session is that there is no possibility for you to accidentely delete or harm your system partitions.
1.3 Create a partition filling the unallocated space. Format it in ext3 format. This can all be done from within gparted. Take note of the device name that is assigned to the new partition (e.g. /dev/sda7)

2. Mounting the partition
Here, we will need some command line work to obtain the needed information.
2.1 Open a terminal and lookup the UUID of the newly created partition: "sudo blkid". Along the lines, you will find one for your newly created partition. It will look like:

```

/dev/sda7: UUID="c9cb8b29-152a-47ac-b952-5b9909a290ba" TYPE="ext3" 

```

You will need the UUID part for your /etc/fstab.
2.2 Open /etc/fstab for editing. At the terminal: "sudo gedit /etc/fstab". This opens the usual text editor gedit, displaying the current contents of your /etc/fstab. Add two lines for your new partition that looks like (the first one is just a comment and can be omitted)

```

# /dev/sda7
UUID="c9cb8b29-152a-47ac-b952-5b9909a290ba" /mnt/data ext3 defaults 0 2

```

(Just copy/paste the UUID from the terminal to gedit: that way, you won't make a mistake).

Save /etc/tab when done and close gedit.

2.3 Creating a mount point and mounting the partition

```

sudo mkdir /mnt/data
sudo mount -a

```

The last command does execute all mounts specified in /etc/fstab. It will therefore also mount the newly specified partition under /mnt/data. THERE SHOULD NOT BE ANY OUTPUT from the mount -a command. If there is, stop here and post the output: it means there is a mistake or something else in your /etc/fstab is not correct.
[/code]

3. Moving the data. Now you can move your current data to the new partition and create symbolic links in your home directory to them. The symbolic links will make sure that you can access the data just like before. In other words: as a regular user, you won't see that the data have actually moved to a new location.

You need to do this with a nautilus with root permissions. Load that with "alt+F2" "gksudo nautilus<enter>". Cut / paste your "Documents" folder (just as an example) to the /mnt/data partition. Next, create a symbolic link. That can be done with nautilus (right-click, Make link, then move the link to the location where your data were intially), or with the command "ln -s /mnt/data/Documents ~/. Now, your data reside on the other partition, but are accessible from within your home just like before.

---

### Post by merkel04 on 2008-10-02
After looking around I think I will go ahead and give moving my home dir to its own partition. I think ill try out the directions that plucky posted tonight sometime.

Another quick question though...

Are program files stored in the home partition or in the file system? I know my wine apps are all in the home partition, but what about native linux programs?


Thanks again,
Brian

---

### Post by plucky on 2008-10-03
> Are program files stored in the home partition or in the file system? 

Programs are installed in the root filesystem,only configuration files are stored in your home partition,usually as hidden files.(i.e they have a . before the filename)

If you follow the link I posted earlier,all your program configurations should stay the same. 

Good Luck

---

### Post by merkel04 on 2008-10-03
Just got done doing it using the directions you posted.

It amazes me how easy that was lol.

Thanks again for the help,
Brian

---

### Post by GetVerticalPV on 2008-10-04
I in the same position and determining how to best regain the space that Windows used to have.  It seems like moving my home directory as recommended here is the best approach, but I'm curious how this will impact my future upgrades?  Will I have to re-establish the symbolic links every time I do an upgrade?

---

