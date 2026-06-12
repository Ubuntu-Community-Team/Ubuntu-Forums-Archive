---
title: "Trying to Dual Boot, using two HD's"
date: 2006-01-24
forum: Installation &amp; Upgrades
---

### Post by stilmatik on 2006-01-24
Greetings,

I am a first time Linux user, trying to broaden my horizons. I just wanted to get some things straight. I just recently got another harddrive from a friend that I want to load Ubuntu onto. Are there any bootloader programs out there that will allow me to select whether I boot from my primary master (running XP) or slave (to be running Ubuntu)? Or will I have to select this from the BIOS anytime I want to change. Also, do the installation instructions for installing Ubuntu change since it is being installed on its own harddrive, without the presence of another OS on the same drive? Thanks in advance for you help. I can provide any information nessecary.

---

### Post by alamba on 2006-01-24
Run a search for dual boot: ubuntu and XP and u'll get a number of threads outlining how to do this.

Akshay

---

### Post by kokiri on 2006-01-24
Grub (the bootloader for ubuntu) will be able to boot between the two drives without a problem. You won't need to go into the bios for anything. The only thing that really changes, since you have mentioned your drive setup, is that you will be installing ubuntu onto /dev/hdb rather than /dev/hda.  hda is the master on the first ide bus, hdb is the slave on the same bus. hdc would be the master device on the second ide bus (ie. your cdrom drive probably) and hdd would be the slave on the second ide bus. For grub to boot windows or ubuntu you will need to install grub on the master boot record of hda. Then you should be off to the races with a dual boot system.

---

### Post by stilmatik on 2006-01-24
Thanks for the prompt replies.

kokiri: I am assuming that the process to install grub on hda is straightforward, and is part of the intial installation of ubuntu? Will I need to install this bootloader first?

---

### Post by alamba on 2006-01-24
Just boot with the ubuntu install CD and during the installation process it'll install grub and even ask you for the boot preferences.

Akshay

---

### Post by lha on 2006-01-24
Hi stilmatik!

As you have the luxury of two hd's, I recommend you to use your new hd as primary master and make the old drive slave. (Secondary master/slave will also do fine.) Install Ubuntu on this new drive. Grub will be automatically installed with Ubuntu. If you are unsure, you can plug out old drive, put in new drive and install Ubuntu. This prevents you from wrecking your current Windows. When Ubuntu is ready to go, plug in old hd. Edit /boot/grub/menu.lst to have

```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

in the end. Now you are able to dual boot without bios-hassle.

Compared to making new drive primary master and installing grub to old drive this method has following

Pros: 
1) Safe to your current files and Windows.
2) If you want to ditch Windows or Ubuntu, you can remove the other disk and make the one you want to keep master. Nothing else has to be done to get a working system. (Grub's menu would have Windows entry but it wont cause troubles and it's easy to remove.)
3) If other system gets corrupted, the other will remain bootable. If you install grub to Windows hd's mbr, you cannot remove Ubuntu without having to fix mbr AND if you want to get rid of Windows, you may have to reinstall grub. (Not a big deal, but still an extra effort.)
4) Every other good reason I didn't remember to write above.

Cons:
1) Does there always have to be something negative?

---

### Post by stilmatik on 2006-01-25
lha, thanks!

Since I am a linux newb, I have a question. After I install Ubuntu on its own like you describe in the first few paragraphs, all I have to do is double click on that file and edit as you said?

also, you say:

> Grub's menu would have Windows entry but it wont cause troubles and it's easy to remove.

Can you describe this procedure? I am a college student, so I will be doing this over the weekend. If I have too much trouble, I go straight back to Windows and finish the semester, then worry about this when I dont need my PC as much.

---

### Post by lha on 2006-01-25
[QUOTE=stilmatik]lha, thanks!

Since I am a linux newb, I have a question. After I install Ubuntu on its own like you describe in the first few paragraphs, all I have to do is double click on that file and edit as you said?[/QUOTE]

No. Menu.lst is owned by root and other users aren't allowed to write to it. You'll need to open terminal (Applications->Accessories->Terminal) and type (or copy&paste) in these commands:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

```
First command takes you to the correct directory, second makes a backup of menu.lst and third opens it in Text Editor. Then copy&paste those lines to the very end of that file. (That "sudo" part gives you root user rights so you can edit menu.lst.)

