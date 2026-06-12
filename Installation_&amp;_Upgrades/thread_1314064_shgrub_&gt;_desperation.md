---
title: "sh:grub &gt; desperation"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2009-11-04
sorry if this mail is duplicated.. it is because of error in the title.
I have installed 9.10 with wubi, no matter how many times I install, when I launch it I land in console
sh:grub> how can I launch the desktop from there ?

---

### Post by nahmsath on 2009-11-06
I am having the same problem with my HP Mini 110. I installed Ubuntu Netbook Remix 9.10 with Wubi from Windows XP. On start up, the first Menu showing Windows and Ubuntu Netbook Remix is not working for ubuntu. It is only after selecting Windows XP that appears a second menu for Ubuntu and Windows (curious!!). But when i selected Ubuntu, then comes this screen:

                    GNU GRUB version 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device/file completions ]

Sh: grub > _


Any help will be appreciated.

Many thanks!

---

### Post by hoboy on 2009-11-06
> **nahmsath said:**
> I am having the same problem with my HP Mini 110. I installed Ubuntu Netbook Remix 9.10 with Wubi from Windows XP. On start up, the first Menu showing Windows and Ubuntu Netbook Remix is not working for ubuntu. It is only after selecting Windows XP that appears a second menu for Ubuntu and Windows (curious!!). But when i selected Ubuntu, then comes this screen:

                    GNU GRUB version 1.97~beta4

[Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB lists possible
device/file completions ]

Sh: grub > _


Any help will be appreciated.

Many thanks!

I did reinstalled it 3 times the third times I was lucky.

---

### Post by lordofallhearts on 2009-11-06
You get this problem once the update manager upgrades grub.I am using Karmic since RC , and got it 3 times and there is not a single solution response that I have come across.Please ....I dont wanna reinstall....Help

---

### Post by jheaton5 on 2009-11-06
if you know your kernel you can load the kernel with the command kernel <kernel name>.  Then you must boot the kernel with the command boot <kernel name>

---

### Post by lordofallhearts on 2009-11-06
@ Jheaton5
Thanks for response , but this doesn't work .
There's no command in Grub by the name of kernel.
By the way , the Kernel is 9.10 kernel 2.6.31-14-generic

---

### Post by jheaton5 on 2009-11-06
Well, you may be right.  I just used this procedure to get out the same situation, but now that I recall that was in grub-legacy not grub2. 

See this article on the [grub2 shell]("http://grub.enbug.org/Manual#GrubShell").

---

### Post by lordofallhearts on 2009-11-06
God knows what the solution is ,I have tried various things and have lost data 3 times. I'm not going to install 9.10 now and will revert back to 9.04 for sure. Its really bad that we could not develop a stable release of Grub2 , while everybody was talking and focusing on grub2 in this flavor of Ubuntu.That shows how amature we are.Hoping Google would come soon with ChromeOS.  What a shame

---

### Post by pdoes on 2009-11-06
When in the shell try:
```
linux /boot/vmlinuz-2.6.31-14-generic ro
initrd	/boot/initrd.img-2.6.31-14-generic
boot
```

If this boots open a terminal:
```
sudo update-grub2
```

---

### Post by lordofallhearts on 2009-11-06
thanks pdoes
but it doesnt really work
after the boot command the screen flashes , and lo ... we endup in initramfs

but thanx anyways

---

### Post by jheaton5 on 2009-11-06
> **pdoes said:**
> When in the shell try:
```
linux /boot/vmlinuz-2.6.31-14-generic ro
initrd	/boot/initrd.img-2.6.31-14-generic
boot
```

If this boots open a terminal:
```
sudo update-grub2
```

Thanks for that.

---

### Post by lordofallhearts on 2009-11-06
Doesnt work.....Doesnt work..........DOESNT WORK

---

### Post by jheaton5 on 2009-11-06
From the link I posted before: > Using the Command Shell

What You Boot Is What You Get. Also note that there are multiple shells/modes available, as indicated by the prompt.

grub>

The sh:grub> prompt indicates the the computer has found grub, and on a PC, that generally means it has found the hard disk. If something is wrong with the menu, it drops to this shell. Although it looks unhelpful to see this, there are a number of commands available to locate, load, and boot a kernel and related files (such as an early userspace).

Here are some commands (regular grub shell, not the cool lua one):

    *

      help - a command that annoyingly scrolls all the useful commands past your screen size.
    *

      ls / - this command does two things at once. First, it shows you what grub is using for /boot. Second, you see what files are there. Some of these are likely to be kernels and initrd. Hmmm....maybe we can load one of those....
    *

      ls - by itself this command is really handy to let you know what devices can be seen by grub's drivers.
    *

      cat /grub/grub.cfg - Even though the /boot partition has a /grub/ dir there, grub itself see this as / so this is the path you'll use to see what's in grub. This command lets you see what grub was trying to use. You can permute one of these stanzas into some bootability.
    *

      cat /boot/grub/grub.cfg - maybe you don't have a separate boot partition. In that case, you really do use a full path.
    *

      [COLOR="Red"]linux /vmlinuz<-your_version_here> [root=/dev/<something>] [some_other_kernel_option] [...] will actually load the kernel into RAM. If you see something similar to [Linux-bzImage, setup=0x3000, size=0x3593e0] then grub found the kernel and loaded it. Note the root= item passed here is just a string to grub, it is neither an env var nor the root command.[/COLOR]
          o

            linux (hd0,2)/boot/vmlinuz-<alternate_version> root=/dev/sda2 is a more complicated example of how to boot a kernel from the second partition. 
    *

      linux16 /memtest86+.bin 16-bit (b)zImage images such as Memtest86+ require "linux16" rather than "linux"
    *

      initrd /initrd-<your_initrd> loads the initrd (if you need one).
    *

      [COLOR="Red"]boot - as Picard would say, "Engage." [/COLOR]

---

### Post by lordofallhearts on 2009-11-06
This too doesnt work.I've tried things before from your previous post.

Sorry.Doesn't Work

---

### Post by DarthBrady on 2009-11-06
Having the same problem. Installed 9.10 with wubi. All was fine until Update-Manager installed a grub update today, now I get the same thing when trying to boot.

---

### Post by pdoes on 2009-11-06
In the grub shell, what is the result of:
```
cat /boot/grub.cfg
```

or 
```
cat /grub.cfg
```

---

### Post by DarthBrady on 2009-11-06
> **pdoes said:**
> In the grub shell, what is the result of:
```
cat /boot/grub.cfg
```

or 
```
cat /grub.cfg
```

"file not found"

---

### Post by lordofallhearts on 2009-11-06
error: file not found
for both commands

---

### Post by pdoes on 2009-11-06
How about
```
cat /boot/grub/menu.lst
```

or
```
cat /grub/menu.lst
```

---

### Post by DarthBrady on 2009-11-06
I guess I'm going to try to reinstall GRUB 2 from the 9.10 LiveCD. I found some instructions here on the forums @ the "Grub 2 Basics" thread:

> Reinstalling GRUB 2 from LiveCD
If you cannot boot from GRUB 2 and need to reinstall it:

    * Boot to the 9.10 Karmic LiveCD Desktop.
    * Open a terminal - Applications, Accessories, Terminal.
    * Determine your normal system partition - `sudo fdisk -l` (That is a lowercase L)
    * If you aren't sure, run `df -Th`. Look for the correct disk size and ext3 or ext4 format.
    * Mount your normal system partition:
      Code:

      sudo mount /dev/sdXX /mnt

          o Note: substitue the correct partition: sda1, sdb5, etc.
          o Note: GRUB 2 counts the first drive as "0", but the first partition as "1"
    * Only if you have a separate boot partition:
          o
            Code:

            sudo mount /dev/sdYY /mnt/boot

            with sdYY being your /boot partition designation.
    * Note: If you have any other system partitions such as "/usr" these should also be mounted in a similar manner.
    * Mount devices:
      Code:

      sudo mount --bind /dev/ /mnt/dev

    * Chroot into your normal system device:
      Code:

      sudo chroot /mnt

    * Reinstall GRUB 2:
      Code:

      sudo grub-install /dev/sdX

    *
          o Note: Substitute the correct device - sda, sdb, etc. Do ''not'' specify a partition number.
    * Verify the install:
      Code:

      sudo grub-install --recheck /dev/sdX

          o Note: Substitute the correct device - sda, sdb, etc. Do ''not'' specify a partition number.
    * Exit chroot: CTRL-D
    * Unmount devices:
      Code:

      sudo umount /mnt/dev

    * If you mounted a separate /boot partition:
      Code:

      sudo umount /mnt/boot

    * Unmount last device:
      Code:

      sudo umount /mnt

    * Reboot.


