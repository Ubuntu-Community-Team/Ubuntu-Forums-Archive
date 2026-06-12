---
title: "How can I uss an external USB DVD rom as apt source?"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by gilf on 2008-02-03
When I try to add repositories on dvd to the Software Sources menu, it does not allow additions from the external USB DVD drive. It always looks for CDs on the internal drive. I have an internal cdom drive only, and can't use it for dvds.

I've tried manually editing the /etc/apt/sources.list with entries from another computer, but these also reference an internal drive. The addition from that computer looks like this:

> deb cdrom:[MainNo2]/ gutsy main
deb cdrom:[MainNo2]/ gutsy-security main
deb cdrom:[MainNo2]/ gutsy-updates main
deb cdrom:[MainNo1]/ gutsy main
deb cdrom:[MainNo1]/ gutsy-security main
deb cdrom:[MainNo1]/ gutsy-updates main
deb cdrom:[Universe-MultiNo4]/ gutsy multiverse universe
deb cdrom:[Universe-MultiNo4]/ gutsy-security multiverse universe
deb cdrom:[Universe-MultiNo4]/ gutsy-updates multiverse universe
deb cdrom:[Universe-MultiNo3]/ gutsy multiverse universe
deb cdrom:[Universe-MultiNo3]/ gutsy-security multiverse universe
deb cdrom:[Universe-MultiNo3]/ gutsy-updates multiverse universe
deb cdrom:[Universe-MultiNo2]/ gutsy multiverse universe
deb cdrom:[Universe-MultiNo2]/ gutsy-security multiverse universe
deb cdrom:[Universe-MultiNo2]/ gutsy-updates multiverse universe
deb cdrom:[Universe/MultiNo1]/ gutsy multiverse universe
deb cdrom:[Universe/MultiNo1]/ gutsy-security multiverse universe
deb cdrom:[Universe/MultiNo1]/ gutsy-updates multiverse universe


I'm assuming I have to change the "cdrom:" entry to something else. Would it be "scd0:"

Thanks in advance for your help.

---

### Post by hyperair on 2008-02-03
How about ```
sudo apt-cdrom -d /path/to/your/cdrom/mount/point/ 
```

---

### Post by gilf on 2008-02-03
Thanks hyperair,

didn't work, here's the output of
[B]
 sudo apt-cdrom -d /media/scd0[/B]


> apt 0.7.6ubuntu14 for i386 compiled on Oct 15 2007 20:39:23
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See fstab(5)


Looks like it wants the name of the individual volume, not the just the drive. So I'd have to do that with all of them. Guess it's do-able, but isn't there an easier way, for now, and the future?

ideally I'd like the "Add CDrom" button of the System>Administration>Software Sources to work with the external DVD drive.

Otherwise you have to know the name of every CD, open the terminal and enter the commands with the properly typed name etc.

---

### Post by gilf on 2008-02-03
I think I was wrong above -- it wasn't complaining about the volume  -- looking at that message a little closer, now -- looks like it actually wanted the word "add" added to the command line.

Something like:

> sudo apt-cdrom -d /media/scd0 **add**

Now the only problem is that it looks like it wants a mount point from an fstab entry, but there isn't one for the external USB DVD player.

How would I add that to fstab?

---

### Post by hyperair on 2008-02-04
Please post the output the two commands "mount" and "cat /etc/fstab". Also, isn't there a rightclick option from Nautilus to add the CD as a software CD?

---

### Post by gilf on 2008-02-05
Thank you Hyperair,

I added an enry to fstab (scd1) and set up a directory (dvdrom0) and link (dvdrom) in /media, and was successfully able to add the repositories using the terminal command you suggested (with the **add** command).

However, though the repositories were added and the contents of the dvd disks read into apt, and though I could now select (using synaptic) the programs I wanted to install, as soon as I would hit "Apply" it would ask for the appropriate named disk. I'd insert it in the drive, and it wouldn't find the "CD"

Ironically, all of the adding by hand of each DVD had created an apt sources list, exactly like the one I'd first copied in (see first post above).

Typically looking like:

> deb cdrom:[MainNo2]/ gutsy main

Seems like the big problem is not in adding these names to the repository list, but getting apt to accept the external drive as the "cdrom:" at the stage when it is trying to install.

Anyway, I'm posting the current terminal output you asked for. This is with the new changes, and with a DVD disk in the drive. It is scd1. The internal cdrom is scd0.

:> steve@steve-ibm-laptop:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda6 on /home type ext3 (rw)
/dev/sda1 on /media/sda1 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd1 on /media/dvdrom0 type iso9660 (ro,nosuid,nodev,user=steve)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=steve)


and
> steve@steve-ibm-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=4547aabd-29e7-46fe-830c-c7a16fc96973 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=216d4830-8e19-4403-8674-3c2b2803ecf1 /home           ext3    defaults        0       2
# /dev/sda1
UUID=1E6A-6E50  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=902f30d5-0080-4a8e-a74c-3d0c27dba7ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/scd1       /media/dvdrom0   udf,iso9660 user,noauto,exec 0       0


Thanks again for your help.

---

### Post by hyperair on 2008-02-05
Strange that it prompts you for a CD. Could you run this command (with the CD inserted):
```
apt-cache policy <packagename>
```
where <packagename> is the package you were trying to install from Synaptic.

---

### Post by gilf on 2008-02-06
Hello Hyperair,

okay, I'm going to start from scratch. Using System>Administration>Software Sources, I unchecked all internet download sources. I then deleted my earlier entries for the DVD disk "Main No1". I unchecked all of the other DVDs listed

I then entered the commands to add the Main No1 dvd disk back again:

> steve@steve-ibm-laptop:~$ sudo apt-cdrom -d /media/dvdrom0 add
Using CD-ROM mount point /media/dvdrom0/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [fe42a07e880b7c155adbf052288edee4-2]
Scanning disc for index files..
Found 3 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
This disc is called: 
'Main No1'
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Main No1]/ gutsy main
deb cdrom:[Main No1]/ gutsy-security main
deb cdrom:[Main No1]/ gutsy-updates main
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.


I didn't repeat for the other disks, because it's a long process, and this is just a test. I'll try to add a piece of software off of the Main No1 disk (with no depedencies needed on other disks). So far so good the disk is definitely loaded, as you can see above.

Now, I open Synaptic and Reload.

Let's try to install apt-doc -- it has no dependencies, and ought to be useful. I hit "Apply" I get:

> Please insert the disk labeled:
Main No1
in drive /cdrom/

It's in there already from adding it before, so I hit OK

The message disappears, then returns, still asking me to insert Main No1.

So then I:

> steve@steve-ibm-laptop:~$ apt-cache policy apt-doc
apt-doc:
  Installed: (none)
  Candidate: 0.7.6ubuntu14
  Version table:
     0.7.6ubuntu14 0
        500 cdrom://Main No1 gutsy/main Packages


So. there we are.

Seems like it's worth trying to change the "cdrom:" designation to "dvdrom" by editing the sources list by hand, to see if that will work.

---

### Post by gilf on 2008-02-06
Nope, no go.

Changing the "cdrom:" to "dvdrom:" in /etc/apt/sources.list:
> deb dvdrom:[Main No1]/ gutsy main
deb dvdrom:[Main No1]/ gutsy-security main
deb dvdrom:[Main No1]/ gutsy-updates main
and trying again to install via Synaptic got me:
> ERROR
E: The method driver /usr/lib/apt/methods/dvdrom could not be found..

Okay......let's change the "dvdrom:" back to "cdrom:". And lets try running apt-get install in a terminal:

> steve@steve-ibm-laptop:~$ sudo apt-get install apt-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apt-doc
0 upgraded, 1 newly installed, 0 to remove and 180 not upgraded.
Need to get 0B/97.8kB of archives.
After unpacking 283kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Main No1'
in the drive '/cdrom/' and press enter

Media change: please insert the disc labeled
 'Main No1'
in the drive '/cdrom/' and press enter


As you can see, hitting ENTER with the disk in the drive doesn't work.

Seems like "cdrom" is hard coded in somewhere?

---

### Post by gilf on 2008-02-06
SUCCESS!!

I noticed that there was a folder link in the root directory called "cdrom" and wrongly assumed that I had accidentally created it while working with the /media folder links. So I deleted it.

Then, after trying to re-direct the /media/cdrom" link in /media so that it pointed to the folder /media/dvdrom0, instead of /media/cdrom0 and then trying Synaptic, I got further along in Synaptic than I had before -- it seemed to try to "download" from the requested CD instead of rejecting it out of hand.

But then there was an error message:
> W: Failed to fetch cdrom:[Main No1]/pool/main/a/apt/apt-doc_0.7.6ubuntu14_all.deb
  Unable to stat the mount point /cdrom/ - stat (2 No such file or directory)
Finally I noticed the slash before "cdrom" 

Oh, click! Root directory That was the link I deleted from / . So that's where apt is looking! I bet it points to /media/cdrom0. Yes it does. So let's try redirecting it to dvdrom0.

Okay, open synaptic and mark apt-docs for installation. Click Apply, and yup, there it goes, spinning up the DVD and installing.

Okay so to reiterate:

1.) I added an /etc fstab entry for scd1 just like the existing scd0
2.) I added a folder to /media called dvdrom0
3.) I added a link to /media called dvdrom, pointing to dvdrom0
4.) I renamed the link /cdrom to /cdrom-old
5.) I copied the link /media/dvdrom to /
6.) I renamed the link /dvdrom to /cdrom

Things workd after that. However I will need to change the /cdrom link back after I'm done.

It would be nice if this wasn't necessary. So I'll be trying to change the sources.list entries from cdrom to dvdrom again and trying out a link named /dvdrom  pointing to /media/dvdrom0. Then I can have a proper /cdrom pointer alongside a /dvdrom pointer.

---

### Post by gilf on 2008-02-06
Nope, doesn't work -- same error message -- not able to use dvdrom.
> ERROR
E: The method driver /usr/lib/apt/methods/dvdrom could not be found. :
So basically it's pretty kludgy to use an external  dvdrom by the method outlined so far even though it does work.

Any suggestions?

---

### Post by hyperair on 2008-02-07
I remember you mentioning that you manually edited your sources.list file to show dvdrom:// instead of cdrom://. Try changing it back.

---

### Post by gilf on 2008-02-08
Thanks hyperair, I already did that. I had to in order to get it to work at all.

Seems like I can only make it work to use DVDs for Synaptic by manually changing several  links in /media and /. No other way. Then I have to change the links back to use the on-board cdrom. Basically I'm fooling apt. Not something you want to do on a regular basis.

I hope someone can suggest a better way to get Synaptic to accept a mounted external DVD drive. This seems like it ought to work normally out-of-the-box. If Nautilus can do it Synaptic should as well.

---

### Post by hyperair on 2008-02-08
I think this should be reported as a bug in Launchpad. Since you're the one facing the problem why don't you file the bug? =) Post the launchpad url here when you're done.

---

### Post by gilf on 2008-02-08
> **hyperair said:**
> I think this should be reported as a bug in Launchpad. Since you're the one facing the problem why don't you file the bug? =) Post the launchpad url here when you're done.

Yes, I thought the same thing and already reported it. Here is the link:

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/190117](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/190117)

Thanks for all your help Hyperair!

.

---

