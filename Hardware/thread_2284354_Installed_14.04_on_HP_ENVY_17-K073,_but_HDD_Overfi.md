---
title: "Installed 14.04 on HP ENVY 17-K073, but HDD Overfilled &amp; Can't Recover"
date: 2015-06-28
forum: Hardware
---

### Post by oldefoxx on 2015-06-28
I'm going to explain this in some details.  What it boils down to is:

(1) I was able to get Ubuntu 14.04 to replace Windows 8.1,  and things were fine.

(2) I have an NTFS formatted My Passport USB drive with folders and files to copy to temporary storage, so that I can reformat the My Passport as ext4 and put the folders and files back.

(3)  The My Passport drive is virtually unused, and yet there apparently errors found.  The absolutely only way I could find online to deal with this is to run chkdsk.exe off a Windows PC to make corrections.  I used my wife's HP laptop with Windows 7 for this, and ran "chkdsk /c " with the My Passport drive.

(4)  Hours later, chkdsk.exe reported it had run out of available clusters to map in in place of existing faulty clusters.  But it had corrected indexes to the existing folders and files.  Now time to get them off that drive and allow me to reformat it before copying the folders and files back.

(5)  The copy to the new laptop HDD failed when the HDD ran out of available disk space.  This should not have happened, and the new Ubuntu install on the new laptop was virtually frozen with no free disk space to write to.  A reboot only showed that it would not boot now, and it won't let me use a LiveCD or usb HDD with Ubuntu on it to boot to instead.

(6)  Looking at the My Passport drive contents, I found that chkdsk,exe had crossthreaded lots of folders and file entries, so that it was now attempting to copy way too many folders and files to the destination drive, which messed up the new drive by filling it up completely.

(7)  Now the HP ENVY 17-K073 laptop wont't boot, and under the F9 key, shows only four choices for boot devices.  One was for my My Passport drive, which is now obsoleted, because I deleted the NTFS volume, added back an ext4 and swap partition, and installed Ubuntu 14.04 on it.  I see no way to add, delete, or modify the boot device choices on my new Laptop.

(8)  The Esc key brings up a grub interface, and "help" typed there will bring up a string of command options.  But the list of commands is huge, and the vast majority just scrolls off the top of the screen.  I try entering "boot", but grub sells me I have to load the kernel first.  What I can see on the screen gives me no clue as to how to load the kernel.  This might help, but I would have to know a whole lot mre than what I can see here to make it work for me.

(9)  On my old laptop, after I installed Ubuntu 14.04 to My reformatted My Passport drive, it would not boot unless the My Passport drive was connected to it.  I fixed this by using "sudo grub-install /dev/sda && sudo update-grub" to fix the problem on the first drive, then doing "sudo grub-install /dev/sdb && sudo update-grub" on the attached usb HDD drive.

Now this is a cross between a hardware and software issue.  My new laptop is currently dead because the hard drive is packed too hard, and I can't get my reformatted,Ubuntu-installed My Passport drive to be booted from instead because of the limited choices brought up by F9.

My LiveCD might boot again, but I don't think so, because there is no hard drive space left to use temporarily, and from the LiveCD, you don't have a provided means of accessing the actual hardware you are running on.  There is probably a way around this, but I don't know what it is.  If I could use either the usb HDD or the usb LiveCD method to get Ubuntu up and running, maybe I can clear off some of the rubbish on that internal HDD and effect a full recovery.

If I had both the usb HDD and DVD/CD drives connected at the same time, why can't I use free drive space on /dev/sdb1 or /dev/sdb2 for immediate LiveCD needs, or is there a way to use existing RAM (I have 12GB) just to get LiveCD to run?  Could I then use a terminal mode to access /dev/sda1 and get rid of some stuff currently packing it?

These are some od the ideas I am currently considering.  I'm not making any progress on my own, and I wrote a long post to HP's forums, but I've never had any hardware support forum come back with any help, so since Ubuntu people do it best, I am here asking for some help or guidance.  So for two final questions:

(1)  What can I do when I see grub> ?
(2)  What can I do when I see grub restore> ?

Two machines involved, the new laptop and the old laptop.  Different circumstances, but in both cases Grub2 wants specific instructions from the user, and I haven't a clue one as to what to put in for either.  At least (1) responded to "help", but with far too long a list of choices, while (2) balked at that as well.

If you can help me, I would appreciate it, very much.

---

### Post by weatherman2 on 2015-06-28
Sorry, but this is a long post with several seemingly unrelated issues.  You may want to split the up into separate posts.

But my quick read response is: boot a live USB on the laptop and delete some of the files you were trying to copy to free up space.  A full hard drive CANNOT prevent booting of a live USB or live CD on your laptop.  You've got some other issue there.  You can boot a live USB/live CD without any hard drive installed.

Also, if you were having problems with the portable drive in Windows, you'd best check the S.M.A.R.T. status and run tests on it.  Try GSmartControl (from a live USB boot - you'll have to enable the Universe software repository, which you can do in Ubuntu Software Center).  It's quite possible the drive is failing.  Look for any Attributes in GsmartControl that are highlighted in red - those are the ones to pay attention to.  If you have a lot of Reallocated Sectors or ANY Pending Sectors, the drive may be failing and you wouldn't want to depend on it for anything.  Hard drives fail routinely, even if they are not old.

---

### Post by NoWayWin8 on 2015-06-29
> **oldefoxx said:**
> My LiveCD might boot again, but I don't think so, because there is no hard drive space left to use temporarily, and from the LiveCD, you don't have a provided means of accessing the actual hardware you are running on.
Sure there is - the computer RAM. You can completely remove the HDD and still be able to boot and run from a live CD/USB.

Either way, shut off the laptop and disconnect the USB drive. Then turn it on and wait to see what it automatically boots to. Don't push any buttons for a minute while it boots.
> 
(1)  What can I do when I see grub> ?
Type the word **normal** and press enter. If Ubuntu's installed it will then boot. It should be doing this automatically each time (if you don't interrupt grub by pressing ESC).

If it doesn't boot now, what error does it give?

---

### Post by oldefoxx on 2015-07-01
I've been real busy, and have learned a lot.  First, the problems relate to GRUB2 and the fact that it won't recognize the UUID that /dsv/sda1 has.  I've learned how to change that UUID, and have confirmed that it matches, but still no-go.  I also checked it in the /etc/fstab file.  Second thing is that GRUB2 wants there to be a FAT, ext2, then an LVM partition.  I wiped that stuff off the hard drive right on with gparted.  I'm strictly ext4 now with a swap partition on the side.   At this point I can only get up with the LiveCD.

I get a boot menu up on my old laptop, and can press the "e" key to see the code behind it.   My /dev/sfa1 drive won't boot anymore. but I can get to my /dev/sda2 or /dev/sda3 installs with no problem.  I'm trying to figure out why /dev/sda1 won't get recognized now.  From the other installs. I can access sda1 with no problems.  Again, it boils down to be a GRUB2 issue of some sort.

I'm researching matters related to GRUB2, but most of the related info has to be extracted fom numerous posts, which were found with numerous searches. and the document I am putting together is getting to be massive.  I haven't had time to absorb it all.

At least the hardware has checked out.  That's goof.

In GRUB2, I want to do three things:

(1)  Get off using UUID to identify where to boot from.  I want to move to using partition labels instead.  I name the partitions after the device names they have in /dev,  and I always use /dsv/sda1 as my primary boot reference.

(2)  Get away from looking for a FAT, ext2, and LVM partition as GRUB2 does now.  This isn't NTFS-land here, and I don't want MS's footprints on these drives.

(3)  Find out how to talk to prompts like grub> and grub repair>.  I have no real documentation on what you can do at that point, and the help is too little, to vague, or simply scrolls its way off the screen so fast that I can only see a few of the options available, and those are the very last ones.  And no examples to work from.