Maybe that will work. So far I only know this:

-I have 9.10 installed on 3 PCs. One installed via Live CD, and two installed via Wubi.

-All 3 PCs installed the grub updates via 'Update-Manager' today.

-The PC with 9.10 installed via the Live CD still boots fine.

-Both PCs with 9.10 installed via Wubi, have this issue now! 

-***After updating, the 9.10 PC installed via the Live CD updated, it asked me which grub menu settings to use (like always - "package maintainer's version, side-by-side comparison," ect.) The 2 9.10 PCs installed via Wubi DID NOT ask me at all after installing the update, it just reported "your system is up to date" like a basic update and closed out.


Could it be possible this is  some sort of bug with this update I installed today?

---

### Post by lordofallhearts on 2009-11-06
Error File not Found for this too

---

### Post by nahmsath on 2009-11-06
> **pdoes said:**
> In the grub shell, what is the result of:
```
cat /boot/grub.cfg
```

or 
```
cat /grub.cfg
```

Thank you very much for the assistance so far...

I got the same (initramfs) failing prompt and when i cat /boo/grub/grub.cfg from sh:grub> prompt, it shows an incomprehensible content made of squares.

Does it mean, my grub config file is corrupted at this stage??

Many thanks.

---

### Post by pdoes on 2009-11-06
> **nahmsath said:**
> Thank you very much for the assistance so far...

I got the same (initramfs) failing prompt and when i cat /boo/grub/grub.cfg from sh:grub> prompt, it shows an incomprehensible content made of squares.

Does it mean, my grub config file is corrupted at this stage??

Many thanks.

Yep it sounds like it.

Try the following in the grub shell:
```
cat /boot/grub/device.map
```

For me the result is:
```
(hd0)	/dev/sda
(hd1)	/dev/sdb
```

My root partition is on /dev/sda1
Next:
```
root (hd0,1)
setup (hd0,1)
```

---

### Post by pdoes on 2009-11-06
For booting try this is in the shell.

```
root(hd0,1)
linux /boot/vmlinuz-2.6.31-14-generic ro
initrd	/boot/initrd.img-2.6.31-14-generic
savedefault
boot
```

---

### Post by nahmsath on 2009-11-06
[QUOTE=pdoes;8258777]Yep it sounds like it.

Try the following in the grub shell:
```
cat /boot/grub/device.map
```[QUOTE=pdoes;8258777]

Same result as cat /boot/grub/grub.cfg

Obviously i can't run the following root (hd0,1) -----> filesystem is NTFS. How else can i get my partition infos

I recall that i am installing it from Windows using Wubi!

Thanks.

---

### Post by icarusburn on 2009-11-07
I installed Karmic Koala using wubi onto an Asus 1101-HAB netbook, after copying the latest remix iso to the root directory of a usb copied with the contents of the iso, and I have the same issue.  

The root is (loop0).  As someone else posted, a cat of /boot/grub/device.map and grub.cfg are just full of zeros.  The version of grub is 1.97~beta4. There is no savedefault command.  Anyway, as someone else posted, after loading the linux kernel and initrd and booting, the usual boot messages appear until:

  Begin: Waiting for root file system... ...

Eventually that times out and the following messages appear next:
=== snip ===
Done.
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the syste wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls/dev)
ALERT! does not exist. Dropping to a shell!


BusyBox v1.13.3 (Ubuntu 1:1.13.301ubuntu7) builti-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
=== snip ===

Still working on how to get around this.

---

### Post by kaelonlloyd on 2009-11-07
I'm also having this problem, but i've been following this site
[https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)
So far with no luck. I think that i'm not giving the computer the right device name (e.g sda1, sda2)

---

### Post by lordofallhearts on 2009-11-07
Wow , so finally Ubuntu is matching up with Microsoft!!!!!
Earlier it used to be seamless.Now it is becoming buggy and pain in the a**.

---

### Post by hoboy on 2009-11-07
Well I know ubuntu is testing with us that is also ok, but it is a bit serious this time the challenges we are facing.
I am back to windows before the situation stabilised, as I am not harcore linux person, this makes me very sad actually as 9.04 is great and lovely product... what has happened with 9.10 ?

---

### Post by lordofallhearts on 2009-11-07
I've been using Ubuntu for past 3 years and its kinda hard to go back to Windows.I had this problem when I installed the beta and RC of Karmic.Yesterday when Grub wanted to upgrade , I allowed it to do so because I was now using the stable release.The thing that really pisses me off is that Ubuntu allowed the update before testing it extensively.If one would search this forum , he  will find out that grub2 is causing problems not only for fresh installs , but also for upgrades. How can Canonical be so casual while all the time you boasted about Grub2 being "the" feature of Karmic and all that b***s*** about Grub2 reducing bootup and shutdown dramatically?

And more than being casual and dumb , how can Canonical be so insensitive ? People must have lost lots of data , which could have been photographs , Documents and things of personal importance.Don't runoff to touch deadlines (like 6 months release) if you are not capable of producing stable software.

Canonical , please be serious on something like this . Things like Grub when get down , take the whole OS alongwith it , so atleast test these things before releasing them for update manager. Be careful , because there are Goliaths like Google lurking to eat you up.

---

### Post by josephdietrich on 2009-11-07
FYI,

I had a similar problem with Wubi and Ubuntu 9.10. Everything had been working fine, then I installed the grub update that showed up in the Update Manager and on next boot I was at the grub shell.

I fixed it by following Zhmurov's directions in this thread (first entry after the bug's description):

[After 9.10 grub update can not boot into Wubi install]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/477104")

I don't know if this totally fixes the problem. Foolishly, instead of being methodical about it, once the system booted normally the first time I:

[LIST=1]
[*]went to System > Administration > Synaptics Package Manager,
[*]searched for grub-pc,
[*]right-clicked on the entry in the list and selected "Mark for Reinstallation",
[*]and the applied the changes.
[/LIST]
This definitely fixed the problem for me, and now my system boots normally again. But I don't know if the reinstallation is the thing that fixed it or not.

---

### Post by jheaton5 on 2009-11-07
I couldn't find in the thread if this has been suggested.  All of you having trouble have one common denominator.  You installed Ubuntu from windows using wubi.  Have you considered downloading the live CD from the Ubuntu site and doing a fresh install with the CD?  If you have any data you can back it up with the Live CD before doing a fresh install.

---

### Post by hoboy on 2009-11-07
As I have mentioned before my solution was to keep rinstalling untill it worked... I haven't faced it ever since.
but that is not a strategy one will recommand.
I will wait 3-4 weeks then get back to ubuntu, not before.
I am doing all my developements on Eclipse and Netbeans on windows

---

### Post by icarusburn on 2009-11-07
I was able to get a good install by starting over and copying wubi and the iso to the windows drive.

Still dropped into grub, but the following booted successfully, instead of dropping into initramfs:

  root (loop0) <== may be unnecessary
  linux /boot/vmlinuz...
  initrd /boot/initrd...
  boot

and this time it did not drop to initramfs!
 
However, it is sloooow and after 10 or 15 minutes of web browsing while waiting for updated to download in the background, video switched to a jumble of colored static. Some type of driver failure.

Not sure if I will keep the netbook, due to poor performance. Need to determine if it is purely a video driver issue. May be as it appears to be primarily vid lag. The Asus 1101-HA supposedly has a better vid chipset.

---

### Post by jheaton5 on 2009-11-07
> **hoboy said:**
> As I have mentioned before my solution was to keep rinstalling untill it worked... I haven't faced it ever since.
but that is not a strategy one will recommand.
I will wait 3-4 weeks then get back to ubuntu, not before.
I am doing all my developements on Eclipse and Netbeans on windows

Yea, but you keep using wubi.

[wubi known bugs]("http://sourceforge.net/tracker/?group_id=198355&atid=965144")

---

### Post by devi59 on 2009-11-07
Well pickles.... still not fixable. i backed up everything and after im done working today im going to reinstall it WITHOUT WUBI. For once Wubi comepletely screwed me up. I wish this didn't happen because I had to lose a partition to install ubuntu now.

---

