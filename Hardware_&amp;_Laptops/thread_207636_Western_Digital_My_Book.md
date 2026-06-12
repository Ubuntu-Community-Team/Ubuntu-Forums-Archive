---
title: "Western Digital My Book"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by Bloch on 2006-07-02
I need to buy an external hard drive.
Does anyone know if the Western Digital 160GB My Book is linux-compatible?
I don't have a huge choice of external hard drives locally. One other choice is a Seagate 160GB external hard drive.

Are external hard drives pretty much covered as much as internal hard drives in linux - i.e. they are pretty much all compatible??

---

### Post by zool2005 on 2006-10-13
> **Bloch said:**
> I need to buy an external hard drive.
Does anyone know if the Western Digital 160GB My Book is linux-compatible?
I don't have a huge choice of external hard drives locally. One other choice is a Seagate 160GB external hard drive.

Are external hard drives pretty much covered as much as internal hard drives in linux - i.e. they are pretty much all compatible??

I noticed on their website that software is installed on first use but I'm waiting for a reply from WD to see if linux is supported.

I was hoping to purchase one for myself but from what I have seen from googling/forums/IRC, there have been mixed responses.

---

### Post by chikko on 2007-02-08
i just bought a 500gb my book, and it;s working just fine via USB (didn't get to check the firewire yet).
two things are missing because there's no software for linux:  no capacity led, no power button.
non of which are extremely needed..

---

### Post by scrambledhelix on 2007-04-24
I've had my eye on this one too, ever since it showed up at my campus's bookstore.  I wouldn't be too concerned about the lack of software though; from what i've been reading elsewhere, it's not only linux they don't support, it's everyone.  gotta love the bare-bones approach.

---

### Post by HawaiinShirts4Life on 2007-06-28
i have a 250 gb mybook and it works fine in linux under my tower maching (its a frankensteind i couldnt tell ya all the parts that go into it) but on my laptop it works sometimes, and other times not at all which i think has more to do with  my usb drivers than the actual hdd (i have an acer aspire 1800)
which i have issues loading it in windows too till i get all the specialty drivers loaded for the laptop then it works fine

not sure if that helped or not but hey its my experience that ive had

---

### Post by AshtonBRSC on 2007-12-28
On my computer the drive wasn't recognised on one USB port but was fine on another.

---

### Post by LauraSakura on 2007-12-28
It works fine on both of my computers. I use it on my XP Desktop, Ubuntu Desktop, and Ubuntu laptop with no issues. Mine is the USB version, so if the one you are looking at is firewire i dont know about that. Mine isnt the fancy one with capacity meters or anything. I don't have any issues with it though, works fine, I was able to partition it up fine with gparted :)

---

### Post by brc816 on 2008-01-01
I have a 250GB My Book that I bought about a year ago, hoping to do a full install of Linux on it.
My current laptop is an HP dv9000z, which has two 80GB SATA drives. One runs Windows XP
Media Edition, the other has openSUSE 10.2 on it. Grub is installed on the MBR of the first disk,
and I've been able to dual-boot successfully for 11 months.

The BIOS does have support for USB booting, and indeed I'm able to install Fedora 8 on it,
although I have to do some handstands to get it to start booting properly - i.e., I had to do a
'mkinitrd' with a quartet of "preload=" stanzas to get the right modules into the initrd file. After
that, it would actually start to boot. (Yes, sorting out who is hd0 or sdc at any given point
in time was, um, interesting, but I worked through that issue successfully with no damage).

But, the REAL problem is that the bloody drive times out after a short while, meaning right in
 the middle of booting! I was about ready to give up on Fedora 8 and try (k)ubuntu when I read
a couple of threads in here that cast substantial doubt about installing Gutsy (Gibbon) on an
HP dv9000 laptop, never mind on a USB disk connected to one.

I can/do tolerate the loss of some functionality when using Linux, e.g., the webcam and
microphone, and I successfully set up ndiswrapper under openSUSE, so wireless networking
works fine.

But has anyone successfully tamed a WD MyBook USB drive so that it will stay awake? (I realize
that the original design intent was to save power and noise and have the drive go to sleep, and
I know some folks have the opposite problem wherein they want to explicity shut it down). But
it just seems real strange to me that I can perform a full-blown installation to it that takes 10-20
minutes, but it won't stay up long enough during boot-up to initialize the driver!

TIA

---

### Post by MaX on 2008-02-09
You are not supposed to install an OS on the WD My Book HDD's

---

### Post by sodmkavc on 2008-02-13
I've just bought My Book Essential Edition 500GB and I have problems mounting it. It wouldn't mount automatically on startup, but if I disconnect it and connect it again then it mounts and is working without any problems.

Any thoughts?

---

### Post by ST.x on 2008-02-13
I just got the my book home 500GB with usb2, firewire, esata support but im trying usb2 at the moment and it connects but disconnects after a bit, just automatically and I haven't put anything on it yet. I get the ubuntu message about unmounting it properly and such even when I havent tried to unmount it myself.

---

### Post by lepus87 on 2008-02-14
I have the same problem as ST.x and a couple of others on this thread. MyBook seems to power itself up and down randomly, which is a bit disconcerting. With XP it came on when I turned on my lappy, stayed on, and powered down when I shut down the lappy. Any ideas how to make it act in a similar fashion with Ubuntu?

---

### Post by ST.x on 2008-02-14
okay I fixed it by shutting down the pc and connecting the mybook with power and usb then powered on again and now it doesnt go on standby and I can transfer stuff without problems.

---

### Post by MaX on 2008-03-10
I can transfer stuff to it, but it takes forever and I can't read ovie or audio files of of it. Totem just hangs...

---

### Post by chochem on 2008-03-10
I bought a 500 Gb MyBook (version 2) three or four months ago. Since I obviously didn't want any of the included windows/mac utils, I figured I might as well format it and chose to go with NTFS (in order to be able to have Windows computers read it without having to install special tools). Haven't had any issues of the kind reported in this thread. Maybe it's a FAT32 thing? Else, have you tried adding the drive to your fstab? That has worked to stabilise things for me with other drives.

---

### Post by jmate24 on 2008-03-10
unplug it when you shut down your laptop/computer then after you start your computer and login plug it in. i have an IDE to USB connecter that can make any IDE HDD into an external USB drive. but for laptop HDD i have to use a power adapter to supply power to the HDD.  Those My Books are a tech's Nightmare! ](*,)

---

### Post by ninjashby on 2008-03-12
I am having a problem (first problem with ubuntu so far... ) with a western digital mybook. It is a 500GB capacity one, similar to the ones described in this topic. 

It will not mount, and i get the error message:

"unable to mount the volume mybook
mount: wrong fs type, bad option, bad superblock on dev/sdb1, missing codepage or helper program or other error" 

I haven't been able to find any specific drivers using synaptic, and I have a similar problem trying to use a creative zen vision M in "removable disc" mode, and a few other devices.

---

### Post by kevhumphreys on 2008-03-15
I recently bought a 500 GB WD mybook & could get it to mount but all the files and folders were** read [/B[B]]only.** Followed all the previous posts about changing permissions and editing fstab but nothing worked. I looked at another external drive that I have and found out that is formatteed as a logical partition, fat32 and it always mount with permissions.
So I rebooted using the boot disk Gparted - gnome partition editor, and eventually saw the drive listed
as Sda ( check the drive size to be sure).
I deleted the partition and then created two new partitions, an extended fat32 partition and a logical fat 32 partition( both occupying the whole disk). Click ADD, Click apply. Done....takes a few minutes.
Upon rebooting into linux, it is listed in COMPUTER under as a 465.8 GB Disk. Sorry the MY BOOK name disappears but can be recreated if you wish.

---

### Post by jmate24 on 2008-03-17
the problem with fat32 is that it cannot copy long file names. some of my music file names are long or have strange characters and so i use ntfs for all of my drives i also use ntfsconfig to configure my drives. i use synaptic to search and get all of the extensions for partition editor so that i have as much compatibility as possible.

---

### Post by xb3rtx on 2008-03-25
I've got a 1TB MyBook, which I'm trying to set up on my ubuntu system.  On windows, I accessed it by using an ether cable that connected it to the wireless router.  I have it connected the same way, but am not sure if I can access it wirelessly with ubuntu.  Does anyone here have a solution to the problem?

---

### Post by etlpkby on 2008-04-04
I have a 1TB WD "My Book" (Essential Edition).  I am running Ubuntu 8.04 (Hardy) on AMD64.

Have you tried to connect it directly to USB first? Make sure all is 100% before you go further. It comes FAT32 8-[ pre-installed. First thing I did was to copy off the pre-installed software to my internal HDD (SATA) and then whip out "fdisk" and partition it to ext3. :D

Then it's time do.

1. # mke2fs -j /dev/sdc1 (or whatever) - for ext3 formatting

2. # tune2fs -m 1 /dev/sdc1 (to reduce the 5% reserved space for root to 1%)

Current issues I have...

3. The 1TB seems remains mounted but accessing it after (say) 5mins it takes about 10-15s to 'warm up' again. Any hints on whether this is tunable?

4. Sick and tired of Ubuntu assigning random mountpoint i.e. /media/disk-[1..8], as I have 2 external USB2.0 drives and "amaroK" playlist gets buggered if it's a diff mountpoint. So I have /etc/fstab entries:-

[B]/dev/sdb1	/media/1tb	ext3	rw,user,auto,exec,nosuid	0	0
/dev/sdc1	/media/lacie	ext3	rw,user,auto,exec,nosuid	0	0[/B]

But they do not automount when I reboot. Why? If I sudo to root and do "mount /dev/sdc1" all is OK. Any clues?

Patrick

---

### Post by etlpkby on 2008-04-04
Let be just be clear on my previous email...

**Running the "mke2fs" command will completely format and _DESTROY ALL DATA_ on your disk. Only proceed if you are happy with that.**

Basically I do not want FAT32 filesystem on my external drives, as I like to control it (chown, chmod and fsck when appropriate etc), which is not possible with FAT32.

---

### Post by Xanf on 2008-04-17
I've got a WD my book premium 1 TB - USB + Firewire, formatted as NTFS

When I connect it via USB - 9 times out of 10 it says that the drive reported being busy used by some another process or system. So I'm able to only with FORCE option. Then it works.

But if I attach it as Firewire - it shows the UNKNOWN Firewire host in the list of devices and doesn't see the drive itself. :-( (I'm using GUTSY)

---

### Post by chochem on 2008-04-17
> **Xanf said:**
> I've got a WD my book premium 1 TB - USB + Firewire, formatted as NTFS

When I connect it via USB - 9 times out of 10 it says that the drive reported being busy used by some another process or system. So I'm able to only with FORCE option. Then it works.

But if I attach it as Firewire - it shows the UNKNOWN Firewire host in the list of devices and doesn't see the drive itself. :-( (I'm using GUTSY)

