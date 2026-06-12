---
title: "Disk Cloned, 2nd try 'success', now what?"
date: 2011-07-18
forum: Hardware
---

### Post by smritam on 2011-07-18
Hi! I've just cloned my 160 GB notebook hard drive onto a 500 GB one using  dd_rescue. Using a 64kB block size for errors, it took about 6-8 hours for 2944kB of errors total. Not too bad I guess. Next time I'll try gddrescue or dd_rhelp...

dd_rescue -B 64k /dev/sda /dev/sdb

Computer Info:
2007 model Dell E1505
160GB Hitachi OEM hard drive 5400rpm
Dual boot: WinXP Pro / Ubuntu Jaunty

New Drive:
500GB Seagate Momentus 7200rpm

I cloned it first and it worked, but then I ran (1) ntfsfix from Ubuntu Jaunty live disk, and then (2) chkdsk upon reboot, then (3) chkdsk /R from windows safe mode command prompt, then (4) chkdsk /f /r upon another reboot. Afterword, the cloned windows install was sort of broken... the quick launch toolbar was gone and some drivers weren't loading and some of the basic drivers dll's etc were crashing. I don't know what did it... any ideas?

Now I have recloned the ntfs partition successfully, and it works. 

dd_rescue -B 64k /dev/sdd2 /dev/sda2 (sda is target output file since the new drive was now master)

However now I have to move/resize my partitions to fill the new disk (I guess I don't have to, but I'd like to). However, gparted still says the new drive has errors/bad sectors (approximately 735 bad sectors to be precise). I am assuming that this is an artifact of the cloning process and that the disk doesn't actually have errors (maybe it does). Will this go away in time as those portions of the disk get written on? I want to run chkdisk /f /r but am scared to since I don't want to clone again for many hours. I have a suspicion that ntfsfix is what caused my problem before but am not certain...

Any thoughts/advice/ideas as to how to proceed?

---

### Post by jerrrys on 2011-07-19
clonezilla would of taken all the work out of your project.
with clonezilla you could of used "beginner mode" and just cloned hdd to hdd.
the rest is figured out by the software...

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by smritam on 2011-07-19
wow... clonezilla seems a bit too good to be true. I'll have to give it a try next time I need to do cloning/backup. Thanks for the recommendation. :)

---

### Post by jerrrys on 2011-07-19
also clonezilla only failed me once in the past years that i have been using it.  or at least it got the blame, could not have been operator error :)

---

### Post by smritam on 2011-08-10
:arrow: "bump"...

I'm still looking for some advice on what to do next. My new drive has 360+ GB of unformatted space. Gparted still shows the NTFS windows partition to have 735 bad sectors (I'm assuming the disk doesn't actually have physical damage and this is just due to it being a clone of a damaged disk). I'd like to:
1. move my Ubuntu Extended partition to the end of the disk,
2. resize the EXT3 partition to be a bit larger, and
3. resize the NTFS Windows partition to be a bit larger (either fill the remainder, or make a separate NTFS Data partition).

However Gparted won't do anything until the bad sectors are "fixed".

Any ideas? :idea: :?: Should I just do chkdsk /f /r and reboot twice as Gparted suggests?

Cheers. :)

---

