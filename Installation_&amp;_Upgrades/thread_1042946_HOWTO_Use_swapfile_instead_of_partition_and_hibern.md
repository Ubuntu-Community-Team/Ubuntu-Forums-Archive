---
title: "HOWTO: Use swapfile instead of partition and hibernate"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by iva2k on 2009-01-18
This HOWTO explains how to use swapfile and still have hibernation working.

(For advanced console users / cmdline junkies - you may find compressed list of commands at the end of this HOWTO)

Why would you want a swapfile? Isn't the traditional swap partition working fine?
Swap partition does work fine, but there are 3 cases when you may want a swapfile instead:
[LIST=1]
[*]You forgot to make a swap partition
[*]You need to have no swap partition, for instance to have Mac trippleboot Ubuntu/MacOSX/Win* and comply with all of the OS's limitations (which in my case allowed only 4 primary MBR partitions, one taken by GUID/GPT/EFI which makes MacOSX comfortable)
[*]Have flexibility of resizing swap at any time. Partition may be impossible to change/resize later.
[/LIST]

This HOWTO was tested only on Intrepid, but may work on other versions.
UPDATE 7 Sept 2011: I tested it with Ubuntu 10.04 LTS (Lucid Lynx) and made appropriate edits.
To reverse back to swap partition: [http://ubuntuforums.org/showpost.php?p=7401680&postcount=13](http://ubuntuforums.org/showpost.php?p=7401680&postcount=13)

DISCLAIMER: Messing up with disk partitions may make your system unusable, cause loss of data, loss of hair and/or sleep. Knowledge of terminal and command line is required. You're warned - proceed at your own risk.

**PREREQUISITES**
[LIST]
[*]Ubuntu installed on disk drive and running
[*]IMPORTANT! Hibernation and resume should already work OK before this change
[*]Enough free space on "/" partition
[*]You should have your sudo password and be on the sudoers list
[/LIST]

**PART 1 - SWAPFILE**

Attention: If you have swap partition and hibernation does not work, STOP HERE. First fix hibernation (seek help elsewhere, try "sudo apt-get install hibernation") before proceeding.

Note: Using swapfile breaks hibernation. We will fix it in PART 2 below.

Boot into your system (reboot is recommended to close all extra applications). Open terminal. Copy & paste one command at a time (making necessary edits as denoted by "<...>").

```
cat /proc/meminfo
```
Note memory size (first line saying "MemTotal"). Graphics card may eat a chunk out of the main RAM, so it is not necessarily a multiple of GiB.

For RAM of size N Bytes we will need a swapfile size of N to 2*N Bytes for both virtual memory and hibernation to work properly. Having swap larger than 2*N Bytes is usually unnecessary and just wastes space, unless you are planning to upgrade RAM in the near future. You can rerun this HOWTO prior to RAM upgrade, or allocate enough swap space now.

```
sudo dd if=/dev/zero of=/swapfile bs=1024 count=XX
```
The swapfile size is equal to [count*bs] (in Bytes), So XX = desired swap size in Bytes / 1024 (bs parameter implies Bytes).

dd can take standard multiplier letters, e.g. count=2M or count=2048K will both result in 1024*2M=2G (note that count parameter has special decoding of multipliers - adding letter B changes from computer 1024 to metric 1000, i.e 1M = 1024*1024, while 1MB=1000*1000). You can dry-run dd with of=/dev/null to see if your numbers will get the desired swapfile size. See "man dd" if you need more information.

You can go ahead and check stock quotes while dd creates the new file for a few minutes.

```
sudo chmod 600 /swapfile && sudo mkswap /swapfile
```
**Important Note:** The UUID that mkswap returns is absolutely useless.

```
sudo swapoff -a
sudo swapon /swapfile
sudo -b gedit /etc/fstab
```
Edit /etc/fstab and :
[LIST=1]
[*]Remove or comment out ALL old swap partitions
[*]Add new line:
[/LIST]
```
/swapfile   none   swap   sw   0   0
```

Verify that everything is done OK:
```
free -m
```
You will see your swap reported.
```
swapon -s
```
- will show you that you are indeed using swapfile


**PART 2 - HIBERNATION**

Now we will make the hibernation work again. Intrepid kernel has all the provisions (thanks to Rafael J. Wysocki), but surrounding files do not tell it how to use the swapfile. Even more:
[LIST=1]
[*]Reinstall or update of initramf-tools won't make the right setup, though it should (maybe it will someday)
[*]Hibernate does not work with swapfiles out of the box and will exhibit behavior similar to this bug: [Ubuntu bug 313724, Red Hat bug 466408] "PM: Swap header not found!
[/LIST]
So we do it by hand:

```
mount | grep " / "
```
Note your /dev/... for "/" disk.
```
sudo blkid -g
sudo blkid
```
Note UUID of /dev/... that corresponds to "/", we will use it in resume=UUID= below.

```
sudo filefrag -v /swapfile | grep "First block:"
```
Note first block, we will use it for resume_offset below.
If there is no output from this command, you have a new filefrag which changed its output. Do this instead:
```
sudo filefrag -v /swapfile
```
...and note the number in the first line under "physical" (3rd column)
Here is an example of the output, the number for resume_offset is 154484:
```
Filesystem type is: 58465342
File size of /swapfile is 8261935104 (2017074 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0   154484          1241648 
   1 1241648  6233816  1396131 775426 eof
/swapfile: 2 extents found

```

Replace UUID and resume_offset:
```
echo "resume=UUID=<your UUID> resume_offset=<youroffset>" | sudo tee /etc/initramfs-tools/conf.d/resume

```

Now edit GRUB configuration:
(for old grub, before grub2)
```
sudo -b gedit /boot/grub/menu.lst
```
Find the line "# kopt=root=UUID=..."
and add to it "resume=UUID=<your UUID> resume_offset=<youroffset>" (without quotes).
Note that your UUID will match root=UUID, unless you have placed swapfile on different partition than "/".

It should look like this (with your UUID and offset):
```
# kopt=root=UUID=... ro resume=UUID=cd71de6f-907a-40d7-bf26-c17f201e5718 resume_offset=66050
```
Make sure you have no carriage returns in this line.

(for new grub2)
```
sudo -b gedit /etc/default/grub
```
Find the line "GRUB_CMDLINE_LINUX_DEFAULT=..."
and add to it "resume=UUID=<your UUID> resume_offset=<youroffset>" (so it stays inside quotes with whatether text was there).
Note that your UUID will match root=UUID in /boot/grub/grub.cfg, unless you have placed swapfile on different partition than "/".

Now let's run the tools to make them work:

For pre-grub2: ```
sudo update-grub -y
```
For grub2: ```
sudo update-grub
```
Answer "instal the package maintainer's version" if it asks.

```
sudo update-initramfs -u
```

Verify that all your kernel stanzas (menu entries) got updated in /boot/grub/menu.lst (or in /boot/grub/grub.cfg for grub2)  with resume=... and resume_offset=..., if not - verify your # kopt= line - it should have # and space (GRUB_CMDLINE_LINUX_DEFAULT= line for grub2 should have quotes). Rerun update-grub if necessary. It may keep your old file if you chose wrong answer above.

Now reboot before trying to hibernate (important), so kernel gets the right resume_offset parameter.

After reboot, try to hibernate. It should get right back to this window after you power your computer back up.

Now you can get rid of the old swap partition and use it for other stuff.


**CONCLUSION**

This is a quick command summary:
Part 1 - make swap file```

cat /proc/meminfo
## Note memory size. Graphics card may eat a chunk of main RAM
## We will need swapfile the size of N to 2*N of RAM
sudo swapoff -a
sudo dd if=/dev/zero of=/swapfile bs=1024 count=8M	;## 2*N of RAM, swap size=count*bs
sudo chmod 600 /swapfile && sudo mkswap /swapfile && sudo swapon /swapfile
sudo -b gedit /etc/fstab
# Remove ALL old swap partitions
# Add: /swapfile   none   swap   sw   0   0
free -m
swapon -s
```

Part 2 - use swap file for hibernation```

mount | grep " / "    ;# Note your /dev/... on /
sudo blkid -g
sudo blkid    ;## get / -> /dev/... -> partition UUID -> resume=UUID=
sudo filefrag -v /swapfile | grep "First block:"	;## get First block -> resume_offset
# for grub2:
sudo filefrag -v /swapfile	;## get first "physical" number -> resume_offset
echo "resume=UUID=cdXX--X18 resume_offset=66050" | sudo tee /etc/initramfs-tools/conf.d/resume
sudo -b gedit /boot/grub/menu.lst
# kopt=root=UUID=... ro resume=UUID=cdXX--X18 resume_offset=66050 
# for grub2:
sudo -b gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="... resume=UUID=cdXX--X18 resume_offset=66050"
sudo update-grub -y
# Answer "use maintainer version" if it asks
sudo update-initramfs -u
```


**APPENDIX - SAME OR SEPARATE FILES FOR SWAP AND HIBERNATION?**

There is some controversy going on in regards to using the same file or partition for both swap and hibernation. If swapfile is not big enough, hibernation may fail, depending on how many applications and documents are open. Some argue rightfully for 2 separate files - one for swap, one for hibernation.

Swapfile approach should make it very easy to have 2 separate files and avoid problems. Given RAM size of N Bytes the above instructions could be used as follows to create two files:
[LIST=1]
[*]/swapfile  of size N Bytes for "swapon /swapfile" only.
[*]/hiberfile of size N Bytes for PART2 - HIBERNATION (use instructions in PART1 to create it, but don't add it to fstab or swapon)
[/LIST]
Unfortunately, when done this way, hibernation fails with kernel message "PM: Cannot find swap device, try swapon -a". It looks like a deficiency of PM code in current kernel. So the answer is no, not yet. For now use single file that is big enough and hope you never run out of space in it and get failing hibernation.

---

### Post by Herman on 2009-01-18
> We will need swapfile the size of N to 2*N of RAM size for virtual memory and hibernation to work properly. What units are you using for N?
In the first command we looked up our Memtotal in kB.
My EeePC has 512 Mb or RAM, and Memtotal is 505744 kB, with 6145 kB MemFree.

So I presume you mean if I want a 512 Mb swap file, I would do 512000/1024=_500_ kB ?

So for me,  N=500 ?

Would that be right?  :)

No, wait ... the dd command 'bs' is in bytes, so 1024 x 500 is only 512 000 bytes, or 500 kB.
I want 500 Mb, so maybe 512 000 would be more like it.
N=512000 ?
```
herman@eeepc-ibex:~$ sudo dd if=/dev/zero of=/swapfile bs=1024 count=512000
[sudo] password for herman: 
512000+0 records in
512000+0 records out
524288000 bytes (524 MB) copied, 54.9668 s, 9.5 MB/s
```Nevermind,got it! Sorry if I bothered anyone.

Thanks very much for sharing your knowledge with that useful post, iva2k, it's just what I needed. :)
I completed part 1, but I don't think I'll use hibernation, so I'll leave part 2 for later maybe. 
__

---

### Post by q41 on 2009-01-18
Wow, many thanks iva2k!

My hibernation didn't work at all, even though I use a swap partition. I followed part 2 of your guide substituting /swapfile for my swap partition and leaving out the *resume_offset=<youroffset>* parts.

Works like a charm!

---

### Post by iva2k on 2009-01-18
Herman - Thanks! I edited HOWTO to explain dd count in more detail.

q41 - you are right, it should work in principle for swap partitions as well. Just keep using corresponding /dev/sdXX instead of /swapfile. Then that "absolutely useless" UUID from mkswap will be your UUID for resume=UUID=, skip or replace dd step with partitioning step and also remove resume_offset from both /boot/grub/menu.lst and /etc/initramfs-tools/conf.d/resume.

---

### Post by Herman on 2009-01-20
:D I have now completed stage 2 of your how-to and hiberated my EeePC to try it out.
It hibernated and resumed beautifully, thanks once again,  iva2k ! :D

---

### Post by bosworthy on 2009-01-25
If I have 1 gig of ram, do I REALLY need 2 gig of ram for my swap space?  I have Ubuntu installed on a usb stick that's partitioned to 7 gig.  I really don't want to waste space.  What will happen if I use a have a swap space of 512meg or 1 gig instead of the recommended 2 gig.  will I still be able to hibernate?  It's hard to imagine that linux will dump the whole ram onto the disk instead of only dumping what's useful in memory.

Thanks.

---

### Post by bosworthy on 2009-01-25
Hi Iva2k,


I'm not sure why, but I don't have a hibernation button. I do have suspend.  i've installed ubuntu on a usb stick.  Before the tutorial i had the hibernation button, but before AND after this tutorial, my hibernation and sleep mode never worked.  It would never wake.  I notice there's no lights on my usb stick.. I'm not sure if this is a hardware issue.  I'm running ubuntu 8.04 on a HP zv6000 laptop.  I remember in windows, you can't wake the computer up via the mouse or keyboard on my hp zv6000 because the usb power is shutdown and won't resume.  I've heard that dell though fixed this on some of their models. 

Thanks,

---

### Post by iva2k on 2009-01-26
> **bosworthy said:**
> Hi Iva2k,


I'm not sure why, but I don't have a hibernation button. I do have suspend.  i've installed ubuntu on a usb stick.  Before the tutorial i had the hibernation button, but before AND after this tutorial, my hibernation and sleep mode never worked.  It would never wake.  I notice there's no lights on my usb stick.. I'm not sure if this is a hardware issue.  I'm running ubuntu 8.04 on a HP zv6000 laptop.  I remember in windows, you can't wake the computer up via the mouse or keyboard on my hp zv6000 because the usb power is shutdown and won't resume.  I've heard that dell though fixed this on some of their models. 

Thanks,

Hi bosworthy,
Sorry to hear that you have hibernation not working for you. One prerequisite of this tutorial is to have working hibernation. It means that following the steps of this howto will not fix your broken hibernation. Something else is preventing it from working.
I would start with making suspend work first. It probably fails due to one or more of the device drivers. 

And yes, it is highly recommended to have swapfile twice the size of RAM so hibernation would work. It really depends on the applications you are running. You could try a smaller swapfile, but if your swap memory is used at all (which can be checked by "free -m" command), you should account for the need to save the whole 1GB of RAM you have on top of the used swapfile space. So by simple math it brings you over 1GB of needed space in the swapfile. As I understand hibernation portion of the kernel, it does not compress memory image, other than writing only your used pages to disk (it has memory controller to gather that information). It would be nice to have compression, but will take extra time to hibernate and wake up.

When your swapfile file is too small for your session (you have too many applications running with a lot of open documents), you could loose it all if you try to hibernate and it fails. In my case it locks up when hibernation stops due to lack of space in the swapfile - I need to power-cycle. So it is risky to have small swapfile and allow hibernation.

Re: waking after sleep.
Try the power button. It should wake the system from suspend. Also you should check your bios settings (press DEL key while powering up on most systems) - it may have some USB settings buried deep into menus somewhere. If not there, try finding firmware/bios update on manufacturer website. They often do have them without letting you know via HP Update and the like.

Once you have your system Suspend and Hibernation work both ways, you could change to a swapfile per the HOWTO. Swapfile will give you flexibility to change its size anytime (by re-doing the HOWTO), and avoid the need to change disk partitions.

Wish you luck!

---

### Post by bosworthy on 2009-01-29
Thanks Iva,
I'll keep you posted. :)

---

### Post by ee19921 on 2009-05-06
Works great! Thank you!

---

### Post by medic2000 on 2009-06-04
1-How can we reverse this? Activation of swap file takes very long at the boot time. 
2-Plus now i am using lvm. It is not a problem to make a new partition. 
3-How can we sure that hibernate works if we already have not a swap partition before making swapfile?

---

### Post by medic2000 on 2009-06-04
Up!

---

### Post by iva2k on 2009-06-04
To reverse swapfile setup, you need to go through these steps:

```

sudo -b gedit /etc/fstab

```
Edit /etc/fstab and :

   1. Reverse changes (Remove or comment out ALL swap files)
   2. Restore / Add new line:

```

/dev/...   none   swap   sw   0   0

```
Where /dev/... is your swap partition

```

sudo swapoff -a
sudo swapon /dev/...

```

Replace UUID and resume_offset:
```

echo "resume=UUID=<your UUID> resume_offset=0" | sudo tee /etc/initramfs-tools/conf.d/resume

```

Now edit GRUB configuration:
```

sudo -b gedit /boot/grub/menu.lst

```

Find the line "# kopt=root=UUID=..."
and change it to "resume=UUID=<your UUID> resume_offset=0" (without quotes).
Note that your UUID in above two cases will be your swap partition UUID.

It should look like this (with your UUID and offset):
```

# kopt=root=UUID=... ro resume=UUID=cd71de6f-907a-40d7-bf26-c17f201e5718 resume_offset=0

```
Make sure you have no carriage returns in this line.

Now let's run the tools to make them work:

```

sudo update-grub -y

```
Answer "install the package maintainer's version" if it asks.

```

sudo update-initramfs -u

```

Verify that all your kernel stanzas (menu entries) got updated in /boot/grub/menu.lst with resume=... and resume_offset=0, if not - verify your # kopt= line - it should have # and space. Rerun update-grub if necessary. It may keep your old file if you chose wrong answer above.

Now reboot before trying to hibernate, so kernel gets the right resume_offset parameter.

After reboot, try to hibernate. It should get right back to this window after you power your computer back up.

Now you can get rid of the old swapfile.

---

### Post by medic2000 on 2009-06-04
Thank you. Should we do anything with this command?

sudo update-initramfs -u

---

### Post by iva2k on 2009-06-05
> **medic2000 said:**
> Thank you. Should we do anything with this command?

sudo update-initramfs -u

You're right, thanks for noticing it. Not only that, but GRUB menu should be changed. I've edited my previous post to include these steps.

---

### Post by frigaut on 2009-07-23
thanks, it worked like a charm (on jaunty, on an apple machine)

---

### Post by asenyshyn on 2009-10-27
Hi, will this howto work for karmic with grub2? Any changes or improvements needed?

---

### Post by iva2k on 2009-10-28
> **asenyshyn said:**
> Hi, will this howto work for karmic with grub2? Any changes or improvements needed?

I did not try it yet, so cannot say definitively.

---

### Post by bLaCkMeTaLL on 2009-10-30
interesting post indeed, thank you very much for your efforts.

Will we have hiberfil.sys-equivalent under karmic?

---

### Post by RBertrand on 2009-11-05
Just got it working with Karmic (Kubuntu amd64).

As in Karmic grub is " upgraded" to version 2, it took some reading (see: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) ).