I only get that when I forget to unmount it in Windows and then boot into Ubuntu. Do you dualboot?

---

### Post by freejam on 2008-04-27
> **xb3rtx said:**
> I've got a 1TB MyBook, which I'm trying to set up on my ubuntu system.  On windows, I accessed it by using an ether cable that connected it to the wireless router.  I have it connected the same way, but am not sure if I can access it wirelessly with ubuntu.  Does anyone here have a solution to the problem?

xb3 - the MyBook World Edition connects via ethernet as a network device so if you can access your network via Ubuntu you will also get access to the MyBook via Places, Network, workgroup and /PUBLIC.

The major benefit of the World Edition is it doesn't need mounting in Ubuntu - it's plug and play.

---

### Post by corticalaxon on 2008-05-23
I think I have the same problem as some others:

I have a 500 GB WD My Book Essentials Edition, formatted in NTFS. It used to refuse to mount because of NTFS compatibility issues, but apparently I fixed that with the NTFS Config tool. However, when I connect the external drive, it says "You do not have the permissions to mount the volume 'My Book.'"


How do I "get the permission?"

edit: I may not have fixed the NTFS compatibility. So, whenever I connect the drive, once or after disconnecting and reconnecting, it doesn't mount.

How do I fix this?

---

### Post by chochem on 2008-05-24
> **corticalaxon said:**
> How do I "get the permission?"

