---
title: "How do i make my second hard drive my home partition"
date: 2008-06-26
forum: Hardware
---

### Post by lillypop on 2008-06-26
Hi my first post and i am completely Noob at linux and Ubuntu i only installed 2 days ago.

When i installed i stupidly installed on my 20gb hardisk not my 40gb i just did the standard disk thing so no home partition was made.

I have just formatted my second hard drive to ext3 and was wandering if i could move my home folder on to there and use the whole drive for that.
As i have wolfenstien ET on there and all the maps and pk3 files i have take up a lot of space plus all my mp3's and pics :)

To move the home directory do i have to make partition the 2nd drive as home ?

Any help would be appreiciated and in as much detail as possible i'm not the most technically minded girl :confused:

I have looked for other posts on similar things i found a few but they didn't really helped me .
TIA

---

### Post by Mazin on 2008-06-26
Yeah, you can just copy all of your stuff from your home folder to that hard drive, and then tell Ubuntu to use that second hard drive as /home

I assume that you can already browse your second hard drive normally in Ubuntu.  I'm not too sure of how to do it through the GUI, but try this:

Copy your home folder to that second hard drive.  There should be a folder with your name in /home; just drag that whole folder over.
You'll have to be root for these next steps  ("gksu nautilus /")
Rename your /home to /old_home
Create a new home directory.
Right-click on that second hard drive's icon, and in the Properties, change its mount point to "/home" and it should work.

Now, the usual way to do it is to edit your "fstab" file, that lists all your hard drives and where to mount them.  As an alternative, instead of the last step, run "gksu gedit /etc/fstab" and look for the line for your second hard drive.  Change it from "/media/whereever" to "/home" and reboot.

---

### Post by Odrodzona-Sarmacja on 2008-06-26
"gksudo gedit /etc/fstab" (gedit/mousepad/kate)
add there this line:
"/dev/sdb1  /home  ext3  relatime  0  2"
I assume it is "/dev/sdb1", but you can find exactly what device it is by typing "sudo blkid". Now save it and reboot your computer and you have home partition on your new hard driver. Although before rebooting you could copy contents of your /home directory to your new hd. Good luck!

---

### Post by lillypop on 2008-06-26
Thanks i will try that. 
Now i'm asuming that i do this in terminal window "gksudo gedit /etc/fstab"

Then add this line to the file ? "/dev/sdb1 /home ext3 relatime 0 2"

Sorry for being so stupid but i would rather make sure b4 i mess something up :)

And is relatime supposed to say realtime?

---

### Post by ukripper on 2008-06-26
for more info try this link -
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by lillypop on 2008-06-26
> **Odrodzona-Sarmacja said:**
> "gksudo gedit /etc/fstab" (gedit/mousepad/kate)
add there this line:
"/dev/sdb1  /home  ext3  relatime  0  2"
I assume it is "/dev/sdb1", but you can find exactly what device it is by typing "sudo blkid". Now save it and reboot your computer and you have home partition on your new hard driver. Although before rebooting you could copy contents of your /home directory to your new hd. Good luck!
says i don't have permission to copy the home file over to the new drive. Meaning i don't have the permissions on the new drive :/

---

### Post by lillypop on 2008-06-26
The permissions to my second hard drive are set as root how do i change the ownership of the harddrive to myself so i have the permissions to read and write on the drive.

---

### Post by Odrodzona-Sarmacja on 2008-06-26
"gksudo nautilus" (nautilus/thunar/konqueror)
should open for you file browser with root privilages. Now you can copy files like on regular windows. BE VERY CAREFUL WITH IT!

---

### Post by lillypop on 2008-06-26
Wouldn't it be better to make myself owner of the drive ? i have seen the command for that somewhere today but i forgot it :(
Then i need to mount the drive as /home copy all of my /home/laurie folder over to new drive then restart pc . 
The problem is when i go into gedit /etc/fstab the 2nd drive isn't listed there but is visable on my computer until i put this line in /dev/sdb1 /home ext3 relatime 0 2 then it disapears from view on my computer so i can't copy and paste my home files over cause i can't find the drive .
as soon as i remove the line the drive its visable again.
Even if i'm not owner of the drive would i still be owner of the home files on the drive ? if you understand what i mean.

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Little tricky that Ubuntu. It seems you better copy files first. Copy hidden files and directories too (they are the ones with . before their name). Then do the fstab job. When you reboot or do "sudo mount -a" then you should get normal access to files on your new /home like you have now on your old /home.

