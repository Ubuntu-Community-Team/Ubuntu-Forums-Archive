---
title: "HP Z800 Max HDD Size"
date: 2017-01-02
forum: Hardware
---

### Post by eunosm3 on 2017-01-02
My new-to-me Z800 (running Ubuntu 16.04 from a bootable USB drive) will not recognize the full size of my 3TB hdd.  It shows only 2.0TB.  The HP support forum pointed out that the disk needed to use GPT, so I used GParted to apply GPT to the disk, The site actually refers to "initilizing" the disk w/ GPT, which I thinkt to apply GPT via GParted.  No joy, though. 
 
This site, [https://support.microsoft.com/en-us/kb/2581408](https://support.microsoft.com/en-us/kb/2581408), seems to suggest I upgrade my storage controller software (?firmware), but the whole thing is really over my head.

Any thoughts on whether the drive size recognition can be fixed via Ubuntu or whether it needs a system setup change? 

The Z800 is a vanilla dual-xeon box.  I will provide more information about the system if needed, of course.

---

### Post by #&amp;thj^% on 2017-01-02
Is there anything on the 3TB disk now? (That you might need or want)
Not sure if you have seen this yet: [http://askubuntu.com/questions/628719/how-do-i-mount-my-new-3tb-hard-drive](http://askubuntu.com/questions/628719/how-do-i-mount-my-new-3tb-hard-drive)

---

### Post by eunosm3 on 2017-01-02
I had not seen that post.  However, I had used GParted anyway with an ext4 file system.  The drive has nothing on it yet; I'm re-using it from a different build.

---

### Post by #&amp;thj^% on 2017-01-03
If you follow this...[COLOR=#ff0000]YOU ARE ON YOUR OWN...I bear no responsibilty if things go Amuck[/COLOR].
Here is how I do it using a ext4 format:

 1. Use "lsblk" to find the drive name (will be something like /dev/sdX where X is a letter)
So enter this in the terminal:
```
lsblk
```
Then enter this:
    ```
sudo parted /dev/sdX
```
Again the drive sdx should read as you found yours with lsblk.
 2.In the parted interactive console type:
      ```
(parted) mklabel gpt
        (parted) unit TB
        (parted) mkpart primary 0.00TB 3.00TB (Changing 3.00TB to the size of your drive)
        (parted) quit
``` 
Next Run:
   ```
sudo mkfs.ext4 /dev/sdX1
``` 
(Where X is the same as above and note the "1" now)
    ```
sudo tune2fs -m 1 /dev/sdX1
```
    ```
mkdir /Your/Mount/Point/Here
```
    ```
sudo blkid
```
    (Copy the UUID of your drive)
    ```
sudo nano /etc/fstab
```
    Add the line UUID=YOUR-UUID-HERE-XXXX    /Your/Mount/Point/Here  ext4    defaults    1   2 then save and exit
   ```
 sudo mount -a
```

Your drive will be partitioned, formatted as ext4, and mounted.

---

### Post by eunosm3 on 2017-01-03
I'll give it a whirl.  I have completed the steps down to tune2fs before, so I'm comfortable with that.  How does setting the reserved-block-percentage help?

Also, for the sake of clarity, the fstab line is:
[COLOR=#000000]UUID=YOUR-UUID-HERE-XXXX /Your/Mount/Point/Here ext4 defaults 1 2[/COLOR], which includes the numbers '1' and '2' at the end, correct?

Thanks for the follow-up

---

### Post by #&amp;thj^% on 2017-01-03
> **eunosm3 said:**
> I'll give it a whirl.  I have completed the steps down to tune2fs before, so I'm comfortable with that.  How does setting the reserved-block-percentage help?

Also, for the sake of clarity, the fstab line is:
[COLOR=#000000]UUID=YOUR-UUID-HERE-XXXX /Your/Mount/Point/Here ext4 defaults 1 2[/COLOR], which includes the numbers '1' and '2' at the end, correct?

Thanks for the follow-up

Yes the numbers (1 2)are at the end.
And you could for the sake of simplicity go this route also.
Run gparted as follows, replace sdb with your real disk name:

```
parted /dev/sdb
```
I use sdb as example of course.

Output would look like this:

```
GNU Parted 3.2-5
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)
```

Now type **&#8220;mklabel gpt&#8220;,** as you see below:
```
(parted) mklabel gpt

```
Output should be something like this:

```
Warning: The existing disk label on /dev/sdb will be destroyed and all data on this disk will be lost. Do you want to continue? 
Yes/No? yes
(parted)

```
Now, let&#8217;s set default size unit to TB, type &#8220;unit TB&#8221; and press enter:

```
(parted) unit TB
```

Type: mkpart primary 0.00TB 3.00TB to create a 3TB partition:
```
(parted) mkpart primary 0.00TB 3.00TB

```
To print the current partitions, type p :

```
(parted) p
```

Sample outputs:

```
Disk /dev/sdb: 3.00TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  3.00TB  3.00TB  ext4         primary
```

Now type quit to exit the gparted console.
```
(parted) quit
```

Now format the new patition:

```
mkfs.ext4 /dev/sdb1
```

Mount the new drive:

```
mkdir /mnt/3tbdisk
mount /dev/sdb1 /mnt/3tbdisk
```

Now add that mount point to /etc/fstab, example:

```
/dev/sdb1 /mnt/3tbdisk ext4 defaults 0 1
```

Now type **"df -ah"** to see if the drive is mounted properly, you should see something like this:

```
/dev/sdb1 3.0T 321M 2.9T 1% /mnt/3tbdisk

```
Hope that is clear enough.

---

### Post by #&amp;thj^% on 2017-01-04
Did I lose you?....Or even further confuse you?
The second method in post #6 should be fairly straight forward.(I had to do it twice though due to some errors that I can't remember [Probably Fat Fingered] ATM)

---

### Post by eunosm3 on 2017-01-04
Oh, no, you didn't lose me.  I spent yesterday evening fulfilling my suburban dad duties, so I could not make any progress.  In the meantime, though, I realized that initializing the disk w/ GPT on the Z800, which only recognizes 2TB in the first place, *might* be an issue.  Tonight I'll use a different box that I know recognizes all 3TB for the process you outlined above.  Also, someone from the HP forum suggested creating two partitions on the a 3TB drive while addressing a different member's question.  If one partition fails, I'll try creating two partitions with less than 2TB each.  No idea if it will work.

---

### Post by eunosm3 on 2017-01-04
@1fallen: The problem rests on the Z800, not the disk as far as I can tell.  I followed your directions, which created a initialized, partitioned and mounted 3TB drive on a spare box.  However, the Z800 still only recognizes 2TB.  I updated the BIOS, but it did not seem to have any effect, either.  Back to the drawing board.

---

### Post by Yellow Pasque on 2017-01-05
> Also, someone from the HP forum suggested creating two partitions on the a 3TB drive while addressing a different member's question. If one partition fails, I'll try creating two partitions with less than 2TB each.
Yeah, that's what I would do, especially if I was going to use the disk on an old-school (pre-UEFI) system like the Z800.

[http://h30434.www3.hp.com/t5/Business-PCs-Workstations-and-Point-of-Sale-Systems/Z800-Max-Disk-Size/td-p/5920000](http://h30434.www3.hp.com/t5/Business-PCs-Workstations-and-Point-of-Sale-Systems/Z800-Max-Disk-Size/td-p/5920000)
I saw in your other thread that there was a question about using "non-HP-certified" SATA 6Gbps drives in this system. Although I'm skeptical that it makes any difference (other than an easy excuse to deny customers support), you can force a WD Red disk to SATA 3Gbps mode with a jumper on pins 5 and 6 : [http://support.wdc.com/knowledgebase/answer.aspx?ID=981](http://support.wdc.com/knowledgebase/answer.aspx?ID=981)

---

### Post by #&amp;thj^% on 2017-01-05
> **Temüjin said:**
> Yeah, that's what I would do, especially if I was going to use the disk on an old-school (pre-UEFI) system like the Z800.

[http://h30434.www3.hp.com/t5/Business-PCs-Workstations-and-Point-of-Sale-Systems/Z800-Max-Disk-Size/td-p/5920000](http://h30434.www3.hp.com/t5/Business-PCs-Workstations-and-Point-of-Sale-Systems/Z800-Max-Disk-Size/td-p/5920000)
I saw in your other thread that there was a question about using "non-HP-certified" SATA 6Gbps drives in this system. Although I'm skeptical that it makes any difference (other than an easy excuse to deny customers support), you can force a WD Red disk to SATA 3Gbps mode with a jumper on pins 5 and 6 : [http://support.wdc.com/knowledgebase/answer.aspx?ID=981](http://support.wdc.com/knowledgebase/answer.aspx?ID=981)

+1 And Nice catch Temüjin :)
Kind Regards

---

### Post by eunosm3 on 2017-01-05
At the  moment, I'm chasing two possibilities.  One is a Z800-specific issue with the hardware, while the other would be related to Ubuntu on USB drive and the HPA setting.

---

### Post by #&amp;thj^% on 2017-01-05
> **eunosm3 said:**
> At the  moment, I'm chasing two possibilities.  One is a Z800-specific issue with the hardware, while the _**other would be related to Ubuntu on USB drive and the HPA setting.**_

You know I looked right past that (In your first post)....That would be my best guess here also.:o

If you don't mind multiple partitions you should be good that way. (With your current Set-up)

---

### Post by Yellow Pasque on 2017-01-05
> It shows only 2.0TB.

What does "it" refer to? I assumed the drive was only showing as 2GB in the BIOS, but the way you're talking, the BIOS shows it as a 3GB drive and you're having the issue specifically in the OS (Ubuntu). Please clarify.

The suggestion to try different SATA ports seems promising. About the only other thing that came to mind when looking at the manual is a setting in the BIOS called "SATA emulation mode" (something like that).

---

### Post by eunosm3 on 2017-01-06
"It" refers to lsblk and parted; so, the OS.  I don't remember whether the BIOS reads it as 3TB or 2TB.  I'll check tonight, but I'm ready to throw in the towel (see my next post).

---

### Post by eunosm3 on 2017-01-06
[COLOR=#000000][FONT=Consolas]*Failed Solutions*[/FONT][/COLOR]

[LIST=1]
[*]Initialize the Drive w/ GPT || Recommendations to initialize the drive w/ GPT instead of MBR outpaced any other erstwhile solution.  Initializing incorrectly must be either really common or top-of-mind or both.  It did not help my situation.
[*]Ubuntu Bug Related to Booting from A USB Drive || This was the most-obscure possible solution.  Apparently Ubuntu 14.04 had a previously-squashed bug reappear.  If you boot off of a USB drive or CD, HPA would be enabled, which somehow or another limits the size of disk the OS can recognize.  This didn&#8217;t work either.
[*]Plug the Drive Into the LSI SAS Ports || According to HP documentation, SATA drives up to 3TB can be used if plugged into ports 2-5 of the LSI controller.  I&#8217;m not sure what I did wrong, or what step I missed, but I could not make it work.
[*]Update the BIOS || The BIOS version was out of date on my Z800, so I updated it from within the BIOS (bios within bios).  The BIOS is updated now, but the computer still only sees 2TB on the drives.
[/LIST]

---

### Post by Yellow Pasque on 2017-01-06
Did you try plugging the drive into one of the other SATA ports (2-5)?
When you tried to use the SAS ports, did you change SATA emulation to IDE?

---

### Post by eunosm3 on 2017-01-07
Thank you for the suggestion - it worked!  The tech manual's reference to plugging into the LSI controller fooled me into using the SAS ports b/c I thought only the SAS ports used the LSI controller.  When I moved them connections, my computer began recognizing 3TB.  Awesome.

---

