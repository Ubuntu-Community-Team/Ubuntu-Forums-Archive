---
title: "fsck on unclean filesystem. Usable alternative for mom and pop?"
date: 2008-11-21
forum: General Help
---

### Post by steckelfisch on 2008-11-21
Hi,

I just had my laptop shutdown due to an empty batery.
When I restarted again, there was an unclean partition. (on other
ocasions there where more than one)

I'm trying to get relatives and friens to at least try Ubuntu,
but fixing an unclean filesystem is not something I would like
them toe experience, (even though it is a piece of cake for me)

Are there any packages I could install or settings I could change
so a 'dumb' user does not have to bother with this kind of
system maintenance?

Regards,

---

### Post by philinux on 2008-11-21
It not a good idea to disable this but you can increase the internal between routine checks.

Shows file state and boot number

sudo tune2fs -l /dev/sda1  (give info)

sudo tune2fs -c 50 /dev/sda1 (changes the routine check interval to 50)

sudo touch /forcefsck  (forces a check next reboot)

---

### Post by steckelfisch on 2008-11-21
Increasing the fsck frequency does not resolve the 'fsck failed, please run it manualy'. Does it?

I also would like to add, that when running it, I continualy hit enter (in response to "fix<y>?". 
So my input to this functionality is rather 'predictable'.

---

### Post by prshah on 2008-11-21
> **steckelfisch said:**
> 
I just had my laptop shutdown due to an empty batery.
When I restarted again, there was an unclean partition. (on other
ocasions there where more than one)


Usually, you should not get the prompt to run fsck manually. This will happen only if the filesystem is in a bad inconsistent state, which is very rare with ext3's journaling file system.

Are you by any chance using ext2? Then you will get the fsck "fix manually" prompt, _everytime_.

The best solution (considering your actions) will be to use ```
fsck -y /dev/sdxx
``` whenever your get the advice to run fsck manually.

---

### Post by steckelfisch on 2008-11-21
that's correct. I just had to run it on a ext2 partition. 
(/tmp is mounted on a ext2)

But I'm quite sure I've experienced it with ext3 filesystems also. 
(my memory may play trick's on me). I will switch my /tmp to ext3 also
and see if it helps.

---

### Post by philinux on 2008-11-21
> **steckelfisch said:**
> Increasing the fsck frequency does not resolve the 'fsck failed, please run it manualy'. Does it?

I also would like to add, that when running it, I continualy hit enter (in response to "fix<y>?". 
So my input to this functionality is rather 'predictable'.

If it needs to run it needs to run, else broken system.

And as the other poster sais adding -y to the command will just let it run without having to says yes everytime.

---

### Post by steckelfisch on 2008-11-21
Ok. I agree it needs to run if it needs to
(and will use the sugested option :-) )

I do not agree that an unskilled user should now how to perform this
action. I could live with an issued warning, but the fix should be 
fully automatic.

But maybe my issue is resolved when I fase out ext2 in favour of ext3

---

### Post by philinux on 2008-11-21
The only time I've had to manually run this was when my hard drive was failing. Then guess what. Gutsy came along with a new fsck routine and it fixed the errors. disk still running at girlfriends. 

Ext3 is the way to go.

---

### Post by prshah on 2008-11-21
> **steckelfisch said:**
> 
(/tmp is mounted on a ext2)
But I'm quite sure I've experienced it with ext3 filesystems also. 


> **steckelfisch said:**
> 
But maybe my issue is resolved when I fase out ext2 in favour of ext3

Yes, as I mentioned, on ext3, this is (rarely) possible only when there is extensive (but recoverable) damage (especially to the journal).

The only difference between ext2 and ext3 is the addition of journaling. You should have no difficulties using ext3. In fact, there are ways to convert an ext2 filesystem to ext3; but it's not foolproof (or is that for the reverse: ext3->ext2?); and since it's only your /tmp that affected, it makes more sense to reformat that to ext3.

---

### Post by Herman on 2008-11-21
> I'm trying to get relatives and friens to at least try Ubuntu,
but fixing an unclean filesystem is not something I would like
them toe experience, (even though it is a piece of cake for me)

Are there any packages I could install or settings I could change
so a 'dumb' user does not have to bother with this kind of
system maintenance?**From GUI in the Ubuntu 'Desktop' live CD:**
Just go 'System'-->'Administration'-->'Partition Editor' (gparted), and open GParted.
Right-click on the partition to run a file system check in, and click 'Check'.
Click 'Apply', and click 'Apply' again to confirm.
Wait a minute or two while the file system check runs.
When it has finished you can click on the '> Details' expansion button and subsequent '>' buttons for the drop-down boxes to read what commands were run and what the results were.
That's an easy 'Mom and Pop' way to run a file system check on just about any file system, and it runs commands that are powerful enough to really fix most file system problems too.

It's important to remind people that we should only run a file system check on a file system that isn't mounted, and that's one reason why it's good to use the live CD for that.

Regards, Herman :)

---

