---
title: "Dual Boot"
date: 2010-06-01
forum: Hardware
---

### Post by YouStoleMyLaptop on 2010-06-01
[SIZE=4][COLOR=DeepSkyBlue][B]Hello, i have just downloaded Ubuntu and dual boot it. But now i like it so much I want to have this permanently with only one OS on the drive. How would i uninstall the Windows 7 on the other?

Edit:
& Sorry for if this is in the wrong section, I didnt know where to put it.
[/B][/COLOR][/SIZE]

---

### Post by BoneKracker on 2010-06-01
If you've just installed it, then the best way is to reinstall, telling the installer to use the whole drive.  It will wipe out everything on there.

If not, here is another discussion going on about this:
[http://ubuntuforums.org/showthread.php?t=1498643](http://ubuntuforums.org/showthread.php?t=1498643)

---

### Post by YouStoleMyLaptop on 2010-06-01
[SIZE=5][COLOR=DeepSkyBlue]Well, um, i dont really know much stuff about computer. So i need someone to do a live support with me via msn or something. Or someone who can talk me through it.[/COLOR][/SIZE]

---

### Post by varunendra on 2010-06-01
> **YouStoleMyLaptop said:**
> [COLOR=DeepSkyBlue]Well, um, i dont really know much stuff about computer. So i need someone to do a live support with me via msn or something. Or someone who can talk me through it.[/COLOR]

What do you do or wish to do with your computer.

Selecting Ubuntu as the only OS would only be great if you are an absolute beginner in computers (i.e., your brain isn't tuned up to Windows), or otherwise, if you have at least so much experience & understanding of them such that you can sort out things using command-line when & if needed.

I don't mean to discourage you from using Ubuntu. It really is great! But IMHO, you should stick to dual boot unless you qualify the above criteria.
Just an opinion though.:)

---

### Post by YouStoleMyLaptop on 2010-06-01
[SIZE=5][COLOR=DeepSkyBlue]Well, pretty much, i would stick to dual booting. But when i installed, i accidentally said to make it only 10GIG of memory. So now i need to uninstall windows 7 so that all the memory would be put into Ubuntu.[/COLOR][/SIZE]

---

### Post by varunendra on 2010-06-01
I assume that by "memory", you actually refer to "hard-disk space" (memory actually refers to RAM, & 10GB is too much for that for a normal user).

I also assume you have downloaded a "Live CD" iso of Ubuntu (the "Ubuntu Desktop" disk, instead of "Ubuntu Alternate")

So all you need is to boot from that live CD and use "GParted" from System>Administration menu to resize the Win7 partition & add the recovered space to the Linux (ext3 or ext4) partition.

I haven't used gparted myself to resize a Win7 partition though.
So be careful with your data on Win7 partition (take a backup first).

Edit: If you want to dual boot, you MUST allocate some space to the Windows partition on which it will reside. A 10-20 GB of Windows partition wouldn't hurt Ubuntu :). Besides, Ubuntu CAN use Windows partitions.

---

### Post by YouStoleMyLaptop on 2010-06-01
Hmm, i dont really know? Im still young..
& 
i just installed linux today. So i havent had really much to do with it yet.

---

### Post by varunendra on 2010-06-01
Just post your computer's specifications (Hard-disk space, RAM, Processor type & speed, etc.) and whatever you want to do on it, and maybe we can suggest an optimal partitioning plan to you.

And yes, we'd love to help you throughout the process provided you have a separate PC to stay online while you repartition the other.


Edit: if you find these terms hard, just answer the following:
1. Do you have a separate pc to stay online?
2. Can you boot into Ubuntu "Live Session" from the CD?
(If it is a live cd, it should give you an option to 'try Ubuntu without making changes to your computer' - when you boot from it)

---

### Post by YouStoleMyLaptop on 2010-06-01
> **varunendra said:**
> Just post your computer's specifications (Hard-disk space, RAM, Processor type & speed, etc.) and whatever you want to do on it, and maybe we can suggest an optimal partitioning plan to you.

And yes, we'd love to help you throughout the process provided you have a separate PC to stay online while you repartition the other.


Edit: if you find these terms hard, just answer the following:
1. Do you have a separate pc to stay online?
2. Can you boot into Ubuntu "Live Session" from the CD?
(If it is a live cd, it should give you an option to 'try Ubuntu without making changes to your computer' - when you boot from it)

hmm, i think i messed up something.. I went into places>computer 
& I right clicked on the drive named "100gb hard disk; 4.3gb free" & i pressed format and pressed format again. & Now when i go into computer. Its empty? what do i do?

---

### Post by varunendra on 2010-06-01
The best quick suggestion is:
DO NOT DO ANYTHING ELSE TILL WE CAN FIGURE IT OUT!!
Just stay online.

What all your Places>computer is showing?
(you can press "Print Screen" on your keyboard (above "Insert" Button) to take a screenshot, then save it on your Desktop & attach it with your post)

---

### Post by YouStoleMyLaptop on 2010-06-01
Yeah i will stay online, so u need my specs? If so, how would i find that?

---

### Post by BoneKracker on 2010-06-01
> **YouStoleMyLaptop said:**
> hmm, i think i messed up something.. I went into places>computer 
& I right clicked on the drive named "100gb hard disk; 4.3gb free" & i pressed format and pressed format again. & Now when i go into computer. Its empty? what do i do?

:lol:

(Sorry, if this is not trolling.)

---

### Post by varunendra on 2010-06-01
> **YouStoleMyLaptop said:**
> Yeah i will stay online, so u need my specs? If so, how would i find that?

Read my last post (I edited it). Do as I told in it.

Maybe some expert (I'm not one-mind you) can suggest a better way, but here's what may work for you:-
1. Goto System>Administration>System Monitor
2. On Window that opens up, selecting three of four tabs (one-by-one), take three different snapshots as I told in the last post. These snapshots would be of:
[LIST=1]
[*]"System" tab
[*]"Resources" tab
[*]"File Systems" tab
[/LIST]
3. Save these snapshots on desktop & post (attach) them here.


Edit: Do you have GParted listed in System> Administration?

---

### Post by YouStoleMyLaptop on 2010-06-01
Heere you go.

---

### Post by dino99 on 2010-06-01
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by varunendra on 2010-06-01
> **YouStoleMyLaptop said:**
> Heere you go.

Are you still able to boot into Windows?
I guess- 'not anymore'

How did you install Ubuntu previously?
I guess you booted into Windows7, inserted the Ubuntu CD which auto-ran, then in the popped-up window, you selected "Install within Windows".

From the snapshots what I get is an impression that your Win7 partition is still there, you've just formatted the boot partition.

I maybe wrong though.

---

### Post by YouStoleMyLaptop on 2010-06-01
I still have my windows 7 portion. I installed Ubuntu, by a program called "wubi" but, it just told me to write my username and pass, and how many gig's i want to put into the ubtuntu file so that i can use. & then it just said install. So i clicked it. & it installed like it was regularly.

heres a picture



& yes i can still boot into it, i just logged in
[IMG]http://www.ghacks.net/files/screens/2007/06/wubi-advanced.jpg[/IMG]

---

### Post by YouStoleMyLaptop on 2010-06-01
my bad i see that they dont accept links?

---

### Post by varunendra on 2010-06-01
> **YouStoleMyLaptop said:**
> I still have my windows 7 portion. I installed Ubuntu, by a program called "wubi" but, it just told me to write my username and pass, and how many gig's i want to put into the ubtuntu file so that i can use. & then it just said install. So i clicked it. & it installed like it was regularly.

heres a picture

[http://www.ghacks.net/files/screens/2007/06/wubi-advanced.jpg](http://www.ghacks.net/files/screens/2007/06/wubi-advanced.jpg)

& yes i can still boot into it, i just logged in
[IMG]http://www.ghacks.net/files/screens/2007/06/wubi-advanced.jpg[/IMG]

I'm unable to access the image. Maybe you can attach it as well as a file but it doesn't seem necessary.
The URL suggests that you perhaps used WUBI to install Ubuntu the way I guessed.

But now that you are still able to boot into Win7, then there should be no problem with the rest you need to do.

You can simply use the GParted tool provided in the "Live Session" to resize the Windows partition & create a new ext3 or ext4 partition from the recovered space to use with Ubuntu.

Alternatively, you can also do it the way dino99 told (follow his link)

The bottom line is: If you want to keep Win7 then just resize its partition, don't delete or format it.
Then you can either fresh-install Ubuntu or simply add the recovered disk-space as a new partition & keep your existing setup as it is.

---

### Post by YouStoleMyLaptop on 2010-06-01
So, then what if I want just the Ubuntu?
Because I only need a fast OS that i will use for surfing the web.

---

### Post by varunendra on 2010-06-01
> **YouStoleMyLaptop said:**
> my bad i see that they dont accept links?

Yess!
The image you've posted shows a WUBI window, exactly what I guessed!

Anyways, to just experience Ubuntu, it's a safe setup. 
But is not a standard one so there will be a slightly (marginal, in most of the cases, you won't even notice it) low performance output.

If you need a standard setup, then dino99's link is the way to go.

I'm going offline for now. Shall be back in 3-4 hrs. & hope to see some positive progress.

Good luck!

---

### Post by varunendra on 2010-06-01
> **YouStoleMyLaptop said:**
> So, then what if I want just the Ubuntu?
Because I only need a fast OS that i will use for surfing the web.

If you are sure you don't need Windows (& the data currently existing on your Hard disk) then the best way to go is post no #2 in this thread (BoneKracker's post).

Just boot from the Ubuntu CD, select Install, then select to 'use whole Hard disk' when asked.

---

### Post by YouStoleMyLaptop on 2010-06-01
but the thing is that i dont have any cd's to burn it onto.

---

### Post by varunendra on 2010-06-01
No problem if you have a usb stick (at least 1GB, or a usb hard disk), and your laptop can boot from usb (which I'm damn sure it can - given the specs you posted)

Just boot into your current Ubuntu, plug in the usb stick/hard-disk, goto System>Administration>USB Startup Disk Creator and select your usb device as the destination to install, & go.
Within 2 min. it should be ready to boot your laptop just like a cd would do.

---

### Post by YouStoleMyLaptop on 2010-06-01
Ohh. I see. I'll try it in a bit. Thanks for all your help :D


But, what do i do after that?

---

### Post by varunendra on 2010-06-01
> **YouStoleMyLaptop said:**
> Ohh. I see. I'll try it in a bit. Thanks for all your help :D 

Any time, mate!

> But, what do i do after that?

Prepare your usb stick first and try booting off it. If successful, then we'll proceed to final disaster (oops.... I mean final installation ;) )

---

### Post by YouStoleMyLaptop on 2010-06-01
Lol, hmm, never mind. I think ima keep the dual boot because im about to get an iphone & all my apps and music etc are on the itunes on windows 7. So yeah, but thanks for your help :D & dont delete this thread? I'll probably come back & use this one day.

& one more question,
What if i dont want the boot screen anymore?(the screen where you select if u want to boot from windows 7 or ubuntu)

---

### Post by varunendra on 2010-06-02
> **YouStoleMyLaptop said:**
> 
What if i dont want the boot screen anymore?(the screen where you select if u want to boot from windows 7 or ubuntu)

Which OS do you want to boot by default? (Win7 or Ubuntu?)

You can change your preference of default OS, then change the timeout to 0 (zero).

Post here (just copy-paste) the contents of the following files:
**/etc/default/grub**
and...
**/boot/grub/grub.cfg**

You can get a detailed info on 'GRUB2' boot loader (the program which presents & handles the boot-menu) [here]("http://ubuntuforums.org/showthread.php?t=1195275").
You can get some quick help [here]("http://ubuntuforums.org/showthread.php?t=1302743").

---

### Post by YouStoleMyLaptop on 2010-06-02
I did that, and a text doc popped up, what do i do?

---

### Post by varunendra on 2010-06-03
> **YouStoleMyLaptop said:**
> I did that, and a text doc popped up, what do i do?

When the text doc opens, press "ctrl+A" to select all the text, right-click on selected text & select 'copy'.
Then start here a new post & 'paste' the copied text in the post by right-clicking & selecting 'paste'.

Thing is, you have to show us what is displayed in those files.

If there's still some confusion, you may simply attach those files (/etc/default/grub and /boot/grub/grub.cfg) in your post.

PS: You didn't answer which OS you want to boot by default.

---

### Post by YouStoleMyLaptop on 2010-06-04
The first one:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

The second one:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 6ad077d3d077a44b
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

---

### Post by varunendra on 2010-06-04
You have to make changes only in the first file (/etc/default/**grub**).
DO NOT MAKE ANY CHANGE IN GRUB.CFG!

Here's what you need to do:
**1) _Changing Timeout_:**
Open terminal (Application>Accessories>Terminal). Type & enter this command (mind the case of letters):```
sudo gedit /etc/default/grub
```You will be asked for your password which you have to supply (terminal won't show any characters while entering a password! Just type & enter).

This will open the grub file on Gedit program in editable mode. Goto the (7th) line that says:```
GRUB_TIMEOUT=10
```10 is the no. of seconds that menu waits before booting into default choice. Change the value to 0 (zero). Now the line should look like:```
GRUB_TIMEOUT=0
```Save & close the file.

Return to the terminal & enter this command:```
sudo update-grub
```It will automatically update the grub.cfg file for new timeout (which is zero now)

Close the terminal & reboot to see the change. Since the timeout is now '0', you won't see the grub menu this time & would directly boot into Ubuntu.



You also asked what if you needed to access the Grub menu to boot into Win7. Here it is:
**2) _Accessing Grub Menu_:**
While the computer is booting, press and hold the 'Shift' key. It will bring up the Grub2 menu regardless of whether a secondary OS (Win7 in your case) is installed or not.



You may also wish at some point to change the choice of default boot option (for example, you may wish to automatically boot into Win7 instead of Ubuntu). Here's how to do it:
**3) _Changing Default Boot Option_:**
As per your boot.cfg file, there should be five options displayed in you grub menu in the following order:> Ubuntu, Linux 2.6.32-22-generic
Ubuntu, Linux 2.6.32-22-generic (recovery mode)
Ubuntu, Linux 2.6.32-21-generic
Ubuntu, Linux 2.6.32-21-generic (recovery mode)
Windows 7 (loader) (on /dev/sda2)Each of the above options is referred by its entry no. starting from zero. So the first option (Ubuntu, Linux 2.6.32-22-generic) is entry no '0', the second option (Ubuntu, Linux 2.6.32-22-generic (recovery mode)) is entry no. '1'..... and so on. This way, the fifth option (Windows 7 (loader) (on /dev/sda2)) is entry no. '4'.

To change the default boot option, open the /etc/default/grub file exactly the way you do to change  timeout:```
sudo gedit /etc/default/grub
```Goto the (4th)line that says:```
GRUB_DEFAULT=0
```Change the value to 4 (which is your Win7's entry no. in the grub menu). The above line should now look like:```
GRUB_DEFAULT=4
```Save & close the file.
Update the grub.cfg file by typing following command in the terminal:```
sudo update-grub
```Thus if you made both changes 1) & 3), then on rebooting, the computer will automatically boot into Win7 without displaying the grub2 menu. Of-course you can always access the menu by holding 'Shift' key down while booting.

But for what you asked, you only need to follow the instruction #1).
Hope you got what you needed.:popcorn:

---

### Post by varunendra on 2010-06-04
A silly mistake on my part! I completely forgot you installed Ubuntu inside Windows through WUBI.
In this case it must be the Windows boot menu that comes first with only two items on the list (Windows 7 & Ubuntu). So you'd have to tackle that one also (i.e., you'd have to change the default choice & timeout for that menu also).

The method to change the boot options in Windows is entirely different. You can find a typical one [here]("http://www.sevenforums.com/tutorials/2282-default-operating-system-change-default-boot-os.html").

To boot directly into Ubuntu, you'd have to change the default choice to 'Ubuntu' & **[COLOR=Red]timeout to '0'[SIZE=2] (DO NOT DO IT!!) [/SIZE][/COLOR]**(currently, the default settings would be- 'Windows 7' & '30')

This will make the first (Windows) boot-menu to skip & the methods in my above post will make the second (Grub2) boot-menu to skip.

To boot into Win7 later, you can use either the method in above post, or **[COLOR=Red]you can simply keep tapping F8 key while booting to bring up the Windows boot-menu [SIZE=3](WRONG-If Timeout is 'zero' !!)[/SIZE][/COLOR]**(which would skip if you don't tap the F8 key). There, you can select 'Windows 7' to boot.


**PS:** You only need to go through this double trouble because you installed Ubuntu 'inside' Windows. If you make a proper install, then only the above post is enough to get going!
[B]
PPS: [/B]Set the timeout to at least '1', or Windows would be screwed! (refer to post #39 of mine below)

---

### Post by YouStoleMyLaptop on 2010-06-04
it doesnt show anything when i try to type my password
Edit:
sorry i didnt read it throughly

---

### Post by YouStoleMyLaptop on 2010-06-05
Omg, thank you! This helped me so much, is there anyway to thank you or something?

---

### Post by varunendra on 2010-06-05
> **YouStoleMyLaptop said:**
> Omg, thank you! This helped me so much, is there anyway to thank you or something?

Yes, you can do two things:

[LIST=1]
[*]post here how it is going now,
[*]if it is exactly what you wanted, mark this thread as [solved]
[/LIST]
**PS:** [I]The fact that you tried everything you were told without complaining or demanding a shortcut- is a good sign. Seems you may learn a lot from Ubuntu! Just keep in mind one thing- while you do what is told by others, try to understand the fundamentals working behind the scenes. After all it is the fundamentals that decide the real strength of your knowledge or understanding of things. You can always demand an explanation of actions here and most often- people would be more than happy to explain if they can.
[/I]
Cheers! :popcorn:

---

### Post by YouStoleMyLaptop on 2010-06-06
1.
It is going great now. Everything has helped me out & my knowledge for ubuntu has been expanding ever since Varunendra has helped me. He is so helpful.

& I would like to thank you again for all the time that you have helped me.

---

### Post by varunendra on 2010-06-07
Pleasure is mine!:)
And your feedback is as much appreciable. For it sometimes helps us dealing with problems without actually facing them.

*(The feeling that you can be helpful is the feeling of ultimate satisfaction, even if it is momentarily.)*

---

### Post by varunendra on 2010-06-14
> **varunendra said:**
> In this case it must be the Windows boot menu that comes first with only two items on the list (Windows 7 & Ubuntu). So you'd have to tackle that one also (i.e., you'd have to change the default choice & timeout for that menu also).

The method to change the boot options in Windows is entirely different. You can find a typical one [here]("http://www.sevenforums.com/tutorials/2282-default-operating-system-change-default-boot-os.html").

To boot directly into Ubuntu, you'd have to change the [COLOR=Red]**default choice to 'Ubuntu' & timeout to '0' **[/COLOR](currently, the default settings would be- 'Windows 7' & '30') ................ .............. ............... ................ ....................  To boot into Win7 later, you can use either the method in above post, or you can simply keep tapping F8 key while booting to bring up the Windows boot-menu ....... There, you can select 'Windows 7' to boot.
I'm afraid I made a critical mistake while suggesting to set the timeout to 'zero' in the above post.
After hearing about problems in booting into Windows again, I tried the whole thing myself (on VMware) & found that once the timeout in Win7 (in Vista also- I assume) is set to zero, the F8 key no longer brings up the 'Advance Boot Menu' (as opposed to 'Prior-to-Vista' versions). In fact- I could find no way to interrupt the boot menu or pause at OS selection screen. So I thought I should post here the [SIZE=4][COLOR=DarkRed]**critical issues people using Ubuntu (WUBI) over Windows 7 should be aware of:**[/COLOR][/SIZE]

[LIST=1]
[*]_**Once the boot menu [COLOR=Black]timeout [/COLOR]in Windows 7 (maybe in Vista also) is **_**_[COLOR=Black]s[/COLOR]_[COLOR=Red]_[COLOR=Black]et to zero,[/COLOR]_ the F8 (or any other key) no longer brings up the 'Advance Boot Menu'[/COLOR]** or interrupts the boot menu to pause at OS selection screen. [COLOR=Red]**Thus making it impossible to select a 'Non-Default' option.**[/COLOR]
[*]_**If Ubuntu is set to default **_in Windows Boot Menu, then even though you still have the option to [COLOR=Red]**select Windows 7 in Grub**[/COLOR] menu, it **[COLOR=Red]actually sends you back to the Windows Boot Menu.[/COLOR]**
[*]_**Combining the above two (Windows menu timeout=0, Default=Ubuntu)**_, [COLOR=Red]**it becomes impossible to boot into Windows again.**[/COLOR]
[*][SIZE=2]_**Solution:**_[/SIZE] Once trapped in this situation, [COLOR=Red]**using bcdedit**[/COLOR] tool [COLOR=Red]**from Windows 7/Vista installation DVD**[/COLOR], or from WinPE disc, or from Windows Recovery Disc [COLOR=Red]**to reset timeout**[/COLOR] is the only way I could find after a lot of googling. Of these, only the installation DVD is 'ready-to-use' solution. The other two- you need to build ones for yourself while Windows is running!:(
[/LIST]

[B]_Using bcdedit_: 
[/B]
[LIST=1]
[*]Boot from installation DVD.
[*]After choosing 'language', select '**Repair Your Computer**' instead of 'Install Now'.
[*]The console should search & list your windows installation. Selecting it, press 'next'.
[*]In the next screen, select the last option 'Command Prompt'.
[*]In the command prompt type- ```
bcdedit /timeout 4
```here '4' is for example. You may change it as per your convenience. (set it at least '1')
[*]You should get 'command completed successfully' message. type 'exit' (without quotes) and press restart.
[/LIST]

[B]_The bottom line is:_
[/B][B]If you're using WUBI to install Ubuntu 'on' Windows 7 (or Vista), and wish to set 'Ubuntu' as default boot option, [SIZE=3][COLOR=DarkRed]DO NOT SET THE TIMEOUT TO 'ZERO'!! Set it at least to '1'!!!!![/COLOR][/SIZE]
Otherwise, keep the Installation DVD handy[/B];)

---

### Post by Ceedub2 on 2010-06-23
> **YouStoleMyLaptop said:**
> hmm, i think i messed up something.. I went into places>computer 
& I right clicked on the drive named "100gb hard disk; 4.3gb free" & i pressed format and pressed format again. & Now when i go into computer. Its empty? what do i do?
I can tell you I have formated something when I first got my pc. Luckily it was just a program called first choice and a 5 1/4" floppy(if you know what a floppy is). 

I kinda forgot about that till now. Now I'm showing my age.

---

### Post by mrdusty on 2010-07-11
I pulled a swift one!  I used wubi to install ubuntu inside windows 7.  All worked well.  Then, days later in a moment of ignorance, looking at c:// I noticed ubuntu .  Dumb my I deleted the folder.
Still get the dual boot at start up, but erroes when click on uuntu (naturally!).
How can I get rid of that boot startup?
I reinstalled ubuntu with wubi, hoping that I'd get the file then I could delete it that way.
Got two ubuntu's to boot from.
Can't find wubi1dr,mbr on drive any where.
Thanks,
Rich

---

