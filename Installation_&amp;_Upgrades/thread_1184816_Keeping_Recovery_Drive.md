---
title: "Keeping Recovery Drive"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by nmaster on 2009-06-11
I'm considering installing Ubuntu on my laptop.  There is a recovery drive that can be used to return the laptop to its factory state.  Can I install Ubuntu over the C drive (which has Vista) and keep the D drive (recovery)?  I'm fairly certain that this can be done, but what exactly are the results?  In other words, how would I use the D drive if I needed to?  Does it show up at the GRUB?  Would I just select the recovery drive as the boot option? 

I have a Compaq Presario C700.  If anyone has done this before, it would be helpful to have any information.  

Thanks!

---

### Post by dE_logics on 2009-06-11
First of all, Linux is very much different than windows, it doesn't have 'driver' or unstable and unreliable storage mechanism like that.


Here a Hdd is detected as a hdx or sdx...where x is an alphabet like a, b, c.

So your hard drivers will be detected as sda or sdb (if a second HDD is present) or sdc (if a third HDD is present) etc...

A partition on sda will be deted as sda1, sda2, sda6 etc... similary for sdb will be sdb1, sdb2, sdb5 etc...

Linux has a philosophy of assuming every attached device as a file...so the HDD is too detected as a file...all these files are placed in the /dev directory.

Pretty confusing...I know...but I sorted it out :)