I remember researching this intensively without much luck. The daemon (service) that does the mounting for you is called 'hal' but I never figured out how to configure it. The daemon that registers connected new hardware is called 'udev' and that one can apparently be configured by socalled 'udev' rules. Basically what you want is a udev rule saying that ordinary users (not just root) are allowed to mount the volume. There is a little tool called 'pysdm' that can help you do that.

---

### Post by corticalaxon on 2008-05-26
Ok. So I got into pysdm, and it recognized the external as sdb, and so i opened the dynamic config for it and clicked new rule. i checked off the characteristics it listed about my external, but I want to be sure I'm putting exactly what needs to be put in the lower boxes.

Which actions do I check, and what do I put?

For example: for "specify owner user" do I just put my username?
What do I put for owner group?
Device file name?
Link for the name?
And how exactly do I type the command for the "users rights?"

Sorry, I'm very much a novice.

---

### Post by peakshysteria on 2008-05-26
> **Bloch said:**
> I need to buy an external hard drive.
Does anyone know if the Western Digital 160GB My Book is linux-compatible?
I don't have a huge choice of external hard drives locally. One other choice is a Seagate 160GB external hard drive.

Are external hard drives pretty much covered as much as internal hard drives in linux - i.e. they are pretty much all compatible??

I have a Western Digital My Book 750 GB. Works like a charm. And there should beno reason for it to not work at your end. Actually I have three internal HDD as well. All Western. And the external is working very smooth on both windows and Ubuntu. Remember to format it as NTFS when you get it. They all come as Fat32. Then enable ntfs-3g and ntfs-config via synaptic and your good to go.

