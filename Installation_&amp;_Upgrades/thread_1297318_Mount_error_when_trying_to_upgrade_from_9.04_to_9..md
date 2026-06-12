---
title: "Mount error when trying to upgrade from 9.04 to 9.10"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by zafo on 2009-10-21
I am upgrading a computer from Ubuntu 9.04 to 9.10. It was downloading and installing files, so I went to lunch. When I came back the computer was on but locked up - keyboard and mouse did not work and there was no output to the display. I rebooted and after the Ubuntu splash screen I get the following error:

One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/6b1dd640-04f1-4f3c-ab91-a537f60841d1
/tmp: waiting for (null)
swap: waiting for UUID=19ec2898-8e83-4b1c-9b8f-8790d42fd56a

Can someone please give me some guidance on how to correct this problem?

Thanks,
Rod
Austin TX

---

### Post by soro2005 on 2009-10-22
I also get that error, but my computer keeps booting (and mounting the partitions it reports it cannot yet mount). I'm trying to find out what's going on there. But your problem is obviously a little bigger since you apparently have a failed upgrade.

You could try to to hit "esc" and log into the recovery shell if that's even an option, which it may not if really no partitions are mounted. Once inside the shell, try all the habitual update/upgrade recovery commands:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```
This assumes that you get an internet connection (i.e. that you can connect with a network cable)

Also, of course, you may want to try interrupting the boot at the beginning by frantically hitting the <esc> key and selecting an old kernel from the Grub menu. If you manage to boot an old kernel, the odds are good that you might be able to fix the upgrade from there.

---

### Post by herberthamaral on 2009-10-22
I am experiencing a similar problem, but in boot. Ubuntu isn't starting after the  upgrade from 9.04 to 9.10.

In some stage of boot it freezes and keep flashing, both video and HDD LED (they flash synchronously) and the text-mode login screen is displayed, but I can't enter nothing but a CTRL+Alt+Del :(

So, I tried to enter in recovery mode. Without success. When I roll over the **fsck**menu, it says something like "System file couldn't be mounted. Returning the maintence shell.". It returns the shell, but I can't type nothing in it.

I tried to do this in 2.6.28 and 2.6.31 kernel and I am using an ext4 filesystem.

Does anyone figure out what is happening? Any help will be useful

Regards

---

### Post by zafo on 2009-10-22
Thanks for your suggestions.

I tried hitting <esc> repeatedly while in the loading grub, but it was unresponsive. I also tried to drop to the root shell prompt with networking, but could not even get a prompt. I can't access the Internet from the recovery shell.

I'm still stuck. This is a secondary computer without a lot of data on it, so it won't be disastrous to reinstall from CD, but I'd obviously like to fix it if possible.

Rod

---

### Post by ken_23434 on 2009-10-22
I had a similar problem when I tried the upgrade.

When I did the ESC trick, I noticed about 4 different OS's to boot to (each with a recovery option).  I picked the 2nd one down on the list and it booted.

I didn't reboot the computer for the next week.

I then tried to run the update manager (hoping a fix came out).  After it did a bunch of updates, the computer failed to boot at all.

Today, I used my 9.04 disk to restore it.

I will just wait till it is no longer a Beta.  I don't know enough about Linux to try and figure out what was happening nor do I have the time.

Having my /home directory on a separate drive really made the recovery easy, though.

---

### Post by sams9 on 2009-10-23
I'm getting something similar after updating from Alpha 5 to Beta.
Something like ...mount error /dev/disk....
Only comes up for a few seconds then loads successfully.
I'll run Update Manager tonight and see if it will pick up the new release candidate updates?!

---

### Post by cviorel on 2009-10-23
I'm running Karmic RC and and after the Ubuntu splash screen I also get the following error:

```
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/6b1dd640-04f1-4f3c-ab91-a537f60841d1
/tmp: waiting for (null)
swap: waiting for UUID=19ec2898-8e83-4b1c-9b8f-8790d42fd56a

```
I tried to force fsck on the next boot by issuing the following command:
```
sudo touch /forcefsck
```
This will get things back to normal ONLY for the next reboot.
Nothing in the logs to trace the problem. :(

---

### Post by soro2005 on 2009-10-23
> **zafo said:**
> Thanks for your suggestions.

I tried hitting <esc> repeatedly while in the loading grub, but it was unresponsive. I also tried to drop to the root shell prompt with networking, but could not even get a prompt. I can't access the Internet from the recovery shell.

I'm still stuck. This is a secondary computer without a lot of data on it, so it won't be disastrous to reinstall from CD, but I'd obviously like to fix it if possible.

Rod

It's possible, it's just a matter of the time and effort you want to put into it. As a first step, however, I would recommend to pop in a Live CD and make a backup of your /home and all your data, important or not (who knows...), either to an external drive or, if you have none but two cd drives, to a dvd or something.

The problem you're currently facing are two, as far as I can see.

1. Your Ubuntu Karmic installation is in a bad state and probably doesn't recognize it's root partition. Odds are you can fix this quite easily by resuming the botched upgrade or, perhaps and in the worst of cases, manipulating some details in /etc/fstab. To do so, however, you'd best start the system. Since your Karmic doesn't start, this would have to be one of the Jaunty kernels that are probably still sitting there. To start one of the old kernels, however, you would need to get a Grub menu listing all the different kernels that are still installed.

2. Absolutely annoyingly for cases such as yours, the new Grub defaults to a zero timeout, making it absolutely hard to catch the moment at which to press <esc> to get to the menu. If there is any such moment, that is. Perhaps it's just plain impossible. I think it's a really bad idea by the maintainers to go for the speed, instead of the safety. Perhaps somebody knows how to get the Grub menu with a zero timeout?

I think you could just use a Live CD to install a new Grub to the harddrive and make sure you set it up to have a decent timeout. But perhaps there is an easier solution.

---

### Post by Mairos on 2009-10-23
I have the same problem -.- I tried to upgrade my 9.04 to 9.10 RC, but suddenly my pc shut off. Now I receive those errors. Everything I tried was not successful, because it says "Read-only file system" and so I'm not able to modify the /etc/fstab for example...

---

### Post by kentaur on 2009-10-23
Your installs have failed.

remount your filesystem like this:

```

mount -o remount,rw / 
```

then do a 

```
sudo dpkg --configure -a 
```

And the installation will continue.

Worked for me. ymmv.

---

### Post by makro on 2009-10-23
Same problem here but from a fresh RC installation.

The error has appeared when I put a new line in fstab in order to mount an ext3 partition under /mnt/music. If I comment that line boot is fine...

---

### Post by zafo on 2009-10-23
And the winner is....kentaur! Your suggestion was right on: straightforward, and not only got me going again, but finished the upgrade to karmic! 

Thanks very, very much for the tip.

Rod

---

### Post by koalo on 2009-10-24
> **kentaur said:**
> 
```

mount -o remount,rw / 
```then do a 

```
sudo dpkg --configure -a 
```


Same error here while updating 9.04 to 9.10 RC and this worked for me too.

---

### Post by slavojzizek on 2009-10-24
> **koalo said:**
> Same error here while updating 9.04 to 9.10 RC and this worked for me too.

This is currently working for me. :KS

View Post
Code:

mount -o remount,rw /

then do a

Code:

sudo dpkg --configure -a

---

### Post by PfeifferA on 2009-10-24
Got the solution idea, but where do input these instructions.
There are several options in start-up to choose from. Need your help .
:P

---

### Post by makro on 2009-10-25
> **slavojzizek said:**
> This is currently working for me. :KS

View Post
Code:

mount -o remount,rw /

then do a

Code:

sudo dpkg --configure -a

Not for me :( 
I did a fresh install...

---

### Post by Mairos on 2009-10-25
Works for me too, thank you kentaur!!

---

### Post by p3pilot on 2009-10-25
I had a very similar error mounting the swap partition after upgrading from 9.0.4 to 9.10.  I would see the error in a window during boot, but eventually the system would finish booting.

In my case the fix involved updating the UUID for my swap partition in the fstab file.  When I ran blkid, I noticed the UUID in the fstab was different than reported by blkid.

I updated fstab to the new UUID and everything is working now.  Not sure if this is what some are seeing here also.

---

### Post by tylerannosaurus on 2009-10-25
I tried the suggestion from kentaur, but it did not work. For those that this worked for, when did you do the code? Once I got to the point where it said <Esc> to go to shell I hit escape and tried typing it in there. Any other suggestions? Does the installation CD have some sort of "recovery"? I am going to try that next I think.

---

### Post by holycalamity on 2009-10-25
This happened to me with clean installs of the last Karmic beta and the current RC.

The only way around it is to comment out the two fat32 partitions that hold all my data from fstab. Then the system boots and can be used normally. The two troublesome partitions can be mounted normally after that.

The solution that has worked for others in this thread does nothing for me.

---

### Post by tylerannosaurus on 2009-10-25
> **holycalamity said:**
> This happened to me with clean installs of the last Karmic beta and the current RC.

The only way around it is to comment out the two fat32 partitions that hold all my data from fstab. Then the system boots and can be used normally. The two troublesome partitions can be mounted normally after that.

The solution that has worked for others in this thread does nothing for me.

How exactly would I do this?

---

### Post by holycalamity on 2009-10-26
Hit control-d to drop into the emergency shell.

Then run:

```
mount -o remount,rw /
```

and

```
sudo nano /etc/fstab
```

Then comment out the offending lines - in my case it was the fat32 partitions - then reboot.

Although I can then mount them manually from inside the working system, I'd much rather have them automount at boot.  I've tried adding them by hand back into fstab to no avail.  A fix for this would be most welcome!

---

### Post by makro on 2009-10-26
I "solved" re-formatting my mounted partition from ext3 to ext4.
This avoids the warning message on the boot... but that is NOT a solution...

---

### Post by ron273 on 2009-10-26
> **holycalamity said:**
> Hit control-d to drop into the emergency shell.

Then run:

```
mount -o remount,rw /
```and

```
sudo nano /etc/fstab
```Then comment out the offending lines - in my case it was the fat32 partitions - then reboot.

Ok, but where exactly do I hit Control-D.

It doesn't work while beeing in de Grub menu, but once I selected a boot option the screen goes blank, only stating:

```
One or more of the mounts listed in /etc/fstab/ cannot yet be mounted:
(ESC for recoveryshell)
/: waiting for /dev/sda6
/tmp: waiting for (null)
swap: waiting for /dev/sda8
```The ESC does not work and also Ctrl-D does not work.

Do I need to boot from the 9.04 live CD first?

Cheers,

Ronald

---

### Post by holycalamity on 2009-10-26
Using a live cd is another option.  Select "try out ubuntu", then open up your root partition from the "places" menu in nautilus.

Then open a terminal and type:

```
sudo gedit /media/[your root partition]/etc/fstab
```

That will allow you to comment out any partitions that aren't root, and may allow your system to boot normally. But it isn't a solution!

---

### Post by holycalamity on 2009-10-26
Don't know about anyone else, but the latest round of updates seem to have fixed this issue for me on Karmic RC1

---

### Post by Findarato on 2009-10-27
I still have the same error.

Could this be linked to the fact I have 3 primary partitions ? (my home, root AND swap are on primary)

---

### Post by ororo on 2009-10-29
> **holycalamity said:**
> 

Then comment out the offending lines - in my case it was the fat32 partitions - then reboot.

Although I can then mount them manually from inside the working system, I'd much rather have them automount at boot.  I've tried adding them by hand back into fstab to no avail.  A fix for this would be most welcome!

Same problem here. Many thanks to holycalamity, I have solved that way :D. Of course, it's not fantastic, I cannnot see why my FAT32 partitions cannot be mounted at boot time.

---

### Post by sexus6 on 2009-10-29
same problem here

I can't access to emergency shell ESC or CTRL+D dotn't works.

I can use live cd, but what "ofending lines" I have to comment? I only have /, /home and /swap...

---

### Post by HolyJoe on 2009-10-30
> **zafo said:**
> Thanks for your suggestions.

I tried hitting <esc> repeatedly while in the loading grub, but it was unresponsive. I also tried to drop to the root shell prompt with networking, but could not even get a prompt. I can't access the Internet from the recovery shell.

I'm still stuck. This is a secondary computer without a lot of data on it, so it won't be disastrous to reinstall from CD, but I'd obviously like to fix it if possible.

Rod

I had the same problem, and <ESC> doesn't work.

---

### Post by Velophile on 2009-10-30
I get the 'cannot yet be mounted' messages during boot, they scroll underneath the white ubuntu logo during boot, before the brown boot screen (so does that make it the grub boot?).  They don't stop the system from booting and I've not been able to
 a) read the message properly before it scrolls out of view
 b) find the errors in a log to investigate further.
