---
title: "Please HELP! My computer was ruined by Ubuntu!"
date: 2008-11-29
forum: General Help
---

### Post by water911 on 2008-11-29
I decided it was about time to try Linux. So I decided that Ubuntu would be the best choice, and I guess it is, but it ruined my computer.

When I decided to install it, I pushed the button that says "Help me to boot from CD". That was after I had already simply pushed reboot now of course. I had left my computer, and and forgot about the disk. So I just pushed help me to start from CD. That is why.

The first time I restarted, like always, even when installing a new OS, it showed the normal OS display window. This is while doing multiboot. This time however (after I used help me to boot from CD), this new window came up, and it apparently altered something apparently like my Master Boot Record (that I am not certian). I was truly at this point not bugged by this, I figured that it would let Windows take back over this configuration if I Uninstalled Ubuntu. So later I felt cramped up in Ubuntu, as none of my needs were filled by this OS (please don't ask about this, only the real problem).

From here, I simply uninstalled Ubuntu on windows. Later on in the day while on windows, I noticed it was not displaying firefox correctly, and games were displaying irradicly. This simply gave me the idea to restart my computer. When restarted, I do not remember what it said, but I know that it was not going to do anything. It simply sat there with nothing to boot at all. So I took the installation CD and re-installed Ubuntu. Then I could get on Windows and go look on the Internet for similar problems. From what I have learned about this issue, it is most likely my master boot record which has been altered by this. Apparently the people who made Ubuntu diden't expect you to uninstall it.

This makes me mad, and being a Microsoft supporter, I was only trying out the other side and being un-biased about this. In the process, I lost my computer. Currently, I have created a 4gigabyte partition on my hard drive containing Ubuntu so that I can use windows.

Someone please explain what has happened. Remember, I used the "Help me to boot from CD" option while installing a full copy of Ubuntu from the newest version's Live CD.

I would be made extremely happy by anyone willing to solve this problem. Please, I beg for any help, I have already had to re-install my OS for something else stupid, I don't want to have to just for Ubuntu's mistake!

PS: I am using Vista. I am using an Acer vista which is not compatible with the normal Vista's Recovery Disk. Vista does also have no way of repairing the MBR from the Command Prompt.

Thanks!

~water

---

### Post by wjp.reg on 2008-11-29
you could check out [this thread]("http://ubuntuforums.org/showthread.php?t=665586").

Good Luck.

---

### Post by Xiong Chiamiov on 2008-11-29
When you first installed it, where you using Wubi, or the normal installation disk?  If the latter, you'd have had to boot into a version of Ubuntu that was running off of the CD in order to install.

When you start up, does GRUB list Windows as an option as well as Ubuntu?  If so, does it work?  If not, what error message do you get?

---

### Post by 10nitro on 2008-11-29
"the normal OS display window"
this is called the "bootloader"  Now, Windows used NTLDR (New Technology Loader), but Vista uses some new fancy boot loader I don't know the name of.  Ubuntu (and many other Linux distros) use GNU GRUB (GRand Unified Bootloader), the boot loader for the GNU operating system.

When a computer boots first it loads the BIOS from a ROM chip on the motherboard.  Then the BIOS checks the CMOS (another chip) to see what the boot device is.  If it is a hard drive, then it loads the first sector of the drive, or the MBR.  It does this because the BIOS is not sophisticated enough to recognize partitions.

So, we developed boot loaders, small programs that can fit into the MBR, to load an operating system.  However, we soon decided that this is not enough- we wanted menus and such, so they expanded onto partitions.  Now, the part of the bootloader on the MBR loads the rest of the bootloader, which in turn loads the operating system.

In GRUB, the part on the MBR is called stage1, and the part of it on a partition is called stage2.

Ubuntu installed stage2 of grub on the same partition as it, so when you delete the Ubuntu partition, you delete GRUB stage2.

What you have to do is reinstall the MBR part of Vista's bootloader.  Now there should be a command line option to do this on the [Vista Recovery CD]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

Or, you can keep using GRUB. (After Ubuntu has been uninstalled) boot up the Ubuntu CD.  Use GParted (System->Administaration->Partition Editor) to create an new EXT2 partition.  Look what its name is (probably "/dev/hda2").  Open the terminal.  Type ```
sudo mkdir /mnt/grub/
sudo mount /dev/*xxxx* /mnt/grub/
sudo mkdir /mnt/grub/boot/grub/
sudo gedit /mnt/grub/boot/grub/menu.lst
```
In GParted, find the Vista partition. It is probably "/dev/hda1" whatever that number is, subtract 1.
Here is menu.lst:
```
default         0
timeout		10

title		Windows Vista
root		(hd0,*the number we just found*) 
savedefault
makeactive
chainloader	+1

```
open the terminal. Type "sudo grub". Type "find /boot/grub/menu.lst" remember what this says. Type "root (*whatever you're remembering*)"  Type "setup (hd0)"

---

### Post by bodhi.zazen on 2008-11-29
> **water911 said:**
> <clip>Someone please explain what has happened. <clip>

I am sorry Ubuntu did not work out for you. Please do not take this the wrong way, but what happened is you installed an OS without understanding what you were doing or making a back up.

Your computer is not in any way "Damaged" and you say Windows boots normally (with Ubuntu installed).

In a nut shell, GRUB has been installed and your Windows boot loader removed.

This is easily fixed :

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

Again, I am sorry you had this experience, but the lesson should be :

Do not alter your computer without both making a back up first and understanding what you are doing. There is a world of difference between a faulty OS and faulty understanding (and you seem to be in the latter).

Again, I do not mean to come across as harsh or flippant, but next time you partition your hard drive and install an OS take more care. With any install CD (Windows included) you can easily do irreparable harm / data loss.

---

### Post by eldragon on 2008-11-29
something you complain about i wanna rectify:

no operating system i know of expects the user will want to 'uninstall' it, the whole idea seems pointless.

thinking ubuntu, or linux is a regular program is a bad misconception, probably thanks to wubi.

i bet you would have had a much better experience if your computer had been preinstalled with linux.

to fix your MBR (giving that you didnt delete any windows partitions) you need to pop any vista disc, and boot into the recovery console, there run fixmbr

---

### Post by scottmac112 on 2008-11-30
Yeah, especially a Microsoft OS. They're so fricking cocky that they don't even think that there's another OS out there. So they rig this new Vi$ta bootloader to wreck whenever GRUB is installed over it. I've trashed three Vi$ta installations on my laptop installing Ubuntu. But I do agree that this was in no way a fault of the Linux community. I think that you (and I assume from the types of words you use that you know some of what you are doing) removed a partition, completely disregarding what it might have had on it. Don't blame the developers. You uninstalled it by trashing your own system. Ponder on that before you blame the entire Linux community for your "ruined" computer. 

Go pay Father Gates for another $200 Vi$ta license. Good luck.

---

### Post by water911 on 2008-11-30
Sory, I know I should have used Wubi, as my freind had told me to in the first place. I have been thinking it over and would like to give Ubuntu another try. If someone could please point me in the direction of the commercial Windows/.exe emulator, that I would appreciate greatly!

I have gotten plenty of responces and definitely know what to do now. I am suprised immensely by how many responses I got. I now have to re-think the Linux community. Also, thanks for your opinions. I like to see each sides oppinions and each side's facts. So, in this way, I think I will have a look around on the forums, so I can get a better look at Ubuntu.

If anyone would suggest to me another Linux OS, I would appreciate that too. I tried OpenSUSE on Virtual Box before, but I suppose that diden't tell me very much.

I would just like to have a OS that can do everything windows can do, but not have all the background programs that I don't need. For instance, I would like to have the computer constantly check for Wi-Fi hotspots/routers like Windows dose. Simple things like that. Yes, I know I can use task manager to assign the computer to these tasks on a set schedule, but I would rather not, as it is quite a lot!

So I was hoping someone could answer some of these questions for me while they are still here.

Thanks for any answers again!

~water

---

### Post by The Cog on 2008-11-30
If you can't persuade Vista to replace its bootloader, there are other live CDs that you can use to install a bootloader. Google for "live rescue CD". Grub isn't suitable for this since it relies on a larger second stage that is located on another partition, normally a Linux partition of course.

I'm surprised you say Ubuntu doesn't constantly check for wireless - I think the 8.10 network manager does, and wicd ( a better network manager in my opinion) sertainly does. 

You will have noticed that Linux is different to Windows. Some things are not as good as windows, some things are a helluvalot better. of course, when you first try it out, it is the things that are missing or different that you notice first, because you aren't looking for the things that are better, because you don't even know they are there. It's like when you move to another country - you notice you can't get some of your favourite foodstuff long before you get so you can't live without some of the new foodstuffs that you had never tasted before. Linux isn't inferior, it's just different.

---

### Post by CatKiller on 2008-11-30
> **water911 said:**
> I would just like to have a OS that can do everything windows can do, but not have all the background programs that I don't need.

I think that you are probably approaching this from the wrong direction. If you want something that's "just like Windows, only better," then you will be disappointed with GNU/Linux. You will be frustrated by the differences and see them as failures. There are unofficially-stripped-down versions of Windows that would probably serve your needs better. I seem to recall hearing the name XPLite, although I've never used it. I haven't used Windows XP for that matter, either.

If you want something that is *different*, then you will probably be quite pleased with GNU/Linux. The things that make GNU/Linux better than Windows, in the eyes of its users, are the things that are very much different. It's a difficult thing to accept, especially if you feel that you are good with computers because you are good at manipulating Windows, but the skillset is quite different. You will struggle as you find that you don't know how to do things that you thought you knew how to do before.

If you have accepted that it will be different, and that you'll need to learn a great deal of new skills, and are eager to learn, then you'll find using GNU/Linux a **very** satisfying experience.

Welcome to the community.

---

### Post by oldos2er on 2008-11-30
The OP might want to read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by radiusbroken on 2008-11-30
how do you post a NEW message in this forum?
Also, how do you subscribe to that post so you can read the replies?
Sorry to threadjack, but this info isn't in FAQ and I have been looking for awhile.

---

### Post by Tobster on 2008-11-30
I don't understand because if you install the Ubuntu live CD or DVD Ubuntu is running off the CD or DVD and so the hardware does not touch you Windows partitions at all - it impossible to do anything to your actual computer with the Live CD.

If you did make the jump and installed Ubuntu and shared your hard drive with Windows.  You may have to reset the boot lodger or simply press the arrow key to Windows when you turn your computer on because the computer is looking for Ubuntu.

Re-setting the boot Logger is not hard but I do not know how to do it so it best to follow the advice above.

But Ubuntu on installation does warn you that if your going shrink your Windows partitions that you could lose any work if they are using those partitions (I personally have never lost anything)  But it is REALLY important to back-up your desktop or save any work if your planning to install a second Operating System. so that that you can recover any lost files after installation. 

Windows itself will never get damaged from installing a second OS but you can lose things like Office documents like your Word, Excell documents and other things you may have saved like your fav game that you installed, for  example...

The rule is to BACK UP... Like I keep telling all the student and staff at the college who e-mail me once they lost something!!!! :)

