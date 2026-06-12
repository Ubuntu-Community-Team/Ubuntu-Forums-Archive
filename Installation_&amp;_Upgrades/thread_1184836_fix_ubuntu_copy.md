---
title: "fix ubuntu copy"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by martiendejong on 2009-06-11
Hello all,

When trying to make multiboot, I accidentally deleted my Ubuntu partition. 
I have a backup though. 
It is on another partition.
I made it by using 'cp / backup'.
Now I copied that folder to my 2nd partition (was on first).
I guess cp does not copy every file so some files are missing?
I think I should also change some config file settings?

The error I get is something like 'KERNEL PANIC! Unmountable partition' and then some more. (I will look it up)

What is the shortest path to getting my Ubuntu running again?

Best regards,
Martien

---

### Post by coffeecat on 2009-06-11
It is possible to backup and restore a Linux root partition with the cp command (I've done it), but 'cp / backup' isn't going to work. You need some options to ensure you do a complete recursive copy **and** preserve permissions. And if you copied from within an installation, as it were, that isn't going to work at all. You have to mount the partition you want to backup from another Linux partition or live CD and then do something like:

```
sudo cp -a /path/to/mounted/partition/* /path/to/backup/medium/
```Anyway....

> **martiendejong said:**
> so some files are missing?

<snip>

The error I get is something like 'KERNEL PANIC! Unmountable partition' and then some more. (I will look it up)

What is the shortest path to getting my Ubuntu running again?

Your shortest path is to reinstall. Sorry.
[B]
[/B]By the way - welcome to the forum.

---

### Post by martiendejong on 2009-06-11
Hi,

Thanks for replying. I have copied everything back to the root of a new partition, but it is a different one from the one I had. (used to be /dev/sda2 now /dev/sda3) and I think the errors are because some config files are pointing to that first partition.

The error I am getting is this one:
VFS: cannot open root device on dev/sda2 or unknown block(0,0)
Please append valid root path option. Availabe partitions:
Kernel panic - not syncing: VFS: unable to mount root fs on (0,0)

What I did was cp -R <backupfolder> /dev/sda3/. to copy everything back to that sda3 partition. So I have the same filestructure as I had before.

I reinstalled grub and that is working now. My other partition (LastXP) is also running.
But I need this specific installation of Ubuntu because it would save me a lot of time reinstalling everything.

Please, is there no way to get it running again?

---

### Post by coffeecat on 2009-06-11
You need to edit /boot/grub/menu.lst and /etc/fstab after backing up and restoring a partition. Ubuntu uses UUIDs instead of device references such as /dev/sda2 in both those config files. The UUIDs will have changed so the easiest way would be to replace **all** UUIDs with /dev/whatever. You can do this from the live CD.

If you need any help, post back with the contents of both those files and the terminal output of:

```
sudo fdisk -l
```and someone will be able to help you. I shall be logging off soon as it's late here, but I'll check this thread in the morning.

That might work, so good luck. But since you didn't use the -p option with cp (which preserves permissions and timestamps) you may still run into big problems even with menu.lst and fstab properly edited. Let's hope not.

**Edit:** there's also a minor complication in menu.lst in that with a UUID, a default Ubuntu one doesn't use the root command. In order to get you going, here's my Jaunty stanza with a root partition on sda6:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        84cf2316-1aa8-4ceb-b425-f8b446d9eae8
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=84cf2316-1aa8-4ceb-b425-f8b446d9eae8 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```If I needed to do what you're about to do, it would have to be changed to:

```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        (hd0,5)
kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet
```

For yours, sda3 would be (hd0,2) and /dev/sda3 .

---

### Post by martiendejong on 2009-06-11
Hi,

I have the menu.lst as you say. I have multiboot working now, but when I try to start the ubuntu it wont log me in because it cannot write to the disk.

The error:
Users' $HOME/.dmrc file is being ignored

And later:
GDM could not write to your authorization file.

I can get to the files from commandline, but not in ubuntu-desktop.

I have the idea that some configuration files still have to be changed to sda2.
Any clues?

Best regards and thanks so far,
Martien

---

### Post by coffeecat on 2009-06-12
> **martiendejong said:**
> I have the menu.lst as you say. I have multiboot working now, but when I try to start the ubuntu it wont log me in because it cannot write to the disk.

The error:
Users' $HOME/.dmrc file is being ignored

And later:
GDM could not write to your authorization file.

I can get to the files from commandline, but not in ubuntu-desktop.

Yes, this sounds like the permissions problems I feared. Anyway, when you say you can't log in but you can get to the command line, do you mean that you can log in to a virtual terminal with your ordinary user account? If so, try this:

```
chown -R yourusername: ~
```Obviously, substitute your user name for 'yourusername', and note the : after your username. There will be some error messages - ignore them for now. If you get a permissions denied, or similar, this will be because some or all of your files are now owned by root. If this happens, try:

```
sudo chown -R yourusername: /home/yourusername
```If this works you now need to:

```
chmod 644 ~/.dmrc
chmod 755 ~
```Hopefully, that will allow you to log in graphically, but be warned, I'm swimming in uncharted waters here. I'm not at all sure this will work. Anyway...

> **martiendejong said:**
>  I have the idea that some configuration files still have to be changed to sda2.
Any clues?

The only other configuration file that would need editing is /etc/fstab as I've already mentioned. But the fact that you've got as far as the gdm login screen suggests that you've already attended to this.

---

### Post by martiendejong on 2009-06-12
Thanks a lot for the help so far!
I edited the /etc/fstab file and now the system starts fine until the desktop.
However I still cannot login, (still the same errors).
I am running another Ubuntu installation on a different partition now.
Are the commands for fixing the owner the same?

Oops, I think I have just found the problem. Seems that I have accidentally changed the user of my home folder to 777 (instead of myself)

I try and restart now, I have confidence! :)

Thanks,
Martien

---

### Post by coffeecat on 2009-06-12
> **martiendejong said:**
> Oops, I think I have just found the problem. Seems that I have accidentally changed the user of my home folder to 777 (instead of myself)

But there's a difference between ownership and permissions. Ownership defines the user and group - for this you use the chown command. Permissions defines read, write and execute access for user, group and other. For this you use chmod. If you've chmod'd everything in your home folder to 777, everyone in the known Universe will be able to read, write and execute everything in your home folder. Oops indeed! :wink:

What you need to do is to chown everything to yourusername: . The trailing colon tells the chown command to set the group as the default group for your account. Then you'll need to...

```
chmod -R 660 ~
```

... to set permissions to all your files to user=read/write, group = read/write, other = no access. 640 would also do, giving group read access only. And then you must reset the permissions for the home folder itself and .dmrc (which are different) with...

```
chmod 644 ~/.dmrc
chmod 755 ~ 
```For the home folder, 750 or 700 are acceptable instead of 755.

That may still leave some odd config files in your home folder with suboptimal permissions, but that should get you going again.

---

### Post by martiendejong on 2009-06-12
Hi,  I accidentally changed the permissions for my other partition too, so now I can't boot from both of them anymore.  I started with the live cd now and did the following:  chown -R root /dev/sda2 chown -R root /dev/sda8  I figured I should set it to the root user since both installations do not recognize the current user, whomever it may be.  After that I ran your commands for both installations. So now I am going to reboot again.  I really appreciate your support, originating from a Windows environment I would never have figured this out on my own.  Best regards, Martien

---

### Post by coffeecat on 2009-06-12
> **martiendejong said:**
> I started with the live cd now and did the following:  chown -R root /dev/sda2 chown -R root /dev/sda8  I figured I should set it to the root user since both installations do not recognize the current user, whomever it may be.

If you've changed the ownership of the contents of /home to root, that's a really big mistake. I doubt whether you'll be able to log in at all now. If I'm right, don't despair. Simply post whatever error messages you get and we'll take it from there. We should be able to re-own the home folder from the live CD, but we won't be able to use user and group names. It'll be a little more complicated, but not impossible.

I hope. :|

---

### Post by martiendejong on 2009-06-12
Hi,

The error that I am getting is something still that .dmrc error. 
It says that the session lasted less than 10 seconds and that I should reboot in safe mode. 

I guess I have to change the username back to something else, but when I try my original username (martien) it says that username is not recognized (that was also the case at first, that's why I chose root). 

So, what user should I give ownership of my home folder?

P.S. Can I create a new user by creating a new home folder and .dmrc file? If that is possible it might be a quicker solution.

Thanks,
Martien

---

### Post by coffeecat on 2009-06-12
> **martiendejong said:**
> I guess I have to change the username back to something else, but when I try my original username (martien) it says that username is not recognized (that was also the case at first, that's why I chose root).

OK. Your username not being recognised is new to me. I can't explain that. Perhaps something went adrift in the original cp process. I doubt we're going to be able to repair the martien account in that case. 

> **martiendejong said:**
> P.S. Can I create a new user by creating a new home folder and .dmrc file? If that is possible it might be a quicker solution.

That's a good idea, but don't worry about the .dmrc file. Each account has its own and the .dmrc of a newly created account will be OK. This is what you do. To show you how it's done, I'll call the new account 'jim'. Obviously, sustitute whatever name you choose.

First, boot up in recovery mode (second boot option), and choose 'drop to root shell prompt'. You'll get a prompt with #. This is a root prompt. You have full root powers. Take care. From the # prompt, do:

```
adduser jim
```You'll be prompted (twice) for a password to be created for this account, and then a few other questions, and the account will be created, but we're not finished. You need to give it admin rights. Now do:

```
adduser jim admin
```...and you're done in the root shell. Now:

```
reboot
```... and when you get to the graphical login, log in as jim. But you're still not done. Go to System > Administration > Users and Groups. Click the unlock button and give your (jim) password. Highlight the jim account (now's a good time to see if martien is still there or not), click on properties, and then on the User Privileges tab. You'll find that only the Administer System box is ticked. You need to tick storage devices, printers, system logs, share files, CD-ROM, modems + anything else you want.

However, you'll find that you'll have to set all your personal settings from fresh.

Good luck.

---

### Post by martiendejong on 2009-06-17
Hi,

I tried adding a new user, but I still keep getting this errors. The user also isn't added correctly and I am unable to add it to any groups(because the system is screwed up probably)
It seems realy very hard to get it working again.
I guess I just have to live with it and be happy I still have my data.

Thanks a lot anyway, you have learned me a lot about Ubuntu/Linux in general.
I am building my new installation in a VM now, so that I can undo my own stupidity :p

Best regards,
Martien

---

