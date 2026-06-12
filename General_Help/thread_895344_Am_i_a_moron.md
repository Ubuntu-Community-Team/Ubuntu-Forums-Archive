---
title: "Am i a moron?"
date: 2008-08-20
forum: General Help
---

### Post by pallikhera on 2008-08-20
Guys,i am new to linux,in fact i decided to install Ubuntu for the first time this morning.But this thing called "GRUB" has reduced my age considerably.
What the heck is a .tar file?...its sitting in my xp,how do i make a bootloader.All over internet there are command lines,where do i put these commands..do i have to make GRUB CD from Ubuntu?

Please tell me,otherwise i'll buy a fat "Ubuntu for dummies" book and smack my head open with it.

---

### Post by falcon61102 on 2008-08-20
I think we all know how you feel having been there once ourselves at one point or another.

A .tar file is a compressed file much like a .zip file that you may have seen in Windows.

The GRUB is your bootloader and was more than likely installed already, but depending on your system, may not be active right now.

First, are you running a dual boot system or is Ubuntu installed on another computer than the one you are working on?

Also, do you have a Ubuntu LiveCD (the install disc) handy?  If so, can you get online if you boot from that.  If you can, great we can walk you through the process from within Ubuntu, otherwise you'll have to print out or copy down our commands to run in Ubuntu to get your system going.

---

### Post by pallikhera on 2008-08-20
Thanks Falcon,
I want to dual boot(xp already installed).All partitions are NTFS and i have Ubuntu 8.04 CD.I also have two HDD's for xp and Ubuntu.

I won't waste your time with "live help",i am really SLOOOOOW.I'll copy commands and do all that stuff later but for now please tell me if i should install Ubuntu,go in Ubuntu,download GRUB or can i make a GRUB bootloader from XP?

---

### Post by hyper_ch on 2008-08-20
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by colobix on 2008-08-20
And the thing with commands is a way you make your ubuntu do different stuff like installing things, get admin access to things etc.
That's called Terminal, and you can find it under Applications > Accessories.
That is one way you can install new software on, but u should start with the easy Add/remove program under Applications, and Synaptic Package Manager under the System menu > Administration.
You can use the Terminal to do things like that much faster.
Forexample. If you know you need a software, go to Terminal, write sudo atp-get install PROGRAMNAME.
You will also very soon find out that there are many folders under file system you can't get access to.
Go to Terminal and write gksudo nautilus .
Sometimes you will have to do that when forexample you have to manually install a program.

Good Luck:)

---

### Post by dustman on 2008-08-20
:) this fella' sounds a lot with me when i first installed linux :D.

So, it's kinda easy...there are a lot of tutorials about installing Ubuntu, like this: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) , or this: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) , and the GRUB is that thing that offers you the possibility to boot one operating system or another (in your case Ubuntu or windows). Normally, GRUB will be automatically installed in the end of the installation process.

And btw, welcome to the Ubuntu community!


Cheers!

Radu

---

### Post by falcon61102 on 2008-08-20
Ok, the install is actually very straight forward and will guide you through all the necessary steps.  It will also install the GRUB for you as part of the install, so you really won't have to worry about that.  When you install you are going to need to create some new partitions on which ever HD you decide to install on.  

If I am understanding you correctly, you have two seperate HDs and you wish to use one for each of your operating systems?

For simplicity reasons, you are going to want to have the XP one as the first drive just because windows does not like being second to anything.

Also, when you go through the install you will have the option on how you wish to partition the drive you are installing on.  Most people recommend three partitions.  The first being your filesystem with a mount point of "/" and file type of ex3 and at least 4 gigs in size, perferably as much as 10gig.  The second being your Home partition with a mount point of "/home" and file type of ex3; your Home partition should take up the remainder of you disk except for the space used by the Root filesystem and SWAP partitions.  The third being your SWAP partition; this one should be roughly twice the size of you RAM unless you have a really large amount of RAM (>2gig), you can get by with a 2gig SWAP partition.

