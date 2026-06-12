---
title: "Ubuntu 11.04 FakeRaid P8H67 partion error"
date: 2011-05-15
forum: Hardware
---

### Post by Zeggi on 2011-05-15
I have been playing around with my new NAS setup and been testing with,  ubuntu 11.04, suse, freenas, xubuntu... well a few distro.

My setup,
ASUS P8H67-M PRO B3
Corsair XMS3 Vengeance 16GB DDR3 PC3-12800 1600MHz
Intel Core i3-2100T 2,5Ghz
Lian Li PC-V354B

with 6hdd, WD20EARS runing at raid5, fakeraid setup by mobo, intel RST.
OS on usb2.0 hdd

The issue im having is that i can't partition the raid array.
in the bios for the fakeraid i see all drives in the array but they are  in a initializing state, which means i have to finish the initializing  setup in what ever os i will run, but i don't know how its done in  ubuntu.

I gave a go with windows 7 and intel has the RST application that lets  the array to continue, what it does is a resync and rebuild.

In ubuntu i can see the array but i cant format it, i use disk utility  in ubuntu and when i try to format the drive as MBR, GPT or Not  partioned i get a error. But the difference is that i can still create a  partion on the array IF i choose the option "not partioned" which  sounds wrong to me.

Anyway i manage to create a ext4 volume on the array but the array is marked as "no partion" by looking at properties of the volume it states 9tb ext3/ext5 while 550gb is used so i get about 8.5tb that i can use and i can mount the drive but with no partition table. at reboot i still see intel bios state that the discs are initializing with a note in bios stating "continue this step in OS" sure but how do i continue the step? 

In windows it works cause i have Intel RST that rebuilds/resync the array.

So my question is what is wrong and how do i get the array fully  functional, i want the array to be stated as "normal" in intel bios not  initilizing, which i can but only running windows, and i really don't  want that mainly because its windows but also with linux distro i can  use all 6 hdds and have the OS on a usb drive.

this is also something i found on intels site,
[http://www.intel.com/support/chipset.../cs-020663.htm]("http://www.intel.com/support/chipsets/imsm/sb/cs-020663.htm")

so what i need mdadm? isn't that only for software raid?

---

### Post by Zeggi on 2011-05-19
gave up on Fakeraid since it doesn't work unless i dualboot and run ntfs.
mdadm FTW! :)

---

