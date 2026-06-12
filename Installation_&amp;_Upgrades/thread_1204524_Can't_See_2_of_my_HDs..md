---
title: "Can't See 2 of my HDs."
date: 2009-07-04
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2009-07-04
Hello I just moved from 8.10 to 9.04.
I have a 250GB HD which I split in order to have a part as root and a part as home.  The root I formated in ext4, but the /home I didn't.  It is still in ext3, because I didn't want to loose my data.

Is there a way to convert ext3 -> ext4 without loosing the data?

I also have 2 HDs.  One of them is 400GB and NTFS.  I used to be able to access it in 8.10 but now it produces an error.

**Error org.freedesktop.Hal.Device.UnknownError.**

So although I can see the HD I can't mount it.

On the other hand I also have another HD which is 120GB, and during the installation I formatted it with ext4, and mounted it to /var or /usr (I am not sure).  I did that because it said that if I don't mount it, I will not be able to use it.

My question is : How will I be able to access this HD?
Can I use this HD to expand the space on my /home?
Is there a way to expand the space of your /home and if there is, how do I access it?

Thank you all in advance :-)

---

### Post by starcraft.man on 2009-07-04
> **Ifaistos said:**
> 
Is there a way to convert ext3 -> ext4 without loosing the data?



[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21]("http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21")

I'd hold off on an EXT4 upgrade for your data though, I only run it on my roots, all my data is EXt3 or NTFS (Windows share). That's my opinion, ya talk to different people you'll get different views. I like my data nice and secure on a proven fs.

> I also have 2 HDs.  One of them is 400GB and NTFS.  I used to be able to access it in 8.10 but now it produces an error.

**Error org.freedesktop.Hal.Device.UnknownError.**

So although I can see the HD I can't mount it.


Not familiar with this particular error. Can't help.
> 
On the other hand I also have another HD which is 120GB, and during the installation I formatted it with ext4, and mounted it to /var or /usr (I am not sure).  I did that because it said that if I don't mount it, I will not be able to use it.
Ok........ that explains some things, both of those directories are necessary (though not vital like bin or lib) and you can't set something to mount over them. The data would still be there, but once you set something to mount over it, you can't read or write to the files as long as it's mounted there. It'd take too long to explain, but I think once we fix this should be ok.

You could simply stop it from mounting there and move it to mount somewhere else but I'm a bit wary that maybe something might have gone wrong during installation and is causing the above error as well. I'd recommend you do a clean install, and this time, please don't mount a drive to any mount point that is only 1 branch off root (/) whether it's /var, /usr, /bin, whatever, don't. Those are all important directories. If you leave it unmounted, it will automatically be mounted at boot.

> My question is : How will I be able to access this HD?
Reinstall, don't mount to important directories.
> Can I use this HD to expand the space on my /home?Not directly, unless you format it (and it's data) and then partition it as EXT3/4 and mount as home at the partition stage. Back your data up if you do this. A few options present themselves:

You could use the entire drive as /home. You could just have it partitioned and let it be automounted at boot as previously said. You could alternatively mount the drive to a folder in your /home directory like say /home/user/storage. 

There is another alternative called LVM, if your reinstalling as I said it's an option. Bascially, an LVM is a more advanced form of partition, rather than being a physical divide of the drive it's almost virtual. It basically becomes a big pool of space (you can add drives as you like to this pool on the fly no less) and then change the size of partitions like /home and / as you like. It's a bit more complicated managing LVMs though, have a look at [this ]("http://sunoano.name/ws/public_xhtml/lvm.html")and if you have any questions reply. The page offers a better explanation than mine, it'd take too long for me to reproduce it here.

Those are your options I believe. Think about it and reply with questions as need.

---

### Post by Ifaistos on 2009-07-05
Hello Starcraft man :-)

Excellent answer!!! Thank you for your time and effort to answer my questions.  I think it is obvious that although I am very computer literate and I use Linux for the past 9 years (4 years as my main), I lack big chunks of understanding of how it works! :(

As far as the upgrade is concerned I'll wait for a little while.. Perhaps until 9.10.

As far as the 400GB is concerned I have no idea... I thought it was because I didn't have SAMBA, but now I do.. and I get the same error.

about my 120GB.
Excellent idea!! Mounting under /home/storage or maybe /home/120GB or smt like that. Duh!!

How will I be able to do that?  I am sure there is a way without reinstalling.  I would hate to reinstall.  There's got to be a way!!  Isn't there?!

btw.. 120GB HD is empty so I don't have to Backup.

Thank you again Starcraft man :-)

Thanks also to anyone who will answer any of my questions.  Please send me any documentation, resources you may think of, that explain your answer.  I would like to read a bit more and expand my knowledge on Linux.

---

### Post by dandnsmith on 2009-07-05
SAMBA wouldn't help with local mounting (of an NTFS filesystem or other) - it allows you to provide access to remote systems running Windows.
To access filesystems on a remote PC running Windows you'd be using smbclient, which is often/usually there by default.

To tackle the local HDD with NTFS you may need to add something like ntfstools - for this sort of thing I tend to try the Synaptic package manager, input a keyword (NTFS here), and let it tell me which tools I might need, and which are already installed (and then let it install the missing bits).

As to documentation, my terrible memory fails to disgorge links to the background material I've used to help.

---

### Post by Ifaistos on 2009-07-05
So I decided to reinstall..

During installation I asked for those two HD, to be mounted under /home/120GB and /home/400GB.  It worked perfectly!! Now I can see both of them, and write.

Thank you all for your help.

ps.  How can I declare this thread solved/closed?
How can I thank a person for helping me?  I remember there was somewhere an option for that....

---