[QUOTE=lha]2) If you want to ditch Windows or Ubuntu, you can remove the other disk and make the one you want to keep master. Nothing else has to be done to get a working system. (Grub's menu would have Windows entry but it wont cause troubles and it's easy to remove.)[/QUOTE]

[QUOTE=stilmatik]Can you describe this procedure? I am a college student, so I will be doing this over the weekend. If I have too much trouble, I go straight back to Windows and finish the semester, then worry about this when I dont need my PC as much.[/QUOTE]

Oops, didn't make myself clear enough. These are instructions what to do if you want to get rid of Windows or Ubuntu for good.

If you want to uninstall Ubuntu, you can make Windows drive primary master and reformat or unplug Ubuntu drive. That's it.

If you want to remove Windows, then you can remove Windows drive or format it. Then open menu.lst with
```
sudo gedit /boot/grub/menu.lst
```
and remove these lines:
```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by JimmyJames on 2006-01-29
Thanks Iha, great post.

I did the same thing you described, but ran into one problem.  I have a HP Pavillion (sigh), and when I tried to boot to XP the system recovery started up.  Not what I wanted.

If you have a HP that has system recovery on it (I'm not sure which models do), you'll want to modify menu.lst file in the following way:

title Windows XP
root (hd1,1)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

The only difference here is the second line.  HP puts the system recovery on (hd1,0), so if use that it will go straight to recovery.  It will roll your XP system back to the way it was straight out of the factory.  If you're not sure if your HP has this setup, you can try doing it exactly as Iha said, but if you see the system recovery start up, quickly turn your machine off and change the menu.lst file as above.  That should fix the problem.

---

### Post by MS_Prisoner on 2006-10-28
> **lha said:**
> Hi stilmatik!

As you have the luxury of two hd's, I recommend you to use your new hd as primary master and make the old drive slave. (Secondary master/slave will also do fine.) Install Ubuntu on this new drive. Grub will be automatically installed with Ubuntu. If you are unsure, you can plug out old drive, put in new drive and install Ubuntu. This prevents you from wrecking your current Windows. When Ubuntu is ready to go, plug in old hd. Edit /boot/grub/menu.lst to have

```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

in the end. Now you are able to dual boot without bios-hassle.

Compared to making new drive primary master and installing grub to old drive this method has following

Pros: 
1) Safe to your current files and Windows.
2) If you want to ditch Windows or Ubuntu, you can remove the other disk and make the one you want to keep master. Nothing else has to be done to get a working system. (Grub's menu would have Windows entry but it wont cause troubles and it's easy to remove.)
3) If other system gets corrupted, the other will remain bootable. If you install grub to Windows hd's mbr, you cannot remove Ubuntu without having to fix mbr AND if you want to get rid of Windows, you may have to reinstall grub. (Not a big deal, but still an extra effort.)
4) Every other good reason I didn't remember to write above.

Cons:
1) Does there always have to be something negative?

Linux noob here. I have a question.  I want to dual boot using the "unpluging the Windows HD" method. :mrgreen:  I have two HDs.  The master is currently Windows XP and the slave is a storage drive (music, pictures, files...etc.).

So are you saying that I should unplug the master (Windows) and make the slave (storage) the NEW master by changing the HD jumper pins to master.  Once I have the new master, then I can install Ubuntu (Dapper, currently more stable IMO).  The installation should be a normal one...as if I have only one OS in the system.

Now, after Ubuntu is installed, I update the menu.lst in Ubuntu.

My question: ](*,) 
- When I reinstall the old master (contain Windows), do I make the current master (storage drive) become the slave again?  Thus, making the old master (Windows) the current master. :confused: 

Thank you for your time. 8)

---

### Post by lha on 2006-10-28
> **MS_Prisoner said:**
> 
- When I reinstall the old master (contain Windows), do I make the current master (storage drive) become the slave again?  Thus, making the old master (Windows) the current master. :confused: 

Thank you for your time. 8)

Yes, you should make Windows drive master before you reinstall Windows.

---

### Post by theplatypus on 2006-10-28
Instead of setting the jumpers to master/slave you could set both drives to cable select. At least thatis what I did and it has been working perfectly for a few years.

---

### Post by Handssolow on 2006-10-28
Thanks Iha from me too.

My wife's XP desktop has a second empty HD but I've formatted it to ntfs. My aim is to move her over to using Ubuntu but still able to use XP. 

Is there any problem installing Ubuntu over ntfs? Does Ubuntu just change the HD over to fat32? 