I have no non-EXT partitions on the disk so can't see that it's NTFS/DOS, though there are LVM ones (not encrypted) and I wonder if it's those, somehow.

If anyone knows how I can get the errors to log to a file so I can read them and try and investigate I'd appreciate it.

---

### Post by revirevy on 2009-10-30
To access to shell try 
[ESC] 
then hit [enter]

That worked for me

---

### Post by FrankCy on 2009-10-30
I'm facing the same problem with the final 9.10 release. After upgrading from 9.04, my filesystem partition disappeared. 

Sadly I can see this problem was there since previous 9.10 releases :/

The temporary solution I used, was to boot 9.10 using an older Kernel version (2.6.28 ).

Disk's UUID is correct in both fstab and grub, but yet 9.10 won't boot using 2.6.31. It always exits Grub with error "Gave up waiting for root device" and then I'm stuck in BusyBox.

While there (or booting from 9.10 LiveCD) my disk's UUID is nowhere to be found. Trying to mount it, gives me: /dev/sdb: TYPE="isw_raid_member"  (i'm not using any kind of RAID configuration)

Also swapping SATA controller with another HD, the filesystem HD was still not accessible, while the other HD was fine.

The funny thing is that I have 2 identical HDs (Hitachi HDS728080PLA380) as my filesystem one, and neither is detected on any controller when running 2.6.31 Kernel, as if this is a compatibility issue with the specific hardware!