### Post by jheaton5 on 2009-11-07
[http://ubuntuforums.org/showthread.php?t=1318240]("http://ubuntuforums.org/showthread.php?t=1318240")

---

### Post by elitenoobboy on 2009-11-07
> **lordofallhearts said:**
> Wow , so finally Ubuntu is matching up with Microsoft!!!!!
Earlier it used to be seamless.Now it is becoming buggy and pain in the a**.

Yep. They say imitation is a form of flattery. MS should be proud.

---

### Post by jheaton5 on 2009-11-07
Don't bite the hand that feeds you.
And it isn't cool to dis a system on that system's board while members of that board are trying to assist you with your problem.  Without being able to connect to your computer via remote access, the only way we can know what is going on is what you tell us.  Keep cool and give us as much detailed information as you can.  We KNOW it's frustrating.

---

### Post by elitenoobboy on 2009-11-07
> **jheaton5 said:**
> Don't bite the hand that feeds you.
And it isn't cool to dis a system on that system's board while members of that board are trying to assist you with your problem.  Without being able to connect to your computer via remote access, the only way we can know what is going on is what you tell us.  Keep cool and give us as much detailed information as you can.  We KNOW it's frustrating.

I expect at least some stability in ubuntu releases. grub was replaced in favor of grub2, which, according to the screen I see when it loads up, still in beta. I don't think putting beta software in a non beta release is a good thing. Especially when it is critical to the running of machine like a boot loader is. The ability to reinstall the original grub 1.0 software isn't even on the livecd anymore. I had to chroot into the old filesystem that I was trying to restore, and then reinstall grub1 from there (my problem wasn't caused in the same way as orig poster). I shouldn't have to do stuff like that. If canonical wants to include the option for grub2, that's fine, but don't force it, and at least keep the option open for putting grub1 on new installs and the tools for reinstalling it as well.

---

### Post by jheaton5 on 2009-11-07
> **elitenoobboy said:**
> If canonical wants to include the option for grub2, that's fine, but don't force it, and at least keep the option open for putting grub1 on new installs and the tools for reinstalling it as well.

If you still have a ext3 file system, you can remove grub2 and install grub-legacy in synaptic.  But grub-legacy does not work well on ext4.  The main reason the developers went to grub2 was because they wanted to go to the ext4 file system.  Even though grub2 is in beta, it still performs well.  I have had no issues with it here on 9.10 or on Debian Squeeze.  I did go through a learning curve trying to configure grub2 the way I wanted it, but I expect that.  What I will say about the grub2 developers is that they have horrible if not non-existent documentation.  A good grub2 manual would be nice.

---

### Post by sklyer on 2009-11-07
I have a similar Grub2 problem. I'm trying to do a fresh install of 9.10 from a LiveCD on a computer that has 8.10 and XP on it. After a "successful" installation, when we try to reboot it, we get an old version of grub, not Grub2. (I know this because it says it is loading stage 1.5 and that's been removed from Grub2, that and it doesn't have the option of booting 9.10) I don't understand where this boot loader can be hiding. There are a lot of partitions on this particular machine, but only one of them is ext3, the rest are NTFS. When we check /boot/grub we find the Grub 2 files; but Ubuntu won't boot. Any ideas?

---

### Post by DarthBrady on 2009-11-08
> **jheaton5 said:**
> I couldn't find in the thread if this has been suggested.  All of you having trouble have one common denominator.  You installed Ubuntu from windows using wubi.  Have you considered downloading the live CD from the Ubuntu site and doing a fresh install with the CD?  If you have any data you can back it up with the Live CD before doing a fresh install.

lol. Actually, yes I did. I got impatient and used a Karmic Live CD and just ran a fresh Install, using the entire HDD. Fortunately, the owner of the PC decided that they didn't need windows anymore anyway after I let him try Ubuntu for a week :D via the wubi install, before this happened.

So now the PC is "Ubuntu-only" and all is well, for me at least. It's a shame, I kinda would have liked to try the fix above and learn something new first, but oh well.

Thanks for your help everybody!

---

### Post by nahmsath on 2009-11-10
> **josephdietrich said:**
> FYI,

I had a similar problem with Wubi and Ubuntu 9.10. Everything had been working fine, then I installed the grub update that showed up in the Update Manager and on next boot I was at the grub shell.

I fixed it by following Zhmurov's directions in this thread (first entry after the bug's description):

[After 9.10 grub update can not boot into Wubi install]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/477104")

I don't know if this totally fixes the problem. Foolishly, instead of being methodical about it, once the system booted normally the first time I:

[LIST=1]
[*]went to System > Administration > Synaptics Package Manager,
[*]searched for grub-pc,
[*]right-clicked on the entry in the list and selected "Mark for Reinstallation",
[*]and the applied the changes.
[/LIST]
This definitely fixed the problem for me, and now my system boots normally again. But I don't know if the reinstallation is the thing that fixed it or not.

Following the instructions from the link you gave, i was able to boot my UNR finally! I am now trying to update the faulty grub. Hope it will be fixed definitely.

Many thanks.

---

### Post by villejer on 2009-11-10
Hi, I'm an ubuntu newbie. I think I messed up my kernel(/s) and I have been experiencing the same kind of problem.

My previously working kernel was 2.6.31-14-generic. I read this interesting thread about compiling you own kernel, and guess what, I made a mistake somewhere in the process. I also found myself helpless in this sh:grub> thing.

When I tried the solutions in this thread, these two worked for me:
    In sh:grub>
    (i didn't use > set root=)
   linux /boot/vmlinuz-2.6.31-14-generic ro
   initrd /boot/initrd.img-2.6.31-14-generic
   boot

After that it started to boot (or at least it appeared to be). It halted at the ...> finding root file system part. I really don't get it, it says it was successful in mounting, but it can't find the root file system or soemthing.

Then the last thing that happens is that the (initramfs) prompt appears.

Please help, I have some files in my karmic OS that I need to recover. Thanks,
Erwin

---

### Post by spasticjustice on 2009-11-14
I'm kinda new to this myself, but have fixed a couple of machines in my household with the same issue. The main thing I noticed is you have to know which partition/drive the ubuntu installation folder is, and direct the root command to that accordingly. Although this may be common sense to many, I'm sure it isn't to some. The basis of the root command in this context is "root=/dev/sda2" the key here being sda2 could just as easily be sdb1 if you have a second drive which you installed Ubuntu on through Wubi. 

sh:grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
 sh:grub> initrd /boot/initrd.img-2.6.31-14-generic
sh:grub> boot


Remember what I specified, and run the command as outlined, but attempt to replace sda2 with sda1, or sdb2, or sdb1 accordingly.


After you boot into the OS successfully remember to run sudo update-grub from the terminal as well as all updates through the update manager.


Hope this helps!

---

### Post by cowbuntu on 2009-11-14
> **spasticjustice said:**
> I'm kinda new to this myself, but have fixed a couple of machines in my household with the same issue. The main thing I noticed is you have to know which partition/drive the ubuntu installation folder is, and direct the root command to that accordingly. Although this may be common sense to many, I'm sure it isn't to some. The basis of the root command in this context is "root=/dev/sda2" the key here being sda2 could just as easily be sdb1 if you have a second drive which you installed Ubuntu on through Wubi. 

sh:grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
 sh:grub> initrd /boot/initrd.img-2.6.31-14-generic
sh:grub> boot


Remember what I specified, and run the command as outlined, but attempt to replace sda2 with sda1, or sdb2, or sdb1 accordingly.


After you boot into the OS successfully remember to run sudo update-grub from the terminal as well as all updates through the update manager.


Hope this helps!

Yep. You nailed it. I came here to post my solution with this issue (had fun for the last hour). The key part is specifying "root=/dev/sdX#".

---

### Post by 5of0 on 2009-11-18
> **villejer said:**
> Hi, I'm an ubuntu newbie. I think I messed up my kernel(/s) and I have been experiencing the same kind of problem.

My previously working kernel was 2.6.31-14-generic. I read this interesting thread about compiling you own kernel, and guess what, I made a mistake somewhere in the process. I also found myself helpless in this sh:grub> thing.

When I tried the solutions in this thread, these two worked for me:
    In sh:grub>
    (i didn't use )
   linux /boot/vmlinuz-2.6.31-14-generic ro
   initrd /boot/initrd.img-2.6.31-14-generic
   boot

After that it started to boot (or at least it appeared to be). It halted at the ... part. I really don't get it, it says it was successful in mounting, but it can't find the root file system or soemthing.

Then the last thing that happens is that the (initramfs) prompt appears.

Please help, I have some files in my karmic OS that I need to recover. Thanks,
Erwin

Well, you're having problems because you didn't include all of the commands.  The root part isn't just in there for kicks and giggles.

I used the instructions in this post to get me up and running:
[http://ubuntuforums.org/showpost.php?p=8330593&postcount=20](http://ubuntuforums.org/showpost.php?p=8330593&postcount=20)

---

### Post by shmk on 2009-11-22
My 2 cents.

I've got the sh:grub> screen and I got back to the ubuntu desktop following this procedure

```

ls /boot
linux (hd0,3)/boot/vmlinuz-MY_VERSION root=/dev/sda3
initrd /initrd-MY_VERSION
boot

```

I've used the ls command to see what was my version (I can't rememeber that long alphanumeric strings... do that easier! :p)

The (hd0,3) and /dev/sda3 is the 3rd partition of my 1st HDD, if you have linux in a different partition you have to change accordingly (something like (hd1,2) and /dev/sdb2 if you want to boot a OS in the second partition of your secondary hd).

Next inside Ubuntu I've used Synaptic searching for grub (found a package called "grub-pc") and reinstalled it, obviously if you like to follow the "hard way" you are free to change the grub config and call a update-grub from the console :P

---

### Post by CrusaderAD on 2009-11-24
> **spasticjustice said:**
> sh:grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
 sh:grub> initrd /boot/initrd.img-2.6.31-14-generic
sh:grub> boot

I tried this... it just reboots the pc, doesn't load anything.

---

### Post by drs305 on 2009-11-24
> **raptormanad said:**
> I tried this... it just reboots the pc, doesn't load anything.

If you type "set" at the grub prompt does the "root=" point to the correct location. If not, you may need to run this command before the ones in the previous post, with X,Y replaced by the correct values (drive1=0, partition1=1):
> 
set root=(hdX,Y)


---

### Post by CrusaderAD on 2009-11-24
Thanks for the reply. I tried a few things... still doesn't work. Here's my output...

```
ls
(loop0)(hd0)(hd0,3)(hd0,2)(hd0,1)(hd1)(hd1,1)

set
root=loop0
```

My root.disk is on sda3.

---

### Post by elitenoobboy on 2009-11-24
If all else fails, you could just install grub1 instead of beta grub2. Boot off of a jaunty cd and install grub1 from there using one of the many manuals for restoring grub that are out there.

---

### Post by CrusaderAD on 2009-11-24
> **elitenoobboy said:**
> If all else fails, you could just install grub1 instead of beta grub2. Boot off of a jaunty cd and install grub1 from there using one of the many manuals for restoring grub that are out there.

Can you do this with a wubi install?

---

### Post by elitenoobboy on 2009-11-24
> **raptormanad said:**
> Can you do this with a wubi install?
Can you tell me more about your system? Wubi by itself should just add an entry to the windows bootloader, not install grub at all. So if you installed wubi and now the windows bootloader won't work, then installing grub won't fix that, since it just chainloads the windows bootloader.

---

### Post by CrusaderAD on 2009-11-24
Windows boots fine. WHen I go into Ubuntu, it brings me to the grub prompt and doesn't let me boot into linux. I tried the suggestions in this thread and upon doing the whole set root, linux, initrd, boot thing... it begins to load (scroll) and then stops, followed by a reboot.

---

### Post by wsscott on 2009-11-25
Same problem.  XP with 9.10 wubi install.  It worked OK until the laptop locked up.  Had to reboot, then received sh > GRUB.  There must be a solution!

---

### Post by CrusaderAD on 2009-11-25
Here's a great way to retrieve your data, it was in the wubi guide:

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition: 

```
sudo mkdir /win
sudo mount /dev/sda1 /win
```

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein 

```
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```

Change to the new vdisk directory and you should be able to view all your stuff. Whew... makes reinstalling a little less painful.

---

### Post by CrusaderAD on 2009-11-25
I just did a clean install and update. Same thing happened... WEAK!

---

### Post by alexlinux on 2009-11-25
I have the same problem... I installed Karmic (using Wubi) and all went well until a few days ago, when Update Manager installed kernel 2.6.31-15-generic and after that I am unable to boot the system. Using a Live CD I was able to copy the files to Windows. I took a look at the foruns and this seems a recurrent problem and nobody seems to have a solution! (Look at bug#484799 and question#91557 to follow the problem).

---

### Post by a_ch on 2009-11-25
I have exactly the same problem - stuck at sh:grub> after system update yesterday and have no idea what to do (new to Ubuntu).

I will bre following this topick and bug report ([https://bugs.launchpad.net/wubi/+bug/484799](https://bugs.launchpad.net/wubi/+bug/484799)) for the solutions.

If you know more sources to follow or solution - please post here.

Thank you!

---

### Post by drs305 on 2009-11-25
[SIZE="3"][COLOR="DarkRed"]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR="DarkRed"]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

> 
# Add the ntfs module
**[COLOR="Navy"]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR="Navy"]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR="Navy"]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR="Navy"]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR="Navy"]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR="Navy"]boot[/COLOR][/B]

* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro"  and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.

---

### Post by Canaryguy on 2009-11-25
Hello,

I had the same problem with the installation of Ubuntu with wubi. Once I installed the updates I saw grub and the system couldn't lunch the graphical interface. But I did something that helped me.

1º Install Ubuntu inside Windows with wubi

2º Install all the updates for Ubuntu when they appear or do it yourself manually

3º After installing the updates when the system asks you to reboot don't do it. Go to the Terminal (Applications/Accessories/Terminal)

4º In the Terminal write: sudo update-grub2 (press enter and write your password if required)

5º Now restart

And that's all

That worked for me.

Good luck.

---

### Post by drs305 on 2009-11-25
> **Canaryguy said:**
> Hello,

I had the same problem with the installation of Ubuntu with wubi. Once I installed the updates I saw grub and the system couldn't lunch the graphical interface. But I did something that helped me.

That worked for me.

Not a bad insurance policy. 

For some background, when Ubuntu installs something which will effect Grub 2, it is *supposed to, and usually does* run update-grub before it asks you to reboot. If you are using a GUI installer/updater, you can see it run update-grub in the details window. Therefore, the system should be searched and the menus updated to account for new kernels, etc.

Of course, if you have custom menus or have disabled any of the /etc/grub.d files those menus will not be updated.

If the system works as it should, when it asks if I want to install the maintainer's version, I don't answer until I've made a copy of the current file(s). Then I accept the maintainer's new version.

---

### Post by louis.haeb on 2009-11-28
Hello,

        I installed Xubuntu 9.10 Karmic 2 weeks ago and am facing the same problem, I installed an update and it asked to reboot, then it stuck to sh:grub>_ shell. I followed [drs305]'s advice and I could boot, so I immediately executed grub2-update from a terminal, and rebooted, but I was still stuck at the shell, no menu!


        In fact, it lloks like the update has not broken anything, it just disabled the menu. So now, it works, but I have to type 7 commands at each boot, so does anyone know how to enable the menu back?

Thank you,
louis_haeb

P.S. Sorry for my poor English, it's not my first language.

---

### Post by phillw on 2009-11-28
are u using Wubi, or a dual install ?

Phill.

---

### Post by phillw on 2009-11-28
> **louis.haeb said:**
> Hello,

        I installed Xubuntu 9.10 Karmic 2 weeks ago and am facing the same problem, I installed an update and it asked to reboot, then it stuck to sh:grub>_ shell. I followed [drs305]'s advice and I could boot, so I immediately executed grub2-update from a terminal, and rebooted, but I was still stuck at the shell, no menu!


        In fact, it lloks like the update has not broken anything, it just disabled the menu. So now, it works, but I have to type 7 commands at each boot, so does anyone know how to enable the menu back?

Thank you,
louis_haeb

P.S. Sorry for my poor English, it's not my first language.


Wubi .....