Right now, if I let UUID rule, I will likely have to have all my /dev/sda1 drives on my several PCs  changed to share the same common UUID, which I can find by using blkid, copy it from there, then treat "UUID=" as a variable assignment, then do "tune2fs /dev/sda1 -U $UUID".  I can repeat the process for every /dev/sda2. /dev/sda3, /dev/sdb1, ... drive if I have to.  Or replace set root=UUID=xxxxxxxx..." with set root=(hd0,1) if that will work. 

Everybody warns you that it you change the UUID on a boot drive, you need to do the same in /etc/fstab.  Well, you can replace the UUID= statement there with /dev/sda1, just as you can in the boot file.  This is just going back to the way things were before GRUB2 showed up.

If you use ls /dev/disk/,  You find the several ways that drives and partitions can be accessed.  You have by-id, by-name, by-label, and by-uuid.  UUID is regarded as the most persistent, but actually every time you do a reformat, the UUID is reassigned randomly.  Not that you reformat that often, but how often do you change partitions around, shrink them or expand them or do you change their names?  My greatest degree of control as a user is the way I choose to name (label) them, and that is why I want to get back to using by-label.

I can't find the answer to a few questions.  For instance, you can edit the boot menu choices, but how do you make such changes permanent?  You can go into a command line mode at that point, but what can you really do there?  At least as far as getting the system to boot up?

And the big topic today in my searches was reverting from GRUB2 back to GRUB, what some call GRUB1.  Seems GRUB2 has caused a lot of problems and provides no easy solutions, so people have opt out of keeping it and moved to doing something else.  They even discuss how to do this from a LiveCD when your system won't boot.

At one point earlier today I found that using tune2fs ,path> -U <uuid> ended up on the wrong drive, so that I ended up with /dev/sda1 and /dev/sdb1 sharing the same UUID.  seems some utilities work differently from others when it comes to accessing block devices, and turn2fs could not fix that problem .. Fortunately, GPartEd (Gnome Partition Editor) sees the drive and partitions by where they are physically and lets you designate that you want a new UUID assigned to any partition, but you get something random, just like you would yourself if you used uuidgen.  Anyway, that cleared the bottleneck with two partitions ending up with the same uuid.  How that happened is still unclear in my mind.

But that does raise another question.  I used the four by- choices and mapped the results from each so that I could make sure I knew what went with what in these references, and I found that I had three more by-uuids than I had drives or partitions for.  Where did these come from?  I reasoned that they were probably associated with the three deleted partitions from my My Passport drive when I trashed everything and had gparted create a new partiton table, then created a new ext4 partition, followed by a swap partition.  Three leftover UUIDs that once belonged to a FAT, ext2, and LVM partition.  Now how do I get rid of them?

That's enough questions for the night.  Believe me, I appreciate every bit of help that I get, and from this community, there has been plenty.

Oh, you see the grub .cfg file?  It is loaded with UUID= assignments.  It warns you against editing it, as it is generated from templates and a resource file.. Probably have to look at the resource file as causing some of the present problems, like why /dev/sda1 won't boot and says the uuid could not be found, and the other two partitions fair much better.

---

### Post by dino99 on 2015-07-01
my advices:
- dont change the system's default: uuid is set by 'formating process', and as 'u' means 'unique' forget about your confuse 'share the same uuid' it cant work.
- ubuntu installation is designed to let new comers out of fear; so let things be simple

---

### Post by oldefoxx on 2015-07-01
Ah, it happened.  I had two partitions with the same UUID, and it even confused gparted to the point that it saw /dev/sda partitions and /dev/sdc partitions (except for either /dev/sdb1 or /dev/sdc1).  I restarted gparted, and it went back to seeing /dev/sda and /dev/sdb partitions.  Then I was able to unmount /dev/sdb1 and change its UUID to a randomly generated one using gparted.  Otherwise I would have likely had been forced to reformat /dev/sdb1.  I'm certain that nobody expected or intended for this to happen, but it can and did.