Another "difference" is the use of filefrag, it seems that one is "upgraded" also, so iva2k's code will not work as printed.

All other commands are valid still.

Things I did:
After creation of the swapfile, I tried to check it with filefrag. However, my 6G file was setting filefrag into a loop and there was no "First block:" output anywhere. It seems that when you have a a file that is bigger than 4G (or about), filefrag restarts counting the logical blocks and gets itself in a loop.

So I checked filefrag out and it seems it is changed conforming some proposals back in 2007. It now uses FIEMAP instead of FIBMAP and its output is changed. From what I found, the first physical (block?) in its output seems to be the needed offset.

In post [http://forums.fedoraforum.org/showthread.php?t=204114](http://forums.fedoraforum.org/showthread.php?t=204114) a swap_offset utility was mentioned, so I installed the corresponding uswsusp and used the tool. It did give me the same number back.

Then I made an 07_hibernation file in /etc/grub.d/ out of the 40_custom file already given there.
I picked 07, so I have this on top and selected in grub during boot time and I wouldn' t have to change the grub file in /etc/default/ also.
```

menuentry "Ubuntu 9.10 Hibernation, Linux 2.6.31-14-generic" {
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set d3b0cf1a-99ca-43c1-a058-d7c38c0b6171
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=d3b0cf1a-99ca-43c1-a058-d7c38c0b6171 ro resume=UUID=d3b0cf1a-99ca-43c1-a058-d7c38c0b6171 resume_offset=1544
    initrd    /boot/initrd.img-2.6.31-14-generic
}

```This text need to come directly below the last comment line in the file, as it seems that when there is an empty line at that position, the entry will not be picked up by upgrade-grub. Note: I omitted the quit and splash parameters to be able to see what was happening, add these if you like.

After this, I used the update-grub code (I think grub2 didn't like the -y at the end, but I am not sure anymore) and the initramfs-tools code.

Hibernation will not work at that point, however.
It seems that you need to reboot the machine and select the boot-option with the resume-entry first, and only then you are able to set the machine into hibernation.

If you boot with any other (non-resume) entry, now or later, you get an "PM: Swap header not found" message during hibernation and the machine will go into a clean boot the next time.

I would like to know if this can be solved, or that it is inherent to the way hibernation (and booting) works. However, given the fact that hibernation is working, I can live with that.

Hibernation in (K)Ubuntu is painfully slow compaired to what I was used to in Windows, but I'll take it because I don' t need to give all my different passwords the next time I boot and want to start WiFi (KWallet), Firefox and my encrypted datacontainers.

---

### Post by suar on 2009-11-06
> **RBertrand said:**
>  a swap_offset utility was mentioned  proper spelling is swap-offset > **RBertrand said:**
>  Then I made an 07_hibernation file in /etc/grub.d/ out of the 40_custom file already given there.
I picked 07, so I have this on top and selected in grub during boot time and I wouldn' t have to change the grub file in /etc/default/ also.  it's much better to adjust /etc/default/grub by changing GRUB_CMDLINE_LINUX_DEFAULT="splash resume=UUID==3f729a36-0b10-447c-83cf-d41deadbeef6 resume_offset=666" where UUID is appropriate id for partition where your swapfile is located and resume_offset is value returned by swap-offset. This way only "normal" and not "recovery" entries of grub menu will be affected. Also it's easier to edit by users and error-prone because that's less text to enter :-)  Don't forget to run  sudo update-grub after this.  Note: you have to reboot to use suspend-to-disk after this because that's the only wy to pass this options from grub to kernel.

---

### Post by ronocdh on 2009-11-14
I have trouble getting beyond this point:```
sudo filefrag -v /swapfile | grep "First block:"
```When I enter that command, I get no output whatsoever. If I trim it down to:```
sudo filefrag -v /swapfile | grep "F"
```then I get:```
Filesystem type is: ef53
Filesystem cylinder groups is approximately 445
File size of 3100MB.swap is 3174400000 (775000 blocks, blocksize 4096)

```Any ideas on why I'm not getting any output for "First block"? The file is already formatted as swapspace. I've tried running the filefrag command with the swapfile turned on and off.

---

### Post by Operan on 2009-11-22
> **suar said:**
> proper spelling is swap-offset  it's much better to adjust /etc/default/grub by changing GRUB_CMDLINE_LINUX_DEFAULT="splash resume=UUID==3f729a36-0b10-447c-83cf-d41deadbeef6 resume_offset=666" where UUID is appropriate id for partition where your swapfile is located and resume_offset is value returned by swap-offset. This way only "normal" and not "recovery" entries of grub menu will be affected. Also it's easier to edit by users and error-prone because that's less text to enter :-)  Don't forget to run  sudo update-grub after this.  Note: you have to reboot to use suspend-to-disk after this because that's the only wy to pass this options from grub to kernel.

Thanks you. I did like that, and my machine can hibernate. The issue that it seems not to be able to restore from resume state. I've waited about 4 minutes while the only cursor blinked on the gray (or black) screen. 4 or 5 mins is not acceptable. 
Any suggestion? How long does hibernation take you to restore from resume state in swap file?


> **ronocdh said:**
> I have trouble getting beyond this point:```
sudo filefrag -v /swapfile | grep "First block:"
```When I enter that command, I get no output whatsoever. If I trim it down to:```
sudo filefrag -v /swapfile | grep "F"
```then I get:```
Filesystem type is: ef53
Filesystem cylinder groups is approximately 445
File size of 3100MB.swap is 3174400000 (775000 blocks, blocksize 4096)

```Any ideas on why I'm not getting any output for "First block"? The file is already formatted as swapspace. I've tried running the filefrag command with the swapfile turned on and off.
You should read the post by RBertrand carefully! :)