---

### Post by lillypop on 2008-06-26
Omg this is harder than i thought it would be.
I still couldn't copy the files using gksudo nautilus this time it said i didn't have permissions on my home directory to move them lol

---

### Post by lillypop on 2008-06-26
maybe this info will help

laurie@laurie-desktop:~$ sudo blkid
[sudo] password for laurie: 
/dev/sda1: UUID="a199e1cb-06d4-4b58-a440-1e09736c5077" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="938421d5-5404-444e-8b7a-e7a22c02d646" 
/dev/sdb1: UUID="b39a74b8-0f53-4bbd-a22a-669cbbc4f1a9" TYPE="ext3" SEC_TYPE="ext2"
 

/etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=a199e1cb-06d4-4b58-a440-1e09736c5077 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=938421d5-5404-444e-8b7a-e7a22c02d646 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

---

### Post by lillypop on 2008-06-27
Just a thought but if i change the format on my second harddrive to ext2  will i be able to copy my files from /home/laurie over without the permission problem ? and could i then make the drive my /home directory with it still being ext2 or does it have to be ext3 which is root i figured out that much :)
I know that where the problem lies if i go in as root i can access the second drive but if i try and copy the files over it tells me i don't have permissions to copy the files even though i am owner of the laurie folder ? so i no longer have the permissions to to my /home/laurie when i have permissions to /media/disk which is the current mount for my second drive.
So would ext2 solve this problem?
I really need get my /home moved on my other drive as i'm running out of space :/
Or if i have to keep ext3 would making myself owner of the drive solve the problem or does it have to remain as root?

---

### Post by Odrodzona-Sarmacja on 2008-06-27
I think you need temporarily mount your second drive on some directory (mount point), so you can copy files over.

"sudo mkdir /media/temporary"
"sudo mount /dev/sdb1 /media/temporary"

Now try copying all your files and dircetories (hidden included) from /home to /media/temporary. Then do add this new line in fstab for your new /home partition and reboot. It should not be more complicated then that.

---

### Post by lillypop on 2008-06-27
Still won't let me copy the file say i don't have permissions to write to the drive.
The drive is set a a primary partition do i need to repartion it and make it a logical ?
Maybe i partitioned it wrong :/

---

### Post by Odrodzona-Sarmacja on 2008-06-27
As root using "gksudo nautilus/thunar/konqueror" (you type it in terminal and it launches the file browser with roots privileges) you should have all right to copy anything from anywhere to anywhere as well as delete everything on your hard drives...

Else open your terminal and type that:
"sudo cp -dpR /home/* /media/temporary"
It should do the trick as well as graphic file browser.

---

### Post by lillypop on 2008-06-27
Right i have managed to copy the files using "sudo cp -dpR /home/* /media/temporary"
but i don't have permissions on the disk to read them or even view them.
Will i get the permissions back when i make /media/temporary into /home ?
Or do i need to do  chown /media/temporary or something along those lines?

I just checked the file sizes and they both seem to be the same size so looks like everything copied over trouble is i can't see in /media/temporary/laurie see if they are all there :p
So next i'm guess i rename the /home to old_home then mount /media/temporary as /home
or do i have to sudo mkdir /home then
sudo mount /dev/sdb1 /home.
then
edit the fstab and add the line /dev/sdb1 /home ext3 relatime 0 2

---

### Post by Odrodzona-Sarmacja on 2008-06-27
> **lillypop said:**
> Right i have managed to copy the files using "sudo cp -dpR /home/* /media/temporary"
but i don't have permissions on the disk to read them or even view them.
Will i get the permissions back when i make /media/temporary into /home ?
Or do i need to do  chown /media/temporary or something along those lines?

