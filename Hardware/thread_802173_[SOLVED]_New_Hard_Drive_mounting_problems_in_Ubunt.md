---
title: "[SOLVED] New Hard Drive mounting problems in Ubuntu 8.04 Hardy"
date: 2008-05-21
forum: Hardware
---

### Post by MachineHead on 2008-05-21
Hello Folks,

I just bought a new 1 TB Samsung HDD.
After adding it to my system I tried to mount the volume with the help of a friend of mine.

[SIZE=5][COLOR=DarkGreen]Found the problem and solved it.
Summary of this topic at the end of the thread.

[COLOR=Black]MachineHead[/COLOR][/COLOR][/SIZE]


Regards,

MachineHead

---

### Post by trojanfoe on 2008-05-21
Doesn't "/dev/sdd" specify the whole disk, where as you want to specify a partition (for example /dev/sdd1).

Also does the parent directory of the mountpoint actually exist (you might need 'mkdir -p <dir>' to create the intermediate directories).

Andy

---

### Post by MachineHead on 2008-05-21
[SIZE=5][COLOR=DarkGreen]Found the problem and solved it.
Summary of this topic at the end of the thread.

[COLOR=Black]MachineHead[/COLOR]
[/COLOR][/SIZE]

---

### Post by Tyler H on 2008-05-22
I'm having the same yet different issue. Mounting on certain HDD's seems to be a complete curse in Hardy.

This crap is giving me a head ache.

---

### Post by MachineHead on 2008-05-23
Hey Tyler H,