> **Re: sh:grub > desperation**             
                                                                [SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR=DarkRed]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

     Quote:
                                                 # Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B]                                 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
                                                                                               __________________
                [GRUB2]("https://help.ubuntu.com/community/Grub2") : [G2-Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") [G2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[G2-Tasks]("http://ubuntuforums.org/showthread.php?t=1302743") [DiskSpace]("http://help.ubuntu.com/community/RecoverLostDiskSpace")  
[Expand /]("http://ubuntuforums.org/showthread.php?t=1219270") [SUM]("http://ubuntuforums.org/showthread.php?t=818177")             
                                                                                              *                                              Last edited by drs305; 1 Hour Ago at 06:24 PM.*                                 We do need someone to try this out & report back if it works.Dual Boot

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Re-install Grub2 ..

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  Reinstalling is about step 11

For any other info - follow Drs's signature links.

/edit - he's on holiday for 2 weeks - a well deserved holiday, I may say, & he's left us the best instructions humanly possible.

Regards,

Phill.

---

### Post by louis.haeb on 2009-11-28
I am using Wubi. I did what [drs305] advised for wubi installs, and I am able to boot, but even if I run update-grub2, the boot menu won't appear and I have to type in all the 7 commands to boot. Would purging grub2 and installing Grub 0.97 fix that? If I do it, will [drs305] commands still work to boot my OS?

Thank you  very much for your quick answer,

louis.haeb

---

### Post by phillw on 2009-11-28
> **louis.haeb said:**
> I am using Wubi. I did what [drs305] advised for wubi installs, and I am able to boot, but even if I run update-grub2, the boot menu won't appear and I have to type in all the 7 commands to boot. Would purging grub2 and installing Grub 0.97 fix that? If I do it, will [drs305] commands still work to boot my OS?

Thank you  very much for your quick answer,

louis.haeb

Have you checked this ??

> **[COLOR=Navy][SIZE=3]Adding Entries to Grub 2[/SIZE][/COLOR] **
Menu entries can be added to [COLOR=DarkRed]grub.cfg[/COLOR] automatically or manually.
[LIST]
[*][SIZE=3]**[COLOR=DarkRed]Automatically.[/COLOR]**[/SIZE]
[LIST]
[*]When "[COLOR=Navy]*update-grub*[/COLOR]" or "[COLOR=Navy]*update-grub2*[/COLOR]" is executed, Grub 2 will search for linux kernels and other Operating Systems. What and where is looks is based on the files contained in /etc/grub.d folder.
[LIST]
[*][COLOR=DarkRed]10_linux[/COLOR] searches for installed linux kernels on the same partition.
[*][COLOR=DarkRed]30_os-prober[/COLOR] searches for other operating systems.
[/LIST]
 
[/LIST]
 
[/LIST]
A fuller discussion of Grub2 can be found here --> [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I don't have a wubi area to 'play' with, but my instinct would be re-install Grub2 via his instructions, and check the grub.d folder - There is also a manual way of doing it in the same area. Sorry I can't be of more help.

Regards,

 Phill.

---

### Post by CrusaderAD on 2009-11-28
Ridiculous.

---

### Post by inedit00 on 2009-11-28
> **raptormanad said:**
> Ridiculous.

Yes, it's ridiculous. But I want to help just a little bit. I'm having the same problem rigth now. Ubuntu 9.10 was working just find, but I've installed Windows7. The OS are in different HDD, but when I try to modify the grub2, **** happens.

I've made a lot of tests and now I don't know what else try ( well, I can reinstall all my Ubuntu S.O. but this is a bad solution for the problem ). But there is one thing that helped me. Probably you know about it:[ Super Grub Disk]("http://www.supergrubdisk.org/").
I have burned in a CD and now I can boot my system ( and use the programs, and view my files ) without problems. That's not a solution!!! But if you have to do tests and every time you want to boot the system you have to put the configuration of grub2 by hand... buff.. this is a lot of job.

Good luck!

---

### Post by phillw on 2009-11-29
> **inedit00 said:**
> Yes, it's ridiculous. But I want to help just a little bit. I'm having the same problem rigth now. Ubuntu 9.10 was working just find, but I've installed Windows7. The OS are in different HDD, but when I try to modify the grub2, **** happens.

I've made a lot of tests and now I don't know what else try ( well, I can reinstall all my Ubuntu S.O. but this is a bad solution for the problem ). But there is one thing that helped me. Probably you know about it:[ Super Grub Disk]("http://www.supergrubdisk.org/").
I have burned in a CD and now I can boot my system ( and use the programs, and view my files ) without problems. That's not a solution!!! But if you have to do tests and every time you want to boot the system you have to put the configuration of grub2 by hand... buff.. this is a lot of job.

Good luck!

Have you looked at > **[COLOR=Navy][SIZE=3]Adding Entries to Grub 2[/SIZE][/COLOR] **
Menu entries can be added to [COLOR=DarkRed]grub.cfg[/COLOR] automatically or manually.
[LIST]
[*][SIZE=3]**[COLOR=DarkRed]Automatically.[/COLOR]**[/SIZE]
[LIST]
[*]When "[COLOR=Navy]*update-grub*[/COLOR]" or "[COLOR=Navy]*update-grub2*[/COLOR]" is executed, Grub 2 will search for linux kernels and other Operating Systems. What and where is looks is based on the files contained in /etc/grub.d folder.
[LIST]
[*][COLOR=DarkRed]10_linux[/COLOR] searches for installed linux kernels on the same partition.
[*][COLOR=DarkRed]30_os-prober[/COLOR] searches for other operating systems.
[/LIST]
 
[/LIST]
 
[/LIST]


Failing that, the manual editing of Grub2 is in the same thread ( [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275))

Remember that after checking the auto system, or manually editing Grub2 - you need to run ```
sudo update-grub
```  For changes to take effect.

Regards,

Phill.

---

### Post by inedit00 on 2009-11-29
Thnks Phil. Yesterday I was doing all this stuff you propose with any result. But finally I FIXED the problem!!!!

Yes! The computer is working now. And I want to share with you the way that it worked for my.


[LIST]
[*]Run a Live-CD
[*]Go to the official webpage of [Super Grub Disk]("http://www.supergrubdisk.org/") and [download]("http://developer.berlios.de/project/showfiles.php?group_id=10921") the software (SG2D CDROM).
[*]Burn-it in a CD
[*]Reboot you system and start from the CD
[*]Select the first option "run linux" (or somthing similiar)
[*]With the Super Grub Disk we have simulated the Grub. Now we are in our Linux partition, all running. But this not fix the problem.
[*]Open a console
[*]and well.... now you just have to start typing commands.
[*]Try the phillw commands  ( not worked for my, but you can try), maybe it fix the problem
[*]And now put:
[/LIST]
[INDENT]cd /
sudo fdisk -l #This way you know where you Linux partition is. My HDD is sdb
sudo grub-install --root-directory=/ dev/sdX
#Where X is the HDD you want to restore GRUB
sudo update-grub
sudo update-grub2
sudo reboot
[/INDENT]And problem _**fixed**_!!!!!!!!!

Good luck!
*Note*: Yes, I know. I have to improve my English level. But I'm doing my best.

---

### Post by CrusaderAD on 2009-11-30
> **inedit00 said:**
> [LIST]
[*]Run a Live-CD
[*]Go to the official webpage of [Super Grub Disk]("http://www.supergrubdisk.org/") and [download]("http://developer.berlios.de/project/showfiles.php?group_id=10921") the software (SG2D CDROM).
[*]Burn-it in a CD
[*]Reboot you system and start from the CD
[*]Select the first option "run linux" (or somthing similiar)
[*]With the Super Grub Disk we have simulated the Grub. Now we are in our Linux partition, all running. But this not fix the problem.
[*]Open a console
[*]and well.... now you just have to start typing commands.
[*]Try the phillw commands  ( not worked for my, but you can try), maybe it fix the problem
[*]And now put:
[/LIST]
[INDENT]cd /
sudo fdisk -l #This way you know where you Linux partition is. My HDD is sdb
sudo grub-install --root-directory=/ dev/sdX
#Where X is the HDD you want to restore GRUB
sudo update-grub
sudo update-grub2
sudo reboot
[/INDENT]And problem _**fixed**_!!!!!!!!!

Thanks for the update inedit00! Has anyone else tried it?

---

### Post by marinkov on 2009-12-01
I DID IT!!!!!!!!

*Change my number 5 in (hd0,5) and sda5 with your number. You can see it when you type in grub> ls

1.
grub> *set root=(hd0,5)*
grub> *linux (loop0)/boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro*
grub> *initrd (loop0)/boot/initrd.img-2.6.31-14-generic*
grub> *boot*

2. After that, when you enter, open the console and write:
*sudo update-grub2*

type your password and press Enter

3. Update your software.

4. Restart.

Done.

---

### Post by KPDXHAM on 2009-12-01
> **spasticjustice said:**
> I'm kinda new to this myself, but have fixed a couple of machines in my household with the same issue. The main thing I noticed is you have to know which partition/drive the ubuntu installation folder is, and direct the root command to that accordingly. Although this may be common sense to many, I'm sure it isn't to some. The basis of the root command in this context is "root=/dev/sda2" the key here being sda2 could just as easily be sdb1 if you have a second drive which you installed Ubuntu on through Wubi. 

sh:grub> linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
 sh:grub> initrd /boot/initrd.img-2.6.31-14-generic
sh:grub> boot


Remember what I specified, and run the command as outlined, but attempt to replace sda2 with sda1, or sdb2, or sdb1 accordingly.


After you boot into the OS successfully remember to run sudo update-grub from the terminal as well as all updates through the update manager.


Hope this helps!

This worked for me also! Thanks!
I'm dual booting with XP on my main hard drive  /dev/sda1 and Ubuntu is on Slave Drive /dev/sbd1
I used Wubi since it's the easiest way for me with limited understanding of Linux to make a dual boot system. For about 2 weeks or so I've installed Ubuntu like this, then messed it up when adding things to it through the Synaptic Package Manager, then I had grub problems. Read here & there trying to figure things out, but usually just reinstalled again, something else would screw things up, so back to the beginning again.
I had backed-up my whole Ubuntu sys to another partition on the same drive (I had split a 160GB HDD into two partitions) using Clonezilla. When I tried to restore that backup there was an error and I didn't want to mess with it, so that's how I got to this point.
I formatted this sdb1 partition as NTFS like the others on my computer only because I want to be able to move files back and forth between drives. And YES, I read about making sure to unmount drives before shutting down system.:wink:
So, I used Wubi to do a clean install onto sbd1, but when it booted it came to the sh:grub>
And in the past I would give up since I could not figure out how to get from there even though I had read through these posts. This explanation that was given worked for me.

Thanks again to all you very patient Linux folks out there!
I couldn't understand Fortran back in 1969 either.....:confused: 

Here's what I got after doing the sudo update-grub

---

### Post by CrusaderAD on 2009-12-04
Which should I do after doing the update?

```
sudo update-grub
```
or
```
sudo update-grub2
```

Or both?

---

### Post by darkod on 2009-12-04
sudo update-grub should do it.

---

### Post by jperez on 2009-12-05
> **josephdietrich said:**
> FYI,

I had a similar problem with Wubi and Ubuntu 9.10. Everything had been working fine, then I installed the grub update that showed up in the Update Manager and on next boot I was at the grub shell.

I fixed it by following Zhmurov's directions in this thread (first entry after the bug's description):

[After 9.10 grub update can not boot into Wubi install]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/477104")

I don't know if this totally fixes the problem. Foolishly, instead of being methodical about it, once the system booted normally the first time I:

[LIST=1]
[*]went to System > Administration > Synaptics Package Manager,
[*]searched for grub-pc,
[*]right-clicked on the entry in the list and selected "Mark for Reinstallation",
[*]and the applied the changes.
[/LIST]
This definitely fixed the problem for me, and now my system boots normally again. But I don't know if the reinstallation is the thing that fixed it or not.

THANK YOU, THANK YOU, THANK YOU!  The information following the link you posted got me booted right up!  Oh you saved me a huge headache.  I also thank **Zhmurov** for the wonderful instructions he posted there...thank you both. :cry:

I'd buy ya beer, but I don't think you live close by or if you're of age. :lolflag:

Jesse~

---

### Post by CrusaderAD on 2009-12-05
> **darkod said:**
> sudo update-grub should do it.

It worked! Thanks everyone!

---

### Post by shujaa on 2009-12-06
My question is when are the egg-heads that designed the program going to fix the sh:grub problem so we the end users don't have to go through all this fuss?

---

### Post by nuzual on 2009-12-08
i am new to Ubuntu, i have the same problem booting after upgraded to 2.6.31.16 version,and after i can boot into 2.6.31.14 with the help of this thread,i looked into the synaptic found the description about compatibility on installing -16 version that it's for more than 4G ram computer.is this the reason of bootfail after upgraded?

---

### Post by marinkov on 2009-12-08
I have a new problem.
The previous decisions don't work on the laptop version.
I do all the steps with the updating at the end and when I restart it again shows grub>

---

### Post by marinkov on 2009-12-10
Ook, I give up... new update and the same error.
It seems that ubuntu is not ready to be the alternative of the Windows for me. I'm really sorry because I like it but the support is not good.

Back to Windows! :(

---

### Post by CrusaderAD on 2009-12-10
That's too bad. Were you using wubi? I've never seen this issue with a full install on the drive without windows.

---

### Post by nuzual on 2009-12-10
i go into desperation again after automatic updated yesterday, your system is up to date, but bootfail all the time,i have to type in: set root.......... there is no boot menu for me to choose again,i love ubuntu(on wubi), somehow i would leave ubuntu until everything become easier(get rid of my headache too)

---

### Post by CrusaderAD on 2009-12-12
Another recent upgrade screwed another pc of mine. Back to Jaunty 9.04, this is ridiculous.

---

### Post by CrusaderAD on 2009-12-18
I figured I'd reinstall a fresh copy and try again... still no good. It didn't even boot once. Bizarre. I downloaded the latest iso... that's probably why.

---

### Post by CrusaderAD on 2009-12-18
Gonna try this:

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

Hopefully this works... I'm loosing faith in wubi installs.

---

### Post by CrusaderAD on 2009-12-19
> **raptormanad said:**
> Gonna try this:

[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

Hopefully this works... I'm loosing faith in wubi installs.

It works but two things... it's a constant live install... no saved changes. It installs on your main partition, no choice to put it on a separate one. Guess I'll have to use the usb method from pendrivelinux.com until this blows over. If it does... this is the first time in a few years I don't have linux installed on the machine I use most. Creepy.

---

### Post by DOS Chuck on 2010-01-30
I have gotten the same thing about 4 times now. I have tried installing through WUBI and, booting from the Live CD, as a new install on a separate partition. I have even unplugged or turned off my dsl modem so there was NO possible chance of automatically upgrading GRUB. Once, when I DID getting it working, I updated, through "update-manager" all but the "grub-common" and the "grun-pc". I STILL got the same error. I think THAT time it may have been caused by updating the headers and the image files.

Everything is working, NOW, but until I know better, I'm NOT updating the grub OR the headers.

---

### Post by CrusaderAD on 2010-01-30
> **DOS Chuck said:**
> Everything is working, NOW, but until I know better, I'm NOT updating the grub OR the headers.

Good idea. Same here!

---

### Post by DOS Chuck on 2010-01-30
As I held my breath....I upgraded the headers and image files to 2.6.31-17. It worked. Whew.....
The ONLY upgrades that "update-manager" shows now is "grub-pc" and "grub-common". I have rebooted twice. just to make sure....using the -14 AND the -17 headers.

I was curious about maybe upgrading to 10.04 but, that may mean getting stuck with grub2. I think I'll hold off for a bit.

---

### Post by meierfra. on 2010-01-30
This problem is caused by a bug in Grub2.  For all the details and an easy permanent fix see


[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by DOS Chuck on 2010-01-30
I'll be damned. THAT worked!!! I put "wubildr" on both of my HD's (I have WinXP Pro-32 on one and WinXP Pro-64 on the other) and updated "grub-pc" and "grub-common" and it works!!! 

Thank you so very much. I do have to admit, I was thinking if "wubildr" MIGHT have some influence but didn't know how I could change it. But, again, THAT worked!!!:popcorn:

---

### Post by knubles on 2010-02-04
meierfa
Thanks for the info.
It worked like a charm.
knubles

---

### Post by hoboy on 2010-02-06
> **meierfra. said:**
> This problem is caused by a bug in Grub2.  For all the details and an easy permanent fix see


[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

meierfa
Thanks it works very very well for me.
It worked like a charm.

---

### Post by arkage82 on 2010-02-08
Newbie Ubuntu user here. I installed a copy of Ubuntu next to my Windows XP to try it out and see what I thought about it. I was just getting to the point of really liking it, and this whole update thing bit me in the backside.

My problem seems a bit more complex here. When I try to boot into Ubuntu, I get the sh:grub deadend. Reading thru this forum I have some avenues to try to remedy my problem.

My complicating issue: I cannot load Windows XP either. The logo page comes up and before the blue bar gets  half way across, I get the Blue Screen of Death.

I would love to try the wubildr remedy listed here, but cant get to Windows to do it. 

I wont be able to try any of the other fixes until tomorrow, and I have no programming background or experience, so much of this conversation is drastically over my head. 

I lost 5 years of work, pictures, music etc on my computer, some of which I have backed up, but some I never even thought to do (passwords to websites I had stored in a program, etc.).

Any advice or guidance before I try some of these fixes would be appreciated. Thanks to all who gave input so far.

---

### Post by meierfra. on 2010-02-08
> My complicating issue: I cannot load Windows XP either.  
Indeed,  you to seem to have  different problem. I suggest to start a new thread. Also follow  these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post RESULTS.txt in the new thread. Feel free to send me a PM with a link to your new thread.

---

### Post by arkage82 on 2010-02-08
> **meierfra. said:**
> Indeed,  you to seem to have  different problem. I suggest to start a new thread. Also follow  these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post RESULTS.txt in the new thread. Feel free to send me a PM with a link to your new thread.

Well, I will start a new thread, but unfortunately, I cannot do anything with downloading and using the Boot Info Script. The affected computer will not read anything off of an optical drive or thru Windows. My only avenue of anything right now is the sh:grub on the Ubuntu side.

---

### Post by CrusaderAD on 2010-02-08
arkage82, don't panic... you're files are still there. We'll get'em for you :) If you're having a difficult time, shoot me a message here on the forums and I'll help you out. One thing you may want to try is pendrivelinux.com and put together a linux desktop on a flashdrive. They all work great, but I lean towards slax. It's fast and simple. You'll be able to boot to your usb drive (bios permitting), mount the file systems, and get your data.

---

### Post by CharlesMcC on 2010-02-08
Thanks so much for this fix. I was really getting frustrated with this error.

---

### Post by arkage82 on 2010-02-09
> **raptormanad said:**
> arkage82, don't panic... you're files are still there. We'll get'em for you :) If you're having a difficult time, shoot me a message here on the forums and I'll help you out. One thing you may want to try is pendrivelinux.com and put together a linux desktop on a flashdrive. They all work great, but I lean towards slax. It's fast and simple. You'll be able to boot to your usb drive (bios permitting), mount the file systems, and get your data.

Well, I just went thru this entire thread and tried every suggestion made, and still no results. Whenever I type in boot, my computer goes back to my selection of OS's and then on choosing Ubuntu, I get the sh:grub again.

I will take a look at the pendrivelinux.com, but right now I'm down to an old desktop running Windows 98SE and a laptop on XP but not a lot of power or "extras".

This has been one very frustrating adventure for me, and I would much rather be productive doing something else than trying to recover my last 5 years of "productivity". 

Thanks to all for the help and suggestions. I will keep plugging away until something gives, me or the system.

---

### Post by CrusaderAD on 2010-02-09
> **arkage82 said:**
> I will take a look at the pendrivelinux.com, but right now I'm down to an old desktop running Windows 98SE and a laptop on XP but not a lot of power or "extras".

The pendrivelinux solutions are actually excellent data recovery and virus removal tools. I'm sure it will get you into your file systems and save the data. You could also try booting into the Ubuntu live cd and see if you can navigate to the data that way.

---

### Post by arkage82 on 2010-02-09
OK upon further review....... my system does not give me the choice of booting from my USB. I can select CD (which I have tried with Windows XP Install disk and no luck) or my hard drive. 

The Hard Drive sequence allows for System BIOS boot devices or for USB device (not installed).... Would it work from here?

---

### Post by CrusaderAD on 2010-02-09
It should work from there. I'm not 100% sure without seeing it. You could try to boot to the live Ubuntu CD, just don't do an install or format the drive. That will get you into a GUI to navigate to the data.

---

### Post by meierfra. on 2010-02-09
I agree with raptormanad advice. You will need to be able to boot from a flashdrive or a LiveCD  to make any progress.  But could we keep all further discussion in the new thread you started:

[http://ubuntuforums.org/showthread.php?t=1402166](http://ubuntuforums.org/showthread.php?t=1402166)

Thanks.

---

### Post by MandeaSaracu on 2010-02-15
> **arkage82 said:**
> Newbie Ubuntu user here. I installed a copy of Ubuntu next to my Windows XP to try it out and see what I thought about it. I was just getting to the point of really liking it, and this whole update thing bit me in the backside.

My problem seems a bit more complex here. When I try to boot into Ubuntu, I get the sh:grub deadend. Reading thru this forum I have some avenues to try to remedy my problem.

My complicating issue: I cannot load Windows XP either. The logo page comes up and before the blue bar gets  half way across, I get the Blue Screen of Death.

I would love to try the wubildr remedy listed here, but cant get to Windows to do it. 

I wont be able to try any of the other fixes until tomorrow, and I have no programming background or experience, so much of this conversation is drastically over my head. 

I lost 5 years of work, pictures, music etc on my computer, some of which I have backed up, but some I never even thought to do (passwords to websites I had stored in a program, etc.).

Any advice or guidance before I try some of these fixes would be appreciated. Thanks to all who gave input so far.
Try booting Xp into safe mode and see if the error is still there.

---

### Post by amin5236 on 2010-02-19
> **meierfra. said:**
> This problem is caused by a bug in Grub2.  For all the details and an easy permanent fix see


[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

You brought my Ubuntu back to life. Thanks a lot :):P

---

### Post by midniteblues on 2010-03-20
set root=loop0
linux/boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
initrd/boot/initrd.img-2.6.31.20-generic
boot

works for me

---

### Post by midniteblues on 2010-03-20
once you boot into ubuntu make sure you update the grub

sudo update-grub

---

### Post by Chengs on 2010-03-31
Hi All,
          Upgraded to Ubuntu 9.10 & faced the following problems.

1) After downloading & during installation towards the last few minutes had a power outage.

2) Managed to over come subsequent problems & am currently stuck with the sh:grub> prompt.

3) During attempts to re-install grub2 have been wrongly assuming that grub2 is installed in sda2. Don't know if my assumption is correct.

4) Have managed to run boot_info_script & the results are pasted below.

