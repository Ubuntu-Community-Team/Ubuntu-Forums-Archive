---
title: "Can't see my RAID 0- BUT KNOPPIX has proven it will work on Linux...."
date: 2007-07-26
forum: Hardware &amp; Laptops
---

### Post by hissingshark on 2007-07-26
HI there,

I'm trying to make the long walk from WinXP Pro to Linux.

I've got striped RAID running on an nForce2 motherboard.
That uses the Silicon Image SiL3112a Controller which DMRAID apparently supports.
From my reading here it represents "fake raid".
I've also seen many similar problems here.
One guy had the identical problem but without response

I first used the KNOPPIX live CD and was delighted to see how easy it all was and was encouraged to stick with Linux.  It saw all my devices straight out of the box as it were, proving that my RAID can work with Linux.

Now I've got an 80Gb emergency drive which I installed Ubuntu 7.04 onto.
My hope is to maintain XP on the RAID and keep my media files etc over there.
But the RAID doesn't feature on the devices list.

I ran:
    sudo dmraid -r
and got
    /dev/sda: sil, "sil_afadddbhabeb", stripe, ok, 321669888 sectors, data@ 0
    /dev/sdb: sil, "sil_afadddbhabeb", stripe, ok, 321669888 sectors, data@ 0

There are the boys.
So I ran:
    sudo dmraid -ay
And got 
    RAID set "sil_afadddbhabeb" already active
    RAID set "sil_afadddbhabeb1" already active

Looking with:
    sudo dmraid -s
i get
    *** Active Set
    name   : sil_afadddbhabeb
    size   : 643339776
    stride : 32
    type   : stripe
    status : ok
    subsets: 0
    devs   : 2
    spares : 0

And:
    sudo ls /dev/mapper
Tells me:
    control  sil_afadddbhabeb  sil_afadddbhabeb1

Is it "control" that needs the attention here?

Many thanks in advance folks,

---

### Post by hissingshark on 2007-07-29
All I've achieved so far is to download a driver for the XP side of things so I can read my Linux Ext3 formatted drive and do some drag-n-drop transfers that way.

It's a start, but I'd really like to get this resolved. Sounds like such a common problem too.
I've posted another thread re: compiling a custom driver.  Silicon Image have released a Linux driver, but not for Ubuntu.  Thought I could salvage something from that, which would help a lot of people I guess.

No replies so far though...

---

### Post by fjgaude on 2007-07-29
Okay, it's been awhile since I've used dmraid, but it works with Sil, etc.

What I think all you need do after you are in Ubuntu is to mount your raid pair. Now using dmraid -tay it tells you what to mount, but not exactly.

What you see is lots of things you don't need, except the /dev/mapper/sil_xxxxxxx part. The latter portion is unique to your raid pair. after you have created the mount point with:

sudo mount /dev/mapper/sil_xxxxxxx /media/raid 

 "raid" or whatever you wish to call the point

Do the above after you have created the mount point with:

sudo mkdir /media/raid

After you get it working you can put a line in fstab to mount the raid at bootup time.

I hope this points you into a direction to get you up and going with software raid. If not, ask questions.

frank

---

### Post by hissingshark on 2007-07-30
Cheers for getting back to me there.

sudo dmraid -tay
Came back with
sil_afadddbhabeb: 0 643339776 striped 2 32 /dev/sda 0 /dev/sdb 0
sil_afadddbhabeb1: 0 643322862 linear /dev/.static/dev/mapper/sil_**afadddbhabeb** 63

Not sure what that 63 is about.
But anyway I proceeded to use the "afadddbhabeb" as you indicated in:

sudo mount /dev/mapper/sil_xxxxxxx /media/raid 

This earned me:
mount: /dev/mapper/sil_**afadddbhabeb **already mounted or /media/raid busy

How odd.  The directory /media/raid/ is empty still.
So we could go for **busy** rather than **mounted.**

Tried it again with the value for sdb which was basically Sil_xxxxx1.
sudo mount /dev/mapper/sil_**afadddbhabeb1** /media/raid
There was no error/response given to that so I guessed it worked.

I now find that **cd /media/raid/** = permission denied.
**sudo cd** is an unknown command.

As viewed from Nautilus it's tagged with a little white X on a red square.
And opening it = The folder contents could not be displayed. You do not have the permissions necessary to view the contents of "raid".

So I launched a "root" Nautilus (which I'm guessing is a bit naughty) to get around it with: 
**sudo nautilus --browser**

Looking in **/media/raid **that way I can see the contents of the RAID!!
But it clearly isn't properly mounted as I can't access it via the terminal and it hasn't appeared on the desktop like all good mounted devices do.  And this isn't a practical way of accessing either as it isn't going to permit links and shortcuts etc.

So progress is made.  But where to from here?  Is **chmod** a safe thing to use given that the RAID has an XP installation on it with all my data within that.

Many thanks,
GeeGee

---

### Post by hissingshark on 2007-12-19
Bumping since the release of Gutsy.
RAID still does not appear to work as it manages to so easily in Knoppix.

I'd rather hoped this would be sorted out in Gutsy as RAID is an increasingly common set-up.

Anyone have any new information on this?
Thanks.

---

### Post by llcawthorne on 2007-12-21
Sounds like a umask issue, not a raid issue.  Any ntfs howto should explain it.  If you use "-o umask=000" in your mount options it should fix it.

IE:  "sudo mount -t ntfs -o noatime,rw,umask=000 /dev/mapper/sil_afadddbhabeb1 /media/raid"

You can put the umask=000 option (or whatever umask you want to use) in your fstab so you don't have to type it everytime.  Sounds like your RAID is working well.

Maybe that'll help.

I'm having my own problem that maybe you or someone else could help out with.  My device was appearing fine under /dev/mapper and I was mounting it fine...  It was also working in Vista and Sabayon.  It still works in Sabayon and Vista fine, but it no longer appears under /dev/mapper in Ubuntu.  I've done "sudo aptitude remove --purge dmraid" and "sudo aptitude install dmraid dmsetup" and manually done a "modprobe dm-mod" (not sure if that's the right module, but i don't have many dm-whatever ot choose from)...  I don't remember upgrading my kernel, but just incase I did a "sudo depmod -a"...  i may have ok'd an update that replaced it, or something...  maybe i should do something to rebuild modules?  dunno.  any pointers from anyone though?  the device just disappeared from /dev/mapper and I can't mount it in Ubuntu anymore.

---

### Post by llcawthorne on 2007-12-21
oh yeah, forgot to include the following info in my the last post.

"dmraid -ay" acts normal.  ubuntu also recognizes the raid array fine when I type "dmraid -r" and "dmraid -s".  I've even gone so far as to do a dump with "dmraid -Dr" then erase the metadata with "dmraid -Er" then restore it with the script that was in the man page.  This obviously didn't hurt the array, since I'm playing music off it in Sabayon right now.  However, the thing still won't show up in /dev/mapper.

after i get my new hard drives this christmas, i'm reconfiguring the whole array mdadm and probably xfs unless i want to keep open the option of shrinking lvm's, but for now, it would be nice to have it functional so I can listen to my music while playing with ubuntu without digging out a dvd.  

never had this problem when playing with an ubuntu install before...  I recently did a series of benchmarks to comparing lvm striping, dmraid and mdadm to see what I wanted to settle on, and never ran into this problem.  this is a fresh install of ubuntu 7.10 that I put into place this morning that has developed this problem...

---

