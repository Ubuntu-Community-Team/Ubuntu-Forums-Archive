---
title: "How can I get back a copy of PQSERVICE ?"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by orault on 2006-12-16
Dear all,

Situation : Whereas the partition PQSERVICE is hidden under a windows OS, It is automatically 
mounted with full permissions on the UBUNTU desktop.

My problem :
I have apparently deleted some files in the "autorun" directory of the partition : PQSERVICE. 
Now I only have 1 file left in this directory : autorun.exe 

I could not recover the files from the trash.


.Can someone tell me if there were others files or was it the only one ?
.If yes, can someone make them available for download to me (in some way or another ?)
.Is there a download site (I could not find It on Acer.com so far )

---

### Post by i.be.doh32 on 2007-01-04
I have serious doubts that you can find a copy of pqservice online.  HOWEVER, there is a possible solution.

As long as you have not written anything to the partition in question, you could recover it in its entirety to another partition or disk or whathaveyou at once, then copy that to the original partition.  In order to do this, we are going to use *dd_rescue* and *dd_rhelp* to copy the ENTIRE partition, including our dearly departed files, and save them to a separate partition or drive.  BE CAREFUL WITH THIS STUFF!  You could accidentally recover one partition over another!  ](*,)   Anyways, if you are wondering, I'm taking these instructions (not verbatim) from Knoppix Pocket Reference by Kyle Rankin, its got some good stuff.  NOW ON TO THE RECOVERY!


1).  First, we need to get a few programs.  The programs that we will use (as said before) are dd_rescue and dd_rhelp.  These are recovery programs, and work very well at recovering information from damaged disks, and can serve (hopefully) the dual purpose of recovering deleted data, as long as it wasn't overwritten.  Make sure that you have all the optional repos.

```

sudo apt-get install dd_rescue

```

Now we are going to have to download and install dd_rhelp from source, so save the source from [http://www.kalysto.org/pkg/dd_rhelp-0.0.6.tar.gz](http://www.kalysto.org/pkg/dd_rhelp-0.0.6.tar.gz) and unzip it to your desktop.  Now open a terminal window and type this in:

```

cd ~/Desktop/dd_rhelp-0.0.6
./configure
make
sudo make install

```

Now everything is installed!  On to the actual grunt work.

2).  Now go back to the terminal, and type in (this is assuming PQSERVICE is /dev/hda1, which it is on my Acer laptop):

```

sudo dd_rhelp /dev/hda1 /path/to/recovery/file

```

This will take a long time, so be patient.  Let it sit overnight or something to do this.  

You can either write the recovery to a partition that has no data on it (which would be best, in my opinion) or to an image, like /mnt/recovery.img .  Afterwards, just mount the recovery file and copy the missing things over.  So say we put the recovery file at /mnt/recovery.img , then we would do this to mount it:

```

mkdir /mnt/recovery
sudo mount -o loop /mnt/recovery.img /mnt/recovery

```

This should show all of the files in the partition under it.  Just navigate to what you are missing.  I sincerely hope that this helps you.

---