My system is a Dell latitude D800 which had xp installed. Had installed Ubuntu 9.04 & had really no problems dual booting between xp & ubuntu 9.04.  Now, am stuck with the sh:grub> prompt after updating to 9.10.

Please help, am desperate to come out of this mess. Have not been able to even use Winxp.

Thanks in advance


Cheers
Chengs

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /grub/menu.lst /boot/grub/core.img /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/disks/boot/grub/menu.lst 
                       /ubuntu/winboot/menu.lst /NTLDR /NTDETECT.COM 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk /grub/core.img 
                       /boot/grub/core.img

sda2/Wubi: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9dc96e9e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197  de Dell Utility
/dev/sda2    *         64,260    78,124,094    78,059,835   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031798272 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015231 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,015,230     2,015,168   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       bc05778a-67b9-4505-8c92-c5dee8209763   ext3                                     
/dev/ramzswap0                                          swap                                     
/dev/sda1        07D3-0712                              vfat       DellUtility                   
/dev/sda2        98C87F09C87EE542                       ntfs                                     
/dev/sdb1        01D3-6A61                              vfat       IBALL                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/IBALL             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


============================= sda1/grub/menu.lst: =============================

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=98C87F09C87EE542

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

### END DEBIAN AUTOMAGIC KERNELS LIST

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/menu.lst
    ??GB: grub/stage2