At the moment I'm using the older Kernel to be able to boot into Ubuntu, but that generates me a ton of other problems :|

---

### Post by mushr00m on 2009-10-30
Same problem here. I've got a NTFS formatted drive in there at the moment so maybe I'll get that out.

---

### Post by Velophile on 2009-10-30
I did get into the recovery console using <Escape><return> didn't get much info though.

Tried changing my /etc/fstab so it used devices rather than UUID's and found it's the two LVM's that the boot sequence is waiting on.

No ideas what to do next though, other than search Launchpad for bugs.

---

### Post by FrankCy on 2009-10-30
> **mushr00m said:**
> Same problem here. I've got a NTFS formatted drive in there at the moment so maybe I'll get that out.

My 2 identical drives have several NTFS and Ext3 partitions, and neither is accessible with 2.6.31 Kernel:

[INDENT]   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5131    41214726    7  HPFS/NTFS
/dev/sdb2            5132       10011    39198600    7  HPFS/NTFS


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9598    77095903+  83  Linux
/dev/sdc2            9599       10011     3317422+   5  Extended
/dev/sdc5            9599       10011     3317391   82  Linux swap / Solaris[/INDENT]


Out of curiosity, what brand/model is your hard drive mushr00m?

---

### Post by Ian Goodacre on 2009-10-31
Try Ctrl-Alt-F8 (and Ctrl-Alt-F7 to get back to the X display). This switches to a console displaying the error message, but not much else. Some posts suggest this console is for boot messages, but it is a very small subset of them. But it does have the error, on my system, which I can't find in any of the log files.

---

### Post by wzaatar on 2009-10-31
I think that several 'errors' are being treated here. However, I do believe that kentaur's post answers the thread's main error.


