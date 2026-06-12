---
title: "lost my ubuntu and vista please help"
date: 2008-11-11
forum: General Help
---

### Post by techjnk on 2008-11-11
Hate to admit this but am a complete noob to ubuntu.  I installed it trying to go for a dual boot with my vista.  with the idea of getting used to it and leaving windows for good.  unfortunately i wiped vista out partitioning for ubuntu incorrectly.  When I tried to reinstall vista (biggest mistake ever) I managed to screw up the other os.  I kept getting the Grub error 17.  I tried to load from a live cd no luck, tried super grub no luck.  went through every thread I could find and still cannot get anything going.  my computer now just tells me that i am missing my os.  when I try to install vista it reuses to do so on the basis that my hd is not formatted correctly.

At this point I would gladly wipe out anything to just get the ubuntu up and running.  Too tired of windows to even care about it anymore.  

If there is any help you could give me I would be grateful.  Sorry for the booklet.  

Gerri

---

### Post by JulesBl on 2008-11-11
What happens when you put the live cd into the machine and re-boot?

---

### Post by techjnk on 2008-11-12
I get the same message missing operating system.

---

### Post by bryncoles on 2008-11-12
if your google-fu is strong, you'll have seen this already. i'll post it anyway for you though...

[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by techjnk on 2008-11-12
Guess my fu is bad because I did not get that one.  I have since then gone through it and still have the notice, operating system missing, will not boot from cd live not gparted or super grub etc.  Any other ideas?  Any help is appreciated. Thanks in advance.

---

### Post by Coreigh on 2008-11-12
Is the computer BIOS set to try booting from CD before the hard drive? What actually *happens* when you try to boot from CD do you get any type of error, or does it just note even try the CD and goes straight to the (broken) hard drive?

---

### Post by techjnk on 2008-11-12
My bios is set to boot from the cd/dvd first then usb hard drive.  I think my primary hd is 5th on the list.  

When I try to boot i get nothing except the missing operating system message. After the first splash screen with hp and the directions to enter setup.  you know the press f12 etc.  thanks for your time

---

### Post by Coreigh on 2008-11-12
Does your machine have the boot menu option in the BIOS? Some of mine offer "Press F8 for boot menu" during the BIOS part of the boot, Like when the HP logo is on the screen before you get the no OS error.

Also unplug it for a minute to make sure it is going ALL the way through the BIOS set up. Sometimes they only reset and don't start from the beginning.

---

### Post by techjnk on 2008-11-12
No it does not allow direct access to the boot menu, I have to go through the bios and system config to get there.  I will turn off and unplug though as that may be the problem.  let me do that now. thanks again

---

### Post by Coreigh on 2008-11-12
I have to head out for the night but I will check here in the morning.

How did you first install Ubuntu? Was it from a bootable CD. I don't know what would have changed that you can no longer boot from CD.

---

### Post by techjnk on 2008-11-12
ok, it will boot from the cd with my windows but then I have no options for reinstalling vista as it says my hard drive is not formatted corectly.  it says that window is unable to find a system volume that meetis its criteria for installation.  

On the ubuntu side of things I still cannot get my live cd to boot.  

I would be willing to reformat both drives and install ubuntu only if I could find a way into the system.  

What do you think?

---

### Post by techjnk on 2008-11-12
oops sorry just reposted and didn't mean to.  thanks

---

### Post by fooman on 2008-11-12
what about gparted?

---

### Post by TeXtonyx on 2008-11-12
You didn't say how this happened. Are you sure it isn't a hard drive
failure? Are you able to get to the Recovery Console, so that you
can overwrite the MBR? Run fixmbr & fixboot if you can (bootrec).


If not, I think you need a rescue cd that will delete the MBR,
and then write a standard MBR. Delete the entire drive. I think
Vista will install then, assuming you have a regular install cd
and not one of those recovery disks. 

After Vista is installed, then resize/shrink with the Vista tool.
That makes unallocated space. During the Ubuntu live cd install you
can choose 'install to largest free space, (guided)' which will
avoid overwriting Vista. Use the Linux partition tool for Linux.

In Step 7, Advanced, you can choose to install grub to the /boot
partition during the Ubuntu live cd install. Then you can manage
with Vista's bootloader Easybcd(bcdedit) to boot all OS. Or you
can leave the default for grub, which installs to the MBR. The
consequence of grub in the MBR is that if you decide to delete
Ubuntu, or the grub support files on the Ubuntu partition become
damaged, you can't boot Vista. Not until you run Vista bootrec.

I see some other posts have come in. I'll mail this now and read.
I think he's right Gparted will remove the MBR. Then delete all
partitions. You want Vista to see a virgin territory to invade.

---

### Post by TeXtonyx on 2008-11-12
This development of the cd no longer working to install an OS seems
like a new nightmare. I didn't encounter it until a customer tried
to install XP SP3 quite unsuccessfully.

You can try putting your drive into another computer as slave,
it should be larger than the master drive. Then clone first drive
to second drive. This will get it into shape so that you can wipe
it with a rescue cd. Another thing is to try the manufacturer's 
diagnostic disk, available now in floppy or cd. There are guides's
about putting rescue files on a usb stick boot, which might work. 
Do you have a floppy drive?

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
That's for people who read this thread later that have an OEM (Vista)
recovery cd, not the real deal, install cd. It does fixmbr/fixboot.

---

### Post by techjnk on 2008-11-13
First thanks for all of the wonderful help.  

Yes, I did try gparted. It wouldn't boot from my cd.   I wondered if I had done something wrong.  I thought it would boot from the cd.  I may reburn and try again.  

I did the fixmbr and fixboot.  that is what i did prior to the message of "operating system missing".  

I wondered about installing ubuntu on an external hd.  Then try to boot it from there to get to the hard drives on my laptop to reset them.  

I going to redownload gparted live.  check it, burn, and try to go that route.  

I do have a vista installation disk but it came with another computer not my laptop.  so would rather go with ubuntu suffer the learning pangs and destroy my windows dependence.  

You are all fabulous.  Your support is amazing.  Thanks for caring.

---

### Post by techjnk on 2008-11-13
OMG, I am sooo excited.  I have no idea why I have gotten this but now I get an installer boot menu.  I chose install ubuntu and get the message loading.  I am soo thrilled .  Here is hoping it works.  Waiting with anxiety.  Ohh I am thrilled that now I can call myself determined and not just stubborn.  lol.  Thanks

---

### Post by TeXtonyx on 2008-11-13
"I do have a vista installation disk but it came with another 
computer not my laptop. so would rather go with ubuntu suffer the 
learning pangs and destroy my windows dependence." 

Some of these laptops come with a hidden partition and/or a recovery
cd. Recovery from the hidden partition uses an F-key (in the manual)
and will fix the problem, I'm pretty sure of the cd not working.

Once the OS is installed from the hidden partition then you can
wipe the new partition (better leave the hidden partition alone),
and install Ubuntu from the live cd. I see that it may be working
so consider this a backup plan.

"Ohh I am thrilled that now I can call myself determined and not just 
stubborn. lol."
 
TeX --

"Nothing in the world can take the place of Persistence. Talent will not; 
nothing is more common than unsuccessful men with talent. Genius will 
not; unrewarded genius is almost a proverb. Education will not; the world
is full of educated derelicts. Persistence and determination alone are 
omnipotent. The slogan 'Press On' has solved and always will solve the 
problems of the human race." Calvin Coolidge quote sig

---

### Post by techjnk on 2008-11-13
THink may I have a bad burn on a cd as no I get disk error 31 and boot failed.

---

### Post by techjnk on 2008-11-13
Ok I redownloaded and burned a new disk.  Now it is is in the process of loading again  I am at the installer boot menu and it is showing some code and dots.  So now I am waiting to see if this cd will work any better.

---

### Post by techjnk on 2008-11-13
Ok am really lost now  I think I have loaded ubuntu but for some reason my screen failed to initialize.  I now get a command line I think but don't know where to go from here.  Am I missing some drivers do you think or what?  should I try to reboot with out the cd in the drive? 

Maybe this is all easy and I am  just too tired to think.  thanks in advance.

---

### Post by TeXtonyx on 2008-11-14
There is nothing useful on your disk, right? So before you install
Ubuntu, run Gparted, or add it with synaptic if you don't see it,
and delete all the partitions on the drive. What this is going to
do is remove any previous code that could possibly cause a conflict.
It only takes a few seconds. Troubleshooting works by isolating 
the parts of a system and testing them one at a time, eliminating
multiple possible causes from the diagnosis. As much as possible,
proceed one step at a time, and verify... that will prevent getting
to the end of the install and having several steps which might be
the cause of the problem. That is just general troubleshooting
advice. You have never described your system or your video card
so that anyone can say something plausible about drivers.

So wipe the drive clean. Try to install Ubuntu again. If that fails
go back and investigate the error message. Is there something
wrong with hard drive? What caused the current problem? Like a
power surge. So if the Ubuntu install fails, try the Vista install.

The idea is to discover if the drive is bad. If the Vista install
goes through, it will clear the situation so that now the Ubuntu
install will work. Just delete the Vista partition with Gparted.

But if the Vista install fails also, it could be the cdrom drive
but that is unlikely. It could be faulty ram. You will have tried
to install cds so it's unlikely the fault of a bad cd.

So download a diagnostic tool which tests disk integrity from the
manufacturer of the hard drive, start bios setup and write down
your drive and model. See if the drive is ok. Then run memtest
to discover if you have bad ram. Much of this stuff is available
from a rescue disk like UBCD including deleting and restoring a
standard MBR. iirc, UBCD has hardware diagnostics from several
drive manufacturers and memtest. This is all if the Vista install
fails after the Ubuntu install fails. The point is not to install
Vista, but Linux and Windows react differently to installs of the
other OS. What prevents a Windows install might not prevent a
Linux install and vice versa. From my point of view as a computer
tech, the goal is to get your computer working again. If you had
a hidden partition for an install that would be the best way.

Did you look up error 31 on Google? Error messages are what I
use to give me a direction on figuring out what the problem actually
is and how to fix it - the most likely possible causes of the problem.

---

### Post by techjnk on 2008-11-15
AM working on it all now and will post later to let you know the results.  I am very hopefull at this point.  I was able to get the live cd running and ran the installation for ubuntu.  It is restarting now with the clean install.  It indeed rebooted and I have more than one installation on my hd  Will need to clean that up but am so excited to have it all up and running.  Thanks for all  of your help.  I don't believe I will install windows, I am in it (linux life that is) for the long run now.  Thanks again.

---