==================== sda2/ubuntu/disks/boot/grub/menu.lst: ====================

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
## kopt=root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-17-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.31-17-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=98C87F09C87EE542 loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Microsoft Windows XP Professional
rootnoverify    (hd0,1)
savedefault
chainloader    +1


======================== sda2/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
    ??GB: grub/core.img
    ??GB: ubuntu/disks/boot/grub/menu.lst
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/initrd.img-2.6.31-17-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-11-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-15-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.28-16-generic
    ??GB: ubuntu/disks/boot/vmlinuz-2.6.31-17-generic

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext3 loop,errors=remount-ro,relatime 0 1
/host/ubuntu/disks/boot /boot none bind 0 0
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  eb 46 90 44 65 6c 6c 20  34 2e 31 00 02 04 01 00  |.F.Dell 4.1.....|
00000010  02 00 02 00 00 f8 3f 00  3f 00 ff 00 3f 00 00 00  |......?.?...?...|
00000020  c5 fa 00 00 80 00 29 12  07 d3 07 44 65 6c 6c 55  |......)....DellU|
00000030  74 69 6c 69 74 79 46 41  54 31 36 20 20 20 00 00  |tilityFAT16   ..|
00000040  00 00 00 00 00 00 00 00  fa b8 00 00 8e d0 bc fc  |................|
00000050  7b fb fc 8e d8 ff 0e 13  04 8b 0e 13 04 c1 e1 06  |{...............|
00000060  8e c1 b9 00 01 33 f6 33  ff f3 66 a5 c7 06 72 04  |.....3.3..f...r.|
00000070  45 44 8e c0 bd 00 7c e8  21 01 0f 82 bb 00 66 0f  |ED....|.!.....f.|
00000080  b7 86 16 00 66 d1 e0 66  0f b7 9e 0e 00 66 03 c3  |....f..f.....f..|
00000090  66 03 86 1c 00 66 89 86  3e 00 8b 86 11 00 c1 e8  |f....f..>.......|
000000a0  04 89 86 46 00 bb 00 05  e8 aa 00 0f 82 8a 00 ba  |...F............|
000000b0  10 00 b9 0b 00 be ec 7d  8b fb f3 a6 74 16 83 c3  |.......}....t...|
000000c0  20 4a 75 ee 66 ff 86 3e  00 ff 8e 46 00 75 d6 be  | Ju.f..>...F.u..|
000000d0  d9 7d eb 6d 66 0f b7 86  11 00 66 ba 20 00 00 00  |.}.mf.....f. ...|
000000e0  66 f7 e2 66 0f b7 8e 0b  00 66 03 c1 66 48 66 f7  |f..f.....f..fHf.|
000000f0  f1 66 01 86 3e 00 66 8b  86 3e 00 66 89 46 fc 66  |.f..>.f..>.f.F.f|
00000100  0f b7 47 1a 8b f8 2d 02  00 66 0f b6 9e 0d 00 66  |..G...-..f.....f|
00000110  f7 e3 66 01 86 3e 00 bb  00 07 c7 86 46 00 04 00  |..f..>......F...|
00000120  e8 32 00 72 14 81 c3 00  02 66 ff 86 3e 00 ff 8e  |.2.r.....f..>...|
00000130  46 00 75 ec ea 00 02 70  00 be cc 7d eb 03 be d9  |F.u....p...}....|
00000140  7d e8 02 00 eb fe ac 3c  00 74 09 b4 0e bb 07 00  |}......<.t......|
00000150  cd 10 eb f2 c3 66 8b 86  3e 00 66 33 d2 66 0f b7  |.....f..>.f3.f..|
00000160  8e 18 00 66 f7 f1 66 42  88 96 45 00 66 33 d2 66  |...f..fB..E.f3.f|
00000170  0f b7 8e 1a 00 66 f7 f1  88 96 44 00 89 86 42 00  |.....f....D...B.|
00000180  b8 01 02 8b 8e 42 00 c0  e5 06 0a ae 45 00 86 e9  |.....B......E...|
00000190  8a b6 44 00 8a 96 24 00  cd 13 c3 80 3e c2 07 06  |..D...$.....>...|
000001a0  74 29 b8 01 02 bb 00 06  b9 01 00 b6 00 8a 96 24  |t).............$|
000001b0  00 cd 13 72 16 c6 06 c2  07 06 b8 01 03 bb 00 06  |...r............|
000001c0  b9 01 00 b6 00 8a 96 24  00 cd 13 c3 44 69 73 6b  |.......$....Disk|
000001d0  20 65 72 72 6f 72 0d 0a  00 4d 69 73 73 69 6e 67  | error...Missing|
000001e0  20 27 69 6f 2e 73 79 73  27 0d 0a 00 49 4f 20 20  | 'io.sys'...IO  |
000001f0  20 20 20 20 53 59 53 00  00 00 00 00 00 01 55 aa  |    SYS.......U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 20 14 00  |.<.MSWIN4.1.. ..|
00000010  02 00 02 00 00 f8 f6 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 bf 1e 00 80 00 29 61  6a d3 01 4e 4f 20 4e 41  |......)aj..NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|
00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|
00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|
00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|
00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|
00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|
00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|
000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|
000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|
000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|
000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|
000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|
000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|
00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|
00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|
00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|
00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|
00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|
00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|
00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|
00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|
00000200

