---
title: "Wheres The 2nd Disk?"
date: 2008-07-12
forum: Hardware
---

### Post by Jeeves1983 on 2008-07-12
Hi all.

I have just installed the latest version of Ubuntu onto my laptop, which is great. My laptop is faster than ever and all the niggley problems like sound and video jumping which i used to experience in windows xp have now gone. There is one issue though.

In my laptop i have a secong Hard Drive. Not a big one, Only 10Gb but i was hoping to use it to store my music.

Ubuntu doesn't find the second hard drive which is highly annoying.

How can i find my missing Hard Drive?

All help welcome.

Many Thanks

---

### Post by matt$2 on 2008-07-12
Let's start with "What have you done to ascertain that it's not found it?"
I find that very hard to believe.  It may be there but you don't know how to access it.

---

### Post by flytripper on 2008-07-12
look in the left column when you are in your home folder. is it there? it may simply not be mounted yet.
In which case just click it.

---

### Post by Jeeves1983 on 2008-07-12
Hi, i have looked down the left hand side of the 'computer' section but cannot find it. How do i mount it or find it.

---

### Post by matt$2 on 2008-07-12
Let's see.
Could you post your
/etc/fstab
?

That will be a good start.

Bring up a console. Enter 

sudo ls /dev/sd*

and try
sudo ls /dev/hd*


There are a number of other options.
Post result and we can take it from there.

---

### Post by Jeeves1983 on 2008-07-12
Sorry matt$2, I have no idea what you mean.

What does 'Can you post your /etc/fstab
?'mean?

I typed in those locations but i get a box saying 'Nautilus cannot handle this type of location'

Can you explain it a bit simpler please. I aint that good!

---

### Post by matt$2 on 2008-07-12
Yes ok I'm with you.

In your root system you hve /boot, /dev, /etc, /home and a few more.  Do it this way.

Bring up a console.  Enter

sudo gedit /etc/fstab

and gedit opens up the file.  Copy the full conents and and paste it all into you next reply space here in the forum. That's posting your /etc/fstab.

---

### Post by Jeeves1983 on 2008-07-12
it still comes up with the same message. I have got to my file system and can see the files you mentioned. just unsure what to do next.

---

### Post by Jeeves1983 on 2008-07-12
Sorry. Being a bit thick. Found it. Here it is

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9bf35c52-1c03-4428-bd34-40c3802f4fae /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c94895c8-853d-41c5-858f-380934f77bf6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by matt$2 on 2008-07-12
Yes ok you're quite right.  It's not found and thus not listed.
So, this is so unusual that I suspect the cable might be loose.

Go into your bios and see if it sees 2 hard drives.  If not, it's got no chance to pass it onto ubuntu.


If it is listed, need to re-think.

---

### Post by Jeeves1983 on 2008-07-12
do i have to go into my bios from the boot menu screen?

---

### Post by boblemur on 2008-07-12
yup prob like tap f<something> or del key on boot... it will be writen their when ur pc boots...

can u run:

sudo fdisk -l | grep 'Disk '

for me please

will give u a list of disks... see if its found there... keep in mind if u have like usb sticks and stuff there they will appear... so check the size

---

### Post by matt$2 on 2008-07-12
Yes. If it doesn't come up with the fdisk search, then you go into the bios at bootup.

---

### Post by Jeeves1983 on 2008-07-12
can you give me directions to where it should be please

---

### Post by boblemur on 2008-07-12
do you mean the command? 

you need to run that in your terminal ( applications > accessories > terminal)

and the bios can be accessed when you first turn your computer on, you will have some kinda logo or slash screen and look for anything that has a key name... and then setup or something, what type of computer do you have?

failing that you can just try spamming your fXX keys and ur del key and stuff and it would prob get you there :P

---

### Post by ChameleonDave on 2008-07-12
To post the contents of a file, there is no need to use "sudo" or "gedit".  Simply use "cat" to dump the contents of the file onto the [terminal]("https://help.ubuntu.com/8.04/basic-commands/C/starting-terminal.html").  Then copy and paste.

```

cat /etc/fstab

```When posting such output on the forum, please put it between [noparse]```
...
```[/noparse] tags in order to make it clear and legible.  You can do it by selecting the text, and then clicking on the "#" button in the forum post editor.