Just type in terminal
"sudo cd /media/temporary"
"sudo ls -aL"
It should show you all files and directories copied over there. If they are exactly the same match with
"sudo cd /home"
"sudo ls -aL"
then I guess it copied over just fine. Remember the magic "sudo" word :)

---

### Post by lillypop on 2008-06-27
what does this mean i just noticed it in terminal 
cp: cannot stat `/home/laurie/.gvfs': Permission denied

---

### Post by lillypop on 2008-06-27
> **Odrodzona-Sarmacja said:**
> Just type in terminal
"sudo cd /media/temporary"
"sudo ls -aL"
It should show you all files and directories copied over there. If they are exactly the same match with
"sudo cd /home"
"sudo ls -aL"
then I guess it copied over just fine. Remember the magic "sudo" word :)

I just tried that and got laurie@laurie-desktop:~$ sudo cd /media/temporary
sudo: cd: command not found
 then when i did sudo ls -aL it did the full list of the contents but is that from the original file or the copied file ? i'm confused :p

---

### Post by Odrodzona-Sarmacja on 2008-06-27
ok. That "sudo cd" was a surprise to me... then do
"sudo ls -aL /media/temporary"
"sudo ls -aL /home"
if both listings are the same, then you are clear to proceed :)

---

### Post by Odrodzona-Sarmacja on 2008-06-27
> **lillypop said:**
> what does this mean i just noticed it in terminal 
cp: cannot stat `/home/laurie/.gvfs': Permission denied

Shouldn't happen if you are using root access.

---

### Post by lillypop on 2008-06-27
lol all i got was .  ..  laurie  lost+found
 but i think it has worked.
So on to nextsteps. do i mount the /media/temp as /home before i change the name of /home to old_home

---

### Post by lillypop on 2008-06-27
Sorry i double posted :/

---

### Post by lillypop on 2008-06-27
right all the files are in the media/temp  i have renamed /home old_home
now do i just edit the fstab and add the line for the sdb1 /home relatime 02 or something like that ?

If i rename home to old_home then the terminal doesn't work

---

### Post by Odrodzona-Sarmacja on 2008-06-27
> **lillypop said:**
> now do i just edit the fstab and add the line for the sdb1 /home relatime 02 or something like that ?


Yep. Do that in fstab. Then reboot your computer. Your new /home should be set to your new hard drive now.

---

### Post by lillypop on 2008-06-27
b4 i do that according to the 2nd harddrive its not mounted
Will the line in the fstab mount it ?

---

### Post by Odrodzona-Sarmacja on 2008-06-27
> **lillypop said:**
> b4 i do that according to the 2nd harddrive its not mounted
Will the line in the fstab mount it ?

Yep. It will.

---

### Post by lillypop on 2008-06-27
ok wish me luck :)

---

### Post by lillypop on 2008-06-27
HELP omg didn't work i'm locked out on my pc i have a root terminal open but i haven't a clue what to do i can't log in only in failsafe on root.

I'm on my husbands pc at the minute

---

### Post by lillypop on 2008-06-27
Oppps i had to reinstall ubuntu lost everything but never mind i learnt a few things :p
Thanks for all the help.
I Installed on my 40gb harddrive this time ;)

---

### Post by Odrodzona-Sarmacja on 2008-06-30
> **lillypop said:**
> Oppps i had to reinstall ubuntu lost everything but never mind i learnt a few things :p
Thanks for all the help.
I Installed on my 40gb harddrive this time ;)

Sorry to hear that.

I use fat32 file system for my file storage purposes. If something doesn't work on exotic journaling systems, then I keep a copy of my configuration (like markings from synaptic manager) there together with my stored files. I use 8gb partition for root partition where I installed my OS and then 2Gb for /home partition and 4gb for /tmp partition. I use the rest of my free gb for fat32 storage. I found it the safest way to deal with with urging needs for constant needs with reinstalling Ubuntu. Also I use hard drive imaging tool to make hard drive copies of my "/home" and "/" partitions. When packed with highest ratio compression it doesn't go above 2Gb in size in total and provides very simple undelete process for entire hard drives.

---