I've tried using grub-install /dev/sda1 and update-grub repeatedly, but can't get pass its inability to recognize the uuid of /dev/sda1.  I only get the messaage briefly, but I seen enough of it to feel confident that it is /dev/sda1's, and yet it doesn't find a match.  I had previously installed boot-repair on /dev/sda3, and was able to use the boot menu to get into it (I can also get into /dev/sda2, but it does not have boot-repair on it).  Anyway, boot-repair would change matters so that it would take the current device and make it the primary boot option.  I've had that happen befor, and may do it again.  Right now though, I am more interested in "fixing" the boot problem with /dev/sda1, as it may be fundamental to tackling the whole boot problem with the new 17-K073 laptop.  Fixing one may lead to answers for the other.

I was successful in retrieving all the folders and files that had temporarily been stored on the new laptop's hard drive, so a reinstall without reformat or a reinstall with reformat are back on the table.  But fixing a boot problem should not force a full reinstall of an OS.  Anyway, boot-repair does run, but makes /dev/sda3 the primary boot choice.  It has Advanced settings which I've tried in part, which are (in part):

(1) Designate which partition is to be primary.  (I tried setting to /dev/sda1, but it rejects this for some reason).
(2)  Designate which partition is Grub to be installed to (I tried /dev/sda1 again, but it wants to be run from a LiveCD for this)
(3)  Purge Grub or revert to Legacy Grub (it warns you to make backups first).

Then it wants you to run some sudo commands, but they are unknown to the bash shell, and apt-get install can't find them in the repositories.  Stuff like dpkg-config.  So boot-repair comes up short of fixing the boot on one partition while running from another.

This is not how I want to be spending my time, but it seems important enough to try to solve.  Or I may throw in the towel and just do a reinstall, but that is so extreme a workaround that I hope for something better.  I mean this is what grub-install and update-grub are suppose to do for you, but because of this UUID hangup, it's not happening.

I think GRUB2 needs to be more thorough in it's examination of whether a given by-uuid is both valid and bootable, and that it should maybe do some file corrections to /etc/fstab and whatever if there is a discrepancy, not only to ensure its own bootability, but so that everything involving uuid goes right from that point on.  Too extreme?  Well, look where I am at, and apparently I am not the only one.  There are many laptops now classified as not being able to have Ubuntu install and run on them successfully, and it is not because the install went bad, but because they had boot problems afterwards. (dual installs with Windows, where you could boot up into Windows but not into Ubuntu, Ubuntu boots, but you get a black screen and nothing happens, or as in my case, boot won't recognize the primary boot partition, even though it is sitting on it).

---

### Post by oldefoxx on 2015-07-01
Okay!  Fixed the problem with my old laptop.  Turns out that my naked eye could not distinguish if the UUID there was the same in /etc/fstab as returned by blkid, so I moved it up a notch:

(1) From the terminal window, I did a **blkid** command and got back a list of all my current HDDs with their UUIDs and partition format.  I used **Ctrl+Shft+C** to copy the sda1 UUID to the clipboard.  (I had to first use the mouse to highlight the portion of the screen that showed the assigned UUID.

(2)  I opened LibreOffice Calc and pasted the contents of the clipboard into cell A1 using** Ctrl+V**.  I then selected that column and used Format >> Column >> Width >> to adjust the column width to an optimal setting.  Not really necessary, but improves my view of the contents.  You have to uncheck the Default Width checkbox for Optimal Width to work.

(3)  I used the terminal again to create a new folder under /media/[username] called "sda1".  In the GUI this is done automatically if you mount a partition from the toolbar, but once mounted, the GUI gives you no direct way to unmount it, and from the terminal, you can't use umount because the GUI already has it mounted, so it is "busy".  To cancel a GUI=mount, you have to logout then login again.  So instead I did the following:
```

sudo **mkdir /media/**[username]**/sda1**
sudo **dir /media/**[username]
sudo **mkdir /media/**[username]**/sda1**
sudo **mount /dev/sda1 /media/**[username]**/sda1**
sudo** cat /media/**[username]**/sda1/etc/fstab | grep " / "**
[I]# / was on /dev/sda1 during installation
UUID=fb2a02a1-a17d-4377-983a-2ce61d7a75a6 /               ext4    errors=remount-ro 0       1[/I]
sudo **umount /dev/sda1**
```
Instead of [username], it would be your account name, without the square brackets.

I really just started with "sudo -s" (or you can use "sudo su") and become super-user until you enter "exit" or close the terminal window.  But some people fuss about anyone actually becoming super-user, that there would be complaints if I didn't put their side forward first.

Anyway, if you become super-user, you can forget about having to use "sudo" with the above actions.  Just think:  Being super-user saves you five keystrokes per line.  Of course it throws off "~" and implicit reference to your user's home account, so to get back there, you would have to do "cd /home/[username]", or in my case "cd /home/oldefoxx".  And it can cause problems with folder and file ownership, so you have to be careful avout that.

I'm making it sound more complicated than it is, but I am all too familiar with a newbee's difficulty in putting all the pieces togther, so I go the extra mile to help them out.They could just copy the code steps out to another document and use them, or copy out the while thing  and highlight what they really have to know and follow.  Hey, to help out, let me go back and do a little highlighting myself
That's done. so now I have blkid and a grepped line or two from the effected /etc/fstab on the screen, and what I did was get the second UUID= assifnment anc copied it into cell A2 of the Calc spreadsheet.  Then in another cell, I just arbitrarily picked B1, I entered the following formula:
```

=if(a1=a2,"Yes","No")

```
And B1 immediately showed me No.  They didn't match.  With one right above the other, I could finally pick out the difference.  It was off by one character.  An "a" had become a "2" when the /dev/sda's UUID was last set.  That would have been my mistake.  I had carefully copied off the expected UUID from the screen when GRUB2 bombed. and I guess I was a tiny bit sloppy in what I jotted down.  Not entirely my fault, as my handwriting suffered a lot years ago when a 1/2-inch drill had jammed in a hole I was boring into a length of pipe and had backlashed around, doing serious injury to the wrist behind my writing hand.  Can't hardly sign my name anymore, and have to hunt and peck in a keyboard with two fingers since otherwise I hit the touchpad and throw my entry or focus point off

Alright, so sda1's UUID does not agree with what is in /etc/fstab.  How do I fix this?  Which one is right.  Neither one is right, but here we have it that the assigned UUID to sda1 does not match what /etc/fstab says, and one has to change.  We change the sda's UUID, that brings it into alignment with /etc/fstab, and what /etc/fstab says is what GRUB2 goes by.  Who knows what other software depends on /etc/fstab as well?.  The simplest choice is to reset the sda2 UUID to what /etc/fstab specifies, although you could go the other way around and gamble that nothing else breaks.  But we will error on the side of caution here:
```

UUID=fb2a02a1-a17d-4377-983a-2ce61d7a75a6
sudo [B]tune2fs /dev/sda1 -U $UUID/B]

```
The first line of the above code block is a direct copy and paste from what is showing on the screen.  Highlight the "UUID=" line that showed up after the combines cat ... | grep " / " line, and paste it to the command line, and UUID becomes an instant variable assignment.   The next statement then threats UUID as a variable by preceeding it with "$".  You have now set a new UUID (actually an existing one according to /etc/fstab and grub) into /dev/sda1, and the next reboot effort worked. 

Now tomorrow I will have to see how this translates to getting the 17-K073 laptop to boot up.  One bad thing I note about GRUB2 is how long it takes to boot up when compared to legacy grub.  The difference seems to have a bit to do with recognizing the new Windows-preferred drive format, meaning the possible presence of three partitions:  FAT, ext2, and LVM.  Grub2 should check for these during the grub-install or grub-update, and if not present, should remove the related tests for them in its boot process.  Since it does not do this, I'm wondering how to eliminate the checks manually on a permanent basis.

---

### Post by oldefoxx on 2015-07-02
I'm still prepping to take on the HP ENVY 17-K073 laptop gain, but today I burned some boot-recovery CDs and worked on the manage of online posts that i gathered into a single file while working on fixing the old Toshiba L355 laptop that I still use.  It's a great laptop, but I need a faster processor and more RAM now, so I need to replace ot.

Anyway, I finished working on the text file. and will attach it here in case others find some advantage in what I've come up with.  Note there are plenty of unanswered questions in it, and I did add a few of my own, so if anybody comes up with answers,  Post them on this thread and I will upgrade this file.

---

### Post by NoWayWin8 on 2015-07-03
Where to start....  > **oldefoxx said:**
> mount a partition from the toolbar, but once mounted, the GUI gives you no direct way to unmount it, Right-click and select "Unmount" > some people fuss about anyone actually becoming super-user, It will cause problems for your system if you accidentally type the wrong thing into the root terminal. > I'm making it sound more complicated than it is, Totally!  You can view your fstab in terminal with this (if run as root, you can edit it too): ```
nano /etc/fstab
``` You can see your disk device partitions along with their correct UUID and mount points with this command: ```
sudo lsblk -o NAME,MOUNTPOINT,UUID,LABEL,SIZE
``` (Or use the "Disks" application or install GParted)


Clean up your /etc/fstab file by commenting out (#) lines that do not correspond to a UUID/mount in lsblk (or Disks or Gparted). fstab entries that aren't valid will dramatically increase the time taken during boot.

---

### Post by oldefoxx on 2015-07-03
Thanks for the tips.  I tried the right click, but unmount was not an option.  Nothing else helped, so I just logged out.

I'm eunning on the HP ENVY 17 laptop right now.  It was recovered with the boot-repair disk that I downloaded and
burned to a CD.  It also seems to have installed itself on the laptop as a future tool.

Boot-Repair told me a few important things:
(1)  Grub2 had it that the /dev/dsa1 partition was removable.  No true, and I answered the question accordingly.
(2)  Boot-Repair told me that if I left Grub2 on my system, it would be unbootable.  I told it to take it off.
(3)  Boot-Repair purged Grub2 and replaced it with something else.  I don't know yet what it used
(4)  Boot-Repair gave me some sudo commands to run from the terminal.  I found a terminal icon on the lower
tool bar.  I did a copy-and-pasre (Ctrl+C to copy, Ctrl+Shft+V to paste).  Be sure to keep going Forward, as this
all takes several screens to complete.
(5)  You get a warning screen at the last from the system that if you don't install Grub, the system won't boot.
Boot-Repair does not prepare you for this.  I chose not to install Grub, which turned out to be the right choice.

I rebooted, and though the new boot process had not picked up on the plugged-in usb HDD as a possible
alternarive boot device, the choice I did nave booted me up on /dev/sda1 with no fanfare.  It works.

But it looks like there is good reason to mistrust Grub2 when it comes to installing correctly on some PCs,
particularly laptops.  That's the word from the developers of the Boot-Repair-Disk.  Best make a second
download, not just the Ubuntu iso, but also the Boot-Repair iso,  so that you can avoid the possibility of
getting stuck with a Ubuntu install that won't boot, and you lack a tool for getting past that point.

Not done on this thread yet.  Next need to see what Boot-Repair put there in place of Grub2, and what it
would take to add in a secondary boot device in the menu.  Not that I have to, I can get to a choice of
boot device via the Esc key or going to F9, or making changes in Systems Settings with the F10 key.
But those steps involve timing your key press to fit in a small time frame, whereas the boot menu  gives
you more time and you can see your choices on the screen.

---

