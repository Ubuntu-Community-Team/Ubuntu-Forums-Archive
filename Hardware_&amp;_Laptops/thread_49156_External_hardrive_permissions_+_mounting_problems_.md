---
title: "External hardrive: permissions + mounting problems in kde and gnome"
date: 2005-07-15
forum: Hardware &amp; Laptops
---

### Post by exiledsoul on 2005-07-15
Hello, newbie here ...

First I want to say that I'm really enjoying Ubuntu right now :)
I installed Ubuntu, then added the Kubuntu Package, so I use both
no windows installed either
I bought and external hard drive (maxtor, 100gb)
I have 2 problems with the hard drive though:

1. 
KDE and gnome don't mount it the same way
KDE recognises it as .../media/sd1
and Gnome: .../media/usbdsk 

it can be a problem when I use amarok and nicotine. I can't change the settings everytime i switch.
can something be done, or it's impossible?

2.
when I first installed it, the system recognised the hard drive. it was automatically mounted
So I was able to transfer, move, delete files, etc. as I wished. there was no problems at all.
all of a sudden this stopped
I don't know why, but once I touch certain  specific folders or files (mp3s) the permissions change. I can't modify these files at all
for example there's a trash folder in the ext. hard drive, once I try to clear it. I am blocked from modifying anything else in the hard drive.
I have to switch the hdd off and on again to be able to transfer again. there are other folders I'd like to delete and I can't :(
I am the sole user on this computer, so I'm supposed to have all powers.

Please help. this is really bothering me :(

thanks

---

### Post by thunderduck3141 on 2006-04-12
for the whole switching amorok thing, its a LOT of trouble to force something to mount in a specific place if u don't know how to do it (requires a fairly high amount of  linux skillz in the command line, a good book is "A Practical Guide to Linux Commands, Editors, and Shell Programing")
as for the second problem, become root or find out who "owns" the file, become them, and moddify the permissions
if u dont have valuable stuff on the drive wipe it, and try setting it up as root
hope that helps

---

### Post by aysiu on 2006-04-13
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

It'll probably be /dev/sda1 instead of /dev/hda1
And it'll probably be FAT16 or FAT32, not NTFS.

---

