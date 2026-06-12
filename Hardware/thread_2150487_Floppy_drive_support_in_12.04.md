---
title: "Floppy drive support in 12.04?"
date: 2013-06-01
forum: Hardware
---

### Post by OldNovice on 2013-06-01
Did the developers of Ubuntu 12.04 LTS decide not to provide any support for floppy drives?

(I've spent half a day looking for help on the forums, and tried lots of suggestions
including from  "closed" threads, and I'm getting nowhere.
I need to recover some old files archived on floppies, and I have kept
precisely one floppy drive (-- plugs into my old Dell Latitude D610 as an
alternative to the CD drive) so that I could get at such files when I needed
to.  I removed the M/S O/S last year and installed Ubuntu 12.04 LTS.
So now I need to know whether Ubuntu is going to let me at the
files, or whether I need to go looking for someone who can let me at 
a networked machine running that other O/S that has or can take a
floppy drive.  I don't suppose I'm the only person in the world who 
needs Ubuntu to do this for me.

The situation is that when I insert a DOS-formatted floppy, the LED
comes on, the thing whirrs a little, and nothing else appears.
The terminal command

nautilus computer://

pops up a window that shows two objects:
floppy drive
file system

Right-click and Properties on floppy drive shows
everything is unknown, except Location is given as 
Computer:///

Straightforward
mount /dev/floppy
fails because there is no entry in /etc/fstab


The command
udisks --mount /dev/fd0 
gives
cannot stat /dev/fd0 .... no such file or directory

In fact, there is no file /dev/fd0.  There is a directory /dev/fd with
4 files called 0,1,2,3. Replacing fd0 by any of fd, fd/0, etc
in the above udisks command gives:
device file dev/fd is not a block device -- resource temporarily unavailable.

One person has suggested a solution that seems to involve
uninstalling udisks and reinstalling some old version.  Their instructions
don't make sense in the interface that came with 12.04.  They
seem to be referring to some other window manager.
The other issue with this is that I don't know what I will break
if I unistall udisks.

I'll spare you the rest of my thrashing about.
What I would appreciate knowing is whether I am wasting my time.
If the Ubuntu community is not planning to support floppies,
then OK, I'll take the problem elsewhere. I'd just like to
know.    If the support is there, perhaps someone could point me
to the right thread.  Thanks.

---

### Post by vanadium on 2013-06-01
Perhaps "mount" support was removed. Youo can still access the contents of the floppies without mounting them using the venerable mtools, that allow you to access the contents of floppies with ms-dos like commands.

---

### Post by Dennis N on 2013-06-01
You didn't say what size floppies, but I have a USB 3.5" floppy drive that is works fine with Ubuntu. Made by TEAC. If it's important that you read these disks, you might look into this type. Inexpensive as well.

---

### Post by OldNovice on 2013-06-01
> **vanadium said:**
> Perhaps "mount" support was removed. Youo can still access the contents of the floppies without mounting them using the venerable mtools, that allow you to access the contents of floppies with ms-dos like commands.

Many thanks for this info. I had a look at mtools. Tried
mdir a:
It said
Can't open /dev/fd0. No such file or directory.
Can't initialize A:

How should I proceed?

---

### Post by OldNovice on 2013-06-01
Thanks, Dennis N.
3.5 in floppies, indeed.

---

### Post by OldNovice on 2013-06-03
> **OldNovice said:**
> Many thanks for this info. I had a look at mtools. Tried
mdir a:
It said
Can't open /dev/fd0. No such file or directory.
Can't initialize A:

How should I proceed?

Am I right in thinking that in order to access a device, I've
got to have a device handle in the file system?  The way I read what 
mtools is up to is that it when I command
mdir A:
it looks at
/etc/mtools.conf or ~/.mtoolsrc
to see how drive A: is specified, and uses that info.
The spec MUST have a clause 
file="some filename"  
which says where the device handle sits in the filesystem,
and MAY have other data, such as the device geometry

The default /etc/mtools.conf
specifies 
drive A: file="/dev/fd0"
so I get nowhere with that, since my system has 
no such file.

I copied /etc/mtools.conf to $HOME/.mtoolsrc
and fiddled with it, trying out various handles
like "/dev/fd/0", etc along with various geometries
appropriate to  3.5" floppies that are described in
the man pages, without success.

Then I thought, OK, when I plug in the CD drive
this system handles it, so maybe I'll try the 
handle for that, and give it the floppy geometry!
But, Lo, I could not find anything in /dev that seemed
to correspond to the CD drive.  
Eventually, by plugging it out and in again, it became clear
that /dev/sg0 and /dev/sg1 were character device handles
(which Ubuntu creates on the fly, apparently, when 
it detects a suitable device.  I could not determine 
block device handles.
Then I tried configuring those handles with floppy geometries,
without success.  

All pointless, I suspect.
The Official Ubuntu Documentation page at
[https://help.ubuntu.com/12.04/installation-guide/i386/linuxdevices.html](https://help.ubuntu.com/12.04/installation-guide/i386/linuxdevices.html)
has a clear and simple explanation of the setup
for device files, and how it is supposed to work.
But it does not appear to have been executed by the developers.
The very first entries are for the floppy drives, and it seems
the drivers are just not there in the kernel, end of story.

I'll wait a little for feedback, but it seems we should close
this one as a lost cause.

---

### Post by vanadium on 2013-06-03
Some operations do not require you to mount the floppy. See [http://linux.about.com/od/lts_guide/a/gdelts59.htm](http://linux.about.com/od/lts_guide/a/gdelts59.htm) for some usage info.
You may need to setup your floppy drive correctly. See here: [http://h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V50_HTML/MAN/MAN1/0304____.HTM](http://h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V50_HTML/MAN/MAN1/0304____.HTM)
Unfortunatelly, I cannot be of more specific help because I do not have experience with the tool, and I have no floppy drives anymore.

---

### Post by OldNovice on 2013-06-03
> **vanadium said:**
> Some operations do not require you to mount the floppy. See [http://linux.about.com/od/lts_guide/a/gdelts59.htm](http://linux.about.com/od/lts_guide/a/gdelts59.htm) for some usage info.
You may need to setup your floppy drive correctly. See here: [http://h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V50_HTML/MAN/MAN1/0304____.HTM](http://h30097.www3.hp.com/docs/base_doc/DOCUMENTATION/V50_HTML/MAN/MAN1/0304____.HTM)
Unfortunatelly, I cannot be of more specific help because I do not have experience with the tool, and I have no floppy drives anymore.

Good man, vanadium!  It works!

Having determined that the drive corresponds to the device file /dev/sdb on my system,
I cd'd to /dev and issued the terminal command

sudo /sbin/MAKEDEV -v sdb

and then put the lines:

drive a: 
 file="/dev/sdb" 
 filter 
 exclusive

in my ~/.mtoolsrc, instead of the default version for drive a:

I could then view the files on a floppy and copy them, using

sudo mdir
and
sudo mcopy 

Many thanks.  Problem solved.

---

