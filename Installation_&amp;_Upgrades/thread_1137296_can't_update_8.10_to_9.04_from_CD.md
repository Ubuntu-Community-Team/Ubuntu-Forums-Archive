---
title: "can't update 8.10 to 9.04 from CD"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by ilantal on 2009-04-25
I would like to update to 9.04 on a laptop which has only 8.10(not Windows). I put in the CD and it tells me that I have a boot error from the CD.
I tried booting from the CD, which comes up live. I then have a choice of having 8.10 along side 9.04, which I'd prefer not to have. (I want only 9.04).
It also allows me to use the entire disk, but this will probably erase my user data which I don't want to do.

What is the easiest way out of this problem?

Thanks,
Ilan

---

### Post by snowpine on 2009-04-25
Do you have an internet connection? If so, discard the CD (sorry), boot into 8.10, and use the Update Manager, or the following terminal commands:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by ilantal on 2009-04-25
I want to do this on several machines, so I downloaded the software ONCE onto a CD and now I want to use the CD. Using the Internet means I have to download it several times.

---

### Post by snowpine on 2009-04-25
> **ilantal said:**
> I want to do this on several machines, so I downloaded the software ONCE onto a CD and now I want to use the CD. Using the Internet means I have to download it several times.

OK, I think you can do that, but you need the Alternate Install CD instead of the Live CD. Sorry I can't be more assistance, but I have never personally used that method. I've heard it can be done though, so don't give up. :)

---

### Post by ilantal on 2009-04-25
The first thing I tried was to boot into 8.10, then insert the CD. Up comes a dialog asking me if I want to use a package manager (i'm not 100% sure what it asks since I didn't write it down).

In any case, after I say OK, it fails. I see in the autorun.inf
open=wubi.exe --cdmenu
and that seems to be what is failing.

---

### Post by aikiwolfie on 2009-04-25
I only managed to get 9.04 working with a distribution upgrade. My laptop also seemed to have issues with either the CD or the installer application. I'm using a Dell M1330n which is Ubuntu compatible certified. ... I think.

The first thing you should do is back up your data. It doesn't matter if it's a distribution upgrade or a fresh installation. Back up your data.

Run the utility on the CD menu to check it's integrity. If there are no errors reboot and install.

When you come to do the installation. Select the entire disk option or select the option that allows you to manually create partitions.

Create three partitions. One for the OS, one for your swap space and one for data.

[list=1]
[*]OS partition: make this 8GB - 10GB. Format as either **ext3** or **ext4**. ext4 is supposed to be faster, but ext3 is more mature and supposed to be more robust.

Set the mount point as **/**.


[*]Swap space. Make this 500MB to 4GB depending on how much RAM you have and how heavy a load your system is under. The more RAM you have, the less swap space you'll need. Note: 4GB is a bit extreme.

Simply set the file system type as **swap**.


[*]Data partition: Use all of the remaining disk space for this partition. It should be formated as **ext3** or **ext4** as above. Set the mount point to **/home**.[/list]

---

### Post by bsmith1051 on 2009-04-25
If you download/burn the Alternate Install CD, when you insert it with Ubuntu 8.10 running you should prompted to update from it.  You'll also be prompted to download any additional updates.

But be warned: I've had this method blow-up in my face on two previous versions (7.10 and 8.04).  So when I upgraded to 8.10 I did a new from-scratch install.

---

### Post by ilantal on 2009-04-26
Thanks for the suggestions.
I think the best one is to make 3 partitions: one for the OS, one for the swap and one for my data. This I failed to do last time around and now I pay the price.
It would mean that next time I can just format the OS partition and load the new software and leave my data in tact. Blunder on my part....

I found out that wubi.exe is for Windows upgrades so that is of no help to me.
I don't get any CD menu to check the integrity of the CD. I see there is a command:
gksu "sh /cdrom/cdromupgrade"

However there is no file called cdromupgrade on the CD. This may be the root of the whole problem.

I would like to confirm that if I make the 3 partitions I will lose all my user data. At this stage that isn't terrible because my real data is still stuck in the Windows world on a different computer. I'm trying to free myself from ugly Windows, but it is a non trivial task.

Thanks,
Ilan

---

### Post by Partyboi2 on 2009-04-26
Another thing you could do is move your /home folder to its own partition
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
That way if you ever need to reinstall anything this is on the /home partition will remain untouched. All you would need to do each time you went to reinstall is choose the "manual" partitioning option and set your mount point again for /home and make sure the box to format your /home is **unticked**.

---

### Post by ilantal on 2009-04-26
I read the tutorial on moving the home folder to its own partition and this looks like the best possible solution. While still in 8.10 I can do the transfer, check that all is well, and then just reformat the partition with the operating system.
I'll have a last look to make sure there is nothing which I don't already have under Windows, but it looks like it will save everything anyhow.