---

### Post by bodhi.zazen on 2008-11-30
> **water911 said:**
> If anyone would suggest to me another Linux OS, I would appreciate that too. I tried OpenSUSE on Virtual Box before, but I suppose that diden't tell me very much.

I would just like to have a OS that can do everything windows can do, but not have all the background programs that I don't need. For instance, I would like to have the computer constantly check for Wi-Fi hotspots/routers like Windows dose. Simple things like that. Yes, I know I can use task manager to assign the computer to these tasks on a set schedule, but I would rather not, as it is quite a lot!

~water

It depends on what you are wanting exactly ...

Linux is not a drop in replacement and for the most part I would not expect your windows applications to run on Linux.

With that said, every OS has advantages and disadvantages. I would suggest your try the "Majors" -> Fedora, Debian (very similar to Ubuntu), SUSE. You might consider Slackware, Arch, or Gentoo, but those latter 3 have steep learning curves.

What is wrong with Ubuntu ?

Wifi can be problematic on any OS, including Windows.

---

### Post by Yellow Pasque on 2008-12-01
I always come back to Ubuntu as my main system, even though it has a "n00b" reputation and I consider myself a more advanced Linux user. I tried Debian and it's nice, but mixing and matching stable(etch) and testing/unstable packages is a good way to give yourself a migraine. Ubuntu's repo system is a lot more straightforward.
Fedora 10 Preview seemed pretty sweet to me in my short time using it. Unfortunately, I needed that disk for something else. I plan to reinstall it once I get my partitions/disks the way I want them.
If you're into minimalism and willing to learn, Arch Linux is very nice. Just be sure to follow the wiki when you install the first time. I've tried Gentoo in the past, but I found it too time-consuming and ultimately opted for Arch Linux instead. I do like Gentoo's package management though.

---

### Post by david819 on 2008-12-01
If you are looking for a stripped down version of Vista, just buy Vista OEM, it's half the price, and there are NO advertisements, trial programs or any of the other trash that fills retail versions.  If you would like to dual boot Vista and Ubuntu, and are more comfortable with Windows, use EasyBCD as your bootloader.  It is windows based, and has a very nice tutorial for setting up with Ubuntu:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

