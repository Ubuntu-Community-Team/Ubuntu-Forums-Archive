---
title: "cannot detect as268l usb lan on xubuntu"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by ghmercado on 2007-05-25
hi i managed to install xubuntu on an ancient p2 laptop (IBM 600e). Everything's ok except it doesn't have a LAN port so I use a USB LAN device to connect to a network. It used to work in Windows as it came with Win drivers.

Here's the /var/log/messages when I plug the USB LAN card in:

May 25 17:35:41 mypc kernel: [10531.231219] usb 1-1: new full speed usb device using uhci_hcd and address 8
May 25 17:35:41 mypc kernel: [10531.417488] usb 1-1: configuration #1 chosen from 1 choice

is there any hope? :( Or do I go back to Win? :(

I searched the net high and low and the only webpage for the USB LAN is this: 
[http://www.made-in-china.com/china-products/productviewTeoQOZKuXmYH/USB-LAN-Card.html](http://www.made-in-china.com/china-products/productviewTeoQOZKuXmYH/USB-LAN-Card.html)

and it's made by this company:
[http://www.made-in-china.com/import-export/CqomRjyDhJYAprofile1/WinWin-indursty-Co-Ltd.html](http://www.made-in-china.com/import-export/CqomRjyDhJYAprofile1/WinWin-indursty-Co-Ltd.html)

finally, i i presume the driver name to be 'as268l' as the folders name is named such on the windows driver cd.

appreciate **ANY** help.

---

### Post by takeawaydave on 2007-05-25
whats the output from running lsusb from term?

---

### Post by ghmercado on 2007-05-26
hi typing in lsusb gave me a clue! This resulted in:

[INDENT]Bus 001 Device 001: ID 0a46:0286 Davicom Semiconductor, Inc.[/INDENT]

So I googled it up and found their [product page]("http://www.davicom.com.tw/eng/products.htm"), which consequently lead me to their [download page]("http://www.davicom.com.tw/eng/download/Driver/driver_9601.htm"). I couldnt find a product named exactly the same, but these Taiwan Products are frequently rebranded and since the 'DM9601' is their only USB LAN product I assume I'm on the right track.

So I downloaded and untarred it onto my /home/user/desktop. The [readme]("http://alcopop.org/unix/linux/dm9601/git/readme.txt") file said I should do 'Make', which I did, resulting in the ff. errors:

[INDENT]ghmercado@mypc:~/dm9601-2.6$ make
make -C /lib/modules/2.6.17-10-server/build M=/home/gary/dm9601-2.6 LDDINCDIR=/home/gary/dm9601-2.6/../include modules
make: *** /lib/modules/2.6.17-10-server/build: No such file or directory.  Stop.
make: *** [default] Error 2[/INDENT]

At some point I'm assuming a file named 'dm9601.ko' is supposed to show up, which again accdg to the readme.txt (ff. the 'for redhat' users instructions, which I wanna try because I seem to have similar folders), I should do the following to:

[INDENT]1.  login your system used the superuser.
2.  copy dm9601.ko into	/lib/modules/2.6.x/kernel/drivers/net/
3.  add the new line with "alias eth0 dm9601" in "/etc/module.conf". 
4.  execute "netconfig -d eth0".
5.  Fill your IP address, netmask and gateway
6.  press <ok> to confirm and exit this setting
7   reboot[/INDENT]

Pls. any help re that Make issue? Thank you!

---

### Post by takeawaydave on 2007-05-26
Make sure you have all the neccesary development tools (i.e. libraries, compilers, headers)

```
sudo aptitude install build-essential
sudo aptitude install linux-headers-`uname -r`

```

and then please try make again.

---

### Post by ghmercado on 2007-05-26
hi thanks so much, here are the results:

```
sudo aptitude install build-essential
```

[INDENT]It asks for the Xubuntu Feisty Fawn CD, which after I insert says "Media Change: Please insert the disc labeled 'Xubuntu 7.04_Feisty Fawn_ + Release i386 (20070415)' in the driver '/cdrom' and press enter[/INDENT]

After I do this the thing just stops and doesnt do anything. Pressing enter retries it but no go. This is the CD I used to install with btw. ALso, I can easily read through the CD via the GUI's File Manager, so the CD is ok. Is there a way I can just move the needed files from the CD? Where are they located in there? I can also use a USB drive btw, I've tried moving files around with it and it works.

```
sudo aptitude install linux-headers-`uname -r`
```

This results in nothing, saying 'No packages will be installed, upgraded or removed'. Does this mean it's already installed?

Many thanks again.

---

### Post by ghmercado on 2007-05-26
hi takeawaydave, to add to this, here is the result when I try 'make' again:


[INDENT]ghmercado@mypc:~/Desktop/dm9601-2.6$ make
make -C /lib/modules/2.6.20-15-generic/build M=/home/ghmercado/Desktop/dm9601-2.6 LDDINCDIR=/home/ghmercado/Desktop/dm9601-2.6/../include modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ghmercado/Desktop/dm9601-2.6/dm9601.o
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:55:26: error: linux/config.h: No such file or directory
In file included from /home/ghmercado/Desktop/dm9601-2.6/dm9601.c:65:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.h:100:1: warning: "ALIGN" redefined
In file included from include/asm/system.h:4,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:46,
                 from /home/ghmercado/Desktop/dm9601-2.6/dm9601.c:56:
include/linux/kernel.h:35:1: warning: this is the location of the previous definition
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;__check_reg5&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:125: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;__check_reg8&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:126: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;__check_reg9&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:127: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;__check_rega&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:128: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;__check_nfloor&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:129: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;get_registers&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:192: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;set_registers&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:230: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;set_register&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:269: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;update_eth_regs_async&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:303: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:317: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:331: warning: passing argument 7 of &#8216;usb_fill_control_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;read_bulk_callback&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:486: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;dm9601_start_xmit&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:605: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;dm9601_open&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:804: warning: passing argument 6 of &#8216;usb_fill_bulk_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:813: warning: passing argument 6 of &#8216;usb_fill_int_urb&#8217; from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function &#8216;dm9601_disconnect&#8217;:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:1017: warning: ISO C90 forbids mixed declarations and code
make[2]: *** [/home/ghmercado/Desktop/dm9601-2.6/dm9601.o] Error 1
make[1]: *** [_module_/home/ghmercado/Desktop/dm9601-2.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2[/INDENT]

---

### Post by takeawaydave on 2007-05-26
At least on my machine - I can the following:

1. insert ubuntu cdrom
2 then prompts me that the cd contains install packages
3 synaptic package manager then starts
4 search in synaptic for build-essentials

then all you need to do is select build-essentials and install

---

### Post by takeawaydave on 2007-05-26
yes I get the same error when I try make. ;)

Also have a read of:

[http://www.linuxquestions.org/questions/showthread.php?t=547397](http://www.linuxquestions.org/questions/showthread.php?t=547397)

---

### Post by ghmercado on 2007-05-27
Hi I managed to install the build essentials and linux headers packages you mentioned using synaptics.

```
ghmercado@mypc:~/Desktop/dm9601-2.6$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

```
ghmercado@mypc:~/Desktop/dm9601-2.6$ sudo aptitude install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

But I still get errors when doing 'make' :

```
ghmercado@mypc:~/Desktop/dm9601-2.6$ make
make -C /lib/modules/2.6.20-15-generic/build M=/home/ghmercado/Desktop/dm9601-2.6 LDDINCDIR=/home/ghmercado/Desktop/dm9601-2.6/../include modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/ghmercado/Desktop/dm9601-2.6/dm9601.o
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:55:26: error: linux/config.h: No such file or directory
In file included from /home/ghmercado/Desktop/dm9601-2.6/dm9601.c:65:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.h:100:1: warning: "ALIGN" redefined
In file included from include/asm/system.h:4,
                 from include/asm/processor.h:18,
                 from include/asm/thread_info.h:16,
                 from include/linux/thread_info.h:21,
                 from include/linux/preempt.h:9,
                 from include/linux/spinlock.h:49,
                 from include/linux/capability.h:45,
                 from include/linux/sched.h:46,
                 from /home/ghmercado/Desktop/dm9601-2.6/dm9601.c:56:
include/linux/kernel.h:35:1: warning: this is the location of the previous definition
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘__check_reg5’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:125: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘__check_reg8’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:126: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘__check_reg9’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:127: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘__check_rega’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:128: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘__check_nfloor’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:129: warning: return from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘get_registers’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:192: warning: passing argument 7 of ‘usb_fill_control_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘set_registers’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:230: warning: passing argument 7 of ‘usb_fill_control_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘set_register’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:269: warning: passing argument 7 of ‘usb_fill_control_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘update_eth_regs_async’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:303: warning: passing argument 7 of ‘usb_fill_control_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:317: warning: passing argument 7 of ‘usb_fill_control_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:331: warning: passing argument 7 of ‘usb_fill_control_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘read_bulk_callback’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:486: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘dm9601_start_xmit’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:605: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘dm9601_open’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:804: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:813: warning: passing argument 6 of ‘usb_fill_int_urb’ from incompatible pointer type
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c: In function ‘dm9601_disconnect’:
/home/ghmercado/Desktop/dm9601-2.6/dm9601.c:1017: warning: ISO C90 forbids mixed declarations and code
make[2]: *** [/home/ghmercado/Desktop/dm9601-2.6/dm9601.o] Error 1
make[1]: *** [_module_/home/ghmercado/Desktop/dm9601-2.6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
```

I really dont know what to do now. I've been following this thread:

[http://ubuntuforums.org/showthread.php?p=2728759#post2728759](http://ubuntuforums.org/showthread.php?p=2728759#post2728759)

but I got lost when he copied the '**dm9601.ko**' file into **/lib/modules/2.6.17-10-generic/dm9601** (a directory he created). I don't have that mystical dm9601.ko file. 

The poster [COBRN1]("http://ubuntuforums.org/member.php?u=258953") linked to this site:

[http://alcopop.org/unix/linux/dm9601/](http://alcopop.org/unix/linux/dm9601/)

but unfortunately there is no **dm9601.ko** either. Just a repository for the contents of the **dm9601.gz** file which i have already. I cant find that dm9601.ko anywhere else on the net. I swear if I ever get it I'll post it on my blog to help future poor sobs like me. ](*,)

Am I missing a step? Help please?

---

### Post by takeawaydave on 2007-05-27
Maybe the easiest way here is to try and get a copy of the dm9601.ko . try:

[http://ubuntuforums.org/showthread.php?t=389330&highlight=dm9601.ko]("http://ubuntuforums.org/showthread.php?t=389330&highlight=dm9601.ko")

---

### Post by ghmercado on 2007-05-27
hi takeaway dave. If you'll notice I had already left a message at the bottom most part of the thread you mentioned. I've even private messaged the person who started the post. The hunt for the elusive dm9601.ko file continues.

---

### Post by Vouno on 2007-07-27
Hi all,

i've had your same problem, but i finally managed to compile the driver.

I'm using Debian Etch stable with kernel 2.6.18-4-686

If someone need the dm9601.ko i can send it.

Now the problem:
after insmod the module and after plugin the usblan adapter, the adapter simpy don't work.
I set (as the readme says) 
1. login your system used the superuser.
2. copy dm9601.ko into /lib/modules/2.6.x/kernel/drivers/net/
3. add the new line with "alias eth0 dm9601" in "/etc/module.conf".
    (i used eth1 'cause the eth0 is the internal lan adapter)

Doing an lsmod i see that module is used by 0.

Trying to "ifup eth1" it say there is no eth1.

What can i do now ?

Thanks

---

