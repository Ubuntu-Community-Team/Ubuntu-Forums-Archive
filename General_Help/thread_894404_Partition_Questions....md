---
title: "Partition Questions..."
date: 2008-08-19
forum: General Help
---

### Post by infinitelink on 2008-08-19
What's the difference between */var* and */swap*? 
And should */tmp* be mounted under */var*? (aren't they similar?)

And if */home* is for the user, then why separate */home* from */usr*? Is there a difference, a reason, or whatever? Will separating them prevent program configuration files (the hidden ones which begin with names begun with a period so that they're hidden) from being placed in the */home/[username]* area? (or is having files there preferable for a later install or sharing between systems?)

And what's */boot* do? I'm setting-up an new install and this kind of information is pertinent. : )

---

### Post by Elfy on 2008-08-19
This should help [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html)

I think that all users have a folder within /home eg /home/user, /home/another, /home/one

/boot contains your saved kernels and GRUB - if you are going to have one don't make it too small and make sure that you have sufficient space before you let kernel updates go ahead.

/var is in the link I gave, swap is a partition in it's own right unless you use swap files instead.

If you are just making a normal install I wouldn't bother with anything other than / and swap and use seperate partitions to store data only using /home for configs, which is what I do now.

---

### Post by Blancmange on 2008-08-19
> **infinitelink said:**
> What's the difference between */var* and */swap*?
/var is for files that get changed often, like e-mail, cache stuff etc. You might want to have it on a separate partition say, to reduce fragmentation. Since lots of strange stuff end up in var, you may even want to give /var some restrictive mount options so trojans that make their way there cannot be executed.

A swap partition on the other hand, is not a proper file system. It's more like a (slower) extension of your RAM. Only ephemeral data goes there (even more ephemeral than /tmp!). Multiple Linux installations can share the same swap partitions(s).
> And should */tmp* be mounted under */var*? (aren't they similar?)
They serve the same function. I think tmp used to be under /var until some bright spark decided it was much more useful to have it separated from /var so you could mount them in different ways. Quite often, you have /var/tmp just be a symbolic link to /tmp. A sombolic link BTW, is like a hyperlink. It becomes a broken link whenever whatever it points to isn't accesible. 
> And if */home* is for the user, then why separate */home* from */usr*?
/home is where the user home directories are. They correspond to what you normally think of as "users". The /usr directory is for "user" level programs and stuff in the technical sense of "user" versus "kernel". The kernel handles low level stuff like memory, disc I/O and interfacing directly with hardware. The bulk of the system such as the terminal sessions and the GUI run at the "user" level, using the services that the kernel offers though safe and consistent abstractions.

/usr is where your program files, libraries and help pages go. (They're run at the user level, rather than at kernel level). Separating the /usr directory from /home means you can easily build a live CD that has many applications installed (in /usr) but allows /home to reside on a RAM disc or a hard disc. On such a system, your personal stuff can get trashed, but the system and the programs you use are immutable ('cos they're on a CD).> And what's */boot* do? I'm setting-up an new install and this kind of information is pertinent. : )
I assume that's where the kernel resides and that it's placed in a special location within the filesytem so that the bootloader can find it without knowing fully how to read a proper file system. You couldn't restore a Linux system just by copying its files, since the /boot directory would end up too hard to reach for the bootloader.

I gather also that it takes special care to backup and restore a linux system by copying and restoring files. You need to preserve all the metadata and hard/soft links. That's what dar is for. I don't trust my ability to use dar though, so I plan to have my Ubuntu system split up into a few partitions plus a big one for /home and use GPartimage to do backups in the one one might use Ghost to backup the OS, programs and settings on the C: drive (the personal data would be on D:).

---

### Post by infinitelink on 2008-08-19
How large should /boot be? (I.e. recommendations.)

I've also seen different stuff on cleaning it up, here for instance, [http://www.linuxforums.org/forum/linux-newbie/10622-how-delete-old-kernel.html](http://www.linuxforums.org/forum/linux-newbie/10622-how-delete-old-kernel.html)

Some of that, however, is lost on me (and it's for a non deb system, I can tell); so any pointers on how to safely clean-out and maintain a */boot* partition?

---

### Post by Elfy on 2008-08-19
I've seen recommendations for 50Mb - which then leads to problems with updating kernels and I've seen a recommendation for 250Mb - personally, unless there is a pressing need for it I would recommend not having it seperate at all and just have it in / 

But as a guide mine is ~60Mb with 3 kernels.

---

### Post by tuxulin on 2008-08-19
here is a live example just to clear up some confusion on how to set a file system up 
hope it helps.

/dev/sda1   287M    49M   224M  18% /boot   - can grow fast depends on use
/dev/sdb3   142G    43G    93G  32% /home   - 
/dev/sda7   4.1G   110M   3.8G   3% /opt    - slow growth unless specified 
/dev/sda8   2.1G    37M   1.9G   2% /tmp     
/dev/sda5   8.2G   4.2G   3.6G  54% /usr    - fairly fast mover 
/dev/sda6   4.1G   491M   3.4G  13% /var    -

Tuxulin

edit
if you have hard drive space to throw around then its best to split up your file
system as above (for example) in case of future trouble and its also better for 
managing

---

### Post by infinitelink on 2008-08-19
Why the fuss on the /boot needing to be big, though, as the kernel itself is only a few megs, right? If you strip-down the system to the kernel it fits on a floppy.

What other files occupy that space that take-up so much room?

---

### Post by Blancmange on 2008-08-19
> **infinitelink said:**
> Why the fuss on the /boot needing to be big, though, as the kernel itself is only a few megs, right?
Some people are hoarders and like to keep all the versions of the kernel they've ever had in /boot, I guess. (The old kernels can't be moved from and then back to the /boot partition, if my understanding of the mystic bootloader is correct.)

Whatever size you make your various partitions, it's rather nifty that GPartimage can move and resize them. (It takes a while, so have proper backups in case the operation fails.)

---

### Post by Elfy on 2008-08-19
There isn't a fuss as such - but if you don't keep an eye on how many kernels are in there you can find yourself in limbo needing to resize the partition because a kernel update has not been able to continue and you'll be left with > gzip: stdout: No space left on device update-initramfs:

---

### Post by infinitelink on 2008-08-19
Well thank you.

And I don't mind people being fussy since they often have good reasons; and if you ask, you get to appreciate them. 

I'm just deciding to really learn some of the linux/unix logic while I'm at it, since I am using it after all. (The linux, not the Unix: but they share logic so...)

Personally I don't like keeping every kernel possible: the Grub list gets too long. 

: )

---

### Post by Elfy on 2008-08-19
No I agree, I don't keep any more than 3, that's beacuse I have proposed open - so I usually have a 'could be dodgy' kernel installed, so I have that and the 2 previous.

Just better to know you have room now rather than later I would say.

---

