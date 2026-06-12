---
title: "Downgrade from 9.10 to 9.04?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by mark92691 on 2009-11-03
Is there a way to do this after completing a 9.04 to 9.10 upgrade?  I do not want to reformat or lose my own data on the HDD.  I don't care about Ubuntu configuration parameters or any other system data.

TIA,

Mark

---

### Post by earthpigg on 2009-11-03
no, there is not.

however, all of your personalized settings (firefox bookmarks, gnome panel customizations, pidgin accounts) are stored in the /home directory.

you could back that up, reinstall 9.04, and restore it on the new install to get your settings back.

ideally, you would have a backup of the 9.04 /home. if you don't, then most of the stuff from the upgraded 9.10 /home will still work, but not all. example: you may keep your pidgin contacts and gnome panel settings, but lose your FF bookmarks.

if you need more help/guidance and/or can't figure out what i am talking about, please let us know.

---

### Post by wilee-nilee on 2009-11-03
Save your bookmarks with the firefox add-on xmarks.

---

### Post by mark92691 on 2009-11-03
I don't care about personalized settings or FF bookmarks.  I have never changed the default GNOME settings and I don't have any pidgin accounts.

I should mention that I am not able to make backups, because I have no drag-and-drop capability, whatsoever (GUI file browsers don't work at all), and I don't know how to do it from Terminal, when all I can "see" from Terminal is the filesystem on the Ubuntu drive.

I just don't want to lose the files that I've created (in Open Office) or downloaded (PDFs).  Can I reinstall 9.04 without having to format the HDD?  If so, how?

TIA,

Mark

---

### Post by dminoz on 2009-11-03
watching for the answer to this one myself. I had 9.04 working just fine, let me go back there...

---

### Post by mark92691 on 2009-11-03
You and me both.  But I had been lulled into a false sense of security by problem-free upgrades since Ubuntu 6.  9.10 has been a real disappointment in that regard.

Mark

---

### Post by ShafterGuy on 2009-11-03
Hello,

You can downgrade it by deleting new headers and modules. Just go in aptitude and remove them, reboot your pc and everything will work normal again. Boot loader will automatically load previous version.

Kind Regards!

---

### Post by FeTTo on 2009-11-03
> **ShafterGuy said:**
> Hello,

You can downgrade it by deleting new headers and modules. Just go in aptitude and remove them, reboot your pc and everything will work normal again. Boot loader will automatically load previous version.

Kind Regards!

can you go into more detail? i was fine with 9.04, upgraded to 9.10 and now i have no start menu on top and bottom of screen, the bottom merged with the top one and they are blank and it takes me like 30 times to reboot before i can accesss the desktop

---

### Post by slakkie on 2009-11-03
> **ShafterGuy said:**
> Hello,

You can downgrade it by deleting new headers and modules. Just go in aptitude and remove them, reboot your pc and everything will work normal again. Boot loader will automatically load previous version.

Kind Regards!

That is only part of the system. Everything else has 9.10 written all over it. There is a document which describes a downgrade, but you void your warranty if you perform this: [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto) 

In other words, you break it, you buy it. You're on your own.

If you want to make a backup of your personal data:

```

cp -rp $HOME /path/to/external/disk

```

Provided /path/to/external/disk is ext3/4. Otherwise you need to do it differently. Be aware of files bigger then 4Gb on FAT filesystems.

Also, this is a reason why most users want to have a seperate slice for /home. Please have a read here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Also, use clonezilla to backup your files PRIOR to upgrading or making changes which could leave your system unusable. The link is clonezilla.org btw.

Best of luck with everything!

---

### Post by wilee-nilee on 2009-11-04
Don't believe that downgrade message the last post is correct. If you notice the person who posted has one bean you have to ask yourself what would motivate somebody to sign up and post a improper procedure which wont do what you want and my cause you to lose that stuff you want to save. Save off your computer on a thumb or external HD and do a fresh install. There may be some ubergeek method but in my 3 years of using Linux I have never seen instructions on how to downgrade.

---

### Post by mark92691 on 2009-11-04
Thanks to the last two posters for the notes of caution.  I was already skeptical that I could downgrade merely by removing a few components.  I'm now trying to figure out how to get a backup of my current user files, and, if I can, I'll then reformat the partition and install 9.04.

On the backup, the problem is that I seem to have no visibility to external drives, or even the other internal drive, which is NTFS and has always been visible until my recent 9.10 troubles.

Also, the box is a dual boot to XP, and I am trying to read the Linux partition from Windoze, but also without any luck so far.  A couple of possible solutions I found on the Net are not working.

Mark

---

### Post by robbiechad on 2009-11-04
Hello, I have had similar problems with 9.10 upgrade, I did have 9.04 working perfectly on my Vaio laptop together with windows vista which I do not like, Ubuntu was my main operating system apart from a couple of things that I found easier to use on Vista, mainly my scanner (Epson3490) and when I wanted to print out some of my digital photos. I do not think Linux is particularly good at doing this. After upgrading to 9.10 I lost my dual boot due to changes in the way the boot system works, I followed instructions to upgrade the boot sequence and ended up with error 15 couldnt boot anything!  I have had to reinstall my Vista and as yet not reinstalled  Ubuntu, I doubt very much I will be using 9.10. Fom what Ive read on here I am not the only one to have problems with "karmic" Is it a case of Linux upgrade ..."oops"

---

### Post by JHCKX on 2009-11-04
I did a downgrade  last night. If you've made a backup of your home directory, you can copy all the files from the backup to your new home directory, then you're (almost) all set. In my case, my old Ubuntu install was in another partition so I could use:

sudo cp -R /media/home/john/.* ~

The R option mean recursive, all folders and subfolders are copied.

The snag is that root is owner of your files and documents. In Nautilis, you could see a lock symbol on the folders I copied. I used

sudo chown -R john /home/john

"john" is the name of my account on my new install as well as the old. Now I was owner of my own files and folders again. After logging out and in again, wireless worked, bookmards were in place, etc.

A bigger problem is getting back your installed packages. I've been unable to find a satisfactory solution on how to do that. A bit of googling will show how to do that with dpgd --get, but that gets everything.

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

I decided I hadn't installed too many programs I wanted to keep. But now I'm struggling with things like Windows networking. I remembered I had to install samba to get that working but I'd forgotten I also needed smbfs. Any trick to get a history of packages selected in synaptic?

---

### Post by nil_orally on 2009-11-04
I am in this with you Mark.

Dual boot system, windows on one disk, Jaunty on the other. Now I can only read the windows disk. The Jaunty disk parameters are read under fdisk, but will not mount.

I will persevere, but all the windows users around me are pointing and laughing. Galling. Pots, kettles and black, but galling nonetheless.

Why do I need to be an uber-geek to write an email from a $1400 machine?

---

### Post by mark92691 on 2009-11-07
slakkie, the target of the copy (cp) command does not have to be ext3/4.  I just cp'ed to an NTFS drive, after mounting it with Palimpsest Disk Utility.  I am following the rest of your advice to the best of my ability.  Thank you.

---

### Post by psonoski on 2009-11-22
I'm the biggest Ubuntu fan, I even wear the shirt proudly, but the last two upgrades have been painful for me.  Really painful.

With the current upgrade 9.04 to 9.10 - several of my nautilus scripts stopped working (parameter passing), Mythtv video editing doesn't work.  Something with the desktop freezes and the icons all disappear.  My screen saver stops responding to keyboard and mice movements - requires a power supply cycling (not good).  Video in Firefox stopped working on my favourite TV site.  

Just to name a few.

Is there a downgrade option please?  I'd actually like to go back to 8.10 (it worked).

Sonoski

---

### Post by Mark Phelps on 2009-11-22
For the umpteenth time -- NO -- there is no "downgrade option"!

There are various schemes you can use, some of them described here, to attempt to save off some of your stuff, install an older version, and then try to restore your stuff -- but there is no general rollback capability.

---

### Post by mark92691 on 2009-11-24
I was able to do the backup, but, instead of downgrading, I wiped my HDD and did a fresh install of 9.10.  Works like a charm.  I suspect that the problem lies in the upgrade process, itself.

Mark

---

### Post by dminoz on 2009-11-24
I'm liking 9.10 now. My sound problems (well, only one problem really -- i.e. no sound at all) fixed itself, either due to me trashing around trying anything I could think of to fix it, or to an update that came down from Update Manager, or a combination of both. Of course, I like to think that I had a hand in it... 

Everything's running perfectly now.

---

### Post by jjavier.santos on 2009-11-24
Is obvious that upgrades should be made for 9.1, but aprox, how long can we wait!
my wireless network is slower, and my performance just drop!

Its really necesary to downgrade or should I wait for the upgrade for some issues?

what you recomend about it?




Ps. sorry about my english.

---

### Post by linuxonbute on 2009-12-05
> **mark92691 said:**
> Is there a way to do this after completing a 9.04 to 9.10 upgrade?  I do not want to reformat or lose my own data on the HDD.  I don't care about Ubuntu configuration parameters or any other system data.

TIA,

Mark

===============================================================
==PLEASE NOTE THAT I CANNOT GUARANTEE THIS WILL WORK FOR YOU.==
===============================================================

In the past, when I have upgraded, I have chosen to manually partition the hard disc.

I think you should be able to do the same if you downgrade.

First I have found out what the current partition sizes are and what is assigned to them. ( eg /   /var   /usr   /home ).
Usually 
cat /etc/fstab | lpr
will print out what is on each partition
and
mount | lpr
will give similar information.If you run gparted you will be able to see the size of each one.
Make a very careful note of of all this information.

When you start the installer choose the option to set up the partitions yourself.
What you will need to do is assign them as you have in your notes
***********************************************************************
>>>>>>>>>>>>>    BUT MAKE SURE YOU TELL IT     <<<<<<<<<<<<<<<<<<<
>>>>>>>>>>>>>         NOT TO FORMAT            <<<<<<<<<<<<<<<<<<<
>>>>>>>>>>>>>  /home and any other partitions  <<<<<<<<<<<<<<<<<<<
>>>>>>>>>>>>>       you want to keep.          <<<<<<<<<<<<<<<<<<<
>>>>>>>>>>>>>     e.g if you have dual boot    <<<<<<<<<<<<<<<<<<<
>>>>>>>>>>>>>          with WINDOWS.           <<<<<<<<<<<<<<<<<<<
***********************************************************************

Then do the rest of the install normally.

If you have told it to format /   /var   /usr  and so on then all you
settings will be ok and you will have the files you need.

The only things you need to be aware of are if you have a local website on the machine and / or a mysql database you will need to back them up BEFORE starting the install.
I usually create a directories ( www  and database ) on my home partition and use 
sudo cp -p /var/www/* home/myuser/web
and
sudo cp -p /var/lib/mysql/* home/myuser/database

If you have more than 1 ordinary user then you 
MUST make sure you create the 
SAME USERS IN THE SAME ORDER 
as you previously created them.

Once you have finished and re-boot all should be well.

This should also work if you change to for example Mandriva or Suse except
that they may might assign different UIDs so in that case what I would do, if there is room on your /home partition, is rename all the users to 
.user
for example if your user is called john he will have a directory
/home/john
as root do
sudo mv /home/john /home/.john
then when you do the install he will be a hidden user.
Once you are up and running find out what the new user.group
the newly created user is then do 
sudo mv /home/newuser /home/.newuser
sudo chown -R user.group /home/.john
sudo mv /home/.john /home/john
reboot and you should have everything back.

If anyone has any thoughts on this then please let me know.
Thanks.

---

