---
title: "trying to erase my harddrive"
date: 2008-08-14
forum: General Help
---

### Post by Champy on 2008-08-14
im trying to delete my harddrive, partitions and everything. and i found a link that SHOULD help me: [http://ubuntuforums.org/announcement.php?f=131](http://ubuntuforums.org/announcement.php?f=131)

it says to epic pwn ur com, type:

mkfs
mkfs.ext3
mkfs.anything

i tryed doing that and nothing happened, then i tryed changing "anything" to "ext3" but that didnt work. i tryed using gparted but it wouldnt let me change anything in my partitions. all i really want is to be able to dual boot vista and ubuntu. so i can do gaming on vista and still be able to use ubuntu but its been really hard for me. so i thought it would be easy to erase everything and try again. even though wubi doesnt work for me very well because i want to have more than 30GBs on ubuntu.

please help me.

---

### Post by zxscooby on 2008-08-14
You should be able to manually delete and edit partitions
using the alternate install cd.
I think with vista it is easier to edit your partitions with the windows partitioning tool first , then install
ubuntu.

---

### Post by erickghint on 2008-08-14
Gparted has a tendancy to mount anything that you're trying to edit if you're running it in the actual OS. Use either the Ubuntu LiveCD or go to [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)   and grab the Gparted LiveCD. If you're using the Ubuntu LiveCD just go to the partition editor like you normally would. The Gparted CD is just a partitioner, and it's very straight forward. 

Hope this helps.

---

### Post by yabbadabbadont on 2008-08-14
Boot a live CD/DVD.  Open a terminal window.  Get root access using sudo or su or both, however you need to for that distribution.  Run "fdisk -l" to list all partitions on all the drives your live CD sees.  Figure out which one is the drive you want to wipe.  [COLOR="Red"]BE VERY CAREFUL TO PICK THE RIGHT ONE[/COLOR].  If you only have one hard drive, then it should be easy to find.  ;)

Now use the "dd" command to overwrite the entire drive with zeros.

[COLOR="Red"]THIS IS VERY DANGEROUS IF YOU ARE NOT CAREFUL[/COLOR].
```
dd if=/dev/zero of=/dev/XXX
```
Replace XXX with the correct device for the drive you want to wipe.

Go enjoy a movie, if the drive is very large.

---

### Post by Champy on 2008-08-14
> **erickghint said:**
> Gparted has a tendancy to mount anything that you're trying to edit if you're running it in the actual OS. Use either the Ubuntu LiveCD or go to [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)   and grab the Gparted LiveCD. If you're using the Ubuntu LiveCD just go to the partition editor like you normally would. The Gparted CD is just a partitioner, and it's very straight forward. 

Hope this helps.

thanks, but what do you mean by, ummm, going onto the live cd? i can boot onto the live cd and be in the menu, but once im there what do i do?

sorry if this is a noob question.

---

### Post by Champy on 2008-08-14
> **yabbadabbadont said:**
> Boot a live CD/DVD.  Open a terminal window.  Get root access using sudo or su or both, however you need to for that distribution.  Run "fdisk -l" to list all partitions on all the drives your live CD sees.  Figure out which one is the drive you want to wipe.  [COLOR="Red"]BE VERY CAREFUL TO PICK THE RIGHT ONE[/COLOR].  If you only have one hard drive, then it should be easy to find.  ;)

Now use the "dd" command to overwrite the entire drive with zeros.

[COLOR="Red"]THIS IS VERY DANGEROUS IF YOU ARE NOT CAREFUL[/COLOR].
```
dd if=/dev/zero of=/dev/XXX
```
Replace XXX with the correct device for the drive you want to wipe.

Go enjoy a movie, if the drive is very large.

thanks! i hope this works but..how do i open terminal when im in the live cd menu? i cant seem to get into terminal!

---

### Post by yabbadabbadont on 2008-08-15
I didn't actually intend for you to use one of the installation CDs...  something like knoppix was what I was thinking of.  :)

---

### Post by Champy on 2008-08-15
> **yabbadabbadont said:**
> I didn't actually intend for you to use one of the installation CDs...  something like knoppix was what I was thinking of.  :)

what does knoppix mean? if i shouldnt use the ubuntu live cd then what should i do? do i get knoppix and then burn the image file to a cd and then run it?

---

### Post by yabbadabbadont on 2008-08-15
> **Champy said:**
> what does knoppix mean? if i shouldnt use the ubuntu live cd then what should i do? do i get knoppix and then burn the image file to a cd and then run it?

Do you really have an ubuntu live CD, or is it just the regular installation CD?  If it is a live CD, then you should have a web browser, terminal (gnome-terminal for example), and some other toys with which to play.

---

### Post by Champy on 2008-08-15
> **yabbadabbadont said:**
> Do you really have an ubuntu live CD, or is it just the regular installation CD?  If it is a live CD, then you should have a web browser, terminal (gnome-terminal for example), and some other toys with which to play.

i have a ubuntu cd, i dont know whether its live or whatever. it gives me the option to try ubuntu without changing my computer, install it, test memory and boot from harddisk and stuff.

cant i do that commands you gave me in terminal just in my ubuntu desktop? 
im sorry to ask so much of you, but im not very computah 1337.

---

### Post by yabbadabbadont on 2008-08-15
> **Champy said:**
> i have a ubuntu cd, i dont know whether its live or whatever. it gives me the option to try ubuntu without changing my computer, install it, test memory and boot from harddisk and stuff.

cant i do that commands you gave me in terminal just in my ubuntu desktop? 
im sorry to ask so much of you, but im not very computah 1337.

No, you have to be booted off of another system, like the CD, in order to wipe the drive on which your current system resides.  Just like you can't remove the ladder on which you are currently standing...  ;)

Take the option to "try ubuntu without changing your computer".  That should put you into a normal gnome desktop session.  Then you can open a gnome-terminal and follow the instructions I gave.  You should be very sure that there isn't anything currently on your computer that you want to keep if you do this.

---

### Post by Champy on 2008-08-15
> **yabbadabbadont said:**
> No, you have to be booted off of another system, like the CD, in order to wipe the drive on which your current system resides.  Just like you can't remove the ladder on which you are currently standing...  ;)

Take the option to "try ubuntu without changing your computer".  That should put you into a normal gnome desktop session.  Then you can open a gnome-terminal and follow the instructions I gave.  You should be very sure that there isn't anything currently on your computer that you want to keep if you do this.

thank you so much for all your help. i was able o delete everything in partition editor, i guess because i was on the cd it was working and now im downloading vista. thank you!!!111one111!one

---

