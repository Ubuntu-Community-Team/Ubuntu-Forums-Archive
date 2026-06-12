---
title: "Just installed alongside windows, no room to update"
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by HolyPhoenix on 2009-10-11
I just installed ubuntu again, and it runs a lot better than when I tried it a couple of years back and had several problems (mainly from my lack of experience).  I chose the option to install it alongside windows xp, very simple.  Now that it finished though I am running into a problem with updating.  When I tell it to grab updates it says   

```
Not enough free disk space

The upgrade needs a total of 483M free space on disk '/'. Please free at least an additional 483M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
```

Is there any easy way I can fix this without completely re-doing the install with a different partition variation?  

Thanks much!

James

---

### Post by Partyboi2 on 2009-10-11
Hi, can you open a terminal (Applications>Accessories>Terminal) and post the output to
```
df -h
```

---

### Post by HolyPhoenix on 2009-10-11
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G   92K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  184K  1.5G   1% /dev
tmpfs                 1.5G   88K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
overflow              1.0M   16K 1008K   2% /tmp


Seems it only created a very small partition for linux...  :\

---

### Post by Bucky Ball on 2009-10-11
Open System->Administration->Partition Editor and see what you have in there.

If you have free space you can resize your partitions without re-installing but best to do this from a Live CD if you are resizing the partition the Ubuntu OS is on as the partitions need to be unmounted and that can't be whilst you are running Ubuntu (if you follow me).

Just boot from the Live CD and go to Partition Editor in there to resize if you can. Defrag Windows partition first in Windows if you are going to fiddle with that. Very Important Point!

---

### Post by HolyPhoenix on 2009-10-11
I am following you.  I am in college majoring in computer science.  :p

Ok, seems I will have to do it from the live cd.  gparted seems missing from my installation.  :confused:

Oh well, thanks!  I will post again if all doesn't go well.  If it does, thank you all so much for your help.  I am totally amazed even without being able to update by ubuntu.  Makes me excited for the next release.

---

### Post by HolyPhoenix on 2009-10-11
Ok, drive is not mounted.  Partition (sd3) for linux has a key icon on it, and I am not able to resize it.  Any ideas?

---

### Post by Bartender on 2009-10-11
Do you have unallocated space between the Ubuntu / and Windows?  I'm not sure about the key, but first things first.  You can't shove Windows aside and make Ubuntu bigger in one fell swoop.  You'll need to shrink Windows, creating unallocated space, then expand the Ubuntu partition into that space.

---

### Post by raymondh on 2009-10-11
> **HolyPhoenix said:**
> Ok, drive is not mounted.  Partition (sd3) for linux has a key icon on it, and I am not able to resize it.  Any ideas?

When using the liveCD to resize, also ensure that swap is not being used.  Rt. Click on swap partition and select SWAPOFF. In fact, doublecheck that all partitions are unmounted by RT. click on each and if given the option to unmount, do so.

Bartender is right.  Need space first.

1.  Defrag windows
2.  Shrink windows (XP's disk manager will not shrink so you'll have to use gparted)
3.  Enlarge Ubuntu to occupy the freed-up space.  If root (/) is inside an EXTENDED, you'll have to enlarge the extended partition first and then the root partition.

Sometimes, it's better/easier to start over.  If you do decide to:

1.  Boot into your windows to delete swap, root and (if any, the extended partition).
2.  Enlarge windows (XP's disk manager will do this)
3.  Defrag windows
4.  Boot into the liveCD and install
5.  In step 4, choose side-by-side and remember to USE THE SLIDER to allocate partition sizing between OS'.  See Attached pic.
6.  Let GRUB reinstall again. (i.e. finish the install)

[http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874](http://ubuntuforums.org/attachment.php?attachmentid=121997&d=1248267874)

Good luck.  Back-up files first.

---

### Post by Bucky Ball on 2009-10-11
Install gparted from System->Administrations->Synaptic Package Manager to get a look while everything mounted. The key probably signifies it's mounted. 

In your System-Admin Gparted is listed as 'Partition Editor'.

As I (and others) mentioned, DEFRAG your Windows OS partition BEFORE shrinking if you do it that way. Have you got any room left on the other side? Can you do a Gparted screen shot and post it? If you right click on the top task bar and Add New Item you should be able to add the screen shot applet then take a snap.

Generally pre-planning and a manual install overcomes these problems from the start. People say something about move the slider to create more space' but I've only ever done a manual install. You can see your Windows partition(s) there so just don't go near 'em. :)

---

### Post by sechjo on 2009-10-11
I experienced exactly the same problem when installing side-by-side. Even if I created a extended partion in gparted before installing, the installation tool just ignores that and expands the Windows partition again at the time of installation. Ubuntu only gets about 2,5 Gb, although I have allocated 20 Gb for Ubuntu.
This was my 6th trial. I have also tried to manually set the partition for Ubuntu, using the bottom option. I set the /partition to 19 Gb and the swap to 512 Mb. When I installed, Ubuntu used up all of the 20Gb and I was not able to update, getting a message saying that there was not enough space . and there wasn't.
Is the installation tool really functioning correctly?

---

### Post by oldfred on 2009-10-11
Why you get 2.5GB
HOWTO: 2.5 GB System Partition - What Went Wrong? 
[http://ubuntuforums.org/showthread.php?p=7658271](http://ubuntuforums.org/showthread.php?p=7658271)

I also have used gparted to set up partitions and then used manual install so I never have had this issue.

---

### Post by HolyPhoenix on 2009-10-11
That makes way too much sense.  

Yes, I did make unallocated space to put into the ubuntu share before doing anything else.  I think my problem is the swap being on.  

I defragged the day before installing ubuntu.  If I can't get gparted in live mode to work I will just re-install.  Thanks everyone who gave advice.  

*smashes head*  can't believe I missed the slider.  Totally did not expect that.  But it makes sense why it didn't work now.  Will be back if it works.

---

### Post by sechjo on 2009-10-12
I have also tried to use the resize bar. It was set to 20 Gb but the installation still used just 2,5 Gb. 
Am very puzzled by the manual install (bottom option), which fills up the partition to 19,8 Gb which doesn't leave any room for updates...
I am just finishing my 8th trial.
Have been considering uninstalling Ubuntu, but noticed that it will be troublesome since I have no CD-ROM (Dell Inspiron 1011). Haven't been able to make my USB boot w/Windows XP setup. Found a HP flash tool but it didn't make any difference.

---

