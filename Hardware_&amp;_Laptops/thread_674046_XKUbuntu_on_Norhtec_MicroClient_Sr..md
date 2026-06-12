---
title: "X/K/Ubuntu on Norhtec MicroClient Sr.?"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by gdinsdale on 2008-01-21
Hi,

I have ordered one of [these MicroClient Sr.]("http://www.norhtec.com/products/mcsr/index.html") SFF PCs from Norhtec in Thailand. I should get it in approximately 2 weeks. The MicroClient Sr. is an uprated version of the [MicroClient Jr.]("http://www.norhtec.com/products/mcjr/index.html") that has been available for a few years now.

The MicroClient Sr. has a 500Mhz[ ULV VIA EDEN]("http://www.via.com.tw/en/products/processors/eden_ulv/") processor and 512MB of RAM.

Can anyone hazard a guess as to whether this will be able to run Ubuntu, Kubuntu or Xubuntu? My preference is for Ubuntu or Xubuntu but any would be fine. If not which lighter weight distro would you recommend?

Thanks,

Graham

---

### Post by gdinsdale on 2008-01-23
bump

---

### Post by Tsega on 2008-02-02
Hey gdinsdale, it's not much but I think I got something some how related to what you are looking for. It's here [http://linuxdevices.com/articles/AT4708024578.html](http://linuxdevices.com/articles/AT4708024578.html). I t may not be about the MicroClient Sr. but its about a closely related product the  eBox 4300  so check it out! Hope it helps.

---

### Post by gdinsdale on 2008-02-04
Thanks Tsega, very interesting article there. My Norhtec MicroClient Sr. is equivalent to the eBox 4300 as you say, so it looks like Xubuntu should be feasible.

I think mine should be delivered late this week/early next week so I will post back with info on how I get on. Might even take some pics... ;-)

I've also started a blog to document the process -> [Adventures with the Norhtec MicroClient]("http://microclient.wordpress.com")

---

### Post by Tsega on 2008-02-04
Good to see it helped! I am also quite interested in getting one of those but I need to know if they work with X/K/Ubuntu so it would be great if you could post back on that along with the pics.

---

### Post by gdinsdale on 2008-02-05
Yeah I'll post back and keep you updated. I'll make sure I take plenty of pictures. :-)

---

### Post by aventrax on 2008-02-07
Hi, I've ordered from thailandia too. 252$ with shipping, not bad. I'll make a small samba/mail/mp3 server and a download client. I've considered a small openwrt router (nslu2 or wl500g) to do this but for mp3 serving was too slow. This Via clocked at 500mhz with 512mb of ddr should be enough for my goals. 

What linux distro? I'm not new to embedded devices, so I'll use the compact flash for a stripped (by me) version of debian, running in a read-only root, with /tmp and /var mounted into ram. In this way I can preserve my CF from write cycles that are not good for it. I'll made my own CF system using an external card reader and my linux desktop, but I want try PXE booting too! :p


Now its time to wait ....


Bye

---

### Post by aventrax on 2008-02-12
Ok, our Microclient is coming in 2 weeks, as the nortec helpdesk said to gdinsdale. Now I've finished my own debian etch, my goal was to fit it into a 32MB CF card and its done using cloop kernel module, a 2.6.24 kernel and an initrd maded from scratch. In details, my root fs uncompressed was 58MB, using cloop utils I can obtain a 24MB cloop image; my kernel is 1.3MB and my gzipped initrd is 1.5MB, so I'm using 26.8MB!!!! My distro has only standard utility, a text editor and samba daemon, but I have ~5MB (should be ~ 15MB unzipped) of free space to put mldonkey and firefly server. It's also simply to maintain because kernel+initrd remains the same and I can modify my system unzipping and mounting the cloop-ed root filesystem, then chrooting into it, then unmounting and re-compressing it. I can boot from USBPEN too without big modifications. Obviously I'm going to use an external usb hard disks for my files. Yes, I could install a standard debian system on it using an usb cdrom, but I want to separe system and my files ....btw doing this kind of systems is very funny and interesting :-D Surely I'll put my  work online soon.. if anyone is interested ;-)

---

### Post by honeydew on 2008-02-15
I just attempted to install dapper drake lts to 2 microclients and right afterboot it fails and restarts the machine.. It gives no errors even with the quiet flag turned off. If I just leave them on it will just loop forever.. hitting grub then hitting the booting linux kernel thing.. and then restarts.. I am attempting to try debian etch now.

---

