---
title: "[SOLVED] GRUB loads the wrong menu.lst"
date: 2008-11-28
forum: General Help
---

### Post by jasonkirk2006 on 2008-11-28
I have several partitions in my harddrive such as

```

sda1 : Windows Vista
sda2 : Ubuntu 8.04
sda3 : Pardus Linux 2008
...

```

I don't use GRUB at the MBR, so Vista Boot Manager welcomes me after BIOS screen. GRUBs of the linux OSs are installed in the first sectors of respective partitions. And i dumped the GRUB code into a binary file with the dd command, so that Vista boot manager can have an entry for them.

Now, when vista's boot manager displays the menu, i choose the 3rd entry to boot Pardus, but somehow, instead of displaying the menu.lst in sda3, it displays that of the sda2 (that of Ubuntu).

At first, i thought this is result of messing up the 3rd partiton with Interpid, so i tried to re-install the grub manually using both grub interactive environment and grub-install command but i've failed.

In fact grub prompt gives the following:
```

grub > root (hd0,2)
grub > setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... [COLOR="Red"]**failed (this is not fatal)**[/COLOR]
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... [COLOR="Red"]**failed (this is not fatal)**[/COLOR]
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded

```

Whereas, grub-install prompts something like 

```

# grub-install /dev/sda3
...
Updated /dev/sda

```

instead of sda3.

With the help of the menu.lst file that resides in the Ubuntu partition, i can boot Pardus. But for some reason, i cannot display the menu.lst of the Pardus (sda3). I think the grub on /dev/sda3 loads (or points to) the wrong menu.lst file. But i know no way of correcting it.

Could anyone please help me determining the problem?

---

### Post by TeXtonyx on 2008-11-28
I have a fairly similar setup although I use XP's boot.ini to 
control Ubuntu on the same drive as XP and Vista and another Ubuntu
on the other drive. I did this by adding Vista to the Ubuntu menu.lst

I suggest copy and pasting from the menu.lst in Pardus, just the 
portion that makes it boot, title, root, kernel, initrd, into
the menu.lst for Ubuntu so that it becomes a boot option on the
grub menu. This should work if Pardus uses a standard menu.lst.

When you compare the two menu.lst files, Ubuntu should be using
root (hd0,1) and Pardus should be using root (hd0,2), check that.
Another way is to boot with the Super Grub Disk and use it to
boot Pardus. If you've used 'with help' it will show the details
of what root information parameter is used (hd0,x)<- correct x.
That info will let you fix a wrong menu.lst partition entry/root.

It's possible you have the same dd 512 byte file for both Linux
OS. I assume you have named them, the .bin files with different
filenames, like ubuntu.bin and pardu.bin. Maybe they have two
different names but they are actually the same file. Since the
ubuntu.bin works, try renaming the pardu.bin to pardu.bin.ORIG
and make a another pardu.bin. I use free Bootpart for this.

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)    	 bootpa26.zip

Unzip bootpart.exe to the root, C:\> then C:\>bootpart.exe <enter>
This will produce an output in a general way like this:

-------------------------------------------

Physical number of disk 0 : 56d9f43b
 0 : C:* type=7  (HPFS/NTFS), size= 64974861 KB, Lba Pos=63
 1 : C:  type=5  (Extended), size= 15028807 KB, Lba Pos=130769100
 2 : C:  type=83 (Linux native), size= 14354046 KB, Lba Pos=130769163

 3 : C:  type=5   (Extended), size= 674730 KB, Lba Pos=159477255
 4 : C:  type=82  (Linux swap), size= 674698 KB, Lba Pos=159477318
 5 : C:  type=83 (Linux native), size= 17354046 KB, Lba Pos=230769163
etc.
etc.
Physical number of disk 1 : 9ad7b

-----------------------------------------

So since Pardu is on the second partition you would use the second
instance of type=83 which is identified by the number 5 (not 2-> Ubu).

C:\>bootpart 5 pardu.bin <enter>

Which creates a 512 byte boot sector fragment named pardu.bin in C:\
If you do this very often it is quicker than the dd command. This
will work for booting from the menu.lst from Linux and I think Vista.
If you resize a partition you have to run the bootpart command
again because it counts sectors from the beginning of the drive.

Sometimes if you resize a partition the UUID, sometimes found in
menu.lst and fstab as an identifier may change. So the new UUID
needs to replace the old UUID. Don't worry about this yet, I think
replacing the pardu.bin and adding the pardu booting information
to the Ubuntu menu.lst will serve as a workaround until you figure
out what is wrong with Easybcd. It might fix Easybcd.

This should work because you do have access to the Ubuntu menu.lst
where the additional Pardu entry will go for another menu boot option.
Are you able to mount the Pardu partition from Ubuntu? To boot it from 
Super Grub Disk? When you run sudo fdisk -l (lower case L) does the
Pardu partition show up in the report? Do you know if Pardu is healthy?

---

### Post by jasonkirk2006 on 2008-11-28
Thanks for your precious reply.

I think the Super Grub CD will do the job.