Well even though the steps I described seem to be the way to go about it...it doesn't work on my machine.
The moment I mount the drive I have no rights, so I reboot.
After reboot the drive is unmounted again :(

Can some more advanced Ubuntu Hardy user help us out here?

MachineHead

---

### Post by Tyler H on 2008-05-26
I've got the same issue where the drive I mounted the time before is unmounted after reboot. Gparted gives me errors of "bad superblocks".

---

### Post by MachineHead on 2008-05-27
Hey Tyler,

The **"bad superblocks"** error sounds like a damaged part of your hdd, though I don't know.
Google on the error and you will find what it means.
Don't be shy in using wikipedia, it has good info on all kinds of ICT related issues.

I have thought up a bitch of a solution for my problem.
I'm going for a new install and make the new hdd my /home.
Maybe a solution you can try aswell?

Good luck mate, keep posting then we might get some more advanced help in here.

Regards,

MachineHead

---

### Post by trojanfoe on 2008-05-27
You shouldn't have to mount the drive as /home in order to get permissions and you shouldn't have to reboot to try things out.

If you want the drive to be writeable by you, simply do:

```
chown -R /path/to/mountpoint yourname:yourgroup
```

For example I have a partition called /data1 where I keep music/videos/other crap, so I would do:

```
chown -R /data1 andy:andy
```

In order to test things out there is no need to reboot; simply unmount and remount the filesystem.  If you have the entry correctly set in /etc/fstab (I assume you do, else you rebooting would have no effect):

```

umount /path/to/mountpoint
mount /path/to/mountpoint

```

(yes that is 'umount' and not 'unmount' - don't ask).

If you don't have an entry in /etc/fstab (cos you are playing/testing the filesystem) then you have to specify the mount point and filesystem type (and sometimes options):

```

mount -t ext3 /mnt /dev/sdb1

```

/mnt is commonly used as a temporary mountpoint while testing, however it might have sub-directories and have partitions already mounted there, in which case the above command would fail.

The -t options tells Linux that the filesystem is an ext3 filesystem (I have assumed you are using the ext3 filesystem).  There is also the -o option which specifies generic and filesystem-specific mount options; for example to mount the filesystem read-only add '-o ro'.  See the mount manpage for more examples.

Cheers,
Andy

---

### Post by MachineHead on 2008-06-01
[FONT=Arial]Hi Trojanfoe,

As you can see the partition on /dev/sdc3 has a mount point named /media/melvin
I can navigate to this folder and enter the folder, though I cannot create files in that folder or copy files to the folder.

On my desktop the partition assigned to /media/melvin appears as a HDD icon with the name: **250.1 GB Media**.
When right-clicking on the icon and checking the information on all properties tabs....**See attachment <screenshot>**

I really need this sorted, that is 250 GB wich I can't use at the moment.
When it works I will update the procedure taken in getting it right so other people can benefit from this.

MachineHead

[B][edit] @ Trojanfoe, You had the right solution, only you copied the code a tiny bit wrong from the Ubuntu help pages.
Thanks for the help mate :) [/edit]
[/B] ______________________________________________________________________________________
[/FONT]         [FONT=Arial][SIZE=6][COLOR=DarkOrange]Howto install a new Hard Drive in Ubuntu Hardy Heron 8.04.
[COLOR=DarkGreen][SIZE=3]
[SIZE=2][COLOR=Black][COLOR=Blue][I]**Mount point:** A folder to which a partition on the hard drive is linked, digital.
**Partition:** A reserved part of an hard drive to be used by the user as he or she wishes, physical.
**Gnome partition Editor:** A program that you can install to easily edit and make partitions inside Ubuntu Linux.
It works quite the same as the partition editor which the Windows installation program uses when installing Windows.
**Ext3:** File system, a way of partitioning, in Windows we had FAT32 and later NTFS, Ext3 is also a way of formatting.
If you want to make the new partition compatible with Windows and Linux, it should be NTFS, Ext3 is not **NOT** recognized by Windows.[/I][/COLOR]

The problem is as mentioned above.
This solution will do the following:[/COLOR][/SIZE][SIZE=2]
[/SIZE] [/SIZE][/COLOR][/COLOR][/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2][COLOR=DarkGreen]Find the information about your new hard drive which you need in this process[/COLOR][/SIZE][/FONT]
[*][FONT=Arial][SIZE=2][COLOR=DarkGreen]Create a new mount point and link the partition to the mount point.[/COLOR][/SIZE][/FONT]
[/LIST]
[FONT=Arial][SIZE=2][B]
What you should have done before following these instructions:[/B]
[/SIZE][/FONT]
[LIST=1]
[*][SIZE=2]Actually install the hard drive into the system and connect it of course.[/SIZE]
[*][SIZE=2]Install Gnome Partition Editor through the *"Add/Remove programs"* option in the *"Applications" *menu.[/SIZE]
[*][SIZE=2]Partition the new hard drive as desired, remember these steps will only mount 1 partition at a time, so If you make 3 partitions you have to repeat the following steps 3 times.[/SIZE]
[/LIST]
[SIZE=2]**There we go:**[/SIZE][SIZE=2]

To get the drive information we need type:
```
sudo lshw -C disk
```[/SIZE] [SIZE=2][FONT=Arial]in your terminal/console.[/FONT]
[/SIZE][SIZE=2][FONT=Arial]This will give you an output that looks like this:
[/FONT]```
  *-disk
       description: ATA Disk
       product: IC25N040ATCS04-0
       vendor: Hitachi
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hdd
       version: CA4OA71A
       serial: CSH405DCLSHK6B
       size: 37GB
       capacity: 37GB
```[/SIZE][SIZE=3][FONT=Arial][SIZE=2]
You need the line in which it mentions the **"logical name".**
Remember the **"logical name"** you might want to write it down.

Then we are to create a mount point.
When you are switching from Windows to Linux this will feel like creating a folder through the console/terminal.
Do this in console/terminal:
[/SIZE][/FONT][/SIZE]```
sudo mkdir /media/whatevernameyouwant
```[SIZE=3][FONT=Arial][SIZE=2]
Change ' whatevernameyouwant' into the desired name for the folder.
When you want to use a folder name with two words in it, for example **"The Vault"** then you have to make the command look like this:
[/SIZE][/FONT][/SIZE]```
sudo mkdir "/media/The Vault"
```[SIZE=3][FONT=Arial][SIZE=2] 
[/SIZE] 
[SIZE=2]Now we have a mount point, you can link the new partition to the mount point.
This is where you need the **"logical name"** of your new hard drive or partition.
To mount use this code in console/terminal:
[/SIZE][/FONT][/SIZE]```
sudo mount /dev/logicalname /media/whatevernameyouwant
```[SIZE=3][FONT=Arial][SIZE=2]

Now the drive is mounted and accessible through the folder you have created in /media.

Another thing left to do is to edit a file named **fstab** after you have edited this file you wont have to mount the partition each time you restart the system.
In console/terminal:
[/SIZE][/FONT][/SIZE]```
gksudo gedit /etc/fstab
```This will open up a text editor.
Add the following line to the end of the file.
Be sure you use the right names for your mount point and/or partition.
```
  /dev/hdd1    /media/whatevernameyouwant   ext3    defaults     0        2
```[SIZE=3][FONT=Arial][SIZE=2]Do not change **"ext3   defaults   0   2"** this part of the code is standard for this action.
Only change /dev/hdd1 and /media/whatevernameyouwant.

Now you wont be able to create files or copy files there yet.
Let's solve this problem.
Enter this code in console/terminal:
[/SIZE][/FONT][/SIZE]```
sudo chown -R username:username /media/whatevernameyouwant
```[SIZE=3][FONT=Arial][SIZE=2]
This should give you as a single user all the rights you need to make use of your new partition.

I have made this short version of an allready existing piece of documentation on the Ubuntu help pages.
For more issues/help/explanations on this subject follow this link:
[/SIZE][/FONT][/SIZE][COLOR=Blue][https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)[/COLOR]

All credits to the man that wrote that tutorial, a real life saver.

Regards and have fun,

MachineHead

---

