---
title: "Ubuntu 9.04 Installation-Help"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by Infinity_RS on 2009-07-15
Hello everyone,I'm new to Linux so I must ask you to help me..
This is my question:
I have recently installed Windows 7 RC on my computer,and I split my HDD(250GB) in 3 partitions,two of that partitions are 50GB each,and the third one is about 135GB...
On first 50GB(C: ) partition I installed Windows 7,and now I want you to tell me how do I install Ubuntu on The second 50GB(D: ) partition,I'm not good with Ubuntu partitioner and I don't want to mess up other partitions i made..I want to use third 135GB(E: ) partition for Data Storage..

So can you please explain me how do I install Ubuntu on already made 50GB partition?

Here is the picture,i already renamed partitions,i just need to install Ubuntu..

[IMG]http://www.dodaj.rs/f/Y/t2/3zqy2mO1/partitions.jpg[/IMG]

---

### Post by dstew on 2009-07-15
You would install it as usual, using the Live CD, but when you get to Step 4 of 7 "Prepare Disk Space", select **Specify partitions manually (advanced)**. You can then tell the installer to use the partition you set aside for Ubuntu.

You might want to create a small 1 Gb partition to use as swap, but it is not absolutely necessary for an Ubuntu installation.

---

### Post by shicy on 2009-07-15
> **Infinity_RS said:**
> Hello everyone,I'm new to Linux so I must ask you to help me..
This is my question:
I have recently installed Windows 7 RC on my computer,and I split my HDD(250GB) in 3 partitions,two of that partitions are 50GB each,and the third one is about 135GB...
On first 50GB(C: ) partition I installed Windows 7,and now I want you to tell me how do I install Ubuntu on The second 50GB(D: ) partition,I'm not good with Ubuntu partitioner and I don't want to mess up other partitions i made..I want to use third 135GB(E: ) partition for Data Storage..

So can you please explain me how do I install Ubuntu on already made 50GB partition?

Here is the picture,i already renamed partitions,i just need to install Ubuntu..

[IMG]http://www.dodaj.rs/f/Y/t2/3zqy2mO1/partitions.jpg[/IMG]
are you from Croatia or somewhere near???
visit
 [http://www.linuxzasve.com/](http://www.linuxzasve.com/)
it's everything that you'll need for Ubuntu ;)

---

### Post by ramnarayan on 2009-07-15
> **Infinity_RS said:**
> 
So can you please explain me how do I install Ubuntu on already made 50GB partition?


am assuming you want to install Ubuntu through Windows -if so use the programme called WuBI - if you pop your live CD in while wincedows is running it should show the programme called wubi

afaik this should take care of your needs and also not make you mess around too much with your partitioning

cheers

---

### Post by Ian C. Purdie on 2009-07-18
Folks, I've searched through these forums and this is the closest thread I can find to my non-install Wubi problems.
 
I've downloaded and saved to a clean directory the installer file from here:
 
[http://wubi-installer.org/](http://wubi-installer.org/) which means I clicked on "Download Now - Wubi 9.04".
 
This gives me a file, wubi.exe of 1.46 meg in size. It does absolutely nothing!
 
Before we go further - this is my system:
CPU: Authentic AMD Athlon XP 1700+
Ram: 1 Gig - but Windoze says 449 Meg.
File System: 32 Bit
OS: Window 98SE 4.10.2222 A
 
In frustration, I then downloaded to the same directory:
 
ubuntu-8.10-desktop-amd64.iso - 699 Meg File
 
Still nothing. OK go for 32 bit.
 
ubuntu-8.10-desktop-i386.iso - another 699 Meg File
 
Still nothing. What am I obviously doing wrong?

---

### Post by merlinus on 2009-07-18
You need to burn the .iso file as a disk image, not a data disk, to a cd, at no more than 4x speed, and then boot from it.

Also, be sure to check the cd for errors at the opening menu.

As for wubi..... wait for someone else to respond.

---

### Post by Ian C. Purdie on 2009-07-19
Thanks so much for your time. Wubi site for whatever reason seem to have a different take on it.
 
"Wubi is Simple
No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you".
 
Oh well!

---

### Post by merlinus on 2009-07-19
FWIW, I was referring to this:

> 
In frustration, I then downloaded to the same directory:

ubuntu-8.10-desktop-amd64.iso - 699 Meg File
 
Still nothing. OK go for 32 bit.
 
ubuntu-8.10-desktop-i386.iso - another 699 Meg File
 

It would seem that wubi.exe is a file that you need to run under windows.

---

### Post by Ian C. Purdie on 2009-07-19
Now understood, many thanks.

---

### Post by stlsaint on 2009-07-19
yes wubi is quick and easy but it has its disadvantages as would all programs within windows would...resources, storage, etc etc...best way is to create bootable cd from iso using poweriso or what may have you. boot to disk and when you get to partition screen you must create two more partitions from within your ubuntu partition(and dont worry about messing anything ub cuz the ubuntu partition creator will restore anything you done wrong back to the way you had it before you changed stuff...trust me ive done it many times!!) so two partitions...  1.swap, 2.ext3 part...make your swap 1024 or 1 gb and make the ext3 part...the rest of the partition after the 1 gb from the swap so 49gb! if you do this wrong ubuntu will not allow you to continue and will take you back to the editing page so there is now going wrong...thats me installing ubuntu ultimate 2.2 on jaunty!! hope this helps!! if not ask you shall receive!!!

---