What you need to do here is the following.

Once the machine reboots let it pass the Grub selection message (the one that counts to 5 and asks you to press ESC).

Once you see the Ubuntu graphical logo and the orange line below, hit the ESC key a couple times. A few seconds later, you'll get a text prompt asking you to press CTRL+D to resume. DON'T press CTRL+D, instead press ENTER and then type in your root password, then type the two commands in sequence:

mount -o remount,rw /
sudo dpkg --configure -a

This will complete your installation.

My 2 cents on why it froze: You probably have tweaked your PC's configuration and Ubuntu install reached a point when it needed some text input, but you were in GUI mode; hence the "freeze".

Hope this helps.

W.

---

### Post by bars123 on 2009-11-01
I upgraded from Jaunty to Karmic. The installation was hassle-free. After the installation process is complete,it prompted me to restart for the upgrade to take effect.When restarting, I observed an error message which is almost similar to the one posted by the thread starter. Then I was guided to a recovery shell and while I was staring at it not knowing what to do, the booting process continued and I was able to log in to Karmic.

I thought of posting the problem and saw this thread. Funny thing is my install is good, but I keep getting that error msg while booting.


Can I issue the commands
[B]
mount -o remount,rw /
sudo dpkg --configure -a 
[/B]
in the terminal after logging in? 

Thanks.

EDIT: All my partitions mount after logging in and I have no problem whatsoever apart from the error message that is thrown beneath the ubuntu logo while booting

---

### Post by CD27 on 2009-11-01
Unfortunately I ran into this EXACT problem upon upgrade. This seems to be a trend, not just in Karmic, but in previous versions. I vote for a bug report.

I tried to fix this by wiping the partition in live cd, but it couldn't boot it. I also tried using the live cd to reinstall ubuntu, it simply couldn't get to the partitioning phase. I then loaded the live cd and just tried to use Gparted, it couldn't load the partitions. I can't mount them, and I simply can't do anything with them. I was almost sure it was a hardware problem, but it wasn't.

My solution to fix this problem?

-Pop in a windows xp install cd and wipe the partitions, then exit out of the install after the partitions were formatted, and install ubuntu. Worked like a charm after that.

---

### Post by ffffuuuu on 2009-11-01
If any of you are like me and are using the an NVIDIA softchip RAID controller, then this might help you:

Change the /dev/sd* /home
line to use the UUID instead.
(Below is what I used but I'm pretty sure there is a command that does it the easy way)

I got the UUID by logging into gnome as root (who's home resides on /) and the mount options in the 'Places' Menu at the top had an entry for my home partition!

After it mounts just run mount on its own to see the listing and you will notice the /mapper/nvidia-[blah] with string of hex e.g. 4bdaaa6a-b765-46c7-ab78-0d0b053a6812
this is the UUID.

Use this to make a new entry in the fstab:
instead of:
```
/dev/sdc1    /home    ext3     defaults,errors=remount-ro,relatime 0     1
```use:
```
UUID=4bdaaa6a-b765-46c7-ab78-0d0b053a6812 /home    ext3     defaults,errors=remount-ro,relatime 0     1
```Save, test by:
```
sudo mount -a
```and reboot.

Hope this helps!

Note:
I tried to use the /dev/mapper/nvidia_ecidceee1 entry you see after it's mounted but it didn't like it. Anyone know why?

---

### Post by xoorox on 2009-11-01
Thanks wzaatar... unfortunately my problem is that they keyboard (just a standard usb model) while being fine in the grub menu is unresponsive when I try and go from there... the cursor is still flashing after the "One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/..." message but I can't use the keyboard... you can't turn any of the locks on and off even.... and to think a couple of months ago I threw away my last grubby ps/2 keyboard...

---

### Post by ffffuuuu on 2009-11-01
It's odd that the upgrade would do this because your problem sounds like a BIOS setting, have you enabled USB legacy support?

---

### Post by kelvinator on 2009-11-01
I hope I am not writing this prematurely but this is the most helpful suggestion I have ever  read. I was dead in the  water for 3 hours until I saw  your post.


> **kentaur said:**
> Your installs have failed.

remount your filesystem like this:

```

mount -o remount,rw / 
```

then do a 

```
sudo dpkg --configure -a 
```

And the installation will continue.

Worked for me. ymmv.

---

### Post by xoorox on 2009-11-01
On this pc there isn't a legacy support option in the BIOS though I can turn USB2 on and off and that doesn't get me anywhere unfortunately.  I'm edging towards pulling everything off and trying a fresh install (though the prospect of trying to restore a mythtv database without a proper dumps isn't appealing).

---

### Post by leoaloha on 2009-11-01
I had the same problem. Seems the update process could not figure out how to move a file in the python directory to an " old-site-directory" and failed.

In any case, I could not get to the rescue shell. My UUID's for the disks were correct

To fix

Download the Ubuntu** alternate** CD. NOTICE **ALTERNATIVE**!
such as 

[http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/](http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/)

Boot it , select your language. Then select
[B]
REPAIR A BROKEN SYSTEM[/B]

This will get you your keyboard and try to mount your original disk. This is important. 
You need to work on the disk that failed. The "repair a broken system" will try to mount that system
with a "mini" kernel of its own. This will allow the keyboard to work if the previous install failed without
installing any X window or keyboard drivers.

 Then enter the commands as stated;

apt-get update
apt-get upgrade
apt-get -f install

watch for errors to correct **YOUR** problem

then

 dpkg --configure -a

no need to; 
*mount -o remount, rw /*
it will be mounted correctly already

---

### Post by leoaloha on 2009-11-01
1

---

### Post by AthenaInternet on 2009-11-02
I, too, got this error, and Kentaur's suggestions saved me as well.

In my case, the issue seems to be affecting my swap partition: it's there, it's in /etc/fstab, and it's properly formatted, but it doesn't seem to actually be being mounted.

When I go to mount it manually, no issues.

---

### Post by atleetalie on 2009-11-02
It maybe this helped only in my case, but instead of running all these things mentioned above, I 'simply' changed the UUID of my swap to the UUID it really had. I looked into gparted for the right code, and changed the fstab. 

But you needs permissions for that I don't have so I used antoher linuxversion (puppylinux) to do this. 

And it works. No errors about mounting anymore!

---

### Post by mortenne on 2009-11-02
I have tried to lookup the uuid of my Linux/Ubuntu partition (ext3 file system) to try the fstab edit option but there are no uuid assigned to that partition.

When starting from live CD this partition didnt mount at all.
I have started the 2.6.28 kernel, had to run remount, and the partition is mounted, but no uuid to find...

Can anyone give me a hint?

Does the boot flags have any role in this matter?
Now the boot flag is set on my Windows XP partition.

---

### Post by ubununtuman66 on 2009-11-02
Glad to see I am not alone with this problem, the reason is a beta version of Grub, how they could ship a beta version with the finally 9.10 release beats me, and Im a total noob. I don't understand how this could happend? doesn't they test the rc's prooperly anymore? sloppy!

---

### Post by philipa on 2009-11-02
How did those of you with unresponsive keyboard problems get past them?

I can boot to a rescue CD, but even pairing down fstab to nothing fails to get me to a point at which I can run dpkg --configure -a.

I think ron273, HolyJoe, xoorox are all in the same hole.

---

### Post by jreiner3 on 2009-11-02
I was in the same boat, unresponsive keyboard, actually the text was blinking at a rate that made it impossible to type my user name or password when I finally got to a prompt, but usually it would boot to Checking battery state done.... and just blink at me. UGH

Heres what I did, booted from a live cd (any linux distro should do I used Fedora 11 because I had it) I found that the uuid for my swap disk had changed, blkid /dev/sda3 in my case, so I edited /etc/fstab to reflect the correct uuid  but I still could not boot into Karmic. Back to the live cd and following the advice of some earlier posters I commented out my windows fat32 partition. After this I was able to boot into 2.6.28.16 (I still could not boot into 2.6.31.14) but booting into the older kernel allowed me to reinstall the nvidia restricted driver, (version 185) and discover I had no sound :( However once I reloaded the nvidia driver I was able to boot into 2.6.31.14 YAY and my sound worked. double Yay! Feeling gutsy (no pun intended) I uncommented out the FAT32 line in /etc/fstab held my breath and rebooted. Everything came up, and has been working five by ever since.

---

### Post by philipa on 2009-11-02
Thanks, but my problem was worse :-) (Wouldn't boot, even with only the root drive in fstab).

I followed the hint from leoaloha (thanks!), and did the following:

   0. Booted from a rescue CD.
   1. Managed to dial out via my DSL modem, and download the 9.10 alternate CD.
   2. Booted the alternate CD into rescue mode. This finally got me a prompt against the old root.
   3. mount -a
   4. dpkg --configure -a


- Phil

---

### Post by SilentSentinel on 2009-11-03
Above worked for me too .... Phew!!! im totally now relieved :)

Thanks guys for the help....

Ted

---

### Post by scawa on 2009-11-03
@Kentar

That does not work for me.  I am getting the same problem.  It seems this problem crops up OFTEN when there is an upgrade.  It happened from 8.10 to 9.04.

The system I have set up is:

Running Parallels 4.0 on Mac OS X Snow Leopard.
I set up Ubuntu 9.04 using the alternate install iso.  It worked like a champ,

When I did the automagic upgrade to 9.10, the install seems to go ok, but I get the following when it reboots:

```

Gave up waiting for root device. Common problems: 4a8a66d7ea8
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modlues (cat /proc/modules; ls/dev)
ALERT! /dev/disk/by-uuid/279b624a-0b14-47c9-a7b2-b4a8a66d7ea8 does not exists.  Dropping to a shell!

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

```

When I check the sets with **set|more**, I get

ROOTDELAY=''
ROOT='/dev/disk/by-uuid/279b624a-0b14-47c9-a7b2-b4a8a66d7ea8'

I checked out the /dev folder and there are no hard drives mounted.
There is no fstab under /etc

The UUID is the same as was under Ubuntu 9.04.  What I'm wondering is why it is loosing track of the hard drive.  

It seems as though Many people are getting this problem here, and they are not using Parallels.

I tried starting an install from the Ubuntu alternate install for 9.10 from the start.  It begins the install, but I get to the detection of the hardware and I get

```

No common CD-ROM drive was detected.

You may need to load additional CD-ROM drivers from removable media,
such as a driver floppy.  If you have such media available now, insert
it, and continue.  Otherwise, you will be given the option to manually
select CD-ROM Modules.

Load CD-ROM drivers from removable media?

```

I am at a total loss as to why:

1) 9.04 works correctly in Parallels
2) 9.10 upgrade looses its way to finding any connection to the Virtual Hard Drive
3) 9.10 alternate install can't install like 9.04?

Thanks for any help.

---

### Post by Frolicsome Otter on 2009-11-03
I had a similar problem in my upgrade.  I kept getting error messages about not being able to mount a partition, the swap partition.  I tried kentaur's suggested commands by logging into recovery kernel.  When I rebooted, I still had the same problem.  

I then tried changing the UUID in fstab for the swap partition since it was different from the one listed with 
ls /dev/disk/by-uuid

Again on rebooting it still hung in the same way with messages about being unable to mount a partition.  Now here's what's different about my solution.

I have had a different version of Ubuntu on another partition which I hadn't been using anymore.  So I installed Ubuntu 8.04 into this partition from my live disk thinking at least I'll have something to work with while I sorted out 9.10.  The installation went fine, and it also reformatted the swap partition and reinstalled and configured GRUB.  I figured that since I was only using one version of Ubuntu at a time, I could just use the same swap for them both.  After this I rebooted back into the 9.10 partition and it worked fine.  This may give a hint to others how to approach their problem since there are two things that might have helped.

You might try:
1.  Reformatting the swap partition with gparted say, or
2.  Reinstalling Grub, if you've got a dual boot system.  

Cheers.

---

### Post by EpoxyRepair on 2009-11-04
I carried out my upgrade from 9.04 -> 9.10 on Monday 2nd-Nov. Overall it was fairly successful but I am getting this error when I reboot.

This thread appears to be covering several serious problems arising from the upgrade, and I'm getting confused following it.

I am wondering about the failure to mount messages, after which it mounts and boots anyway. So I have three questions:
 
1) What is the best way to investigate them?
2) Is there a fix to remove them - or do I just wait for the update?
3) Could this lead to a boot failure in the future?

---

### Post by xoorox on 2009-11-05
> **leoaloha said:**
> I had the same problem. Seems the update process could not figure out how to move a file in the python directory to an " old-site-directory" and failed.

In any case, I could not get to the rescue shell. My UUID's for the disks were correct

To fix

Download the Ubuntu** alternate** CD. NOTICE **ALTERNATIVE**!
such as 

[http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/](http://mirror.anl.gov/pub/ubuntu-iso/CDs/karmic/)

Boot it , select your language. Then select
[B]
REPAIR A BROKEN SYSTEM[/B]

This will get you your keyboard and try to mount your original disk. This is important. 
You need to work on the disk that failed. The "repair a broken system" will try to mount that system
with a "mini" kernel of its own. This will allow the keyboard to work if the previous install failed without
installing any X window or keyboard drivers.

 Then enter the commands as stated;

apt-get update
apt-get upgrade
apt-get -f install

watch for errors to correct **YOUR** problem

then

 dpkg --configure -a

no need to; 
*mount -o remount, rw /*
it will be mounted correctly already
A big thank you to Leoaloha - this got me back up and running :)

Plenty of smaller probs to sort out but that finished off the meat of the upgrade.

---

### Post by gumrol on 2010-02-26
I had exactly the same problem as **zafo**. I didn't have the option of re-installing from Live CD though as it just wouldn't work - my upgrade from 9.04 to 9.10 really bombed : power down while installing. I was also in the same boat as a few others, where I just couldn't get into the command prompt no matter how hard I tried. In desparation I just held my finger on the ESC key while it was trying to boot & then mount discs & eventually it dropped to the command prompt & was able to run the fix **kentaur** suggested. Good one mate - saved me a lot of hair pulling!

---

### Post by pterosky on 2010-03-30
I also got the problem after upgrading to 9.10 (Karmic Koala); The computer crashed during boot with the error message: "One or more of the mounts..." and "swap: waiting for UUID: 62265758-9845..." -- it couldn't find the swap partition.

I managed to get it through this problem by hitting escape a few times after the Ubuntu loader graphic appears, and the boot went through. I then updated the swap info in the fstab file.

To verify this is the problem: under 'System Monitor', 'Memory and Swap History' it will say "Swap -- 0 bytes (0,0 %) of 0 bytes"

To open the fstab file and point it to the correct UUID for the swap:

```
sudo gedit /etc/fstab
```

locate the swap and update it, it says 'swap' somewhere on the line 8o)

```
# the swap partition
UUID=62265758-9845-42e4-a4we-6345i44d595fa13 none            swap    sw              0       0
```

To get the new swap UUID, open Gparted (System > Administration > Gparted, you might have to install this program) right-click on the swap partition (linux-swap), select "Information" at the bottom and copy the UUID, something like b13a169b-1e7d-4204-a423-66564595fa13 and update the UUID in the fstab file. Perhaps leave the old one, but comment it out with an "#":

```
# the swap partition - updated after upgrade to 9.10 (Karmic Koala)
# UUID=62265758-9845-42e4-a4we-6345i44d595fa13 none            swap    sw              0       0
  UUID=b13a169b-1e7d-4204-a423-66564595ferf33d none            swap    sw              0       0
```

Save, reboot and verify that it no longer says "Swap - 0 bytes (0,0 %) of 0 bytes" under the 'Memory and Swap History'.

---

