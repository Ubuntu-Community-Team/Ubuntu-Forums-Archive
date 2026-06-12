---
title: "Invalid mount option when attempting to mount the volume 'UDF Volume'."
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by Exefurious on 2007-12-26
I insert a DVD with data burned on it.  The disk spins, but I receive this message:

Invalid mount option when attempting to mount the volume 'UDF Volume'.

Assistance?

---

### Post by Yellow Pasque on 2007-12-26
Please post your /etc/fstab file

---

### Post by nimbledinosaur on 2007-12-26
I'm having the exact same problem.

This is my fstab:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b945cfbd-8137-4fb3-a1c3-0f46480e51b6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=dc013a55-2f54-42c1-8c9c-cce190260740 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto rw,user,auto,exec 0       0

---

### Post by Yellow Pasque on 2007-12-26
Maybe because you're trying to explicitly mount every CD/DVD as read/write? Just remove the "rw," from the last line and see if that does the trick

---

### Post by nimbledinosaur on 2007-12-26
No dice, still the same error:

> Invalid mount option when attempting to mount the volume 'UDF Volume'.

Thanks though.  Any other thoughts?  Could I be missing any packages associated with UDF?

---

### Post by Yellow Pasque on 2007-12-26
Damn, I though that was it...
Anyway, the way I literally read the error is that the system does not like one of the options you're using. Since you're only using rw,user,auto,exec , it should be an issue with one of those options.

Have you tried mounting it manually at the command line?

---

### Post by Exefurious on 2007-12-26
Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=999830d8-8e0f-4659-a14e-0700fd5fb4e0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d825b6fd-9609-47c6-afa7-65bc84cf0020 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



I'm new to Ubuntu - to Linux in general really - but I'm trying guys, I'm really trying to not bother people with questions I can or should be able to figure out myself... but this one got me.

---

### Post by Yellow Pasque on 2007-12-26
> Mount options for udf

       udf is the "Universal Disk Format" filesystem defined  by  the  Optical
       Storage  Technology  Association,  and  is often used for DVD-ROM.  See
       also iso9660.

       gid=   Set the default group.

       umask= Set the default umask.  The value is given in octal.

       uid=   Set the default user.

       unhide Show otherwise hidden files.

       undelete
              Show deleted files in lists.

       nostrict
              Unset strict conformance.

       iocharset
              Set the NLS character set.

       bs=    Set the block size. (May not work unless 2048.)

       novrs  Skip volume sequence recognition.

       session=
              Set the CDROM session counting from 0. Default: last session.

       anchor=
              Override standard anchor location. Default: 256.

I'm just brainstorming here: If it was a self-made data CD, perhaps it didn't follow the file system standard correctly and you'd have to mount it with "nostrict" option.

---

### Post by Exefurious on 2007-12-26
I'm sorry, but I'm slightly confused.

The Data DVD in question works on a WinXP machine.  Putting it in my laptop however, yields the problem I started this thread with.

How would I alter my fstab (as given above) to accomplish what you're asking me to do with the nostrict?

---

### Post by foresthensley on 2007-12-27
[INDENT]wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/INDENT]

Im having the same problem. The above is the result of "sudo mount -nostrict /dev/scd0"

---

### Post by nimbledinosaur on 2007-12-27
I have the same problem and have been trying all the solutions suggested with no effect.  I was wondering how many others with the same problem had burned their failing dvd's or cd's in Vista.  I've been researching and I think that MS Vista defaults burns to the "[Live File System]("http://beranger.org/index.php?2007/05/14/14/41/52-burned-with-vista-only-readable-&page=diary")".  Pretty awesome considering that it is only readable by Vista and XP.  Of course, I also backed up everything before my move to ubuntu on DVD with the presumption being that it was relatively platform independent.  

Well, I'm going to try copying the dvd over to a linux compatible format on a MS machine and see if that fixes it.

---

### Post by Exefurious on 2007-12-27
> **nimbledinosaur said:**
> I have the same problem and have been trying all the solutions suggested with no effect.  I was wondering how many others with the same problem had burned their failing dvd's or cd's in Vista.  I've been researching and I think that MS Vista defaults burns to the "[Live File System]("http://beranger.org/index.php?2007/05/14/14/41/52-burned-with-vista-only-readable-&page=diary")".  Pretty awesome considering that it is only readable by Vista and XP.  Of course, I also backed up everything before my move to ubuntu on DVD with the presumption being that it was relatively platform independent.  

Well, I'm going to try copying the dvd over to a linux compatible format on a MS machine and see if that fixes it.

I may do the same... or put the DVD into a WinMachine and drag the data onto my flash drive, then putting the data on my Linux laptop via the flash drive.  

All other CD's and DVD's I have tried work well.  This particular one however, was burned on Vista before I eradicated Vista from my HD.  I wouldn't be a bit surprised to find out data burned onto a disk in Vista would be rendered unreadable on other OS's.  Wouldn't be surprised at all...