In the past I've ghosted XP copies onto her second HDs which came in very useful when HDs have failed. Instead would we be able to dual boot into Ubuntu and backup XP data, Outlook Express emails etc from the slave XP HD? 

If I had to do a fresh install of XP on a new HD, from Windows could I access  the previously saved windows data now on the Ubuntu slave HD?

Or are there any other suggestions to protect data loss?

---

### Post by MS_Prisoner on 2006-10-28
Thanks for the reply guys.

> **theplatypus said:**
> Instead of setting the jumpers to master/slave you could set both drives to cable select. At least thatis what I did and it has been working perfectly for a few years.

This leads me to another question, how do I know my system supports the cable select?  I hear old PCs don't.  I have a Dimension 4400...I think it's about 4yrs old now.  Thanks!

---

### Post by gn2 on 2006-10-28
Here is one way, nice and simple: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by cage cat donnie on 2006-10-28
I put a switch on the front of my computer in an unused bay, and it determines which hard drive is the master and which is the slave.  I love it.   You can boot to whichever you want, but don't switch it while the computer is on!!  

[http://www.dvhardware.net/modules.php?name=Sections&sop=viewarticle&artid=4](http://www.dvhardware.net/modules.php?name=Sections&sop=viewarticle&artid=4)

---

### Post by gn2 on 2006-10-28
**Cage Cat Donnie:** Brilliant solution, but scary stuff! What if you accidentally catch the switch with something or accidentally nudge it?

I would suggest using a key lock switch and having the key out when in use.

Hang the key on a string away from the PC maybe beside the wall socket...

Use the safety technique used for moving light aircraft on the ground.
When you get the tow bar to move a plane, you do not let go of the tow bar till it's back on the rack in the hangar where you got it from.
Thus preventing flying off with it hanging from the nose wheel and potentially jamming the wheel retraction mechanism.

A similar approach would be to never pick up the key till you have confirmed PC fully powered off at the wall, and do not let go of the key till it's back hanging on it's hook.

I work as a Railway Signalman, so safe systems are my thing...;)

---

### Post by MS_Prisoner on 2006-10-28
> **MS_Prisoner said:**
> Thanks for the reply guys.



This leads me to another question, how do I know my system supports the cable select?  I hear old PCs don't.  I have a Dimension 4400...I think it's about 4yrs old now.  Thanks!

I found that Dell Dimension 4400 supports cable select.  I'm going to keep this as simple possible (e.g. without switches or going into the BIOS).  Here are the steps I plan to take:

- Unplug my current Windows XP drive
- Plug my 2nd drive as "master"
- Install Ubuntu (as if there is only one drive...and there is!)
- Update the menu.lst as mentioned on previous posts (remapping the drives when Windows XP is booted)
- Reinstall the Windows XP drive as "slave"
  - Ubuntu drive will still be "master"

I'm hoping for this to work. :mrgreen:

---

### Post by cage cat donnie on 2006-10-28
GN2,

In your line of work, ya don't want switches getting flipped by accident, lol.  It might spoil someones day.

I did use a flat switch, at least.  The kind from the back of a computer that changes voltage.  It's not foolproof, but it is actually pretty hard to flip it by accident.  It's the "second" computer, too.  Not that I want it wrecked, but it wouldn't be the end of the world if it did.

When I was a kid, I used to dream of working on a railroad.  I especially liked steam trains.  I used to live near Steamtown, VT and my dad and I would go a lot.  Good times!!

---

### Post by Ichido on 2006-10-30
> **Handssolow said:**
> Thanks Iha from me too.

My wife's XP desktop has a second empty HD but I've formatted it to ntfs. My aim is to move her over to using Ubuntu but still able to use XP. 

Is there any problem installing Ubuntu over ntfs? Does Ubuntu just change the HD over to fat32? 

In the past I've ghosted XP copies onto her second HDs which came in very useful when HDs have failed. Instead would we be able to dual boot into Ubuntu and backup XP data, Outlook Express emails etc from the slave XP HD? 

If I had to do a fresh install of XP on a new HD, from Windows could I access  the previously saved windows data now on the Ubuntu slave HD?

Or are there any other suggestions to protect data loss?