I tried to change the binary dd dumps several times. I'm pretty sure that there is nothing wrong with them. I, infact, compared the two files byte by byte, using the output of the od command and yes, they're different. And one of them correctly points to the Ubuntu partition. The other one, somehow, points to he same partition again :(

By the way, i learnt something new from you : bootpart.exe! One more thanks for this also. But the info page mentiones about some limitations, such as the first partition on the first hard disk to be FAT16:

> The only thing I **highly** suggest is : your active partition on your first hard disk must be a FAT16 primary partition. 

I think you didn't applied this and you managed to solve your case - then no problem!

I hope it was super grub CD that i was looking for, and will try it soon, giving information about the result.

---

### Post by caljohnsmith on 2008-11-28
> **jasonkirk2006 said:**
> 
```

grub > root (hd0,2)
grub > setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... [COLOR="Red"]**failed (this is not fatal)**[/COLOR]
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,2)"... [COLOR="Red"]**failed (this is not fatal)**[/COLOR]
 Running "install /boot/grub/stage1 (hd0,2) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded

```

I just wanted to mention that the above behavior is totally normal when you install Grub to the boot sector of a partition; when Grub installs to the MBR, it embeds its stage1.5 file in the sectors immediately following the MBR, because those sectors are usually available. But the sectors following the boot sector of a partition are usually not available, so Grub always takes the safe route of not installing the stage1.5 file to those sectors of the partition.

I don't think the Super Grub Disk is going to help you much since you want to keep Vista as your boot loader. I would  recommend using [EasyBCD]("http://neosmart.net/dl.php?id=1"), as TeXtonyx mentioned in passing. Here is a tutorial for using EasyBCD to do what I think you are trying to accomplish:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Good luck and let us know how it goes. :)

---

### Post by meierfra. on 2008-11-28
> and yes, they're different. And one of them correctly points to the Ubuntu partition. The other one, somehow, points to he same partition again


Could  you boot from Pardu and  post the output of

```
sudo dd if=/dev/sda2 bs=1 skip=64 count=2 2>/dev/null |hexdump|awk '{print $2}'

sudo dd if=/dev/sda3 bs=1 skip=64 count=2 2>/dev/null |hexdump|awk '{print $2}'

sudo dd if=/boot/grub/stage2 bs=1 skip=528 count=32 2>/dev/null|hexdump -C |awk '{print $18$36}'


 
```

---

### Post by jasonkirk2006 on 2008-11-28
Thank you for your explanation, caljohnsmith. I was wondering about the reason of this weird output (e2fs_stage1_5 thing).

I'll try both super grub CD and EasyBCD and report the output.

---

### Post by TeXtonyx on 2008-11-28
I downloaded bootpart260a again to read the documentation, and it says (bootpart.txt),

----------------------------------

This zipfile contain:
32bits\bootpart.exe: 32 bits executable, for 32 bits Windows x86
ia64\bootpart.exe: 64 bits executable, for 64 bits Windows for Intel Itanium
x64\bootpart.exe: 64 bits executable, for 64 bits Windows extended (for
       AMD64 and Intel EM64T : 64 bits Windows on AMD Athlon 64, Opteron,
       Intel Pentium 4, Xeon or Celeron with EM64T) 

---------------------------------------

Nowhere in bootpart.txt for 260a does it say, Quote: 
"The only thing I highly suggest is : your active partition on 
your first hard disk must be a FAT16 primary partition."

Bootpart has been around since 1995 and I think you read some old
documentation even if it is still on the website. I use Bootpart
on two systems and I have 3 web references that use Bootpart and
none of them have a fat16 partition nor is it mentioned.

I think Bootpart works best with XP. But I thought you had a use
for just a *nix.bin generator that works in 12 seconds. Bootpart
also will work with two drives, reaching across, whereas dd will
only work on the same drive for multiple partitions. Also I thought
that you had already tried the Easybcd method of selecting 'add
an OS' to the menu, under Linux, as well as the tutorial way.
But I won't assume that you named your dd dumps with different
filenames. Did you use the neo-grub method of Easybcd? 

Now you said you can boot to Pardu, but don't see a menu.lst.
In Ubuntu the menu.lst is found at /boot/grub/menu.lst
I think you need to compare the two menu.lst files. 
(gk)sudo /boot/grub/menu.lst [I think that's where Pardu's menu.lst is]
Ubuntu's menu.lst root should say (hd0,1) and Pardu's should say (hd0,2)
If Pardu's menu.lst says (hd0,1) then of course it will boot Ubuntu.
This seems like the high % reason for the problem. If not, then the
next paragraph lists other reasons for the problem. You say you can
boot Pardu, so this is the very first thing you should have checked. 
If you have to boot Pardu with SGD, then see if it uses (hd0,2) and
that Ubuntu uses (hd0,1) and that the menu.lst content agrees with it.

It seems like the tutorial method worked for ubuntu. The same
method should work for Pardu (if it's standard) unless the dd
file is wrong, the filename for it is wrong, you didn't follow
the instructions exactly, or you had a typo. I'd think the tut
would mention if its method only worked for adding just one OS.

---

### Post by TeXtonyx on 2008-11-28
"I don't think the Super Grub Disk is going to help you much since you want to keep Vista as your boot loader. I would recommend using EasyBCD, as TeXtonyx mentioned in passing. Here is a tutorial for using EasyBCD to do what I think you are trying to accomplish:"

The purpose of Super Grub Disk is to boot Pardu since it doesn't
boot from the Vista bootloader. Then OP can look/edit the Pardu
menu.lst and see if it points to (hd0,2), Pardu's partition. 
OP will be able to see if (hd0,2) works to boot Pardu and that
the Pardu menu.lst agrees with the SGD settings. He can also see
what setting (hd0,1?) works to boot Ubuntu. I think the wrong
root (hdo,x) pardu menu.lst entry is the big favorite for the
cause of this problem, and one needs (most conveniently) to be
in Pardu in order to edit its menu.lst file. That has nothing
to do with another function of SGD which is to reinstall grub
to the MBR, nor did I say anything about doing that. I think that
most likely, Pardu wrote the wrong menu.lst entry to (hd0,1).

If his current method works for Ubuntu then it should work for
Pardu also, if the menu.lst entry is at fault for Pardu's behavior.

---

### Post by caljohnsmith on 2008-11-28
> **TeXtonyx said:**
> 
The purpose of Super Grub Disk is to boot Pardu since it doesn't
boot from the Vista bootloader. Then OP can look/edit the Pardu
menu.lst and see if it points to (hd0,2), Pardu's partition. 
OP will be able to see if (hd0,2) works to boot Pardu and that
the Pardu menu.lst agrees with the SGD settings. He can also see
what setting (hd0,1?) works to boot Ubuntu. I think the wrong
root (hdo,x) pardu menu.lst entry is the big favorite for the
cause of this problem, and one needs (most conveniently) to be
in Pardu in order to edit its menu.lst file. That has nothing
to do with another function of SGD which is to reinstall grub
to the MBR, nor did I say anything about doing that. I think that
most likely, Pardu wrote the wrong menu.lst entry to (hd0,1).

If his current method works for Ubuntu then it should work for
Pardu also, if the menu.lst entry is at fault for Pardu's behavior.
That's true, if he wants to boot into Pardus to edit its menu.lst, Super Grub can help him do that; but I think it is just as easy to simply mount the Pardus partition while he is in Ubuntu and modify Pardus' menu.lst that way if he needs to. Either way of course will work. :)

---

### Post by jasonkirk2006 on 2008-11-28
To start from the beginning, it's not Pardu, but Pardus. That means Anatolian Leopard. It's a KDE based independent linux distro. Visit [http://www.pardus.org.tr/eng/index.html]("http://www.pardus.org.tr/eng/index.html") for more info.

My apologies to TeXtonyx. I misunderstood the proposal about SGD, as if it was able to fix the GRUB code on the boot sector. After your words, i'm not after SGD anymore.

And for an explanation, yes, i can boot Pardus with the help of the entry written to the menu.lst of sda2 (Ubuntu Partition). I can access the Pardus partiton (which is sda3) and copied the related title/root/kernel/initrd lines to Ubuntu's menu.lst. To re-emphasise my problem, let my repeat these:

1. I use Vista's boot manager in MBR, and installed grub on boot sectors of Linux partitions. I have two more entries for Ubuntu and Pardus in Vista BCD.

2. For this purpose i created binary images of the grub code of the respective partitions (let say ubuntu.bin and pardus.bin) and copied them to active partition (sda1). I also created entries in Vista boot manager. It was working in the beginning.

3. A few week ago, i installed Interpid on that partition, played with it for a while and then restored Pardus from image, which i created with a partition cloning tool beforehand.

4. The problem was a little bit different at first. But now, this is the case: Vista's boot manager entry for Ubuntu works, but that of Pardus does not. When i select Ubuntu from the boot menu of Vista BCD, /dev/sda2/boot/grub/menu.lst is displayed. Selecting Pardus from the same menu displays the same menu.lst, instead of /dev/sda3/boot/grub/menu.lst. I tried chainloading GRUBs like this:

```
title Pardus 2008
root (hd0,2)
chainloader+1

```

but i again see /dev/sda2/boot/grub/menu.lst.

5. Since there is no problem with the Ubuntu entry, i kept ubuntu.bin and changed pardus.bin a few times, after reinstalling grub onto sda3 with different methods.

The following is for meierfra. I booted Pardus and Ubuntu, both gave the same output though.

```

$ sudo dd if=/dev/sda2 bs=1 skip=64 count=2 2>/dev/null |hexdump|awk '{print $2}'
00ff

```


```

$ sudo dd if=/dev/sda3 bs=1 skip=64 count=2 2>/dev/null |hexdump|awk '{print $2}'
00ff

```

```

$ sudo dd if=/boot/grub/stage2 bs=1 skip=528 count=32 2>/dev/null|hexdump -C |awk '{print $18$36}'
|..0.97./boot/gru|
|b/menu.lst

```

But neither i'm familiar with this notation nor i can interpret the output. Could you possibly tell me what they did?

So i'm in a state where GRUB code on sda3 is lost connection with the menu.lst (should i say stage 2?) file that belongs to it. EasyBCD is a Vista tool, right? Can i solve this from Ubuntu without using any non-open source / Windows tools? I don't want to install such third party software, even if they are free of charge.

Thousands of thanks for all of you, even to those who just read this long post.

---

### Post by caljohnsmith on 2008-11-28
How about trying the following command:
```
echo $((16#`sudo dd bs=1 skip=68 count=4 if=/dev/[COLOR="Blue"]sda3[/COLOR] 2>/dev/null | hexdump -e '1/4 "%02X\n"'`))
```
That command looks in the sda3 boot sector and reads the hexadecimal location of the Grub stage2 file that the boot sector points to; then it converts that value to sectors so that the final result is the location of the stage2 file from the beginning of your HDD in sectors. So if you compare that with:
```
sudo fdisk -lu
```
Then you'll want to check that the output of the first command above is within the start/end sector values of your sda3 partition. How about posting the output of the above commands so we can check. :)

---

### Post by meierfra. on 2008-11-28
> But neither i'm familiar with this notation nor i can interpret the output. Could you possibly tell me what they did?

The output of the third command "/boot/grub/menu.lst" tells us that the stage2 file on sda3 is looking for the "menu.lst" in the correct folder: "/boot/grub".    I was worried that it would say "(hd0,1)/boot/grub/menu.lst", (reinstalling grub via "setup (hd0,2)"  wouldn't fix this problem)

We curently don't know for sure  which stage2 files the boot sector on /dev/sda3 is using. The ones on sda2 or the ones from sda3.
I thought the other two commands would  reveal that. But I must have been asleep,  since  those commands only reveal the hard drive, but not the partition. (FF stands for the boot drive)

Luckily caljohnsmith is awake and alert, his command in the previous post will tell us exactly which stage2 file the  sda3 boot sector is using.

Did you run "grub-install /dev/sda3" from Pardu or from Ubuntu?

---

### Post by unutbu on 2008-11-28
Woohoo! More magic! :) Caljohnsmith, how did you know that bytes 69--72 contained the number of sectors from the beginning of the drive to stage2 file?

I have GRUB installed on /dev/sda. When I run
```
echo $((16#$(sudo dd bs=1 skip=68 count=4 if=/dev/sda 2>/dev/null | hexdump -e '1/4 "%X\n"')))
```
I get 
```
1
```
but this of course is not the location of my stage2 file. How do I find out the location in this case?

---

### Post by meierfra. on 2008-11-28
> I get 

 1

but this of course is not the location of my stage2 file.

It's the location of your stage1.5 file. 

>  How do I find out the location in this case?
When the stage1.5 files are used, grub does not store the location of the stage2 files. Instead it stores the path "/boot/grub/stage2". 

But you can use

```
sudo grub

"blocklist (hdX,Y)/path/to/any_file"
``` 

to determine the location of any_file of size up to 3.1MB.

---

### Post by caljohnsmith on 2008-11-28
> **unutbu said:**
> Woohoo! More magic! :) Caljohnsmith, how did you know that bytes 69--72 contained the number of sectors from the beginning of the drive to stage2 file?
Well, what I did first was install Grub to the boot sector of some of my linux partitions using different locations of Grub's boot files:
```
sudo grub
grub> root (hd0,X)
grub> setup (hd0,Y)
```
So I used different X values for the location of the Grub boot files, but I also installed Grub to the boot sector of different partitions using different values of Y. Then I copied the boot sectors of those partitions with "dd", and after that I dug out my hex comparison program that compares binary files; it became immediately clear that bytes 69-72 were the values that changed when I changed the partition containing Grub's boot files (the X value). But then came the problem of trying to figure out how those 4 bytes corresponded to the location of the stage2 file. I knew those bytes had to somehow give the physical location of the stage2 file and not the partition containing stage2, because only the stage1.5 file is capable of searching for the stage2 file if given the partition to look in. So to find the physical location of stage2 I did:
```
sudo grub
grub> blocklist (hd0,X)/boot/grub/stage2
```
And that returns the physical location of the stage2 file in sectors from the beginning of the (hd0,X) partition. I also took that number and added it onto the starting sector of the (hd0,X) partition to get the location of the stage2 file from the beginning of the HDD. Then I started playing with that 4 byte hex number from the boot sector by converting it into decimal to see how it compared with the value given by blocklist. And after a little trial-and-error, I found out that the 4 byte hex number from the boot sector is actually "little-endian", meaning that if you read it backwards and convert it to decimal, it gives the sector offset of the stage2 file from the beginning of the drive. So at least I had a manual way of figuring out the stage2 location, but what I really wanted was a command that would do it all for me.

I found out the hard way that given my minimal bash skills, coming up with a command to read that 4 byte value and convert it from little-endian hexadecimal form into decimal was not trivial (at least for me). I think the hardest part was coming up with the correct hexdump options to output the hex value in little-endian form and as one single hex number, because I all ready knew about the $((16#<hex value>)) bash trick to convert hex to decimal. So after quite a bit of trial-and-error, hacking, and googling, I finally came up with the command I gave in my previous post, and it seemed to work. :)

---

### Post by TeXtonyx on 2008-11-28
@jasonkirk2006 Besides Easybcd I've used the bcdedit command,

[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

Did you use a guide like the one above which has a step
----------------------------------------------
Step 2 &#8211; Get a copy of Linux boot sector

We will need to instruct Windows Boot Manager how to boot 
correctly Linux using Linux boot sector, which we will extract using dd.

&#8226;        On Linux, launch a Terminal with root privileges

&#8226;        Take a copy of Linux boot sector : dd if=/dev/sda1 of=/tmp/linux.bin bs=512 count=1

&#8226;        Copy linux.bin on a FAT formatted USB key or any storage accessible from Windows Vista
-------------------------------------

The second part of the article deals with Vista Bitlocker protection
which comes with Vista SP1 if you have Vista Ultimate or Enterprise.
But the dd method doesn't work across two drives, only bootpart.

SGD is like a Swiss knife, it can install grub too.

I've seen the command
grub> find /boot/grub/stage1

grub> find /boot/grub/stage1
 (hd0,1)
 (hd2,0)

If you pick the wrong one for root, it will boot the wrong OS.
I looked for that but in your first post you wrote,

grub > root (hd0,2)
grub > setup (hd0,2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes

Since Pardus is installed on sda3, that is the correct root.

I think your post #1 mentioned the below quoted phrase, and I
think the implication is that if this was done after the first
method that it might have used the grub files from Ubuntu which
is insightful.

meierfra asked,
Did you run "grub-install /dev/sda3" from Pardu or from Ubuntu?

I think there is an implicit suggestion to again run from Pardus

grub > root (hd0,2)
grub > setup (hd0,2)

Since this doesn't change the size of the partition the dd 512
bytes you already have may still work. Good luck

---

### Post by meierfra. on 2008-11-28
> But then came the problem of trying to figure out how those 4 bytes corresponded to the location of the stage2 file.

I  use "khexedit" to look at binary files. It automatically converts all 1,2, 4 and 8 byte strings (which start at the location of the cursor) into decimals (and uses little endian decoding by default)

---

### Post by unutbu on 2008-11-28
meierfra., caljohnsmith, thank you both very much.
You guys are really good. 

caljohnsmith, that was a fantastic explanation. If I were twice as smart, I could almost imagine discovering that myself. :) Wonderful. Simply wonderful.

---

### Post by meierfra. on 2008-11-28
> think there is an implicit suggestion to again run from Pardus

grub > root (hd0,2)
grub > setup (hd0,2)

Since this doesn't change the size of the partition the dd 512
bytes you already have may still work. Good luck

You will  have to use "dd"  to update the  "Pardus.bin" file.  Reinstalling grub only changes the boot sector of sda3. But the Vista Boot loader uses the file "Pardus.bin" and does not look at the boot sector.  

This is different if you use bootpart, bootpart does not create a copy of  the boot sector. Instead it stores the location of the boot sector. So bootpart only needs to be updated if you resize a partiton, but not after reinstalling grub. EasyBCD actually uses bootpart, so the same is true for EasyBCD.

---

### Post by TeXtonyx on 2008-11-29
It's possible jasonkirk2006 has already tried reinstalling grub
from the Pardus partition with a new pardus.bin. In any event if
it doesn't fix it, I've thought of something else to try.

jasonkirk2006 said this used to work properly, but broke after
a failed 8.10 install. I think he has to use bcdedit to create
the boot file for the vista bootloader. So he could rename that
file and go through all the steps again making a new Vista bcd
using known good Ubuntu and Pardu .bin files (or whatever suffix).

{Linux ID} is the id that returns from the first bcdedit create command
An example of {LinuxID} is {81ed7925-47ee-11db-bd26-cbb4e160eb27}

I'm thinking that with Pardus installed again, that it might need to
have a new {LinuxID} assigned to it for inclusion into the bcd database.
I haven't heard of another tool for manually (CLI) editing the Vista
bootloader database except for bcdedit (Easybcd = GUI).  
So it would be best to start fresh if doing grub->bin again doesn't work,
maybe {LinuxID} works like the Linux UUID, same # of digits and pattern.

Thanks for the explanation meierfra, my expectation was based on
bootpart behavior which I use all the time now rather than dd.

---

### Post by caljohnsmith on 2008-11-29
Unutbu, just thought I would let you know that meierfra and I talked about it a little, and we came up with an even simpler solution to finding the stage2 file location:
```
sudo hexdump -s 68 -n 4 -e '"%d\n"' /dev/sda3
```
So hexdump can do everything, including reading the boot sector (no "dd" required, I don't know how we overlooked something that obvious all this time), and meierfra figured out the correct hexdump option '"%d\n"' to go directly from the little-endian hex format to decimal. :)

---

### Post by jasonkirk2006 on 2008-11-29
> **caljohnsmith said:**
> How about trying the following command:
```
echo $((16#`sudo dd bs=1 skip=68 count=4 if=/dev/[COLOR="Blue"]sda3[/COLOR] 2>/dev/null | hexdump -e '1/4 "%02X\n"'`))
```
That command looks in the sda3 boot sector and reads the hexadecimal location of the Grub stage2 file that the boot sector points to; then it converts that value to sectors so that the final result is the location of the stage2 file from the beginning of your HDD in sectors. So if you compare that with:
```
sudo fdisk -lu
```
Then you'll want to check that the output of the first command above is within the start/end sector values of your sda3 partition. How about posting the output of the above commands so we can check. :)

The following are run on Pardus:

```

$ echo $((16#`sudo dd bs=1 skip=68 count=4 if=/dev/sda3 2>/dev/null | hexdump -e '1/4 "%02X\n"'`))
147916838

```

```

# fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x499b499a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   104859647    52428800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       104859648   146802687    20971520   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3       146802726   188747684    20972479+  83  Linux
/dev/sda4       188747685   488392064   149822190    5  Extended
/dev/sda5       188747776   463032311   137142268    7  HPFS/NTFS
/dev/sda6       463032320   479809535     8388608    7  HPFS/NTFS
/dev/sda7       479813418   488392064     4289323+  82  Linux swap / Solaris

```

So does that mean stage2 location falls in the range of sda3? If so... what am i missing?

---

### Post by jasonkirk2006 on 2008-11-29
> **TeXtonyx said:**
> Did you use a guide like the one above which has a step
----------------------------------------------
Step 2 &#8211; Get a copy of Linux boot sector

We will need to instruct Windows Boot Manager how to boot 
correctly Linux using Linux boot sector, which we will extract using dd.

&#8226;        On Linux, launch a Terminal with root privileges

&#8226;        Take a copy of Linux boot sector : dd if=/dev/sda1 of=/tmp/linux.bin bs=512 count=1

&#8226;        Copy linux.bin on a FAT formatted USB key or any storage accessible from Windows Vista
-------------------------------------

Yes, i did.

> **TeXtonyx said:**
> 
The second part of the article deals with Vista Bitlocker protection
which comes with Vista SP1 if you have Vista Ultimate or Enterprise.
But the dd method doesn't work across two drives, only bootpart.


I have Vista SP1 Home Premium

---

### Post by caljohnsmith on 2008-11-29
[QUOTE=jasonkirk2006]So does that mean stage2 location falls in the range of sda3? If so... what am i missing?[/QUOTE]
Yes, your stage2 is inside of your sda3 partition where it should be; also, I assume in your post #10 that you have a small typo when you posted:
```
title Pardus 2008
root (hd0,2)
chainloader+1
```
It should be "chainloader +1" with a space after chainloader. Have you tried using the configfile notation to link directly to Pardus' menu.lst? How about trying:
```
title Pardus 2008
root (hd0,2)
configfile /boot/grub/menu.lst
```
How about giving that a shot and let us know how it goes. :)

---

### Post by meierfra. on 2008-11-29
Could you also post the output of

```
sudo grub
root (hd0,2)
blocklist /boot/grub/stage2
```

This is just to make sure that "147916838" is really the location of your current stage2 file.

Also are you sure that /dev/sda3 is Pardu and /dev/sda2 is Ubuntu? Could it be the other way around?

---

### Post by jasonkirk2006 on 2008-11-29
> **TeXtonyx said:**
> It's possible jasonkirk2006 has already tried reinstalling grub
from the Pardus partition with a new pardus.bin. In any event if
it doesn't fix it, I've thought of something else to try.

jasonkirk2006 said this used to work properly, but broke after
a failed 8.10 install. I think he has to use bcdedit to create
the boot file for the vista bootloader. So he could rename that
file and go through all the steps again making a new Vista bcd
using known good Ubuntu and Pardu .bin files (or whatever suffix).

{Linux ID} is the id that returns from the first bcdedit create command
An example of {LinuxID} is {81ed7925-47ee-11db-bd26-cbb4e160eb27}

I'm thinking that with Pardus installed again, that it might need to
have a new {LinuxID} assigned to it for inclusion into the bcd database.
I haven't heard of another tool for manually (CLI) editing the Vista
bootloader database except for bcdedit (Easybcd = GUI).  
So it would be best to start fresh if doing grub->bin again doesn't work,
maybe {LinuxID} works like the Linux UUID, same # of digits and pattern.
bc
Thanks for the explanation meierfra, my expectation was based on
bootpart behavior which I use all the time now rather than dd.

I reinstalled Pardus grub on sda3 both from within Ubuntu and Pardus, using grub interactive shell and grub-install command. Afterwards, i recreated the pardus.bin file using the dd command. Then renamed the old pardus.bin to pardus_old.bin and copied the new one instead, to the first primary active partition sda1 that Vista was installed into.

By the way, are you sure that creating the vista bcd will to the job? I'm not sure if it has something to do with my situation, forgive me if i'm going to far as a newbie ;)

---

### Post by jasonkirk2006 on 2008-11-29
> **caljohnsmith said:**
> Yes, your stage2 is inside of your sda3 partition where it should be; also, I assume in your post #10 that you have a small typo when you posted:
```
title Pardus 2008
root (hd0,2)
chainloader+1
```
It should be "chainloader +1" with a space after chainloader. Have you tried using the configfile notation to link directly to Pardus' menu.lst? How about trying:
```
title Pardus 2008
root (hd0,2)
configfile /boot/grub/menu.lst
```
How about giving that a shot and let us know how it goes. :)

Oops..! A space? I'm sorry, there wasn't. I catched the Pardus' menu.lst after adding a space.

I'm going to repeat the grub installation and dd command once more.

---

### Post by jasonkirk2006 on 2008-11-29
Now it works.

From Pardus, i reintalled grub with grub interactive shell, dumped both GRUBs (that of sda2 and sda3) to respective files once more and copied them to C:

What did i wrong yesterday, and the day before yesterday? Just a typo in menu.lst file? May be more typos when using dd

I checked it, Pardus is on sda3 - no dubt.

Anyway, i took your time in vain. Please forgive me.

---

### Post by caljohnsmith on 2008-11-29
We're glad the problem is resolved, that's what counts. Cheers and have fun with all your OSes. :)

---

### Post by TeXtonyx on 2008-11-29
"By the way, are you sure that creating the vista bcd will to 
the job? I'm not sure if it has something to do with my situation, 
forgive me if i'm going to far as a newbie."

No, I'm not sure, it could have something to do with your situation.
So it is a good question, also because I get to write about the
principles of troubleshooting.

You told me that you once had this working. Therefore, if you
deleted everything and started over without making any mistakes
then your setup would work once again. 

So before doing something that drastic, one does the simple and
usually faster fixit steps first. So I wrote before,

"It seems like the tutorial method worked for ubuntu. The same
method should work for Pardu (if it's standard) unless the dd
file is wrong, the filename for it is wrong, you didn't follow
the instructions exactly, or you had a typo."

So you reported checking and double-checking the filenames, and
that the 512 bytes were actually different and that the menu.lst
entries were correct. Remember to do the grub from Pardus last,
not Ubuntu. So it was Sherlock who said something like,

'When you are trying to solve what appears to be a mystery, eliminate the
obvious first. Whatever is left, no matter how extraordinary, is the answer...'

So you did some steps with dd and then there was a major step
of adding your linux entries with bcdedit. This is the type of
Windows structure which can hold onto old data that may come
into conflict with newer information. Windows used to hold onto
device drivers/printer drivers like a miser which would cause
problems. Some programs when they are uninstalled don't remove
their entries to the registry. Now when you go to install the
same program a few months later, it won't install because their
is conflict in the registry with the old registry entries. I've
seen fixes where you have to work your way through the registry
hunting for and eliminating keywords just like trojan filenames.

So bcd is a database storage function. So I know that it could
be a problem with your recent inputs to that database, if you
write to it again. I don't know that this is the problem until
all the other stuff including typos is eliminated, and so bcd
remains as the only possibility of creating the error. Since
you would have verified the other steps in getting Vista to boot
those programs, so that bcdedit was the only step not completed
and known to be accurate, then I would be sure that bcd was the
culprit. Because you would be recreating all the steps which
worked before when this all worked right. Well, almost sure,
because some rather distant seeming changes can reach out across
the causal chain and screw things up in totally unpredictable
ways. I happen to know a theorem which says that all processes 
which are known to have rules, do not necessarily have an 
algorithmic method to detect such rules (lines of connection). 

I've actually tested the method you have used (which would be
quite rare on this forum) and using dd several times gets to be
a real pita and takes a couple of minutes. I told you about
bootpart because it takes 12 seconds and I seem to recall it
working with Vista as a substitute for using dd. Btw, I checked
on the Wayback Machine and that webpage with the reference to
the importance of fat16 is over 11 1/2 years old, some of these
developers are one-man shows and are too busy to update docs.

To summarize. You had this working once. If you started from 
scratch and undid your input, and redid all your steps taken, 
then your method would work again. So the bcdedit step hadn't
been tried and it looked like you were running out of options,
till caljohnsmith of the Eagle Eye, spotted the omission of a
space much like that poor horse which lost a nail in his horse 
shoe, which lost the battle, which lost the war, and so the 
enemy captured the poor horse and et him for supper.

EDIT: I just noticed that you reported it's working, that's great!

---

### Post by jasonkirk2006 on 2008-11-30
> **meierfra. said:**
> Could you also post the output of

```
sudo grub
root (hd0,2)
blocklist /boot/grub/stage2
```

This is just to make sure that "147916838" is really the location of your current stage2 file.

Also are you sure that /dev/sda3 is Pardu and /dev/sda2 is Ubuntu? Could it be the other way around?

This gives the following output:
```

grub> root (hd0,2)

grub> blocklist /boot/grub/stage2
(hd0,2)-16695116[0-324]1114112+11114114+11114116+11114118+11114120+11114122+111
14124+11114126+11114128+11114130+11114132+11114134+11114136+11114138+11114140+1
1114142+11114144+11114146+11114148+11114150+11114152+11114154+11114156+11114158
+11114160+11114162+11114164+11114166+11114168+11114170+11114172+11114174+111141
76+11114178+11114180+11114182+11114184+11114186+11114188+11114190+11114192+1111
4194+11114196+11114198+11114200+11114202+11114204+11114206+11114216+11114218+11
114220+11114222+11114224+11114226+11114228+11114230+11114232+11114234+11114236+
11114238+11114240+11114242+11114244+11114246+11114248+11114250+11114252+1111425
4+11114256+11114258+11114260+11114262+11114264+11114266+11114268+11114270+11114
272+11114274+11114276+11114278+11114280+11114282+11114284+11114286+11114288+111
14290+11114292+11114294+11114296+11114298+11114300+11114302+11114304+11114306+1
1114308+11114310+11114312+11114314+11114316+1


```

Although everything is fine now, i'm after what caused this strange problem. This incremental behaviour is normal? I expected a single number.

---

### Post by TeXtonyx on 2008-11-30
EDIT: Comment withdrawn after understanding question.

---

### Post by jasonkirk2006 on 2008-11-30
> **TeXtonyx said:**
> 
Did you think that "chainloader+1" was a system generated typo?
I'm curious, so I will test this theory on my machine.

Not, it was my mistake, not a machine generated code. I wrote it manually.

---

### Post by TeXtonyx on 2008-11-30
> **jasonkirk2006 said:**
> Not, it was my mistake, not a machine generated code. I wrote it manually.

I realized this question wasn't to the point once I understood 
that by "this" you meant the output of blocklist, which is why
I withdrew my comment.  

My blocklist output doesn't look like your sample either. Does your 
blocklist output look more normal now that you changed the +1 ? 
I am curious about what can cause so many instances, is there 
a switch or is it a feature of Pardus, a primitive list? I have 2~4 
numbers which are more like ranges for my blocklist output, far fewer.
"shortcuts like "+1" for "0+1,512" now work correctly"

"Stage 1 "knows" where Stage 2 is by entries in a block-list loading 
table embedded in it. It loads the lists of blocks off of the booting 
drive, then jumps to a specified CS:IP in 16-bit real mode. These are 
described in the page on embedded data. It queries the BIOS for the 
disk geometry, and maps the linear block numbers there to C:H:S 
addresses used by the INT 13h BIOS interface."

---

### Post by jasonkirk2006 on 2008-11-30
> **TeXtonyx said:**
> ... or is it a feature of Pardus, a primitive list? I have 2~4 
numbers which are more like ranges for my blocklist output, far fewer.


Right. My Ubuntu has the following output for both partitions:

```

grub> root (hd0,1)

grub> blocklist /boot/grub/stage2
(hd0,1)25247744+96,25247848+116

grub> root (hd0,2)

grub> blocklist /boot/grub/stage2
(hd0,2)1114112+96,1114216+102

```

where as Pardus gives:

```



grub> blocklist /boot/grub/stage2
(hd0,1)25247744+125247746+125247748+125247750+125247752+125247754+125247756+1252477
58+125247760+125247762+125247764+125247766+125247768+125247770+125247772+125247774+
125247776+125247778+125247780+125247782+125247784+125247786+125247788+125247790+125
247792+125247794+125247796+125247798+125247800+125247802+125247804+125247806+125247
808+125247810+125247812+125247814+125247816+125247818+125247820+125247822+125247824
+125247826+125247828+125247830+125247832+125247834+125247836+125247838+125247848+12
5247850+125247852+125247854+125247856+125247858+125247860+125247862+125247864+12524
7866+125247868+125247870+125247872+125247874+125247876+125247878+125247880+12524788
2+125247884+125247886+125247888+125247890+125247892+125247894+125247896+125247898+1
25247900+125247902+125247904+125247906+125247908+125247910+125247912+125247914+1252
47916+125247918+125247920+125247922+125247924+125247926+125247928+125247930+1252479
32+125247934+125247936+125247938+125247940+125247942+125247944+125247946+125247948+
125247950+125247952+125247954+125247956+125247958+125247960+125247962+1

grub> root (hd0,2)

grub> blocklist /boot/grub/stage2
(hd0,2)-16695116[0-324]1114112+11114114+11114116+11114118+11114120+11114122+1111412
4+11114126+11114128+11114130+11114132+11114134+11114136+11114138+11114140+11114142+
11114144+11114146+11114148+11114150+11114152+11114154+11114156+11114158+11114160+11
114162+11114164+11114166+11114168+11114170+11114172+11114174+11114176+11114178+1111
4180+11114182+11114184+11114186+11114188+11114190+11114192+11114194+11114196+111141
98+11114200+11114202+11114204+11114206+11114216+11114218+11114220+11114222+11114224
+11114226+11114228+11114230+11114232+11114234+11114236+11114238+11114240+11114242+1
1114244+11114246+11114248+11114250+11114252+11114254+11114256+11114258+11114260+111
14262+11114264+11114266+11114268+11114270+11114272+11114274+11114276+11114278+11114
280+11114282+11114284+11114286+11114288+11114290+11114292+11114294+11114296+1111429
8+11114300+11114302+11114304+11114306+11114308+11114310+11114312+11114314+11114316+
1

```

So this must be a result of Pardus design.

---

### Post by caljohnsmith on 2008-11-30
From your Grub blocklist output in Ubuntu, Pardus' stage2 file begins at 1114112 sectors from the beginning of the partition, and since sda3 is 146802726 sectors from the beginning of the drive:
```
114112 + 146802726 = 147916838
```
Which is exactly what you got in post #22 for the location of the stage2 file, so that agrees. That would mean your Pardus Grub blocklist output for stage2 appears bogus. If I were you, I would try purging/reinstalling the entire Grub package in Pardus, and after that, reinstall Grub's files to /boot/grub using "grub-install":
```
sudo grub-install /dev/sda3
```
And then try the blocklist command again. What version of Grub does Pardus use?

---

### Post by jasonkirk2006 on 2008-12-01
> **caljohnsmith said:**
> What version of Grub does Pardus use?

```

# grub --version
grub (GNU GRUB 0.97)

```

> **caljohnsmith said:**
> If I were you, I would try purging/reinstalling the entire Grub package in Pardus, and after that, reinstall Grub's files to /boot/grub using "grub-install"

There are some differences in Pardus, compared to other distros. I'll write this issue to Pardus' forums, and learn if it's normal or not. And if nothing works, purge & reinstall!

Thank you very much for your directions.

---