You have to make a different drive to install ubuntu in...actually ubuntu does it automatically (though I've never done that; that map and all seems pretty confusing to me), you can also do it manually if you want, for that you have to resize the partition and make space for ubuntu.

The recovery will be from the BIOS I guess....

---

### Post by nmaster on 2009-06-11
> **dE_logics said:**
> 

The recovery will be from the BIOS I guess....


Yeah, HP says the following at [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00809678&lc=en&dlc=en&cc=us&product=3758055&rule=3550&lang=en#RecoverOS](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00809678&lc=en&dlc=en&cc=us&product=3758055&rule=3550&lang=en#RecoverOS)


                                          **Restore the PC to its original condition with the HP Recovery Manager if Windows Vista is not accessible**                     
                     If the PC cannot launch into Windows, it may still be possible to use the HP Recovery Manager on the hard drive to restore the computer to its original operating condition by first pressing the **Power button**  to start the PC, and then pressing the                      [FONT=Courier]F11[/FONT]  key to start the HP Recovery Manager.                                                                                    
                    [COLOR=#0000A0]                     **NOTE: **                      [/COLOR]                                          Depending on the BIOS version, your computer may display multiple prompts during startup including                      [FONT=Courier]F11[/FONT]   to start System Recovery. Pressing the                      [FONT=Courier]F11[/FONT]   key on a computer with an HP factory image will start System Recovery even if the prompt is not displayed.                                                                                     
                     
                                          
[LIST]
[*]If the HP Recovery Manager can access the hard drive, a prompt is displayed to backup the user files before beginning the recovery. Follow any on-screen instructions.
[*]If the HP Recovery Manager cannot access the hard drive to fix any system errors, use the set of recovery discs to recover the hard drive to its original condition.
[/LIST]



I just want to confirm that this will work as long as I keep the recovery partition.

---

### Post by nmaster on 2009-06-11
I do have the recovery disks, but I would like to have 2 options just to be safe.

---

### Post by dE_logics on 2009-06-12
That recovery option is MS savvy...what I think is that there's a specific path that the recovery program takes to restore the original files in the default state of the system.

If the files will not be found, it will ask for the disk (I think so.....)
before
So according to me, if you want recovery from the HDD, the partition number should be the same as from the factory...you just gotta ensure that this driver number should not change, i.e installing ubuntu (which will make a partition after the windows partition, which is before this recovery partition) will change the number of the recovery partition...so it wont work if you install ubuntu...that's what I think

The best option is installing ubuntu in a partition which is AFTER the recovery partition.

Personally I find that recovery option crap...its like reinstalling any MS OS with tons of MS products...and if you continue using windows, you gotta do it every week.

---

### Post by nmaster on 2009-06-14
Sorry for not replying sooner, I've been busy at work.

So you don't think that I can just install ubuntu on the partition that is currently for windows?

Windows in on my C drive and the recovery partition is D.  Why can't I just put ubuntu on what is now the windows parition? Why would that change anything?

---

### Post by solitaire on 2009-06-14
I've got an HP laptop and I've still got the Vista "Recovery Partition" intact.

I've actually got it listed in my Grub (I've called it Boot'n'Nuke since if I ever use it the laptop would probably wipe all my partitions and multiple OS's and it will die a death! lol!!).

---

### Post by lisati on 2009-06-14
My preference is to leave the recovery partition(s) untouched until I'm sure that having Ubuntu on my system isn't going to be a major pain. And having some kind of bootable backup of the recovery partition is a good idea. That way, if something goes wrong, I've got something to fall back on. **Only after making sure that I can revoer the system to a usable state would I delete the recovery partition(s) or use them for some other purpose.**

---

### Post by solitaire on 2009-06-14
Also ive noticed that 9.04 recognized the Recovery Partition and does not mount or list it as an accessible drive (so you have to manually mount it). But 8.10 did mount it like a normal drive.

It's safe to say you'll forget about the recovery partition unless you go into the prtition editor..

---

### Post by merlinus on 2009-06-14
You can of course do this, but I would bet you will not be able to restore vista afterwards.  As others have said, it will not want to restore anything on a partition that has linux on it.

Redmond does not work and play well with anyone but themselves.

---

### Post by nmaster on 2009-06-14
> **merlinus said:**
> You can of course do this, but I would bet you will not be able to restore vista afterwards.  As others have said, it will not want to restore anything on a partition that has linux on it.

Redmond does not work and play well with anyone but themselves.


So saving the recovery parition won't do anything?  Has anyone who kept their recovery partition ever used it?  Did you have to add an entry into menu.list (I think thats the file) for the partition to show at grub?

Thanks for the responses, I appreciate the help.

---

### Post by merlinus on 2009-06-14
What is the point of having grub list the recovery partition?  It is not an operating system.

Does it contain an .exe file?  Is it bootable on its own?

---

### Post by solitaire on 2009-06-14
> **merlinus said:**
> You can of course do this, but I would bet you will not be able to restore vista afterwards.  As others have said, it will not want to restore anything on a partition that has linux on it.

Redmond does not work and play well with anyone but themselves.

You not used a "recovery Partition" lately!

They tend to wipe all partitions except the recovery partition.
Then recreate the single partition and install the OS. 

I've known a few people who use the Recovery partition to later find out that their entire Disk was wiped and they have lost Partitions and data!

Also I've got my Recovery partition listed in my grub since, for some reason, the "hold f11 for Recovery" does not work for me!

---

### Post by presence1960 on 2009-06-14
> **neal.m.master said:**
> I do have the recovery disks, but I would like to have 2 options just to be safe.

Neal, leave the recovery partition untouched. Install Ubuntu to the Vista partition. When you install Ubuntu you should get an entry in GRUB for the Recovery partition. If it does not get an entry you can add one by editing the menu.lst file just as you would to add a Windows entry.

When you select the recovery partition from the GRUB menu it will work because that partition is bootable. Just note it will restore your machine to the factory specs. Plus you have the bootable recovery discs so you should be safe since you will have two options to recover your factory settings.

I just did this on a clients eMachine. When I selected recovery partition in GRUB menu it went right to the recovery process. I clicked cancel of course!
> I've known a few people who use the Recovery partition to later find out that their entire Disk was wiped and they have lost Partitions and data!
That's why it is called recover. It recovers the machine to it's original factory specs and condition. And it gives you a warning it is going to do that before you click OK to proceed.

---

### Post by solitaire on 2009-06-14
> **presence1960 said:**
> That's why it is called recover. It recovers the machine to it's original factory specs and condition. And it gives you a warning it is going to do that before you click OK to proceed.

I know that! One of my mates (who though he knew more than me because 'I only used Linux' and he knew Windows!!) decided it was safe to run as it would just repair the install....

How I laughed at the inevitable results... ^_^

---

### Post by presence1960 on 2009-06-14
> **solitaire said:**
> I know that! One of my mates (who though he knew more than me because 'I only used Linux' and he knew Windows!!) decided it was safe to run as it would just repair the install....

How I laughed at the inevitable results... ^_^

I guess they don't read the messages before click OK. If they would have read it tells you what it is going to do...LOL

---

### Post by nmaster on 2009-06-14
Thank you everyone.  This makes me feel really good about going forth with installing Ubuntu. I love this community!  Its so helpful.  If I wanted help with Vista I would have to call a help center and deal with someone who doesn't really want to help but is being paid.  This is so much better.  :)

---

### Post by merlinus on 2009-06-14
@[presence1960]("http://ubuntuforums.org/member.php?u=657448")

Thanks for the recovery partition info.  Live and learn....  but hopefully I will never have to run windows again!

---

### Post by presence1960 on 2009-06-14
> **neal.m.master said:**
> Thank you everyone.  This makes me feel really good about going forth with installing Ubuntu. I love this community!  Its so helpful.  If I wanted help with Vista I would have to call a help center and deal with someone who doesn't really want to help but is being paid.  This is so much better.  :)

The old saying "the best things in life are free" still is true today.

---

### Post by presence1960 on 2009-06-14
> **merlinus said:**
> @[presence1960]("http://ubuntuforums.org/member.php?u=657448")

Thanks for the recovery partition info.  Live and learn....  but hopefully I will never have to run windows again!

I hear you I only have it for work because they made it clear to me NO open office- something about formatting not 100% between Open office & MS Office.

On the bright side though I decided to install wubi on the XP partition and give it a whirl, just to increase my knowledge. After the test I will remove wubi.

---

### Post by nmaster on 2010-06-27
This is over a year later, but I just wanted to let everyone know a couple things.

1) the recovery partition did boot.
2) i got an error (don't remember what it was) and the the recovery process did not work.

i was just curious to see what would happen but i guess it didn't work as planned.  i think if i ever need to reset the machine, i'll create two NTFS partitions (just like the laptop came with) and put the recovery partition (currently stored on an external hdd as a dd image) on the second.  maybe then it will work.  i still have the recovery DVDs though so i guess i still have a safety net.

---

