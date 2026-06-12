---
title: "floppy problems"
date: 2006-02-13
forum: Hardware &amp; Laptops
---

### Post by jamesr on 2006-02-13
Hi,

I am having floppy problems:-

1) Will not  mount in kde, gives an error about being unable to identify type, but can mount in console but after changing /etc/fstab to read 

/dev/fd0   /media/floppy0  auto,vfat,msdos,ext2  rw,user,noauto  0   0

can 

mount /dev/fd0 or mount /media/floppy0

or

sudo mount /dev/fd0 or mount /media/floppy0

I can see floppy on the desktop but cannot copy to it

umount seems to work as well.

But cannot copy

2) Also cannot format floppies, different errors from no permission which is the most frequent in KDE to not installed (once)

I have seen that there are many problems with Breezy and floppies but no mention of the problem in Hoary. The only suggestion that I have not tried is the pmount suggestion, is that valid for Kubuntu?

On a general comment, how did a distro get out without checking floppy support, I know Micro$oft is trying to kill the floppy but does that mean Ubuntu has to follow. Sneakernet can still be very useful. I know that penultimate comment could be taken as inflammatory but after having spent  a time on a problem that SHOULD not exist, I am feeling grumpy.


 
 
  Logged  

--------------------------------------------------------------------------------

Best Wishes

Jim R.

System running Kubuntu 5.04
AMD k6-2/450 128MB 2GB HD I know it needs more memory to run KDE but I am using it as a test bed system

---

### Post by David Haas on 2006-02-14
Hi Jamesr--Floppies work fine in Hoary. I've been runniny Hoary since last Spring. Because you are familiar with the command line, I'd recommend formatting and mounting/unmounting  with the terminal (shell). I can't tell whether your floppy has been formatted and had the Linux filesystem installed. Here are the commands I use for this:
1: Type (in your home directory, say): fdformat /dev/fd0
2: Then, install the ext2 filesystem with : mke2fs /dev/fd0

3: Then mount the floppy with: sudo mount /media/floppy0. For this to work, you must have the floppy0 directory in your media directory--it should be there by default in Hoary. If not, make one there with the mkdir command. Also, your fstab in the etc directory must refer to this directory, as mine does. Here is mine: 
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

If not, open your text editor, go to the etc/fstab file and change it to this. 

Don't forget that the unmount command is umount (no "n").

Once mounted, you copy files from the hard drive to the floppy with the cp command. You copy to /media floppy0. You may need to type 'sudo" (without the quotes)  (which transiently makes you root) to mount/unmount.

I hope this helps.

David

---

### Post by jamesr on 2006-02-14
Hi David,

Your reply was very useful because I forgotten the console lines.

> 
1: Type (in your home directory, say): fdformat /dev/fd0
2: Then, install the ext2 filesystem with : mke2fs /dev/fd0



And also because of your comment
> 
Floppies work fine in Hoary.


I am using the Kubuntu form and I have an independant though I believe a relavent error when copying using KDE  

"Could not start 'mdir'.
Ensure that the mtools package is installed correctly on your system."

When trying to update from the Kubuntu auto update site error =>
Package mtools is not available

and it is not my system. Since the floppies that I am trying to see are msdos floppies that could explain a lot.

The package is on the ubuntu site but what changes are required to access the ubuntu site from a Kubuntu machine.

---

### Post by David Haas on 2006-02-15
Look in Synaptic Package Manager under the "all' listing to see whether you have mtools installed -- apparently not. They are not installed by default. In Synaptic, highlight mtools and select install. You may need to enable more than the default repositories--"main and restricted". You may need "universe and multiverse" too. I don't know which repository mtools is located in. Ubuntu Linux should be able to work with MS-DOS floppies. If you can do this with mtools, then okay, but if not, then it can be done with the command line. I've never had to do this, but I have the commands listed in "The Linux Cookbox."
David

---

### Post by jamesr on 2006-02-15
Hi David,

It was not installed. I found a reference to file to method to update the list to include the other repositories. I can now download mtools and I did. This gets rid of the error about mtools, but still cannot copy to the floppy when using a DOS diskette.

I will be formatting a floppy as a ext2 floppy and will try again.

I think that this could be a problem with the Kubuntu distro only as the mtools was available on the Ubuntu components list and the problem would only be seen when copying to a DOS diskette.

---

### Post by David Haas on 2006-02-16
Jim--I guess you want to use MS-DOS floppies to exchange data with windows machines. If the mtools GUI doesn't do this for you, then you can try the command line. According to the book I mentioned, an MS-DOS disk can be accessed without mounting it (not so for linux floppies). To copy from the hard drive to the floppy, the comand is "mcopy filename.txt a:" (without the quotes) where "filename.txt' is the name of the file to copy.  To copy from the floppy, give the drive letter (a: usually) of the floppy followed by the file name to be copied, and mcopy will copy the file to the current directory in your hard drive.
David

---

### Post by jamesr on 2006-02-17
Hi David,

Just a short update after formatting a floppy using the console commands, I can use KDE to mount and u(N)mount. In addition , I can now copy to a linux floppy, not quite way I understood that it should work ie drag and drop, or using a drop down menu with a copy to function, but the old ways of cut and paste work. Of course, console still works. 

So what is the system doing when it sees a dos floppy?. These are vfat floppies ie with long names enabled perhaps I should try old style 8.3 floppy.

I will be trying the mcopy commands etc from the console but certainly the KDE front end no longer gives the missing package error but now a different error.

As a tryout, I installed LinTools on one of my W2k systems and I was able to copy from the EXT3 floppy to the windows desktop. It was slow but it worked.

---

### Post by David Haas on 2006-02-17
Jim--Because I'm running Ubuntu, I'm unfamiliar with the KDE desktop and its GUIs. I recommend that for questions related to this, go to the Kubuntu section of Hoary. Folks there should be able to help you.  
Good luck,
David

---

