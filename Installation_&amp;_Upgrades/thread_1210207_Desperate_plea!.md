---
title: "Desperate plea!"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by ravindra.rajaram on 2009-07-11
I'm trying to get Ubuntu (any version!) installed on an assembled PC.
I've installed Ubuntu before on Intel PCs and Laptops without so much as a hiccup!
But, now I do not understand what might be going wrong here and even after all kinds of attempts,I'm still stuck with no Ubuntu on the PC :(


and some details about the kinds of installations I tried:

1. Ubuntu 9.04 desktop live cd - shows the first screen which allows me to choose to test, install etc, but nothing happens after that
2. Ubuntu 8..04 desktop live cd - same as above
3. Ubuntu 9.04 alternate cd - keep getting errors like so and so DEB is corrupted and could not download it - I'm connected to the Internet and the DHCP address assignment completes successfully
4. Ubuntu 8.04  alternate cd- the farthest I was able to proceed - have seen errors like so and so DEB is corrupted, but was able to download successfully; BUT,  the "Select and install software" dialog holds me up at 6% for a looong time! I got to this stage many times, but only once I moved up to 18%, but the installation bailed out after that. I've used two different CDs, one burnt at 24x and the other at 4x.
5. USB installations with 8.04, 9.04, 8.04 alternate, 9.04 alternate, 8.04 netbook remix all end up in the

Could not find kernel image linux

error and I'm stuck there

I've tried many google searches, but the content of the USB seems to contain all that was suggested in different posts!
6. Ubuntu unetbootin - just says "boot error!"


oh and btw, I've tried Fedora 11 and met the same fate as of Ubuntu 9.04
This is a very desperate plea for any clues/hints/suggestions to get a Ubuntu installation done on this PC!

I've a power outage now and will post the hardware details in a response to this post!

-RR

---

### Post by phillw on 2009-07-11
[SIZE=2][FONT=Arial]Hi,

Errrrrmmmmm .......  Wierd, to say the least.

I suppose the 1st thing to check is is the kit okay - i.e. is there a hardware problem.

Can you boot the LiveCD and get access to Ubuntu that way ?

You would be unfortunate if 'all' your Ubuntu images were corrupt. A quick check would be to try it with DSL from here ....

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

We need to ascertain that Linux actually can live on your box. 

Assuming you get either DSL or a LiveCD actually running, from a terminal type 

df -h

that will tell you what hard drive(s) and partitions it can see.

and 

sudo  fdsik -l

will also tell you what it can see.

If you are still having problems 'seeing' the hard disk(s), it is looking like you may lose data. Before continuing MAKE SURE you back-up your drive(s)

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

Let GParted at the miscreant disk - delete all partions, reboot & start again with the disk at 100% free.

The LiveCD version of GParted is here

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

A discussion on the 'joys' of not having a CD to install with can be found here

[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)


Hope this is of help.

Regards,

Phill.

[/FONT][/SIZE]

---

### Post by ravindra.rajaram on 2009-07-11
Hi Phill,
I could get booted using GParted.
So,I believe it could be safely assumed, Linux can live on this system!
The fact that Ubuntu 8.04 alternate CD could actually start installing software also probably means Linux can be installed on the system.
I've read through multiple forum posts where people had similar issues with installation hanging up at 6% (select and install software dialog), but atleast some of them, trying with a new CD (burnt at 4x) or trying multiple times solved their problem. So, I can probably safely assume, if I can boot this system up using USB, I could probably get the installation completed.

Okay.. here are the hardware details.

BIOS Version GC11010N.86A.0311
Mother board Information
         Intel 
         Product D101GGC (not sure what this xactly means)
Drive Configuration options:
      Onboard Chip SATA   SATA Disabled | IDE Controller
      S.M.A.R.T           Enabled | Disabled
Hmm..one catch could be the memory on the system: 512 MB but my experience with Ubuntu suggests it should be otherwise, as I already have about 3GB of swap created.

---

