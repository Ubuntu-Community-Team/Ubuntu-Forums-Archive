---
title: "External HD unavailable"
date: 2015-12-09
forum: Hardware
---

### Post by Windoze Refugee on 2015-12-09
I have a 3tb external Seagate HDformatted for Mac, that was in a caddy.
It contains a great deal of importantdata so a reformat is not an option.
Although the drive is a couple of yearsold, it has only got around 40 hours run time – HD fail seems veryunlikely


I seem to remember having tried to makeit portable between systems (apart from ubuntu, on othermachines I also run Mac OSX, and various windoze (xp/vista/7etc). But I definitely would not have changed the file format.
In the process I think I may haveinadvertently deleted the MBR or something similar. 


I'm pretty sure all the data is stillthere, but I can't get to it as it comes up as unrecognised in Ubuntu(although showing the correct size) and not showing up at all in macDisk Utility.


I think I just need to rewrite theheaders or something, but cant quite remember how.
Any help very gratefully received.

---

### Post by sudodus on 2015-12-09
> **Windoze Refugee said:**
> I have a 3tb external Seagate HDformatted for Mac, that was in a caddy.
It contains a great deal of importantdata so a reformat is not an option.
...

In this case I recommend that you ***clone the drive and work on the cloned copy*** in order to avoid further damage on the faulty drive.

Install ***ddrescue***

```
sudo apt-get install gddrescue
```

and read the info page which is a good tutorial.

```
info ddrescue
```

When you have a cloned copy, I suggest that you try first ***TestDisk*** and if it fails then ***PhotoRec***.

TestDisk can often re-create a working file system.

PhotoRec can identify the data on the drive without any file system, and you can get back a lot of files. But the directories and file names are lost, so, yes, it works, but it is a lot of hard work.

[http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by Windoze Refugee on 2015-12-09
Thanks for your input Sudodus.
However I don't think the drive is faulty, just had a header or MBR removed or something ( I really can't remember)
Will Testdisk be able to restore the missing header file (or whatever) if this is the only thing wrong? Is there nay danger it could make the data less recoverable?

---

### Post by sudodus on 2015-12-09
> **Windoze Refugee said:**
> ...
Will Testdisk be able to restore the missing header file (or whatever) if this is the only thing wrong?

Yes, it might be able to repair the access to a file system.

If the problem is with the bootloader, you might have better luck with [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).
> 

Is there nay danger it could make the data less recoverable?

Yes, these kinds of actions (on the partition table, file systems and boot-loader) are always risky. So you should have a backup (or work on a cloned copy, if there are important files on the drive.

---

### Post by J_Me on 2015-12-09
You should consider sudodus advise and clone the drive before attempting anything.

---

### Post by Windoze Refugee on 2015-12-09
Thanks again for your input. 
Just so were clear though, the drive isn't required to boot - it's data storage only.
Would that still mean boot repair is the right tool for the job?

---

### Post by weatherman2 on 2015-12-09
> **Windoze Refugee said:**
> I have a 3tb external Seagate HDformatted for Mac, that was in a caddy.
It contains a great deal of importantdata so a reformat is not an option.
Although the drive is a couple of yearsold, it has only got around 40 hours run time – HD fail seems veryunlikely


Hard drives can fail at any time.  They can fail the first week after use or they may not fail in 20+ years of use.  Don't make assumptions.  Check the S.M.A.R.T. status of the drive.  Use GSmartControl, something you can install in Ubuntu (on a live boot, you need to enable the Universe repository first in Ubuntu Software center, the install it).

You can check the current S.M.A.R.T. Attributes in GsmartControl - look for any Attributes that are highlighted in pink/red.  (You could run S.M.A.R.T. tests but that's not required.)  You can also try the command "sudo smartctl -a /dev/sda" to check drive sda.  (Replace with whatever your drive's device ID is.)

For an external/USB drive you may need to add parameters to smartctl like -T permissive and/or -d sat.  So your command might be "sudo smartctl -T permissive -d sat -a /dev/sda" .

> I seem to remember having tried to makeit portable between systems (apart from ubuntu, on othermachines I also run Mac OSX, and various windoze (xp/vista/7etc). But I definitely would not have changed the file format.
In the process I think I may haveinadvertently deleted the MBR or something similar. 

Let's see what the current status of your drive's partitions is.  Try this command:

```
sudo parted -l
```

and tell us the output.

---

### Post by sudodus on 2015-12-10
> **Windoze Refugee said:**
> Thanks again for your input. 
Just so were clear though, the drive isn't required to boot - it's data storage only.
Would that still mean boot repair is the right tool for the job?

No Boot-Repair will probably not help, if you do not intend to boot from the drive.

Using a cloned copy can protect the valuable data that you want to recover. This is important ***both*** for a physically failing drive (damaged hardware) and for a drive where the file system or partition table is corrupted (damaged software).

---

### Post by Windoze Refugee on 2015-12-12
Hi Folks, 
Thanks again for all your input.
OK - Ive been working with Testdisk and have had encouraging results, but not felt brave enough to hit the "write" key. Main reason - havent been able to make a clone :(
And it is driving me nuts!!!
Without going into all the gory details, my main Ubuntu machine is a very old distro that I can't update. The mac won't recognise the 3TB HD at all, so I am forced to try and clone through the windoze machine, albeit through bootables into a mostly linux environment.
And this is the issue - I've tried Clonezilla, and hit problem after problem: First of all I bought a new 3TB HD to clone to, only to discover that it was EIGHT SECTORS smaller than the original and therefore would not work!!
So I went and got a 4TB HD, only to discover that > Error! Destination disk (/dev/sde) sizeis 4.00TB, which is larger than the MBR partition table entry maximum2 TiB (~ 2.2 TB). You have to use GUID partition table format (GPT)[SIZE=2][/SIZE]
[SIZE=2]Arghhhh[/SIZE]

[SIZE=2]So then I tried to get dd[/SIZE]rescue[SIZE=2] to run from a bootable disk, but that was so unbelievable complex and user-unfriendly I simply could not get it to work.
So now I don't know what to do&#8230;
Find another cloning tool? But then will I be faced with the same incompatibility issues?&#8230;
Stuck and frustrated :([/SIZE]

---

### Post by sudodus on 2015-12-12
According to

[http://clonezilla.org/](http://clonezilla.org/)

> Both MBR and GPT partition formats of hard drive are supported. Clonezilla live also can be booted on a BIOS or uEFI machine. 

so it is possible to clone a GPT (GUID partition table) with Clonezilla. What partition table is it in your current 3 TB drive? (It should be a GPT, because it is greater than 2 TB.)

---

### Post by Windoze Refugee on 2015-12-12
If theres an option in clonezilla to choose this, I'm not seeing it.
I tried formatting the disk as GPT in windoze, then ran clonezilla from boot, but still no joy

---

### Post by Windoze Refugee on 2015-12-12
the partition table on the 3TB I'm trying to clone is (as far as I know) HFS+ but as I can't get into it I don't really know for sure :(..

---

### Post by sudodus on 2015-12-12
If you clone the 3 TB disk to the 4 TB disk, I think it is not meaningful to format the 4 TB disk, because it will be completely overwritten anyway.

So you should not create an image (compressed image file), you should ***clone*** from a source drive to a target drive.

---

### Post by Windoze Refugee on 2015-12-12
Thats what I thought too. But it won't do it - keeps coming up with the error above. 
I don't know how to correct the partition table format if its going to be overwritten anyway!!
Grrrr

---

### Post by sudodus on 2015-12-12
If it does not work with ***Clonezilla***, you can do it with ***ddrescue*** - at least with some help, or with ***mkusb*** (which is safer, less risk for mistakes). But mkusb uses dd under the hood, which is slower than Clonezilla, and less robust than ddrescue, if there are bad sectors on the disk.

---

### Post by Windoze Refugee on 2015-12-12
I had zero success even getting ddrescue to run :(
Im also a little nervous as I have 7 HDs in this machine and I really don't want to mess em up.
I tried system rescue cd which contains ddrescue but not in a graphical interface and I found it completely baffling

---

### Post by Windoze Refugee on 2015-12-12
Whats the worst that could happen if i completed test disk  - took the last step and clicked "write partition structure to disk"?

---

### Post by sudodus on 2015-12-12
> **Windoze Refugee said:**
> Thats what I thought too. But it won't do it - keeps coming up with the error above. 
I don't know how to correct the partition table format if its going to be overwritten anyway!!
Grrrr

Maybe the problem is the source drive (the partition table and/or the file system). In that case I suggest that you try ddrescue again.

According to the first part of Example 1 in ```
info ddrescue
```

Boot from a live drive, where ddrescue is installed.

```
sudo ddrescue -f -n /dev/sdx /dev/sdy logfile
```

where x is the drive letter on the source drive (3TB) and y is the drive letter of the target drive (4TB).

**logfile** will be written to the working directory and should be copied to some persistent drive before you shut down the live session.

---

### Post by sudodus on 2015-12-12
> **Windoze Refugee said:**
> Whats the worst that could happen if i completed test disk  - took the last step and clicked "write partition structure to disk"?

That it will be very difficult or impossible to recover the files, and there will be no second chance.

---

### Post by Windoze Refugee on 2015-12-12
> **sudodus said:**
> 
Boot from a live drive, where ddrescue is installed.

```
sudo ddrescue -f -n /dev/sdx /dev/sdy logfile
```

OK - so get to a terminal within the bootable environment run the above?
What is the working directory? And how do I copy a log file from there? flash drive?

---

### Post by Windoze Refugee on 2015-12-12
BTW this is just to get info, right? This won't alter the HDs yet?

---

### Post by sudodus on 2015-12-12
> **Windoze Refugee said:**
> OK - so get to a terminal within the bootable environment run the above?
What is the working directory? And how do I copy a log file from there? flash drive?

Yes - a terminal window.

If you don't change working directory, it will be your home directory.

Yes, you can copy it to a[nother] flash drive.

---

### Post by sudodus on 2015-12-12
> **Windoze Refugee said:**
> BTW this is just to get info, right? This won't alter the HDs yet?

If you run ddrescue you will clone from the source drive (3TB) to the target drive (4TB). You will overwrite what is on the 4TB drive (but it should be empty). And the process will be slow, many hours, maybe one or two days and nights depending on the speed of the connection. SATA connections to both drives would be the best. eSATA and USB 3 are second best. USB 2 works but will be very slow.

---

### Post by Windoze Refugee on 2015-12-12
Just encountered another hurdle - probably because the mac drive I want to recover isn't showing up anywhere useful, it doesn't seem to have a drive letter assignment&#8230;
Any ideas?

Oh and BTW - very many thanks for taking the time to help me with this :)

---

### Post by sudodus on 2015-12-12
The tools we are discussing are assuming that the disk is recognized as a mass storage device /dev/sdx, where x is the drive letter.

Please run the following commands (maybe after rebooting into a linux live drive) and post the output :-)

```
sudo parted -ls

sudo lsblk -fm
```

---

### Post by Windoze Refugee on 2015-12-12
ok - ran both apps and got the following
In testdrive:
4TB seagate backup drive - &#8220;J&#8221;(physical drive 8)


3TB lost mac drive - "?" (physical drive 9)


In clonezilla:


sde	4TB seagate backup drive
sdj	3TB lost mac drive

---

### Post by sudodus on 2015-12-12
> In clonezilla:

sde 4TB seagate backup drive <--> target drive
sdj 3TB lost mac drive <--> source drive


If I understand correctly, this means

```
sudo ddrescue -f -n /dev/sdj /dev/sde logfile
```

---

### Post by sudodus on 2015-12-12
Now, remember that ***all the partitions on the source drive and the target drive must be unmounted***. It means that you boot from a third drive, for example from live drive or an installed system, that is independent of both of these source and target drives.

Check again that the drive letters are correct before you run the command.

---

### Post by Windoze Refugee on 2015-12-12
ok - and this is **only **to generate a log file or will this start the cloning?

---

### Post by sudodus on 2015-12-12
It will do both, create a logfile at the same time as it is cloning.

---

### Post by Windoze Refugee on 2015-12-12
ok. fingers crossed. Ill get back to you in a couple of days I guess :)

---

### Post by sudodus on 2015-12-12
Please check a final time that the drive letters are correct, and the go.

Good luck :-)

---

### Post by Windoze Refugee on 2015-12-12
Hmmm. OK - well I ran this command before launch just in case > lsblk -o name,label,size,fstype,model
and got two different drive assignments : sdg (3.7t) and sdj (2.7t) . Neither are quite right as they are 4tb and 3tb respectively.
Does this seem right to you?

Also, could you explain what the f- switch is for, as I don't understand what an outfile is? cheers

---

### Post by Windoze Refugee on 2015-12-12
I've had a close look at a ddrescue guide here [https://www.technibble.com/guide-using-ddrescue-recover-data/](https://www.technibble.com/guide-using-ddrescue-recover-data/) 
From this it looks like this might be a better command line - what do you think?
> [COLOR=#000000][FONT=Courier]ddrescue -d -f -r3 /dev/sdj /dev/sdg[/FONT][/COLOR]

with this line added to send the log file to a flash drive
> [COLOR=#000000][FONT=Courier]/sdk/sdk1/LJUBICA'S/rescue.logfile[/FONT][/COLOR]

?

---

### Post by sudodus on 2015-12-13
Good morning :-)

> **Windoze Refugee said:**
> Hmmm. OK - well I ran this command before launch just in case 

```
lsblk -o name,label,size,fstype,model
```

and got two different drive assignments : sdg (3.7t) and sdj (2.7t) . Neither are quite right as they are 4tb and 3tb respectively.
Does this seem right to you?

Also, could you explain what the f- switch is for, as I don't understand what an outfile is? cheers

3.7 Tibibytes (base 2 such that 2^10 = 1024) is 4 Terabytes (base 10 such that 10^3 = 1000) and 2.7 Tibibytes is 3 Terabytes.

Sorry I meant output (output to the terminal window rather than outfile). From ```
man lsblk
```

```
       -f, --fs
              Output info about filesystems.  This option is equivalent to "-o
              NAME,FSTYPE,LABEL,MOUNTPOINT".   The  authoritative  information
              about filesystems and raids is provided by the blkid(8) command.
```

> **Windoze Refugee said:**
> I've had a close look at a ddrescue guide here [https://www.technibble.com/guide-using-ddrescue-recover-data/](https://www.technibble.com/guide-using-ddrescue-recover-data/) 
From this it looks like this might be a better command line - what do you think?

```
ddrescue -d -f -r3 /dev/sdj /dev/sdg
```

with this line added to send the log file to a flash drive

```
/sdk/sdk1/LJUBICA'S/rescue.logfile
```

?

That line with -r3 should be used in a second pass, if there are physical damages, bad sectors, on the source drive, that were not read during the first pass. Otherwise you don't need it. And you don't know about that until you have run the first pass with the command line I suggest. It is important to write and save the logfile, particularly if it turns out, that you need such a second pass.

These things are explained in the info page ```
info ddrescue
``` I suggest that you do something similar to Example 1 'Rescue a whole disk ...' and start with the first command line. I have used ddrescue like this, and I succeeded using it. It is possible that you can do it also with the LJUBICA'S line, but I have no experience of that. (I think you should avoid using a single quote, ' , it should be matched by a second quote (and is typically used to protect special characters in file names)).

***If you want my detailed help to write the ddrescue command line, please post the whole output of this command***

```
[SIZE=3]sudo lsblk -o MODEL,NAME,FSTYPE,LABEL,MOUNTPOINT,SIZE[/SIZE]
```

You can mark and paste it from the terminal window to the edit box for a reply in this thread at the Ubuntu Forums. ***Otherwise I can only say "Yes, probably that is OK"***

And I would recommend that you use the command line in my previous post (with modified drive letters for the current state of the system)

```
[SIZE=3]sudo ddrescue -f -n /dev/sdj /dev/sdg logfile[/SIZE]
```

It is also possible to point the logfile directly to another pendrive

```
sudo ddrescue -f -n /dev/sdj /dev/sdg path-to-partition-on-another-pendrive/logfile
```
or
```
sudo ddrescue -f -n /dev/sdj /dev/sdg 'path-to-partition-on-another-pendrive/logfile'
```

where you replace the text 'path-to-partition-on-another-pendrive' with the real path.

---

### Post by Windoze Refugee on 2015-12-13
Hi. In the end I ran it just as per your original command line, altered for the results of the drive enquiry. Its been going now for 10.36 hours (although weirdly, this seems to be metric hours???) and has covered 730000 mb. By my calculations I think this means it shoulder done sometime around midnight tomorrow (GMT)
Fingers crossed...

---

### Post by sudodus on 2015-12-13
Good luck :-)

---

### Post by Windoze Refugee on 2015-12-15
Just to let you know, cloning and recovery was a success!
Many thanks for your help and patience :)

---

### Post by sudodus on 2015-12-15
Congratulations :KS

So cloning with ddrescue worked :-)

Could you repair the file system with testdisk, or did you use some other method?

-o-

Finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