---

### Post by suar on 2009-11-23
> **Operan said:**
>  Any suggestion? How long does hibernation take you to restore from resume state in swap file?


Have no idea what's wrong in your case. For me it was about 10-30 seconds of disk drive activity before I see gnome's lock screen with prompt to enter password. Are you sure that you carefully followed how-to steps? uswsusp is installed and so on?

---

### Post by ronocdh on 2009-11-23
> **Operan said:**
> You should read the post by RBertrand carefully! :)
Thanks! That's gotten me much further. Now when I try to do **sudo s2disk**, it goes to an all-text screen, says it successfully created the snapshot, then counts up to 100% on "Saving 352645 image data pages." Once it reaches 100%, however, it prints "Done" and I'm right back at my desktop!

So, clearly there's more work to be done, but I'll be darned if I know where to start! I'll post back if I find anything of substance, naturally.

---

### Post by excogitation on 2009-12-31
> **RBertrand said:**
> Just got it working with Karmic (Kubuntu amd64).


I'm still trying to make it work with Karmic (x86) but can't manage.

When adding resume=UUID= and resume_offset= to the boot options the system doesn't boot up with that particular entry.

```
menuentry "Ubuntu, Linux 2.6.31-17-generic (Hibernate)" {
        recordfail=1
        if [ -n  ]; then save_env recordfail; fi
	set quiet=1
	saved_entry=
	save_env saved_entry
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 1cc935ad-91a9-4be3-ae71-0a23b1ade94f
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=1cc935ad-91a9-4be3-ae71-0a23b1ade94f ro resume=UUID=1cc935ad-91a9-4be3-ae71-0a23b1ade94f resume_offset=598016
	initrd	/boot/initrd.img-2.6.31-17-generic
}

```