(Helpers: the same goes for when you are giving newbies instructions.  Please don't confuse the newbies with ambiguous or vague instructions.)

If your device is not listed in /etc/fstab, it will not be automatically mounted.  We therefore ought to add an entry in /etc/fstab to correct this situation.  However, we first need to see whether the device is visible to the operating system.  Please use the following command:

```

sudo blkid

```Post the results here.

---

### Post by Jeeves1983 on 2008-07-12
Right this is what you wanted. While your thinking of something, ill restart my comp and go into my bios. Back in a bit...

ryan@ryan-laptop:~$ sudo fdisk -l | grep 'Disk '
Disk /dev/sda: 40.0 GB, 40007761920 bytes
Disk identifier: 0xed55ed55

---

### Post by Jeeves1983 on 2008-07-12
also my dvd drive won't read dvd movies? any ideas there?

---

### Post by Jeeves1983 on 2008-07-12
Hi Chameleon Dave. Inputted the command as instructed

```
ryan@ryan-laptop:~$ sudo blkid
/dev/sda1: UUID="9bf35c52-1c03-4428-bd34-40c3802f4fae" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c94895c8-853d-41c5-858f-380934f77bf6"
```

Any Ideas?

---

### Post by matt$2 on 2008-07-12
Chameleon's request only confirmed what seemed already established.
Your system is not seeing the second drive.

You will have it resolved if you fixed the deficit in the bios.  You sort of haven't mentioned what happened about that.
The dvd movie viewing will be fixed by installing the required codecs.

Firstly, the drive.

---

### Post by ChameleonDave on 2008-07-12
> **matt$2 said:**
> Chameleon's request only confirmed what seemed already established.
Your system is not seeing the second drive.

You will have it resolved if you fixed the deficit in the bios.  You sort of haven't mentioned what happened about that.
The dvd movie viewing will be fixed by installing the required codecs.

Firstly, the drive.
Yes, "sudo blkid" and "sudo fdisk -l" provide very similar results.  I don't know why "grep" was used though, as it is only useful for grabbing important bits from commands that have large amounts of output (and fdisk isn't very verbose).

If you want more data, you can use "sudo lshw -sanitize -C disk".

I agree that the BIOS settings and the physical cables need to be checked.

---

### Post by Jeeves1983 on 2008-07-12
Sorry. Had to nip out. 

The bios is not showing the second drive either.

---

### Post by ChameleonDave on 2008-07-12
> **Jeeves1983 said:**
> Sorry. Had to nip out. 

The bios is not showing the second drive either.
OK, now you say that this is in your laptop.  It's not normally possible to install multiple internal hard drives in a laptop.  There's just no space.  Perhaps you could explain your physical set-up a bit more for us.

---

### Post by Jeeves1983 on 2008-07-14
ok. i dunno how to do that can anyone explain?

The only thing i can think of is that the hard drive was partitioned to make two drives. But the system says that i have just one 40gb hard drive when i used to have a 40gb and a 10gb one?

Im stumped. Any news on how to find the code required to show you guys would be appreciated.

Many thanks again tho for all your help, i do appreciate it.

---

### Post by ChameleonDave on 2008-07-14
> **Jeeves1983 said:**
> ok. i dunno how to do that can anyone explain?

The only thing i can think of is that the hard drive was partitioned to make two drives. But the system says that i have just one 40gb hard drive when i used to have a 40gb and a 10gb one?

Im stumped. Any news on how to find the code required to show you guys would be appreciated.

Many thanks again tho for all your help, i do appreciate it.
Thanks, that's the sort of info I was after.

So, you only have one actual hard drive as such, but it is divided into two partitions.

Well, as far as we can see from those commands, you do have two partitions, but one is ext3 (with Ubuntu on) and the other is swap (providing an area for Ubuntu to use as virtual memory).  There is nothing else.  You presumably deleted everything else.

If you open up GParted (look for it in the application menus, or type "*gksudo gparted*" on the command line), what do you see?  (You could explain, or show a screenshot.)

---

### Post by Jeeves1983 on 2008-07-15
Here is the screen shot u wanted. Its in the attachment. But the partition is really small. Not the 10Gb i had previously.

---

### Post by thegodfaza on 2008-07-15
I assume that when you installed Ubuntu you chose the option in the partitioner to let it automatically partition your hard drive. This wipes your drive and makes a / partition and a swap partition. So any data that was there is now gone. What you should have done is choose the advanced partitioner and choose the partition you wanted to be the system partition.

---

### Post by Jeeves1983 on 2008-07-19
I am not sure. Think i used the option where it wipes everything. I am sure i will never get that 10Gb back so im gonna move on to my next problem.

My dvd won't play dvd's. It says that the media is incompatible, even though i downloaded the codecs for the O/S.

Any Ideas?

---

### Post by Pro-reason on 2008-07-19
> **Jeeves1983 said:**
> im gonna move on to my next problem.

My dvd won't play dvd's. It says that the media is incompatible, even though i downloaded the codecs for the O/S.

Did you install libdvdcss2 from Medibuntu?

But this is really a subject for a separate thread.  There are many already covering the topic of DVDs.

---

### Post by Jeeves1983 on 2008-08-04
How do i install it. i have it downloaded. This ubuntu is good i must say but installing items is a pain in the butt!

---

### Post by Pro-reason on 2008-08-05
> **Jeeves1983 said:**
> How do i install it. i have it downloaded. This ubuntu is good i must say but installing items is a pain in the butt!

The thing is that you don't have to download stuff separately and then install it.

Search the forums on how to enable the Medibuntu repositories.  Then, you just have to use Synaptic to install stuff.

---