---

### Post by Exefurious on 2007-12-28
Bump.  Anyone have a solution?

---

### Post by revelationman on 2008-01-01
I have the same problem disc with music and data burnt in Windows Vista  
option was  selected to be read on all systems ,  but it looks like Lord Bill has other ideas 

I have my system dual booted with Linux to read the disc 

I have searched everyone maybe it is something that could be added to the next update in Ubuntu  who knows  

Once  this issue  is sorted i am going to remove windows and just run  ubuntu  

I will say this i am starting to love computers again thanks to Ubuntu  
:guitar:

---

### Post by Warrior on 2008-01-05
Also having the same trouble with a data DVD burned for me from an unknown OS.
my Fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0fae83d8-fa8b-4381-8ee3-04a99d2431a6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=7fc74856-96af-11dc-96ec-75335902ef18 /home           ext3    defaults        0       2
# /dev/sda5
UUID=6a5fe62c-9877-4ba0-8f72-3d368a7bb1a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```
Interesting thing to me (I'm still pretty new at this) is that I have just installed the dvd burner {sdc0} but I also have a CD-RW {scd1} that is not listed in my fstab. 
Any help? It's really important to view this disc as it has my wedding pictures from the photographer on them!!

---

### Post by jKeats3 on 2008-01-08
I'm having the same issue.  fstab contents:

=============================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=96381fd6-9691-4df0-8d9d-b315e176a423 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1ae11137-6c26-4be9-8bef-471665aa1fa5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
====================================================

---

### Post by bawigga on 2008-01-10
I am seeing the same issue with a DVD, works fine on XP machines, but no dice with nix.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=df4cf302-b655-4891-9b85-2720d1ac4c3b /               xfs     defaults        0       1
# /dev/sda5
UUID=9c7ed3ea-456b-4020-9ab5-b2a32e1a84a6 /boot           ext3    defaults        0       2
# /dev/sda8
UUID=615d9c10-f8d1-44fd-8f9d-ba1a77bed441 /home           xfs     defaults        0       2
# /dev/sda2
#UUID=3EC6-2E70  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
#UUID=0C00B32100B310A6 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda9
UUID=3D14-7A32  /share          vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=74ACB04BACB0099E /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=d9a30600-6a0f-480f-b044-abd24b635e45 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```

---

### Post by Yellow Pasque on 2008-01-10
Can you mount manually by typing:
```
mount -t udf /dev/scd0/ /media/cdrom0
```

---

### Post by kenjiru on 2008-03-09
Same problem here. This is annoying...

---

### Post by foresthensley on 2008-03-09
Linux UDF does not recognize Windows Vista file compression. So if your disc was written in a machine running Vista, chances are it will not run in your Linux. 

Unless someone has found a way around that.

Best bet: load the files onto a flash drive and transfer them from Windows Vista or XP to Ubuntu.

---

### Post by GlorytheWIz825 on 2008-03-16
I am also having the same problem. 

I hope people from the community are on top of this issue! :)

---

### Post by noland on 2008-04-28
Well its the same in hardy.  My boss just made me a data DVD on f*** vista, and i dont have access to it.  im glad i trashed vista, but its annoying to see the ghost of gates making life hard for OS with new file formats or i dont know what just so it works on his machines.  Sorry for complaining, its just that ive been trying to have that work for hours and i dont want to tell my boss so he does not tell me "well you should have windows"...  Gonna try to run a guest XP and transfer it like that, wish me luck!

Trying to sell something free is though because people dont believe it... long live open-source!!!!  and sorry again for b****...

---

### Post by Yellow Pasque on 2008-04-28
If your boss wants you to work at home, then tell him to give you a Vista laptop. Tell him you don't want to run Windows on your home box because of the security and data corruption risks. This is 2008 and Vista is a piece of s***. The time is now.

---

### Post by marshcast on 2008-05-25
same problem.

/etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system>         <mount point>           <type>          <options>       <dump>  <pass>
proc                    /proc                   proc            defaults        0       0
# /dev/sda4
UUID=b89ea202-deb8-4988-8a57-13d5831531b4 /     ext3            defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=900a108c-47ee-4dfe-9003-8ab48505c75e none  swap            sw              0       0
/dev/scd0               /media/cdrom0           udf,iso9660     user,noauto,exec        0       0
# Farm Samba
/192.168.1.100/MEDIA    /SHARES/RMFMedia        smbfs   user,uid=1000,umask=0222,credentials=/etc/sambapasswords        0       0
//rmfserver/Share    /SHARES/RMFShare        cifs    user,uid=1000,umask=0222,credentials=/etc/sambapasswords        0       0

/usr/share/pycentral/gmailfs/site-packages/gmailfs.py /media/g gmailfs username=***,password=***,fsname=RANDOM

looks like bill thinks he's clever again...

Battles and Wars spring to mind... 

:)

---