How about fixing it for everyone: [#313724]("https://bugs.launchpad.net/ubuntu/+bug/313724")

---

### Post by AkifTariq on 2010-01-05
I have the same problem as with ronocdh. I cannot get any output of the command:
sudo filefrag -v /swapfile | grep "First block:"

Can anyone please help me on this? I have tried everything to get the output (turning swap off and formatting swap etc.)

ronocdh and I have one thing in common. His swap file is just over 3 GB as mine. Can this be the cause of the problem? Shall I try smaller swap file?

I am stuck at this point. Please help.

---

### Post by ronocdh on 2010-01-05
> **AkifTariq said:**
> I have the same problem as with ronocdh. I cannot get any output of the command:
sudo filefrag -v /swapfile | grep "First block:"

Can anyone please help me on this? I have tried everything to get the output (turning swap off and formatting swap etc.)

ronocdh and I have one thing in common. His swap file is just over 3 GB as mine. Can this be the cause of the problem? Shall I try smaller swap file?

I am stuck at this point. Please help.
Thanks for the followup, AkifTariq! Very interesting that you notice we both have large(r than normal?) swap files. I'll give it another go this weekend, as I recently freed up a ton of space on my laptop.

I'll definitely try with multiple swap files and see whether that affects anything. I'm doing this on a MacBook Pro (3 years old) with 3GB of RAM, so I don't think s2disk will work with a smaller swap file.

---

### Post by RBertrand on 2010-01-21
Just a follow-up with some experience with hibernation, maybe some other (K)Ubuntu users will be helped with this, I think ronocdh and AkifTariq could be experiencing similar problems...

As I am a linux newbie, I'm not sure whether I am 100% correct about my conclusions, so I am going to write out my experiences.

**Bottom line:**
- Hibernation using the kernel seems to be broken with ext4 fs; possibly because of journal checks during boot or a bug concerning large files on ext4 partitions (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/453579) )
- However, I managed to get it working with uswsusp (s2disk)
- filefrag has a bug when used on large files (> 4G) on ext3