I Booted with a KNOPPIX disk, then FORMATTED my 2nd Drive to "ext2".
Then I booted with Ubuntu Install Disk and Installed it onto my 2nd Drive, unstalling GRUB for my Boot Loader and it works Great.
You might make a Linux=Swap Drive of 500MB to 1GB.
Ubuntu/Kubuntu needs 8-15GBs of space, or more, for O.S., programs and documents.
I also have a Laptop (Dell c-600), with a 20GB drive.
I partitiond my WinXP (hda1) down to 10GB, AFTER I Defraged.
The 2nd Partition (hda2), is the remainder of the Drive.
This also uses GRUB with no problems.
Good Luck.

---

### Post by badguyanil on 2006-10-31
ok guys i am a bit confused. this is wht i did can u tell me how and why is it not working.

I have 2 hdd's 20 GB and 40 GB. 
1.40 GB has Win XP and Win 98 installed and was the master drive.
2.I disconnected this drive. Connected 20 GB as Master(Hdd jumper settings) and installed Ubuntu(6.10)...smooth!
3. Conencted back windows drive (40 GB) as slave(HDD jumper setting).

now i can boot from either of the HDD by connecting and disconnecting the power cable and and checking thru bios once!

4.With both the HDD's connected (Ubuntu master, Win (XP + 98) Slave), if i try to boot it boots up ubuntu! Well that is wht it shld do.

5. In grub menu.lst i made the entries...

    title Windows
    .
    .
    chainloader +1
just above the entiers of Ubuntu...

_Now the Problem :_... when i boot up i get the menu asking me to choose between Windows and Ubuntu. But when i select Windows..i get the error "Error : Unrecognised Device String". What shld i do??????

I want to keep ubuntu as master!..Please help!

---

### Post by badguyanil on 2006-10-31
Any suggestions on the above post???

---

### Post by Ichido on 2006-11-01
Okay. here's what I did:

First, I have both my HD Connected!
  Windoze on the First HD and my Second HD was new, so I BOOTED a Knoppix.iso CD and ran the QtParted program to Format my new Drive (hdb) as "ext2".
NOTE: I have found that I like the KNOPPIX version of QtParted better than others I have used.
NOTE: Some say that you need a "Linux-Swap" Partition of 500MB to 1GB on the same drive that you install Linux..

Next, I shut down the Knoppix.iso, removed the CD and Booted (AGAIN From my CD/DVD Drive) This Time using my Ubuntu/Kubuntu.iso CD.

When the Ubuntu Options screen came up, I chose "Install".
Then I chose my Second HD, hdb, and installed Kubuntu there!
when it asked to "Re-write" my MBR, I said OK.

After the Install, GRUB Automatically Found Kubuntu as the First Boot Option and Windoze as the Second Boot Option!

Now when I start my PC, I get...

Loading Grub...
Then it displys a list of my two O.S.s and a Choice as to which one I want to boot to.

I do NOT have to 'Plug-in' or 'Un-plug' any Drives.
It's all Software (GRUB) now!  :-)

Hope this helps.

---