### Post by yragrelluf on 2008-05-28
same problems here. similar fstab. i have tried everything that i can find about it online. do the developers know about it? lets all figure this out and spread the word.

---

### Post by ertrules22 on 2008-06-19
This one is tough!  If anyone has any suggestions, I am having a similar problem.  I have tried all the suggestions and nothing worked.:confused:

---

### Post by DPic on 2008-06-23
I have a couple DVD's from a friend that were made with Vista giving me the same error. They are both DVD-R if that matters. Is there a bug report for this?

---

### Post by Yellow Pasque on 2008-06-24
> Is there a bug report for this?
[https://bugs.launchpad.net/ubuntu/+bug/1](https://bugs.launchpad.net/ubuntu/+bug/1)

---

### Post by the_darkside_986 on 2008-06-25
No solution? I am just going to promote OpenOffice and Firefox even harder now. This is the sort of **** that M$ should be sued for, not stupid reasons such as including a webbrowser with the OS.

This is so ****ing annoying, I hope Microsoft meets the fate of SCO--within my lifetime--I would give everything to watch it.

But first, as the responsible IT person at the company, the only one here who knows what an "OS" is, I am going to go around telling people to quit using Vista's default option to burn a damned CD. If I have to reboot into freakin' Vista on this work machine, I swear, I'm gonna reinstall Windows XP with my special CD regardless of what anyone thinks.

---

### Post by iainv on 2008-07-15
Now i'm confused.

I burnt a DVD of photos on my laptop, and was transferring them across to my unbuntu desktop.

DVD went in, started copying.

Froze at picture 71, and then locked up.

Ever since, getting the "unable to mount UDF" error described here.

??????????????????

---

### Post by Yellow Pasque on 2008-07-15
> Now i'm confused.
Microsoft doesn't follow the UDF standard with Vista.

"Vista does not play nice with the other children"

---

### Post by aurous on 2008-07-15
same problem here. I wonder if I install vmware and boot xp if I'll be able to access the cd. I'm going to try after work and let you guys know if it works.

---

### Post by crazy ivan on 2008-07-15
Guess Temüjin got the main problem right, but its still a very clever trick they pulled.. Since old XP already has it built in.

Have a look at [Ubuntu bug tracker]("https://bugs.launchpad.net/ubuntu/+bug/193017"), revelation writes there:

"I have solved the mystery and really it comes down to the version of UDF if you choose the default version with Vista it is not going to work . I choose the next one down and that seem to work."

Well he's got the problem solved for him, but I'm stuck here with a CD that won't mount. Anyone with a faster workaround than "vmware, vbox etc."?

---

### Post by aurous on 2008-07-15
> **aurous said:**
> same problem here. I wonder if I install vmware and boot xp if I'll be able to access the cd. I'm going to try after work and let you guys know if it works.

I installed vmware and loaded windows xp. I am now able to view the cd's. I know this isn't a "fix" but hopefully it'll help for the mean time.

---

### Post by lausianne on 2008-07-16
Everyone seems to be writing about problems with Vista-written CDs. 

I've got a couple of CDs written with XP, same problem. One of the CDs is pretty old (2004). Still works fine on XP.

Of course I tried everything I found in this thread. No avail.


NEWS: A minute ago I installed the latest updates - now the old CD works!
Still not the newer one, though.

____
Hardy (8.04)

---

### Post by iainv on 2008-07-16
> **Temüjin said:**
> Microsoft doesn't follow the UDF standard with Vista.

"Vista does not play nice with the other children"

What I really don't get (and what therefore confuses me) is not how easily Vista can make life difficult, but why the DVD-RW was originally recognised by my Gutsy desktop in the first place, and that I was able to copy some photos across before it halted.

What is more disturbing is when I then put the DVD back in my Vista laptop it now says it's a blank disc - my photos appear to have been wiped by my ubuntu desktop.

Concerning - had it been critical data I was attempting to transfer, or an old back-up I was trying to retrieve data from, as I may have permanently lost data.

Iain

---

### Post by rdrey on 2008-07-16
I feel disgusting doing it, but I will quickly boot into my windows XP (only exists for GTalk (using linux Skype in my holiday right now, but port blocked at home in university network) and the odd game...) and load the stuff to my FAT drive... aaargh! I hope that there'll be a work-around one day...

---

### Post by scrime on 2008-07-19
It appears that currently the only work around is to patch your kernel with UDF 2.5 support

[http://ubuntuforums.org/showthread.php?t=718744]("http://ubuntuforums.org/showthread.php?t=718744")

[http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295]("http://sourceforge.net/tracker/index.php?func=detail&aid=1671912&group_id=295&atid=300295")

---

### Post by the_darkside_986 on 2008-07-24
I followed all those instructions in the thread and it built and installed successfully, but it still can't mount the UDF volume.

[quote=Cannot mount volume.]
Invalid mount option when attempting to mount the volume 'UDF Volume'.
[/quote]

---

