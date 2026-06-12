---
title: "Sharing a USB stick formatted as ext2 between two different Linux boxes"
date: 2008-08-21
forum: Hardware
---

### Post by sickpuppet on 2008-08-21
Hi - 

I just picked up a new 2Gb USB stick (€7.50 in Aldi) and formatted it as ext2 for the heck of it. I normally use FAT32 on USB sticks for best cross-platform interoperability, but seeing as I use Linux exclusively at work and at home, I decided to switch to ext2.

On my Hardy Heron laptop, I used 'parted' (running as sudo, as required) to remove the existing partition and replace it with a new primary partition formatted as ext2. I umounted and remounted, only to discover that the USB stick would only (auto)mount as root, so I chown'ed /media/stick to my normal user and group. Umount and mount again, everything shows up with the expected permissions. I copied some files onto the stick and took it to work.

In work (on my Fedora 8 box) I inserted the USB stick and it automounted successfully.

However, looking at the permissions, I see that the files and directories on the stick have the UID and GID of my Ubuntu user (1000:1000, as it happens.) My UID:GID on my work Fedora box are 500:500.

Who can tell me a non-hacky way to get the USB drive to automount with the correct permissions - eg, those of the user who's currently logged in at the console?

Best Regards
SP

---

### Post by forger on 2008-08-21
Might be simple as asking the administrator at your workplace to change your UID/GID to 1000? :) or change your ubuntu UID/GID to 500

for your ubuntu desktop at home:
```
usermod -u 500 -g 500 $USER
groupmod -g 500 $USER
```
or if it doesn't work, try in superuser mode:
```
sudo usermod -u 500 -g 500 $USER
sudo groupmod -g 500 $USER
```
log out and log in again (or preferrably reboot the machine)

(never tested it, **[COLOR="Red"]could break stuff[/COLOR]**!)

It should work :)

---

### Post by silkstone on 2008-08-21
I hope that forger's suggestion works for you, but there may still be file permission issues with files created on the different machines. Maybe this is a situation where FAT32 is the best option, as you don't run into these problems and can also use the stick to copy files to a Windows machine if you ever wish to.

---

### Post by forger on 2008-08-21
true silkstone, fat32 partition doesn't handle/have file permissions (i think), which might be the best alternative way to use :)

---

### Post by sickpuppet on 2008-08-21
Hi guys - 

Thank you for your very prompt feedback. Forger's suggestion to change my user and group IDs on one of the machines makes the most sense. I'll give that a go tonight.

However I think this issue highlights one of the deep problems with Linux: since its origination in 1991, the various distros haven't been able to agree on a simple thing like where to start UID:GID for ordinary users. Fedora picks 500, Ubuntu picks 1000. Most Linux administrators will use the user account which is created first as their day-to-day login - so starting UID:GID from the same point on all distros would make this issue go away. Only secondary users would need their UID:GID changed.

