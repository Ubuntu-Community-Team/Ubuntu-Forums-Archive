---
title: "Having some troubles with a hard drive enclosure"
date: 2008-06-25
forum: Hardware
---

### Post by arberb on 2008-06-25
Having some troubles with a hard drive enclosure.
I have a 2.5 hard drive inside a hard drive enclosure case and when every i plug it in via usb it shows up as cannot mount drive. Why is this happening and how could i fix.

---

### Post by eldragon on 2008-06-25
first off.

is it externally powered? if it is, then that might be your problem

if its usb powered, these drives come with a 2 port wire, in order to get the needed juice out of your usb ports. some computers can provide the power through 1 port only, others cant. try plugging both connectors.


now last but not least. has your hdd been formatted? how?

---

### Post by arberb on 2008-06-25
i formated it when i was using windows. yes i use both usb ports.

---

### Post by eldragon on 2008-06-26
> **arberb said:**
> i formated it when i was using windows. yes i use both usb ports.

well, you probably formatted to ntfs.

all i can think of is to check if you have ntfs-3g installed and configured

i dont know much about it since i dont use ntfs :(

maybe someone else can give some help.

if you are going to use this hdd under linux only, id suggest to have it formatted to ext3.

another more convoluted solution would be to:
a) split the drive into 2 partitions. one small partition which should be formatted to fat32 and one big partition formatted to ext3.

in the small fat32 partition, download and save the ext3 drivers for windows from here: [http://www.fs-driver.org/](http://www.fs-driver.org/)

so, if you encounter a windows machine that lacks the ext3 windows driver, you will always have a copy ready to install from :D


otherwise, format the entire drive to fat32. that works seamless under windows and linux.


again, maybe setting up ntfs reading/writing isnt much of an issue now.

serach info on how to setup ntfs-3g to read/write your drive

---

