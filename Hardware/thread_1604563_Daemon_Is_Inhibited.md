---
title: "Daemon Is Inhibited"
date: 2010-10-24
forum: Hardware
---

### Post by Th3Blaze on 2010-10-24
If it says Daemon is inhibited, just reboot the computer, unplug everything to do with what you are trying to format, then start again.

---

### Post by Th3Blaze on 2010-10-24
Please!!
I looked everywhere and I Couldn't find it.
I used G-Parted to turn it to FAT 16 and then I tried to mount it using Disc Utility.

---

### Post by Th3Blaze on 2010-10-24
Please I am desperate.
8 Views and No Help.
Please!!!!!:(:(:(:( :confused:::confused::cry: :cry:

---

### Post by IcarusR on 2010-10-24
Be patient, your original post was only two & half hours ago !!

---

### Post by Th3Blaze on 2010-10-24
How is that help?
Can you help me please?

---

### Post by iveand on 2010-10-26
I have the same problem.  Trying to talk to a Micro SD in my Motorola L7 phone.  Disk Utility "sees" the drive and lists it as Fat32.  But when I try to "mount" or "format" it gives same error: "Daemon is inhibited".  

Confused.


iveand

---

### Post by goltoof on 2010-10-26
Same problem here.  Looks like a problem with the device it's mounting from since I'm reading it from my phone too.

---

### Post by youbuntu on 2010-10-26
Hello :)

I had this issue earlier today. My fix was to reboot the machine - give that a try? 

**Best.**

---

### Post by Sergtek on 2010-10-27
I had the same problem and reinstalled udisks in Synaptic.

The command below will do the same:

sudo apt-get install udisks libgdu0 gnome-disk-utility policykit-desktop-privileges --reinstall

Hope that helps.

---

### Post by vipuh on 2010-12-14
FYI...I am running fedora 14 i686 (PAE) on one of my machines and ran into this same issue then came across this thread by google search. I installed the udisks-devel package and it resolved my problem.

---

### Post by scinziatu on 2010-12-15
I had the same problem after using GParted.
I solved launching from a terminal:
[INDENT]    sudo killall udisks[/INDENT]

---

### Post by MGPB1936 on 2010-12-19
I have been trying for sometime to load 10.10 netbook to an Acer AOA 150ab netbook from a USB flash stick without any success.
When selecting Install it just hangs. In have tried to reformat my 120gb drive and I get 'Daemon Is Inhibited'.
Can anyone help please?
Richard

---

### Post by wyth on 2011-01-06
> **scinziatu said:**
> I had the same problem after using GParted.
I solved launching from a terminal:
[INDENT]    sudo killall udisks[/INDENT]

Brilliant, cheers.

I can now sync my podcasts and walk my dogs. The beagles thank you.

---

### Post by maya123ca on 2011-02-01
Thanks scinziatu. I spent a couple of hours working on this problem until I came across your post. Incidentally, I have now given up on gparted. In the process of researching the problem, I discovered Palimpsest Disk Utility (gnome-disk-utility) which performs all the functions that gparted sometimes does. Just run "sudo palimpsest" at the prompt and go to work on your partitions.

---

### Post by lewisskinner on 2011-02-15
had the same problem myself, performed a google search and found this thread.

Then decided to try the following:

In terminal:

sudo umount /dev/sdg1*

worked a charm.  I can now load gparted and format my sdg USB drive

*obviously, check first which disk you want to unmount.  Gparted is your friend ):P

---

### Post by adduds on 2011-02-23
> **scinziatu said:**
> I had the same problem after using GParted.
I solved launching from a terminal:
[INDENT]    sudo killall udisks[/INDENT]

huge buddy i was tryin to format my new laptops hd from live ubuntu 10.10 kept getting that error n i really wanna get my partitions set up so i can play with my new lappy lol thanks much mate

---

### Post by cmcanulty on 2011-03-20
Wow I have had mount problems for years with ubuntu and that actually worked as opposed to the other 99 things I have tried, thanks!!!

---

### Post by parsim on 2011-03-25
I got this message when running Disk Utility and GParted at the same time. Simply closing GParted fixed it, and allowed Disk Utility to work as normal.

---

### Post by kellemes on 2011-06-13
> **scinziatu said:**
> I had the same problem after using GParted.
I solved launching from a terminal:
[INDENT]    sudo killall udisks[/INDENT]

Just one post but of fine quality.. :popcorn:

Have this quite often with flash drives for some reason..

---

### Post by earlf on 2011-06-23
@parsim
thanks for the tip; I was able to mount the drive. 

I had this issue when booting off of a 10.10 LiveCD. The error came when attempting to mount an external drive.

---

### Post by omegaFil on 2011-07-02
> **scinziatu said:**
> I had the same problem after using GParted.
I solved launching from a terminal:
[INDENT]    sudo killall udisks[/INDENT]

+1

Solved.

---

### Post by tin22ooo on 2011-08-11
> **scinziatu said:**
> I had the same problem after using GParted.
I solved launching from a terminal:
[INDENT]    sudo killall udisks[/INDENT]

thanks a lot ! It did the job for me too.

---

### Post by Daniil_xXx on 2011-09-14
killall helped me as well :)

---

### Post by Bucic on 2011-09-16
I get
```
sudo killall udisks
[sudo] password for *****: 
udisks: no process found

```

---

### Post by Th3Blaze on 2011-09-18
For any formatting problem you have, copy the files somewhere else, format it and then put them back on. Usually format them FAT 32

---

### Post by Bucic on 2011-09-18
IMO this topic should not be marked as solved. I tried 3 ubuntu versions in total and on neither of them the tool worked (checking fs errors).

---

### Post by livinglou on 2011-10-02
> **scinziatu said:**
> I had the same problem after using GParted.
I solved launching from a terminal:[INDENT]    sudo killall udisks[/INDENT]
I love linux!! Thank you for this tip. It recovered my 16GB flash drive that only showed 1GB. After killing it I had to unmount it and delete the partitions. I then formatted the 16 GB with Fat. It is completely restored. Thank you!!!!:KS:KS:KS

---

### Post by tredsyn on 2011-10-10
> **earlf said:**
> I had this issue when booting off of a 10.10 LiveCD. The error came when attempting to mount an external drive.

> **parsim said:**
> I got this message when running Disk Utility and GParted at the same time. Simply closing GParted fixed it, and allowed Disk Utility to work as normal.

I just used gparted to fix my partitions.I tried mounting an external harddrive (ntfs) and that's the time I got this error "daemon is inhibited". Tired of rebooting the PC(about 20x for the last 9 hrs), I just browsed the forums to check the easiest way to get rid of the error. This ---> "Simply closing GParted fixed it". I guess the command "sudo killall udisks" closes ALL disk utility applications :)

---

### Post by blindox on 2011-10-17
+1 Solved ! Thanks for the tip!

---

### Post by cmcanulty on 2011-10-17
The nice thing it will work also if you ever inadvertantly remove a drive without unmounting. Just run script and it reappears

---

### Post by ganjan on 2011-11-09
what is happening i have a 160gb ide seagate out of a sky + box and it was saying sdb1 or somthing i couldant mount or delete it it is now no longer there but still powered on ide slot 2 i believe  as master and a 1tb usb seagate freeaget go flex and I get in the /dev/sdb location in disk utility saying:

error formating drive

an error occurred while performing an operation "1tb hard disk" (seagate goflex)the operation failed

Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No such device or address
close

1408 firmware seagate 1tb usb "sata"!!!! this drive crashed my windows pci raid card computer when i tried it then came up as a disk  with microsoft driver and was not in my computer

i would like to get this working the 1tb is coming up as HPFS/NTFS (oxo7)volumes unknown partitioning unknown scheme flags bootable 5000RPM 

error creating file system Daemon is inhibited
unrecognized 

smart status not supported Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1f.2/usb1/1-2)

     re:Code: that i get to

     sudo killall udisks [sudo] password for ganja951: *c*gamertagonxbox*c* udisks: no process found

ubuntu on x86 kernal version 11.04 thinking of updating to 12 you all should maby cheack it out

---

### Post by thesappho on 2011-11-18
> **scinziatu said:**
> I had the same problem after using GParted.
I solved launching from a terminal:
[INDENT]    sudo killall udisks[/INDENT]

Thanks, saved my reboot :)

---

### Post by jimbo99 on 2011-12-28
This is not a resolved thread.  The original poster never indicated his problem was solved.  Though this is a 14 months old it was inappropriate to mark it solved, primarily due to the fact that others are searching Google and finding this thread marked solved.  Some people have solved their problems.  The original poster did not indicate their issue was resolved nor how to do it.

---

### Post by jackharvest on 2012-01-11
> **scinziatu said:**
> i had the same problem after using gparted.
I solved launching from a terminal:
[indent]    sudo killall udisks[/indent]

thank you!

---

### Post by Dlambert on 2012-04-24
Thank you so much!

---

### Post by abilashgt on 2013-03-30
it worked... thanks

---