---

### Post by tfa on 2010-03-31
hi


I changed the name of grub.cfg to o.cfg inadvertently and  now when I turn on my pc appears sh:grub>   What do I do now?

---

### Post by drs305 on 2010-03-31
> **tfa said:**
> hi


I changed the name of grub.cfg to o.cfg inadvertently and  now when I turn on my pc appears sh:grub>   What do I do now?

tfa,

Welcome to Ubuntu and the Ubuntu forums. 

You have a couple of options. Here is one: 

You can boot to the LiveCD desktop using the Ubuntu CD. Mount your Ubuntu system, and rename the file. 

Do you know which partition your Ubuntu installation is on? If Ubuntu is your only system, it is usually on sda1. If it is on a single drive with Windows, it is normally on sda5. If you have multiple drives, who knows?

From the LiveCD Desktop, open a terminal from Applications, Accessories, Terminal. Then type this command:
```
sudo fdisk -l
```
The -l is a lowercase L. You will be asked for your password. As you enter it, you won't see anything. This is normal - just type it in and press ENTER. Your Ubuntu partition will be on the line with "83 Linux". The drive/partition will be at the start of that line.

Let's use **sda5** for this example. Substitute your Ubuntu partition if it is not **sda5**

Run these commands:
```
sudo mount /dev/sda5 /mnt
sudo mv /mnt/boot/grub/o.cfg /mnt/boot/grub/grub.cfg
```

If the commands work, you won't see anything. Reboot and your problem should be fixed. 

If you have questions, can't decide which partition is your Ubuntu partition, or the commands above don't work, come back and ask for additional help.

---

### Post by tfa on 2010-03-31
> You can boot to the LiveCD desktop using the Ubuntu CD. Mount your  Ubuntu system, and rename the file. I don't  have the Ubunto cd... there is no command that can  change the file name in sh:Grub>? what  other options i have?

---

### Post by drs305 on 2010-03-31
You can boot from the grub command line following the guidance provided here:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")

It's just there may be more pitfalls associated with this method. Follow the instructions and come back here if you have questions.

---

### Post by tfa on 2010-03-31
ok, I'm downloading the Ubunto  cd to try your first option( the page of that link is confuse to me) then If i need help i reply. 
thanks!

---

### Post by tfa on 2010-03-31
> sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo mv /mnt/boot/grub/o.cfg /mnt/boot/grub/grub.cfg
Thanks! Thanks! Thanks!
Problem Solved!

The partition is sda3, and now i have my ubuntu and windows back!

---

### Post by Isaacm on 2010-05-25
_Solution 1._
When you get sh:grub> error,try running this code on grub.The codes are in bold.
[B]
set root=(hd0,2)[/B]     (Your drive with ubuntu varies e.g (hd0,2) or (hd0,5) etc....)
[B]loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk
initrd	/boot/initrd.img-2.6.31-14-generic
boot

[/B]If the machine boots  go to terminal and run: **sudo update-grub** then restart the machine.
[U]
Solution 2.[/U]  
Works for ubuntu 9.10 and beyond,lower version of ubuntu will turn unbootable.
Download wubidr file go to C drive and replace wubidr file
and restart ubuntu.
You can also copy wubidr from a working ubuntu computer from C drive or the drive with wubidir
file and replace it on the machine that is not working.

If that fails,download or copy from another machine both wubidr and wubidr.mbr files 
and replace those on the machine that is not working and restart the computer.

_Solution 3_
Re-install ubuntu.

---

### Post by nNeedofrepair on 2010-08-22
> **DarthBrady said:**
> Having the same problem. Installed 9.10 with wubi. All was fine until Update-Manager installed a grub update today, now I get the same thing when trying to boot.
I to am having the same problem after an update
when I type in initrd /boot/initrd.img-2.6.31-14generic 
I get the following response. need to load the kernal first
whats a kernal?
Good luck

---

### Post by drs305 on 2010-08-22
> **nNeedofrepair said:**
> I to am having the same problem after an update
when I type in initrd /boot/initrd.img-2.6.31-14generic 
I get the following response. need to load the kernal first
whats a kernal?
Good luck

You load the kernel with an entry similar to this at the grub rescue prompt, modified to match your Ubuntu drive/partition:
> linux /vmlinuz root=/dev/sd**a5** ro
You can find out the correct partition (in this example, sda5), by typing "ls (hdX,Y)/boot" at the Grub2 command prompt. The first drive is 0, the first partition is 1.
Example: ls (hd0,5)/boot
If this is the correct partition for your Linux boot partition, it should show at least one "vmlinuz" and one "initrd" file.

[Command Line and Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode")

---

### Post by ankitsunny on 2011-01-17
I got the same problem on my dual-boot (Win 7 and Ubuntu).
I had installed Ubuntu using wubi.Everything worked fine until I updated the system after which the sh:grub CLI would come up
The following link solved the problem for me
Hope it for you too!!!
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by ankitsunny on 2011-01-17
I got the same problem on my dual-boot (Win 7 and Ubuntu).
I had installed Ubuntu using wubi.Everything worked fine until I updated the system after which the sh:grub CLI would come up
The following link solved the problem for me
Hope it for you too!!!
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