EDIT: [COLOR="Red"]corticalaxon[/COLOR], do you have ntfs-3g enabled?? And do you use the HD both on windows and Ubuntu? Sometimes if the drive wasn't removed properly from windows it will come back with a fault in Ubuntu. Try to mount the disk in windows again and remove it properly. The mount it in Ubuntu and you most likely are good to go again.

---

### Post by corticalaxon on 2008-05-26
I do have ntfs-3g enabled. However, I don't have windows anymore. I'm trying to reinstall it, and i created a partition using the ubuntu live cd, but when in the vista installer i try to activate the partition i made through the command line, the partition i made doesn't show up in the "listpart" list. So I kinda am stuck without it for the time being.

---

### Post by Robsteranium on 2008-05-27
[SIZE="1"]If you are thinking of buying one of these the best deal I've found is PC World selling the 1TB World Edition (i.e. gigabit ethernet version) for £149 at the moment!  I don't know if this tip is of use to anyone outside of the UK![/SIZE]

Since the Western Digital website suggests that their Access Anywhere software doesn't officially support osx and linux (despite having linux inside the machine) I thought I'd check on here before buying.  :wink:

Judging by Freejam's post it sounds like I won't have any problems connecting via Samba.  It remains to be seen whether this will work from the other side of my router!

Just in case I don't find myself back on the thread I thought I'd share this link with you...

[Hacking Western Digital MyBook World Edition]("http://martin.hinner.info/mybook/")

---

### Post by Psykotik on 2008-06-22
Since so many people own a WD My book hard disk, could you confirm you're experimenting the same bug as I, regarding the [My book's (unmount) shut down]("https://bugs.launchpad.net/ubuntu/+bug/241927")? The hd is supposed to power off when unmounted (at least, it works in this way on Windows), but it don't.

---