Is that pretty understandable or just clear as mud?

---

### Post by pallikhera on 2008-08-20
OK,i got it.3 partitions for Ubuntu.GRUB will install itself.So if i do this will i see both OS's when computer starts or am i getting ahead?

---

### Post by falcon61102 on 2008-08-20
Yes, when the GRUB installs, it should detect the WinXP install.

Do you have two seperate hard drives or was I misunderstanding you?

---

### Post by pallikhera on 2008-08-20
Yes two separate HD's.I'll keep Xp on master and first disk(as you said,XP always wants to be first,:lolflag:)

---

### Post by pallikhera on 2008-08-20
I think i got a little bit of idea,all thanks to you guys,especially Falcon.You sir are an angel of God.May be some day i will help others,lets spread linux.

---

### Post by falcon61102 on 2008-08-20
Exactly.  Ok, when you boot up from the CD, you will be asked to select your languange and then you will be offered a few choices.  I recommend that you first Check CD, which will run a test on the CD to make sure that there are no corrupt portions which could ruin your day during the install.  I believe it will ask for a reboot after that test, but either way, when you get back to the menu, select Install Ubuntu.

It's a fairly straightfoward install that will guide you through setting everything up.  A couple areas you need to really pay attention to are the partitioner and the summary page.

For the partitioner, make sure you select your second disk to install on.  And you can either use the guided which will create the basic partitions for you or you can select manual to create the three individual partitions as I discussed above.  Either way works.  

Once you partition your HD you will be presented with a Summary screen that gives you a chance to review everything.  There will be an Advanced button.  Click that.  The advanced options give you the opportunity to select where you wish to install the GRUB.  There will be a drop down menu with options to select.  I recommend that you install the GRUB to the partition that is going to have your Root Filesystem on it.  That will be you primary Ubuntu parition that you just created and it will be listed in the Summary box if you are unsure of it's name.  It will look something like /dev/sdb1.  Once you select that and continue with the install, it will install the system files.

The way the GRUB works is that it places a very small section of code in you MBR and then the rest of the files are placed in a destination that you choose during the install.  When the computer boots, it reads the MBR and that directs it to the files on your HD which will give you the options to boot both systems.

---

### Post by mb_webguy on 2008-08-20
Ok, if I understand you correctly, you have XP currently installed, and you want to install Ubuntu as well.  You also have two hard drives, one for your XP installation, and one you want to use for Ubuntu, correct?  If there's any data on that second drive, back it up now.  Afterwards, you may want to do a quick format of the drive to FAT32, just to make one small but significant step later on a bit easier.

You also have your Ubuntu LiveCD.  Make sure that the disc is the one you need for your system.  There's a version for 32-bit Intel-based systems, and another for 64-bit AMD and Intel-based processors.  (Even if you have a Dual-Core processor that's capable of 64-bit processing, you may still want to go with the 32-bit installation, unless you plan on doing things like encoding video and compiling programs.) There's also an alternate install CD for each, which has a non-graphical installer you can use if you have a problem with the LiveCD.

So you know where you want to install Ubuntu, and you have the right disk...  The last thing you need is a network cable.  If you have that, then great!  You're ready to install Ubuntu.