### Post by ravindra.rajaram on 2009-07-11
also, like I mentioned, I did try Unetbootin; the USB key is able to boot off on a different system (a laptop), but not on the PC!

I'm okay, with wiping the hard disks clean. no data to backup here.

-RR

---

### Post by carml on 2009-07-11
How much time you saw the 6% bar? Me too,when I installed from the alternate cd I thought it was immobile,but after a few minutes it restarted the process,then to 18% the same,but in about a half a hour a had my system ready to be used.
By the way to burn a cd at a low speed is a must in every attempt to install a new OS. 
I hope this can help you :).

---

### Post by b@sh_n3rd on 2009-07-11
Hey dude. What exactly are your PC specs? I get awfully annoyed whenever someone looks down at a PC when they can't install something like Ubuntu. My PC specs would make you rethink the possibility of RAM fault. My one is an 11yr old Dell Dimension XPS D266 with an Intel Pentium II 266Mhz, 256MiB, 8MiB ATI 3D Rage Pro (no hardware accel), 20GiB Samsung HDD and a 20x LG DVD-RW. I've also got only 386MiB for swap BTW. So 512 is more than enough of RAM if you ask me.

If you could stick to a single version of Ubuntu, that'd help us determine what and where the bugs are. So choose between Intrepid and Jaunty, OR, if you want an LTS version, Hardy. Jaunty would be best with compatibility but it *does* have a couple of bugs. As I mentioned earlier, explicit system specs would help us take the first step in debugging your fault line...

---

### Post by Arup on 2009-07-11
Looks like a burning issue here, have you tried to change the DVD writer? Linux distros need to be burned on very good media at a slow speed, it may sound like urban legend but experience has taught me that.

---

### Post by phillw on 2009-07-11
Hmmm.... Still puzzled

This is pretty drastic 

But.... If you clear out the MBR (Master Boot Record) of your hard-disk and let GParted loose at it to re-slice and format it at least you will know the HD is okay.

If you can boot LiveCD from a Ubuntu CD then it looks like the CD is okay - I'm pretty much at a loss of what else to suggest.

Your Swap only needs to be 1GB (So I was told, when I asked the question)

To 'nuke' your MBR the command is

sudo dd if=/dev/zero bs=512 count=1 of=/dev/sda
MAKE SURE THAT sda IS the disk you want to 'nuke' - in case you have more than 1 hard disk connected to your machine !!!

Bear in mind that issuing that command will COMPLETELY DESTROY any chance of getting data back off the hard disk.

I wish you well & will be back on-line in a few hours time - please let me know how you fare.

[email]phillw@uk.vpolink.com[/email]

Regrds,

Phill

---

### Post by ravindra.rajaram on 2009-07-11
thx for the replies everyone!
Well,
The system is Intel P4, 512 MB RAM, 75 GB hard disk. It has already been configured with 3GB Of Swap.

@Carml
The installation proceeded past 6% only once after about half an hour..but again took up about another half an hour at 18% and then bailed out!

@bash_n3rd
I understand most Linux's run perfect with anything above 256MB; its just that one time, I had trouble getting Ubuntu started on a 256MB RAM; so had to boot using other means and a setup a SWAP to get the installation started.
I've been trying to get any version of Ubuntu started on this PC, so had tried so many options. I think I'll stick with Jaunty now and provide more information.

@Arup
Hmm..I did try buring at 4x on a Dell laptop's burner.

---

### Post by ravindra.rajaram on 2009-07-11
Phill,
I think your suggestion did some trick, but does not solve my problem yet.
After removing the MBR and re-formatting the entire disk, the USB boot atleast once in a while does show the Ubuntu live cd options (but does not show the text completely)
But like I said, does not solve the problem completely as I click on Install Ubuntu, the USB's light is switched off and the installation hangs :(
-RR

---

### Post by ravindra.rajaram on 2009-07-18
All,
Thx a lot for your replies!
I've more or less concluded that there is some problem with the hardware and having it replaced now.

Thanks again!

-RR

---