**What I did:**
I made a mistake updating my Kubuntu Karmic amd64, leaving it non-usable, so I decided to reinstall. As I experienced numerous rough edges using Kubuntu, I decided to try the Gnome 64bit version and see whether this distro delivered a better and more integrated application suite. I don't know why, but somewhere in the process I went with the defaults Ubuntu presented and installed the system onto an ext4 partition.

I followed iva2k's guide, but was unable to get hibernation working. First, I thought this was because I forgot to set the resume-file in /etc/initramfs-tools/conf.d/, but after correcting that going into hibernation worked, but resume still didn't work, leaving the PC hanging without usable prompt after going through the local-premount scripts where resume is called and I had to reboot the PC from scratch.

Because this wasn't going to work, I installed uswsusp and checked out s2disk. First, that didn't work either. That seemed due to the fact that all parameters in grub told the kernel to use its own resume option. I deleted the offset value from grub and after a s2disk hibernation, the PC came back to life (and a lot faster than it did before with kernel based resume).

But at that point, I was unable to modify the Ubuntu (Gnome) startmenu and the power management to point to s2disk instead of the "normal" hibernation AND Gnome was a bit too polished to my liking, so I decided to go back to Kubuntu, where I also knew hibernation did work before.

**Going back to Kubuntu Karmic amd64...**
I formatted the root partition and installed Kubuntu. Then I followed iva2k's procedure again and hibernation DIDN' T WORK!?  :confused: I had exactly the same issue that I had with Ubuntu Karmic amd64.

But then I remembered I had no problem with filefrag, however! The output still didn't contain the *"First block:"* string, **as is expected**, but it didn't go into an endless loop. At that point, I knew what the difference was: the first time I installed Kubuntu, I decided to stick with ext3, because there were numerous bugs, and one of them was that ext4 possibly corrupted large files (>512MB). And my swapfile is a large file (6GB)...