Plug in the network cable.  Reboot your computer with the LiveCD in the drive, and at the POST screen (the one with the logo of your computer's manufacturer), press whatever key you need to open the boot menu so you can boot from the CD.  When the CD boots up, you'll be given the opportunity to boot into Ubuntu from the CD or begin installation.  (Actually, there are several other options, but I'm ignoring those for now -- though you may want to choose to check the disc for errors before you continue.)  

If you boot into Ubuntu from the disc, you'll notice an icon on the desktop to install Ubuntu.  It doesn't really matter if you choose to install Ubuntu from the LiveCD menu or by clicking this icon, the process is the same.

Once you start the installation, you'll be asked some basic information about your computer (i.e. language, keyboard, etc.).  Give it all of the appropriate information, until you get to the point where it asks you whether you want to do a guided or manual installation.  Choose to do a manual installation.

You should see two drives listed.  If you did as I suggested earlier and formatted the second drive to FAT32, it should be very easy to determine which is which -- the NTFS drive is your Windows installation, which you don't want to touch.  The empty FAT32 drive is the one you want to use for installing Ubuntu.  (If you didn't take my advice, look at the drives *very* closely before continuing to make sure you're not about to reformat your Windows drive.)  Select it, and create a new partition of between 15 and 20GB.  You want to format this partition to ext3, and use it as the root ("/") partition.  Now make another partition equal in size to the amount of memory on your system, and use this as "swap".  Now with the rest of the space on the drive, make one more partition, format it as ext3, and use it as "/home".  Double-check to make sure you've done everything correctly, then continue.

The installer will begin doing its thing, and eventually you'll be prompted to remove the disc and reboot the computer.  When you do, after the POST screen (remember, it's the one with the manufacturer's logo on it), you'll see a new screen -- this is the GRUB menu, which lets you pick which operating system you want to use.  If all went well, you'll see an entry for Ubuntu and another for Windows.  Boot into Ubuntu.

At this point, a few things might not quite work as they should yet.  Your screen resolution in particular might be a little wonky, and you may not be able to use your wireless card (if you have one).  The first is hopefully easy to remedy.  In the upper-right corner, you may see a pop-up saying something about restricted drivers.  Click on it, and then in the window that pops up check the box next to the driver(s) listed.  You'll probably have to restart your system for the change to take effect.

If you have a wireless card and it doesn't work, then you have a slight bit of work to do, because you'll have to use the Windows driver.  First, go to the System menu (in the upper-left of the screen) and select Administration->Synaptic Package Manager.  This is the big brother of the Add/Remove Programs utility.  You'll be asked for your password, so type it in.  Once Synaptic opens, click Reload to update your package list, then do a search for "ndisgtk".  You should have one result.  Click the box next to it and select "Mark for Installation", then click the Apply button to install the program.  Now for the "hard" part -- you need to find your Windows wireless driver.  

If you have a Dell or other computer from a major distributor, you can usually use their website to identify (and download) your wireless driver.  If you can locate it on your Windows drive (which you should be able to access from Ubuntu) then great.  If not, then download it from the manufacturer's website, and open it with Archive Manager.  (Yes, I know it's probably a .exe file, but it's likely a self-extracting archive, and you can open it with Archive Manager as if it were a .zip file, ok?)

Once you have your wireless driver, go to System->Administration->Windows Wireless Drivers, click Install New Driver, and select the driver you just found -- the .inf file is the one you want.  Click Close and, possibly after one of the last reboots you may ever need to do, you'll be able to use your wireless card.

After that, it's just a matter of playing around with your new Ubuntu installation.  You may want to read [this page]("http://ubuntuguide.org/wiki/Ubuntu:Hardy") for a few ideas of that to do (and what to install) next, particularly the section on multimedia support.


EDIT:  Well, crap.  I typed so much that... well, *everyone*... got their posts in before me.  *sigh*

---

### Post by falcon61102 on 2008-08-20
lol... hate when that happens, but nice post none-the-less.

---

### Post by caljohnsmith on 2008-08-20
[CENTER][SIZE="3"][B]I am proud and honored to inform you:
[SIZE="5"]mb_webguy[/SIZE]
that you are hereby nominated for the Ubuntu Forums':[/B][/SIZE]


:KS :KS :KS   [SIZE="5"]**[COLOR="Blue"]Most Detailed, Comprehensive, and Helpful[/COLOR]**[/SIZE]   :KS :KS :KS 
[SIZE="5"]**[COLOR="Blue"]Single Post Award of the Year[/COLOR]**[/SIZE]

[SIZE="4"]Congratulations![/SIZE]

[SIZE="3"]Thank you for taking your time to write such a detailed and helpful post.
It's people like you who are the reason the Ubuntu community has a reputation
for being so incredibly helpful and being wholeheartedly newbie-friendly.[/SIZE] :)







[/center]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

---

### Post by falcon61102 on 2008-08-20
LMAO... nice.  If I was creative enough, I'd award you the most creative post award... lol.

---

### Post by caljohnsmith on 2008-08-20
> **falcon61102 said:**
> LMAO... nice.  If I was creative enough, I'd award you the most creative post award... lol.
I hope you don't feel slighted, falcon61102, because your post was obviously incredibly helpful too; but I just couldn't pass up saying something about what mb_webguy wrote as I've never seen anything that lengthy and detailed. :)

---

### Post by falcon61102 on 2008-08-20
Not at all.  I'm simply here to learn and to pass on the little knowledge I have.  And I have to agree, that is some post.  It's got directions for before, during and after all in one.

---

### Post by Mgiacchetti on 2008-08-20
I would like to add that if you choose the option to 'try ubuntu' from the live cd menu you can basically troubleshoot problems before installing the operating system, example:

Say you want to be sure things work before you install so you boot to the live cd.

You find out that in order to get your network card working correctly you must open /etc/network/interfaces and edit some lines, 

you also find out that in order to get your video card working properly, you must install proprietary drivers.

Well you do this in your live cd and then click the install icon on your desktop.

Well, gladly, you figure out that everything you did in the live cd session will be carried over through the install process, and the settings will be saved so you dont have to do all of that to get your install working.

Nice huh?

---

### Post by falcon61102 on 2008-08-20
You can also mess up the system many times over and just reboot.  That's what I've always liked about the LiveCD.  But you're right; it's great to tweak and play with before actually installing, though you can't really predict and overcome GRUB issues just by playing with the LiveCD.

---

### Post by Mgiacchetti on 2008-08-20
also, would like to mention, that you may run into problems booting to windows from the grub's windows option.

This can be solved, although it is a bit tricky.
(if you have already gone through the setup process)
```

1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reach "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partitions

/
swap
/home
..... 

5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...." (at step 6 of 6 there will be an advanced button, click it.)
11. Install grub into the partition that '/' is mounted at (not the main disk or the NTFS or Swap partitions)
12. Once it is finished, just restart your computer

```Now, grab your XP disk, pop it in and restart pressing any key to boot from cd.

When prompted hit whatever key corresponds to "recovery console"
Log in to your current windows installation.
After logging in, execute:
```

fixmbr

```this will restore the original windows Master Boot Record.
Now type exit and hit enter, and restart the computer and remove the xp cd.


Whilst in xp (as you can only boot to this now because of the NTLDR) open your favorite web browser and navigate to [this page]("http://www.winimage.com/bootpart.htm") and download bootpa26.zip to your desktop.

Now, unzip this to c:\bootpart

once done, start > run > cmd
```

cd C:\bootpart
bootpart
[\code]

This will list all of your partitions.
[code]
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : [http://www.winimage.com]("http://www.winimage.com/") and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : c608cccb
 0 : C:* type=7  (HPFS/NTFS), size= 102399198 KB, Lba Pos=44
 1 : C:  type=f  (Win95 XInt 13 extended), size= 141735660 KB, Lba Pos=204798440

 2 : C:  type=7   (HPFS/NTFS), size= 141735638 KB, Lba Pos=204798484
Physical number of disk 1 : 10a03
 3 : D:* type=7  (HPFS/NTFS), size= 102400000 KB, Lba Pos=2048
Physical number of disk 2 : 85fca
 4 : E:* type=83  (Linux native), size= 104391 KB, Lba Pos=63
 5 : E:  type=8e , size= 104856255 KB, Lba Pos=208845
 6 : E:  type=6  (BIGDOS Fat16), size= 51207187 KB, Lba Pos=209921355

```you find your "linux native" partition number then enter the following

```

bootpart x LBA c:\bootpart\ubuntu.lnx Ubuntu Hardy Heron 8.04

```
replace 'x' with the number partition that corresponds to the linux native partition that has grub installed. (in the above it would be 4 yours may be different)

---