The solution of using FAT32 is a non-starter. I chose ext2 as the file system for the USB stick precisely because I wanted file permissions. (I try to imagine a world in which operating systems using FAT32 don't exist.)

Thanks very much to all of your for your rapid yet considered responses.

regards
SP

---

### Post by forger on 2008-08-21
I didn't know until now that file permissions are saved using user and group ID numbers instead of owner and group name.
I see it as an extra layer of security, and since you want permissions, you want security. It's a one-time change per computer (and per user you want to use the usb flash disk) anyway :)
By the way, just curious: why are you using ext2 and not ext3? Journaling that ext3 has would be a nice addition for the usb flash disk

---

### Post by eldragon on 2008-08-21
having ext2 on a usb stick doesnt add any security at all.

the permissions can be changed with no problem using a livecd and sudo chmodding the entire drive.

a better approach should be to standarize a guest user/group to which every user in the system has r/w access to, and make all removable media default to write as those.

as an extra security, guest user/group files should not be allowed to be +x

just a thought, anyone care to brainstorm it?

---

### Post by sickpuppet on 2008-08-21
> **forger said:**
> I didn't know until now that file permissions are saved using user and group ID numbers instead of owner and group name.
I see it as an extra layer of security, and since you want permissions, you want security. It's a one-time change per computer (and per user you want to use the usb flash disk) anyway :)
By the way, just curious: why are you using ext2 and not ext3? Journaling that ext3 has would be a nice addition for the usb flash disk

Hi forger - take a look in [FONT="Courier New"]/etc/passwd[/FONT] - that's where your human readable login name is mapped onto your UID. Same for [FONT="Courier New"]/etc/group[/FONT].

Each user has a unique UID, so for example user 'tedpuppet' with UID 1001 sharing my machine couldn't access my files on the USB stick.

I chose ext2 because parted doesn't offer ext3 as an option!

regards
SP

---

### Post by sickpuppet on 2008-08-21
Hi eldragon - 

> **eldragon said:**
> having ext2 on a usb stick doesnt add any security at all.

the permissions can be changed with no problem using a livecd and sudo chmodding the entire drive.


The same is true for any Linux filesystem, whether it's on a USB stick or an internal drive. Are you saying the Linux file permissions security model is worthless?

Actually I wasn't looking for security at all, just playing with my new USB stick and wondering how Linux would behave if it was formatted as ext2. The whole point of USB sticks is that they move between machines.

> **eldragon said:**
> 
a better approach should be to standarize a guest user/group to which every user in the system has r/w access to, and make all removable media default to write as those.


Now you're talking! How do I configure the automounter to behave as you describe, assuming a guest:guest login and group already exist?

> **eldragon said:**
> 
as an extra security, guest user/group files should not be allowed to be +x

just a thought, anyone care to brainstorm it?

That's configured with a custom umask, right?

regards
SP

---

### Post by forger on 2008-08-21
> **sickpuppet said:**
> that's where your human readable login name is mapped onto your UID

Thanks but I knew that one, what I didn't know was that the numbers (UID/GID) are the ones that are assigned with the files :)

> **sickpuppet said:**
> 
I chose ext2 because parted doesn't offer ext3 as an option!


How about gparted? (Gnome partition editor)
```
sudo apt-get install gparted
```
and menu System > Administration > Partition Editor

There's also the *mkfs.ext3* command (which I never tried :( )

---

### Post by forger on 2008-08-21
> **sickpuppet said:**
> Hi eldragon - 
Now you're talking! How do I configure the automounter to behave as you describe, assuming a guest:guest login and group already exist?


I think he meant to standardize it to all distributions, so that removable media could be detected just like fat32 and that allows r/w access without the executable bit.

I suppose it's possible, though you have to set it up for each machine, you make a group with the same GID for all:
```
sudo groupadd -g 3000 removable
```
then you add yourself to the group:
```
sudo adduser $USER removable
```
(I think you have to log out and log back in for it to take effect)

And when you create files you make sure the group is removable:
```
sudo chown -R $USER:removable /path/to/usb
```
and of course modify the permissions to allow user/group rw
```
sudo chmod -R 660 /path/to/usb
```
(this gives read/write access for user and group, but not for other people)

If anyone adds it in [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) I'll add my support :)

---

### Post by sickpuppet on 2008-08-21
> **forger said:**
> Thanks but I knew that one, what I didn't know was that the numbers (UID/GID) are the ones that are assigned with the files :)


Sorry dude, didn't mean to patronise! :) Check out [FONT="Courier New"]ls -n[/FONT].

> **forger said:**
> 
How about gparted? (Gnome partition editor)
```
sudo apt-get install gparted
```
and menu System > Administration > Partition Editor

There's also the *mkfs.ext3* command (which I never tried :( )

Yes, I've used both of those. (The [GParted Live CD]("http://gparted.sourceforge.net/livecd.php") is an amazingly slick utility for dual-booters.) I just used parted because that was handy and is was easier to use than old fdisk.

Like I say, this was really just an experiment in the feasibility of using a USB stick formatted with a Linux fs for day-to-day tasks. I hate to say it, but unlike Windows or Mac, it doesn't "just work". Mostly, thanks to Ubuntu, Linux *does* "just work".

Remember also that if I just transfer the stick between my Ubuntu 8.04 laptop and Ubuntu 8.04 desktop, I wouldn't have run into this problem. It's only when I introduced another distro that things got a bit more complicated.

---

### Post by sickpuppet on 2008-08-21
> **forger said:**
> 
I suppose it's possible, though you have to set it up for each machine, you make a group with the same GID for all

Hi forger, thanks for that. Most interesting. I'll try it out!

regards
SP

---

### Post by sickpuppet on 2008-08-21
> **forger said:**
> 
If anyone adds it in [http://brainstorm.ubuntu.com](http://brainstorm.ubuntu.com) I'll add my support :)

We'd have to phrase it properly for that forum... what would you suggest?

regards
SP

---

### Post by forger on 2008-08-21
I know the subject:
Standardize a group for removable media

It should specify that we need it to *magically*:
- give read/write access permissions for the group (660)
- disable the executable bit by default (-x) on each mount
:)

The problem is that this should be done virtually somehow, at least for the execution bit, not to change the permissions (yeah, pretty confusing :P)

---

### Post by eldragon on 2008-08-21
> **sickpuppet said:**
> Hi eldragon - 



The same is true for any Linux filesystem, whether it's on a USB stick or an internal drive. Are you saying the Linux file permissions security model is worthless?

SP

actually, within a running system, filesystem rights are what makes linux quite secure.

of course having physical access to the system defeats the purpose, but the whole point of usb sticks is to be able to share within different ecosystems. ext2/3 isnt meant to do that. 

how to set what i said up is beyond my skills. and anyway, if there is no standard guest UID/GID within the linux world, doing it in 1 computer wont help at all. thats why i proposed a brainstorm idea. so that it MIGHT make it to an official release...

---