Looking into the logs, I can see that resume finds the correct hibernation image, but fails to resume correctly. Later on in the boot process, it tries to resume again "manually" (I don' t know what  that is). Around that time, the journal is read also, so that could be interfering with the resume process, but it can also originate from large file corruption on ext4, reported by several users. I don't know.

So I installed Kubunutu again onto ext3 and I configured hibernation. Again, filefrag went bezerk, so I used swap-offset instead. But I did not need to use s2disk, because after booting with the said kernel parameters, the hibernation and resume worked again.

I hope for you this ext4-thingy is the cause of your hibernation troubles, because you might find a solution by ging to ext3 as I did.

Note: suspend (or more exactly: resume from suspend) worked on my box only after installing the 185 nVidia drivers, not with the default X-window drivers. As I checked suspend before setting up hibernation, it is possible that you need to install the correct video drivers before resume from hibernation will work.

The behaviour of the PC is different when hanging on video drivers during resume (my box beeped not being able to present a desktop-image and I had working terminals with an login prompt) and you might find out in the logs whether this plays a role in your situation.

---

### Post by suar on 2010-10-12
This how-to was wroking perfectly with ext4 & 10.04 Unfortunately it will not work with btrfs and 10.10 due to incompatibilities with swapon.  As a possible workaround it is mentioned that we can use loopback device. Unfortunately I was unable to find any sort of instructions on how exactly to do that.  If somebody managed to figure it out - please share.

---

### Post by dralastair on 2011-01-07
Just want to add I've got this working with Ubuntu 10.10 and ext4 filesystem on an eeepc 1005. I've got 4G swapfile (for 2G RAM) on root partition.
Suspend was working correctly prior to the mod.

I used the original HOWTO with RBertrand's update for grub2 and filefrag.

The only issue I'm noticing at the moment is that on resume the sound is muted - but that's something I can live with...

**Update**

Hibernate working fully now - had to install hibernate package:

sudo apt-get install hibernate

probably should have had this to start with!

---

### Post by nakednous on 2011-01-07
Hi all,

I'm running ubuntu 10.10 which uses grub2 and I hope suspend to work with a swap file (read somewhere uswsusp is needed).

I suppose I need to edit /etc/default/grub before running update-grub. According to your instructions (thanks for such great tutorial) anyone knows how this file should be edited?

Thanks in advanced. Regards,

Jean Pierre

---

### Post by nakednous on 2011-01-07
> **nakednous said:**
> Hi all,

I'm running ubuntu 10.10 which uses grub2 and I hope suspend to work with a swap file (read somewhere uswsusp is needed).

I suppose I need to edit /etc/default/grub before running update-grub. According to your instructions (thanks for such great tutorial) anyone knows how this file should be edited?

Thanks in advanced. Regards,

Jean Pierre
sorry I didn't notice that the thread was more than one page long :) Will check dralastair and RBertrand's posts in detail before asking something again.

---

### Post by nakednous on 2011-01-07
> **nakednous said:**
> Hi all,

I'm running ubuntu 10.10 which uses grub2 and I hope suspend to work with a swap file (read somewhere uswsusp is needed).

I suppose I need to edit /etc/default/grub before running update-grub. According to your instructions (thanks for such great tutorial) anyone knows how this file should be edited?

Thanks in advanced. Regards,

Jean Pierre
sorry I didn't notice that the thread was more than one page long :) Will check dralastair and RBertrand's posts in detail before asking something again.

---

### Post by nakednous on 2011-01-07
> **nakednous said:**
> Hi all,

I'm running ubuntu 10.10 which uses grub2 and I hope suspend to work with a swap file (read somewhere uswsusp is needed).

I suppose I need to edit /etc/default/grub before running update-grub. According to your instructions (thanks for such great tutorial) anyone knows how this file should be edited?

Thanks in advanced. Regards,

Jean Pierre
sorry I didn't notice that the thread was more than one page long :) Will check dralastair and RBertrand's posts in detail before asking something again.

---

### Post by nakednous on 2011-01-07
sorry I didn't notice the thread was longer than its first place. Will check RBertrand and dralastair posts before asking again (if necessary).

---

### Post by nakednous on 2011-01-08
(sorry for my previous repeated posts I had a bad connection and hit many times the "submit reply" button)

I'm exclusively running kubuntu 10.10 (maverick) on an asus N53J with a SSD of 120GB and 10GB of RAM, with a single ext4 partition (without swap partition which seemed a good configuration for my hardware). I followed the instructions found here to make suspend to a swap file work without success.

First of all I'm confuse about which suspend method to use: the in kernel default method (aka suspend or **swsusp**) or user space suspend (**uswsusp**). I tried both. I did it as follows:

**1. swsusp**

Followed the instructions here ***without*** installing **uswsusp**. To get the swap offset I ran: sudo filefrag -v /swapfile without problem. The output was:

```
Filesystem type is: ef53
File size of /swapfile is 5215938560 (1273423 blocks, blocksize 4096)
 ext logical physical expected length flags
   0       0 10649600            2048
...
```

I noted the 10649600 number. To configure grub2 (before running sudo update-grub, I changed the GRUB_CMDLINE_LINUX_DEFAULT variable found in /etc/default/grub. It looks like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=deadline resume=UUID=2e55de9d-891f-4040-b9a5-6c96b6bfb650 resume_offset=10649600"
```

**Note**: It's also possible to configure the variable GRUB_CMDLINE_LINUX in grub. In this case, the changes will affect also the "recovery mode" kernel images.

Then I configured the /etc/initramfs-tools/conf.d/resume and run sudo update-initramfs -u just as suggested here.

**Result**: suspend to ram works fine. Suspend to disk puts my screen to black and hangs. After some minutes I reset the laptop. I noticed that when hitting the power button the machine turned off with activity as if one has turned it off correctly.

**2. uswsusp**

I made the following changes respect to the previous method:
1. I installed hibernate and uswsusp: sudo apt-get install hibernate uswsusp
2. To get the swap offset I ran: sudo swap-offset /swapfile. The output was:

```
resume offset = 10649600
```

Same offset as in the previous case.
3. I then edit the /etc/uswsusp.conf file running sudo dpkg-reconfigure uswsusp. It looks like this:

```
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda1
compress = y
early writeout = y
image size = 4.79866e+09
RSA key file = /etc/uswsusp.key
shutdown method = platform
resume offset = 10649600
compute checksum = y
suspend loglevel = 5
max loglevel = 5
```

Before editing it, I was surprised by the fact that the file was already well configured (it had the correct offset. I just ended adding the log entries to it).

**Result**: same as with **swsusp**. I also tried to integrate uswsusp with pm-utils without success as explained [here]("https://help.ubuntu.com/community/PowerManagement/Hiberate#Integrating uswsusp with pm-utils") (seems that **swsusp** installation routine already does it).

---

### Post by bilkay on 2011-01-11
I thought I couldn't get the laptop to hibernate because selecting "Hibernate" from the shutdown menu only brought up a gray screen. However, I found the the command "sudo hibernate" from a terminal DID put it into hibernation.

How do I get it to work from the menu?

p.s. Selecting "Hibernate" from the shutdown applet causes a blank gray screen to come up for several seconds, then the computer goes off. Next boot goes through normal start-up to login-screen.

Selecting "Hibernate" from the indicator applet first brings up a locked-screen password entry, then shuts down. Next boot goes through normal start-up to login-screen. However, after login, network starts out disabled (?).

---

### Post by el_jee on 2011-01-19
Can't seem to get this working on my fresh Maverick install.

Tried all the suggestions in this thread, but none helped unfortunately. Even removed all (non-essential) pieces of hardware, without success.

The swsusp method does shutdown, but is unable to load the image.
In my boot.log I found the following:
```
Invalidating stale software suspend images... /swapfileswapon: /swapfile: software suspend data detected. Rewriting the swap signature.
```

The uswsusp method saves all the data to the swapfile, but goes straight back to login screen or the open session, depending on how it is called.
I couldn't find any errors in dmesg between the process of shutting down devices and starting them again:
```

 7546.652403] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[ 7548.374093] PM: Marking nosave pages: 000000000009e000 - 0000000000100000
[ 7548.374097] PM: Basic memory bitmaps created
[ 7548.724812] snapshot_deprecated_ioctl: 14359 callbacks suppressed
[ 7548.724819] snapshot_ioctl: ioctl '80043307' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7548.724823] Syncing filesystems ... done.
[ 7548.727977] Freezing user space processes ... (elapsed 0.01 seconds) done.
[ 7548.744065] Freezing remaining freezable tasks ... (elapsed 0.01 seconds) done.
[ 7548.760073] snapshot_ioctl: ioctl '4004330c' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7548.760143] snapshot_ioctl: ioctl '40043306' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7548.760146] snapshot_ioctl: ioctl '40043303' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7548.760170] PM: Preallocating image memory... done (allocated 300494 pages)
[ 7548.900908] PM: Allocated 1201976 kbytes in 0.14 seconds (8585.54 MB/s)
[ 7548.900910] Suspending console(s) (use no_console_suspend to debug)
[ 7548.901192] sd 0:0:1:0: [sda] Synchronizing SCSI cache
[ 7548.901563] parport_pc 00:07: disabled
[ 7548.901778] serial 00:06: disabled
[ 7548.901833] HDA Intel 0000:01:05.1: PCI INT B disabled
[ 7548.901856] ACPI handle has no context!
[ 7548.972167] ahci 0000:00:11.0: PCI INT A disabled
[ 7548.977048] [drm] Disabling audio support
[ 7548.978053] radeon 0000:01:05.0: c177a800 unpin not necessary
[ 7549.046497] PM: freeze of drv:radeon dev:0000:01:05.0 complete after 144.670 msecs
[ 7549.046533] PM: freeze of drv:pci dev:0000:00:01.0 complete after 138.024 msecs
[ 7549.046549] PM: freeze of drv: dev:pci0000:00 complete after 137.952 msecs
[ 7549.046554] PM: freeze of devices complete after 145.489 msecs
[ 7549.046914] PM: late freeze of devices complete after 0.358 msecs
[ 7549.046981] ACPI: Preparing to enter system sleep state S4
[ 7549.047871] PM: Saving platform NVS memory
[ 7549.052818] PM: Saving platform NVS memory
[ 7549.057760] Disabling non-boot CPUs ...
[ 7549.164040] CPU 1 is now offline
[ 7549.164044] SMP alternatives: switching to UP code
[ 7549.167788] Extended CMOS year: 2000
[ 7549.167856] PM: Creating hibernation image:
[ 7549.168021] PM: Need to copy 288902 pages
[ 7549.168021] PM: Normal pages needed: 107541 + 1024, available pages: 120620
[ 7549.168021] PM: Hibernation image created (288902 pages copied)
[ 7549.168021] Extended CMOS year: 2000
[ 7549.168021] Enabling non-boot CPUs ...
[ 7549.168021] SMP alternatives: switching to SMP code
[ 7549.171364] Booting Node 0 Processor 1 APIC 0x1
[ 7549.167504] Initializing CPU#1
[ 7549.296286] CPU1 is up
[ 7549.296620] ACPI: Waking up from system sleep state S4
[ 7549.297219] PM: early thaw of devices complete after 0.072 msecs
[ 7549.297329] ahci 0000:00:11.0: restoring config space at offset 0x1 (was 0x2300103, writing 0x2300107)
[ 7549.297348] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 7549.297414] radeon 0000:01:05.0: setting latency timer to 64
[ 7549.297790] [drm] Clocks initialized !
[ 7549.299480] serial 00:06: activated
[ 7549.300664] parport_pc 00:07: activated
[ 7549.300890] sd 0:0:1:0: [sda] Starting disk
[ 7549.312375] HDA Intel 0000:01:05.1: BAR 0: set to [mem 0xfeae8000-0xfeaebfff] (PCI address [0xfeae8000-0xfeaebfff]
[ 7549.312394] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 7549.312398] HDA Intel 0000:01:05.1: setting latency timer to 64
[ 7549.355414] [drm] ring test succeeded in 1 usecs
[ 7549.355427] [drm] ib test succeeded in 0 usecs
[ 7549.355429] [drm] Enabling audio support
[ 7549.464046] ata1.01: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 7549.464050] ata1.01: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 7549.472883] ata1.00: ACPI cmd ef/03:46:00:00:00:a0 (SET FEATURES) filtered out
[ 7549.472886] ata1.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 7549.488801] ata1.00: configured for UDMA/33
[ 7549.494264] PM: thaw of drv:radeon dev:0000:01:05.0 complete after 196.876 msecs
[ 7549.510037] ata1.01: configured for UDMA/100
[ 7549.532387] PM: thaw of drv:sd dev:0:0:1:0 complete after 231.493 msecs
[ 7549.532399] PM: thaw of drv:scsi_disk dev:0:0:1:0 complete after 151.913 msecs
[ 7549.532447] PM: thaw of drv:scsi_device dev:0:0:1:0 complete after 231.532 msecs
[ 7549.532451] PM: thaw of devices complete after 235.202 msecs
[ 7549.532677] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7549.532749] snapshot_ioctl: ioctl '80043307' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7549.532809] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7549.532812] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7549.532996] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7549.533043] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7549.616389] ata3: SATA link down (SStatus 0 SControl 300)
[ 7549.616419] ata5: SATA link down (SStatus 0 SControl 300)
[ 7549.616444] ata4: SATA link down (SStatus 0 SControl 300)
[ 7549.620388] ata6: SATA link down (SStatus 0 SControl 300)
[ 7553.775965] snapshot_deprecated_ioctl: 20159 callbacks suppressed
[ 7553.775971] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776098] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776180] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776248] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776296] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776380] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776432] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776497] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776562] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7553.776626] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.780650] snapshot_deprecated_ioctl: 24918 callbacks suppressed
[ 7558.780657] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.780770] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.780845] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.780910] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.780975] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.781040] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.781104] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.781168] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.781231] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7558.781296] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791124] snapshot_deprecated_ioctl: 27059 callbacks suppressed
[ 7563.791131] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791257] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791266] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791331] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791395] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791459] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791522] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791585] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791648] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7563.791711] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940264] snapshot_deprecated_ioctl: 29822 callbacks suppressed
[ 7568.940270] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940372] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940434] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940504] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940569] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940632] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940696] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940760] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940824] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7568.940887] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944026] snapshot_deprecated_ioctl: 23028 callbacks suppressed
[ 7573.944032] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944117] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944193] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944237] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944344] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944379] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944438] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944504] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944568] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7573.944652] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948074] snapshot_deprecated_ioctl: 22062 callbacks suppressed
[ 7578.948081] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948402] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948455] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948484] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948564] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948633] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948707] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948775] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948848] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7578.948911] snapshot_ioctl: ioctl '80043308' is deprecated and will be removed soon, update your suspend-to-disk utilities
[ 7583.844256] Restarting tasks ... done.
[ 7583.901304] PM: Basic memory bitmaps freed
[ 7583.919312] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 7584.582194] r8169 0000:02:00.0: eth0: link up
[ 7587.009789] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0

