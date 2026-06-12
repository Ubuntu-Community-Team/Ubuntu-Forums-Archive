---
title: "linux ubuntu doubts"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by arai on 2006-02-02
i have winxp pro (ntfs 80 gb = 40 + 20 + 20 gb ). i have a 20 gb partition free (ntfs) and i would like to install linux (ubuntu downloaded via torrent). 

the problem is linux needs a fat32 but i have complete ntfs. i could atmost change a partition (20 gb) from ntfs to vfat. but will this help in installing ubuntu. I ask this becoz i tried to install redhat in it but could not install.

any solution for this problem ?

i earlier used linux (redhat & mandrake) but discontinued due to the reason that i couldnot connect to the net. 

is connecting to the internet easy using ubuntu linux?

my most important reason for opting linux is security as windows is found to be unsecure mostly. is linux stable ?

pls clarify. thanks in advance. :)

---

### Post by jumiclads on 2006-02-02
I installed on my 1st laptop which wasnt partitioned which was all ntfs and had no problem creating a new partition. Abuntu installed perfectly and connected to the net automatically, not sure about stability as new to this aswell.

---

### Post by darth_vector on 2006-02-02
you dont need to have a fat partition. the best thing would be to delete the partition and create new ext3 partitions.

---

### Post by CompShrink on 2006-02-02
Those are very vauge and hard (...impossible...) questions to answer propperly.

Linux is not stable. Neither is Windows XP. It's arguable which is more stable. The most common opinion seems to be linux needs more effort set things up propperly (if you want to add anything on top of the software included on installation) than windows, but after that it's more stable. This is not everyone's view. It's a matter of opinion.

As for stable as in virus and spyware/adware, there are no wild virus/trojan or adware/spyware on linux.

Linux can read NTFS, and with some extra programs write to it, but NOT SAFELY. Linux can safely read and write FAT32.

But linux doesn't get installed on FAT32! There are a few exceptions, but Ubuntu is not one of them. Linux has it's own file systems. And windows can't read these, by the way, so many people who run both linux and windows on one computer set up a 3 (or more) partition system. Windows is installed on NTFS, Linux on it's file system, and a FAT32 for them to share files.

As for connecting to the internet, what do you use? Dial-up, cable modem, DSL? Do you use a router or not? In windows, do you sign in to broadband/dial-up, or is it litterally always on, without entering a password ever, or running any log-on software? Ubuntu isn't too hard to get online usually, but it depends.

Also, wired internet, or wireless? Or both?

---

### Post by arai on 2006-02-02
i use adsl modem (no login = may be automatic) 380 kbps line. yes its an always on while i use windows.

---

### Post by nickpaton on 2006-02-02
I had the same doubts (and situation) as yourself, and found the following useful for partitioning and set up:

[http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/](http://www.crhc.uiuc.edu/~mjmille2/howtos/dual-boot-linux-and-windows/)

Also for laptop-specific information try:

[http://www.linux-on-laptops.com/](http://www.linux-on-laptops.com/)

Hope that helps.

---

### Post by arai on 2006-02-03
i installed ubuntu. for partition i used 10 gb fat32 and (automatic partition for linux by ubuntu). installation was nice and simple. 

now i have this problem. i am able to open firefox but unable to browse the sites. 

i use UTStarcom ADSL modem (384 kbps).

thanks in advance. i am excited having installed linux but couldnt surf the net. pls help. thanks. :-D

---

### Post by arai on 2006-02-03
Yes i think there is a router (think so).

---

### Post by Haegin on 2006-02-03
If you have a router you should just be able to tell the router how to connect to the internet (using either a web based config utility accessible through the ip of the router or using telnet - check your documentation you got with the router).
After the router is set up you can just plug a network cable between the pc and the router and then tell linux to use DHCP (if your router is set up to use DHCP) or a static IP address (the gateway IP is the IP of the router and the DNS server should either be set by the router or you can use 212.74.112.66 (tiscali uk primary dns - if you are not in UK then try and find another DNS server from your ISP). DHCP is much easier...
If you don't have a router then it may be slightly harder but I would start by looking at Gnome-PPP ([http://www.gnome-ppp.org]("http://www.gnome-ppp.org")) which is a tool to configure modems for dial up and broadband access without a router.

Hope this helps

---

### Post by arai on 2006-02-03
hi human prototype,

thanks for the reply. to simplify things i noted down and did some things. 

1. went to applications >> system tools >> network tools >> devices >> under network devices >> there is a dropdown 1. loopback interface (lo) 2. ethernet . the second one is the one that shud be selected. i selected the second one, pinged some sites like google.com, yahoo.com and my own ip address. it pinged perfect. so i closed and tried to connect. but it is not. one more thing. when i returned to network tools >> devices >> network device >> again i see loopback interface (lo) which shud not be there. and instead ethernet shud be there. 

any idea? i think i may very near to connecting but not able to. i hope somebody  helps.

---

### Post by gosh on 2006-02-03
How is your computer connect to the modem?

---

### Post by arai on 2006-02-03
via adsl router. adsl router working fine. i pinged yahoo and google works well. but no connection. i dont know how to solve this.

---

### Post by arai on 2006-02-03
1. went to applications >> system tools >> network tools >> devices >> under network devices >> there is a dropdown 1. loopback interface (lo) 2. ethernet . the second one is the one that shud be selected. i selected the second one, pinged some sites like google.com, yahoo.com and my own ip address. it pinged perfect. so i closed and tried to connect. but it is not. one more thing. when i returned to network tools >> devices >> network device >> again i see loopback interface (lo) which shud not be there. and instead ethernet shud be there.

adsl modem ut300r2 from utstar . ppoe configured correctly. lights glowing perfect.

this is my problem. pls help me in connecting to the net.

---

