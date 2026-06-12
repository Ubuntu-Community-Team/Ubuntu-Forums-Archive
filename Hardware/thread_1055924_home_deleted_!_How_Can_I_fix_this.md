---
title: "/home deleted ! How Can I fix this"
date: 2009-01-31
forum: Hardware
---

### Post by tamer_radi on 2009-01-31
In Berief
I had some hardware problems that caused ubutnu to restart during installing a program.

after (partially) fixing the hardware error ...
Ubuntu can't boot , it restarts when it begin to check the Journal system
the problem was in /dev/hda3 , whenever Ubuntu tries to access it , computer restarts
even form a live CD , using gParted to check the partition for errors , also restart
So , I formatted it :D 

The problem here is that , this partition was mounted as /home ....

From Here the Real Problem begins ....
When I booted to Ubuntu , it gave some errors mentioning harddisk
then it opened a console session as Root .. I am supposed to fix things , which I couldn't :D ( This my second day with Linux :$ )
, So I typed Reboot , but instead of rebooting , It opened the GUI !
I typed my username and password ,
I got 2 messages , the first (prompt) : is that /home found but empty , so it will use root's home , then another (warning) about using the same folder or something like that

just after this , a third error msg came , 
says that I am logged out , and my session was less than 10 second , which probably caused be an error , then it display the login screen again .


.....
Well thats my Story , Sorry for long post :$
The Question is ,
How could I tell Ubuntu to reCreate /home ?
[LIST]
[*]I have no backups
[*]I am using Ubuntu 8.04 , 64-bit
[*]I use Ext3 for / and /home 
[*]I am a newbie in Linux World :D
[/LIST]

---

### Post by Hobgoblin on 2009-01-31
Since it's only the 2nd day and you've lost /home you can't have much to lose by simply reinstalling from scratch.

---

### Post by tamer_radi on 2009-02-01
mmm, I wanted to make this my last option
If there another way to fix this without reInstalling will be better.

thanks,

---

### Post by cariboo on 2009-02-01
Is /home missing. or /home/<user> missing? If it is the later, just create a new user. Start in recovery mode and at the prompt type:

```
useradd -d <user>
```

Then you need to create a password for the user

```
passwd <user>
```

You should now have a /home/<user> directory.

Jim

---

### Post by jocko on 2009-02-01
> **cariboo907 said:**
> Is /home missing. or /home/<user> missing? If it is the later, just create a new user. Start in recovery mode and at the prompt type:

```
useradd -d <user>
```Then you need to create a password for the user

```
passwd <user>
```You should now have a /home/<user> directory.

Jim

That will just make a new user directory in the empty /home folder on the root file system (=the mount point where the /home partition should be mounted), and will NOT use the actual /home partition.
The problem is that something is wrong with the file system on the /home partition, so it can't be mounted (thus leaving the mount point empty).
The simplest way to fix it is by booting up a live cd, open up a terminal and run:
```
sudo fsck -fpvC 0 [COLOR=Blue]/dev/hda3[/COLOR]
```That will force a file system check, repair any errors and show some information about what's being done.
Remember that the device nodes (/dev/[COLOR=Blue]h[/COLOR]d[COLOR=Blue]xY[/COLOR], /dev/[COLOR=Blue]s[/COLOR]d[COLOR=Blue]xY[/COLOR]) can change between boots.
To figure out which device node the partition has on this boot, you can check the output of running this command in a terminal:```
ls -l /dev/disk/by-path/
```
If the repair works you should be able to boot up your computer normally and find that all your files are still in your /home directory.

---

### Post by jocko on 2009-02-01
Ok. I missed the part in the first post where you said you formatted the drive.
That was a mistake, as I'm sure it would have been possible to fix it with the instructions in my post (above).
But, your problem now is that during boot ubuntu looks for your old /home partition but can't find any such partition (when you formatted it, the new partition got a new uuid).

To fix it, first boot up a live cd and mount your root partition (the one where ubuntu is installed, I'll assume it's in /dev/hda1, but you'll have to check it yourself).
In a terminal:
```
sudo mkdir /media/hda1
sudo mount /dev/hda1 /media/hda1
```

You will have to find the correct uuid for your hda3 partition from the command:
```
ls -l /dev/disk/by-uuid
```
That will show you a line looking something like this for all file systems:
```
lrwxrwxrwx 1 root root 10 2009-01-31 14:33 [COLOR=Red]0e305a79-d82d-4979-b8a7-764ea161a7fa[/COLOR] -> [COLOR=Blue]../../hda3[/COLOR]
```
Then you have to edit the file /etc/fstab, which is the file that contains the parameters for which filesystems to mount and where to mount them.
```
gksudo gedit /media/hda1/etc/fstab
```
One of the lines will look something like this:
```
[COLOR=Red][COLOR=Black]UUID=[/COLOR]21786441-b78e-4705-bc7e-7c81c98f2c62[/COLOR] [COLOR=Blue]/home[/COLOR]           ext3    relatime        0       2
```
Just copy the correct uuid from the "ls" command above and paste it instead of the old one in the /etc/fstab file.
Then reboot to recovery mode (right after the bios self tests you will see a message from grub. When you see this, hit Esc to see the boot menu, select the second option and hit enter to continue booting).
This will get you to a screen where you can choose some different options (xfix, root terminal and a few more options).
Select the root terminal option, and use the commands from cariboo907's post above to make a new user.

---

### Post by tamer_radi on 2009-02-01
Thanks all for help.
I did the First part (jocko's Second post's instructions) successfully and fixed the UUID thing

BUT, when  I tried to do the second part ( cariboo907's instructions )
I got error msg "invalid home directory '*<user>*'"
So I tried the same command but without the -d option
```
useradd <user>
```
I got msg that user exists , seems the System still remember me :D
(also in the GUI login I noticed the my username sill in the select menu )

anyway ... I Deleted my username , then tried to reCreate it using
```
useradd -d <user>
``` , but I got the same error msg
again, I tried the same command , without -d ... 
It did work ! , But without creating home folder for me
when I ```
ls /home
``` I got nothing but [COLOR="Blue"]**LOST+FOUND**[/COLOR]
and when I try to login through GUI , I got the old error messages
> **tamer_radi said:**
> 
I got 2 messages , the first (prompt) : is that /home found but empty , so it will use root's home , then another (warning) about using the same folder or something like that

just after this , a third error msg came , 
says that I am logged out , and my session was less than 10 second , which probably caused be an error , then it display the login screen again .


I even tried to create a new user which didn't exist before
but I got same results , couldn't create with -d option , and in case of without -d I couldn't log in in GUI with it .

---

### Post by tamer_radi on 2009-02-02
I solved the problem .

I was missing a little step
seems .dmrc was deleted somehow
so I created it , and chmod + chown it , and also for the home directory

The Exact commands for any one have the same problem :

```

(as root , or use sudo)
touch .dmrc
chmod 644 .dmrc
chown <user> .dmrc
chmod 755 /home/<user>
chown <user> /home/<user>

```

Thanks all for helping me.

---