```

I also tried tuxonice, which didn't work right away. Since I like to use rt-kernels sometimes, i guess it wouldn't be a solution for me anyways.

Any suggestions on what else there is to try?

---

### Post by ronocdh on 2011-01-20
Thanks for mentioning the quirk-checker.sh script. It worked for a friend of mine on a new Sony VAIO with two SSDs, but my MacBook Pro is still without hibernate, after all these years.

From the man page on uswsusp: 
>  resume offset
Necessary if a swap file is used for suspending. In such a case the device identified by the "resume device" parameter is regarded as the partition that contains the  swap  file,  and "resume  offset"  must  be  equal to the offset from the beginning of this partition at which the swap file's header is located, in <PAGE_SIZE> units.  The value of this parameter for given swap file can be determined by the swap-offset program (has to be run as root) included in this package. **[For this feature to work, you will need an -mm  kernel,  2.6.18-mm3  or newer.]**
Most unfortunate. For those not familiar, the -mm tree is [no longer maintained]("http://en.wikipedia.org/wiki/Mm_tree"), not since 2007. Given that the hibernate command just calls other scripts, this would explain why hibernation isn't working, even with a properly configured uswsusp.conf. Found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/278573") interesting, particularly comment #6.

Hate to be pessimistic, but I'm near giving up on this s2ram works OK, but I've never had s2disk working on this laptop.

---

### Post by ronocdh on 2011-01-20
Thanks for mentioning the quirk-checker.sh script. It worked for a friend of mine on a new Sony VAIO with two SSDs, but my MacBook Pro is still without hibernate, after all these years.

From the man page on uswsusp: 
>  resume offset
Necessary if a swap file is used for suspending. In such a case the device identified by the "resume device" parameter is regarded as the partition that contains the  swap  file,  and "resume  offset"  must  be  equal to the offset from the beginning of this partition at which the swap file's header is located, in <PAGE_SIZE> units.  The value of this parameter for given swap file can be determined by the swap-offset program (has to be run as root) included in this package. **[For this feature to work, you will need an -mm  kernel,  2.6.18-mm3  or newer.]**
Most unfortunate. For those not familiar, the -mm tree is [no longer maintained]("http://en.wikipedia.org/wiki/Mm_tree"), not since 2007. Given that the hibernate command just calls other scripts, this would explain why hibernation isn't working, even with a properly configured uswsusp.conf. Found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/hibernate/+bug/278573") interesting, particularly comment #6.

Hate to be pessimistic, but I'm near giving up on this. s2ram works OK, but I've never had s2disk working on this laptop.

---

### Post by bilkay on 2011-01-30
I'd like to pass on what I've learned from a situation where I changed swapfiles after getting hibernate to work on the old one, AND I updated the kernel to 2.6.32-28-generic, but due to a problem with sound, I prefer to stay with the previous kernel version. (running ubuntu 10.04.1)

First, after determining the new resume_offset, it has to be changed in three places:

/etc/default/grub
/etc/uswsusp.conf
/etc/initramfs-tools/conf.d/resume

If the 2.6.32-28 is installed, but you want to stick with 2.6.32-27, do the following:

In /etc/default/grub, change GRUB_DEFAULT=0 to GRUB_DEFAULT=2

Run the following:

$ sudo grub-update
$ sudo update-initramfs -uk $(uname -r)

---

### Post by bilkay on 2011-02-05
I'm having one significant problem with this. Hibernation (and resume) works OK, but only by the command "sudo hibernate". Clicking "Hibernate" on the shutdown menu apparently causes the image to be saved - at least according to /var/log/pm-suspend.log. However, on restart, /var/log/syslog contains:

```
...
Feb  5 15:00:10 Laptop kernel: [    0.388681] PM: Checking image partition UUID=e42b5082-99ef-4740-a1e1-4f45af8de261
Feb  5 15:00:10 Laptop kernel: [    0.408956] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
Feb  5 15:00:10 Laptop kernel: [    0.453478] ACPI: Battery Slot [BAT0] (battery present)
Feb  5 15:00:10 Laptop kernel: [    0.659187] isapnp: No Plug & Play device found
Feb  5 15:00:10 Laptop kernel: [    0.659207] PM: Resume from disk failed.
...
```

What am I missing?

---

### Post by iX9 on 2011-05-11
Hi! :D

  And what now?
  Is possible to hibernate with **Kubuntu 11.04, ext4 **partition and** 2GiB swapfile?**
  I tryed it by using posts here, my system do hibernate - takes about 15s to writte ~750MB, then comp is turned off. But when loading, it freezes..:(:(:confused:

---

### Post by raacer on 2011-06-06
Maybe this will help somebody to find some good solution for the resume problem.

I've got hibernation working on my Eee PC 901 just by fixing the GRUB_CMDLINE_LINUX_DEFAULT option. However it hangs on resume after loading the dumped memory. I tried to do soft reset by typing magic combination RSEIUB via Alt+Ctrl+PrtSc. And the system came back to life just after "E".

So, there is no need to reset pc as some people did here before. Just kill the loader instead.

---

