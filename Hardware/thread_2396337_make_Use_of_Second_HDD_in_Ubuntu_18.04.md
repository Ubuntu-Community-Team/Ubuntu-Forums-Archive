---
title: "make Use of Second HDD in Ubuntu 18.04"
date: 2018-07-14
forum: Hardware
---

### Post by sparks79 on 2018-07-14
My System is ASUS H370m-Plus, 16gb Ram, Two Samsung 970 Evo NVME M.2 250gb, Using Onboard Video.
I have Installed Ubuntu 18.04 on One M.2, The Second One is Not Used yet.
I would like to Create a Raid0 Array Using Both M.2's.
I want the Existing Installation of Ubuntu to somehow be Incorporated In the Raid for Speed.
How do I do this.
Any Help would be appreciated.
John

---

### Post by gpaunescu2 on 2018-07-14
To create Raid 0, both SSD should be the same capacity; you have to setup in BIOS the disks in RAID 0. Next you have to reinstall Ubuntu (you loose what do you have on disks).
But, from my experience, the speed difference will not be so big. In tests you will see the difference, but in reality, not too much.
Additionaly, if one of SSD is corupted, you will loose everything in RAID 0. Personally I prefer 2 separated SSD and I install the OS on the fastest one.

---

### Post by sparks79 on 2018-07-14
Thanks for that Info [[COLOR=#000000]gpaunescu2[/COLOR]]("https://ubuntuforums.org/member.php?u=1983615")[COLOR=#000000] .[/COLOR]
[COLOR=#000000]I have Tried Several Times to Setup the Raid0 with Ubuntu Server Install, and have trouble every time.[/COLOR]
[COLOR=#000000]Gee it's a Long Setup Sequence.[/COLOR]
[COLOR=#000000]You really have to know what your doing, and clearly i don't , that,s why failed.[/COLOR]
[COLOR=#000000]It would be good if I could get some good Printable Info in Layman's Language.
[/COLOR]I am Used to Raid0, In Windows,That,s where I come from.
I'm New to Linux, But I don't give up easily.
I have Tried Using These Instructions From [https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04) .
But when I try to continue with it Installing Ubuntu Server, I get Lost in their partitioning part.
And at the end I get an error telling me it couldn't install a Boot loader,or Grub or some strange stuff.
So for now I have Dumped it , Reformatted and Reinstalled Windows 10 in Raid0.
Untll I can get some Concrete Instructions.

---

### Post by gpaunescu2 on 2018-07-14
You welcome.
Unfortunately is long time since I did try RAID 0; and now I not a have a machine to try again (my laptop I need at my daily job).
As I remember I configure the RAID from BIOS and was independent by OS: was seen by OS as single disk. This is the best option because the disk can be accessed by multiple operating systems.
I found this link, might be helpful.
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
But there they configure the RAID using some linux utility; if you do this I don't this you will be able use also in windows.
If you let me to know the exact error that you get, maybe will find a answer.
In the link is stated that have to use separate partition for /boot if created RAID is different than 1, which is your case.

---

### Post by sparks79 on 2018-07-28
Hi All, I got it Working.
It has taken me Months and Hours of Time.
But I recently found some good info , can't find it right now, but it works.
In essence it is relatively easy, but takes some time.
Basically what I did was Install Ubuntu 18.04.1 Server.
Onto Two SSD's and Created a Raid0 Array.
Then Rebooted into that.
Then ran some terminal commands and converted the server o/s to the desktop version of ubuntu.
I Tuned Ubuntu to the way I like it Then Cloned it to My Two NVME HDD's.
I did that from a Live CD of Clonezilla, One Drive at a Time.
Removed my two ssd's and bingo it Booted from the NVME Array.
And it is FAST, 
I am getting 2700/mb/s out of the array.
It is so Fast I had to Use a Rope to tie it down to the desk/ ha/ha/ha.
So if anyone would like anymore advise on doing this, I am only to happy to help out.

---