Thanks for the suggestion.

---

### Post by Sef on 2009-04-26
> Do you have an internet connection? If so, discard the CD (sorry), boot into 8.10, and use the Update Manager, or the following terminal commands:

 	Code:
 	sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade 


That way is no longer supported.  It is best not to upgrade that way.

---

### Post by fvasil on 2009-04-26
Hi all.
Sorry me for my opinion and bad English (not native).
I think to make /home partition not solve the upgrade problem due to installed progs. For example I have Eclipse, Bender, MySQl and ...
In this way (/home partition) I will have to reloaad and reinstall all of them.
I hope somebody help us and give the right way to upgrade 8.10 to 9.04 directly from CD
Best wishes

---

### Post by telmac on 2009-04-26
atleast you are doing better than me, I can't even use it as a live cd.

---

### Post by snowpine on 2009-04-26
> **Sef said:**
> That way is no longer supported.  It is best not to upgrade that way.

I did not know that. What is the new correct command?

---

### Post by aikiwolfie on 2009-04-26
Didn't know that either. apt-get is still there. Works just fine. So far as I knew all the GUI installers were just front ends for apt-get.

---

### Post by fvasil on 2009-04-29
Did you upgrade Ubuntu from 8.10 to 9.04?
If not please do follow:
1. download Alternate CD
2. burn it
3. insert into cd drive. You will see prompt Upgrade or in shall run "sudo /media/cdrom/cdromupgrade"
4. follow the dialog box

It will be good if you have internet connection on upgrade. Some newest package will be download.
Good luck

---

### Post by ilantal on 2009-04-29
Thanks for your interest. I took the advise to split off my home directory to another partition. I had a hitch or two but I got it to come up with the home in the second partition under 8.10.

Next I decided it would be best to format the operating system partition and start from scratch with it. I've been learning Ubuntu by experimenting with different things and along the way managed to mess up skype. I thought I could avoid grief by starting out again with a clean copy of 9.04.
Thus I went into advanced mode, asked it to format sda1 in install the software. It went along OK until it discovered a read error on my CD, at which point it killed the installation. Now I have nothing I can boot, but will burn a new copy of 9.04 on a fresh CD.
This is a bit harder than I expected, but in the end I expect that it will work. In any case an upgrade at this point is impossible.

---

### Post by aikiwolfie on 2009-05-01
I had issues upgrading my laptop. The way I got it to work was to get an 8.10 CD I knew was good because I've used it before. Once the basic 8.10 copy was installed I just choose the upgrade option from **System > Administration > Update Manager**. 

That seemed to work just fine. It's a bit of a long walk for a shortcut. But it worked.

---

### Post by ilantal on 2009-05-02
I hate to admit it but I finally gave up trying to save my home directory. SOMETHING was wrong and I couldn't figure out what it was. The bottom line was that there wasn't anything I really needed in the home directory and I wanted to start enjoying Ubuntu rather than fighting it.
I went to a clean slate, boot from a CD, chose a new partition table and set up 10 GB for the OS, almost the entire disk for home and 2 GB at the end for swap. (I have 2 GB of RAM so don't really need swap.) I let it format the disk and now it works.
From now on at least I can format the OS partition without touching my home partition - which I was I wanted up front.
The upgrade was much more difficult than what I've seen in the past, but now my system is the way I want it.
I am grateful for all the suggestions because I did learn several new things about Ubunutu.

---

### Post by mahela007 on 2009-05-02
Hello everyone.. I'm having a similar problem with upgrading. I tried to use the alternate CD of 9.04 to upgrade 8.10 but contrary to all the tutorials on doing this upgrade the dialog asking me to upgrade doesn't show up.
I then entered the command that the ubuntu upgrade page shows and it went though a few steps of the upgrade. However before the actual installations began I got a message saying
"impossible to locate package KDE-Desktop". It is possible to continue but I didn't know what the results would be so I stopped the upgrade. How can I fix this?

---

### Post by sandy8925 on 2009-05-03
I used the alternate install cd to upgrade and it worked flawlessy for me. Infact I even saved the trouble of burning the cd by mounting the iso under /media/cdrom0 as given in the upgrade page in the Ubuntu webite. The popup came, did the upgrading (took 2.5 hours for me) and restarted and worked. Except for some small trouble involving the nvidia drivers (I have my comp connected to my LCD TV through component so needed nvidia driver to have proper display).

All my settings and data were still intact (i was lucky there although i don't think anything would have happened to the data anyway) and everything worked and works fine.

---

### Post by mahela007 on 2009-05-03
Do you use ubuntu or kubuntu? and did you select Yes or No when prompted to allow further upgrades via the network?

---