### Post by Ichido on 2006-11-03
Check out this link.
[http://ubuntuforums.org/showthread.php?t=120994&highlight=stilmatik](http://ubuntuforums.org/showthread.php?t=120994&highlight=stilmatik)

---

### Post by AceRimmer on 2006-11-04
Excellent guide!  Now I have Edgy running on a 120GB master, and my old XP Pro install on a 120GB drive in the slave position, both are in cable select mode.  

Now my question is, I have my NTFS drive mounting in Edgy so I can access it, how do I access the linux drive from XP?

---

### Post by MS_Prisoner on 2006-11-04
> **lha said:**
> Hi stilmatik!

As you have the luxury of two hd's, I recommend you to use your new hd as primary master and make the old drive slave. (Secondary master/slave will also do fine.) Install Ubuntu on this new drive. Grub will be automatically installed with Ubuntu. If you are unsure, you can plug out old drive, put in new drive and install Ubuntu. This prevents you from wrecking your current Windows. When Ubuntu is ready to go, plug in old hd. Edit /boot/grub/menu.lst to have

```
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

in the end. Now you are able to dual boot without bios-hassle.

Compared to making new drive primary master and installing grub to old drive this method has following

Pros: 
1) Safe to your current files and Windows.
2) If you want to ditch Windows or Ubuntu, you can remove the other disk and make the one you want to keep master. Nothing else has to be done to get a working system. (Grub's menu would have Windows entry but it wont cause troubles and it's easy to remove.)
3) If other system gets corrupted, the other will remain bootable. If you install grub to Windows hd's mbr, you cannot remove Ubuntu without having to fix mbr AND if you want to get rid of Windows, you may have to reinstall grub. (Not a big deal, but still an extra effort.)
4) Every other good reason I didn't remember to write above.

Cons:
1) Does there always have to be something negative?

Hello folks.  I finally installed Dapper and I like it!  Anyway, if you've been following this thread, I am attempting to dual boot with Windows XP as described in the above quote.  I have another question:

I updated the menu.lst with what was mentioned above and I'm about to reinstall the Windows XP drive as the master and the Ubuntu drive as the slave.  When that is done and I will boot up the system...question: how does the PC system know about the menu.lst? ](*,)   I mean, is the point of the menu.lst to give me an option to boot with Windows XP or Ubuntu Dapper? :-k  Should I update my bios boot priority to first read the Ubuntu slave drive so it can access the menu.lst file? :confused: 

Well, if the PC system reads the master drive (Windows XP) first, isn't it going to automatically boot up Windows XP without giving me the option to select between XP and Dapper?  :???:

Thanks for any info.

---

### Post by MS_Prisoner on 2006-11-05
> **MS_Prisoner said:**
> Hello folks.  I finally installed Dapper and I like it!  Anyway, if you've been following this thread, I am attempting to dual boot with Windows XP as described in the above quote.  I have another question:

I updated the menu.lst with what was mentioned above and I'm about to reinstall the Windows XP drive as the master and the Ubuntu drive as the slave.  When that is done and I will boot up the system...question: how does the PC system know about the menu.lst? ](*,)   I mean, is the point of the menu.lst to give me an option to boot with Windows XP or Ubuntu Dapper? :-k  Should I update my bios boot priority to first read the Ubuntu slave drive so it can access the menu.lst file? :confused: 

Well, if the PC system reads the master drive (Windows XP) first, isn't it going to automatically boot up Windows XP without giving me the option to select between XP and Dapper?  :???:

Thanks for any info.

Ahh.  I figured out the solution...it's simple once you know it.  Windows XP drive is on slave and Ubuntu drive is on master.  Both are cable select mode. The system will read the Ubuntu drive first...which has the menu.lst!

Aside from the hard drive swap option in menu.lst, I updated the TIMEOUT to 20 seconds, hiddenmenu is commented out, uncommented colors.  Anyway here's my setup:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.15-26-386
#boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

## MY ADDED SCRIPT
## Used to dual boot with Windows XP
title Microsoft Windows XP [Operating System that you know]
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

## End of Windows XP option

```

One thing that I wasn't sure about is that the Ubuntu boot options are written in the menu.lst twice...so I commented out the last two.  Here's the code:

```
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.15-26-386
#boot
```

I'm hoping it's ok to comment out.  It just doesn't make sense to write it out twice.  Does anyone know why this is?

Anyway, thanks for all your help y'all.

---

### Post by lha on 2006-11-05
> **MS_Prisoner said:**
> Ahh.  I figured out the solution...it's simple once you know it.  Windows XP drive is on slave and Ubuntu drive is on master.  Both are cable select mode. The system will read the Ubuntu drive first...which has the menu.lst!

Aside from the hard drive swap option in menu.lst, I updated the TIMEOUT to 20 seconds, hiddenmenu is commented out, uncommented colors.  Anyway here's my setup:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.15-26-386
#boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

## MY ADDED SCRIPT
## Used to dual boot with Windows XP
title Microsoft Windows XP [Operating System that you know]
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

## End of Windows XP option

```

One thing that I wasn't sure about is that the Ubuntu boot options are written in the menu.lst twice...so I commented out the last two.  Here's the code:

```
title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
#root		(hd0,0)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
#initrd		/boot/initrd.img-2.6.15-26-386
#boot
```

I'm hoping it's ok to comment out.  It just doesn't make sense to write it out twice.  Does anyone know why this is?

Anyway, thanks for all your help y'all.

You have two Ubuntus listed because you have two versions of kernel installed, 2.6.15-**27**-386 and 2.6.15-**26**-386. When a new kernel is installed, the old one will still be available, just in case the new kernel won't work for you properly. So if you are certain your new kernel won't give you any trouble, you could even uninstall it. Commenting it out is also ok. You can boot it from grub even if it is not listed as long as you know the version number.

If you aren't low on disk space, you can change line "# howmany=all" to "# howmany=2" or even "# howmany=1" to show only two or one lastest kernel(s), respectively, and not worry about editing menu.lst or uninstalling unneeded kernels after every kernel upgrade.

---

