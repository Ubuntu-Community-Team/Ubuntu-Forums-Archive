---
title: "Using VirtualBox"
date: 2009-02-28
forum: Installation &amp; Upgrades
---

### Post by roshanjose on 2009-02-28
I have 2 disks

160 GB ----> Hardy Heron

80  GB ----> XP

While using Ubuntu, sometimes i need to switch my work to XP.

To work with XP, I need to reboot and change my booting device order to read another disk. Is there any way that I can omit this rebooting and get to work directly in XP from Ubuntu. Someone said VirtualBox works fine.

---

### Post by zvacet on 2009-02-28
Virtual box is good solution,but you have to know in that case you can use just a half of your ram(it split to Ubuntu and Virtual box).Try it and see if you like it.

---

### Post by roshanjose on 2009-02-28
Can I know how i can do this??

---

### Post by howefield on 2009-02-28
There are two versions of Virtualbox.

Firstly and in the repository is the OSE version, (Open Source Edition) and secondly the PUEL version available from the virtualbox website, (Personal Use and Evualation Licence).

There are some benefits of using the PUEL version, principally the ability to use usb devices., which cannot be done with the OSE version.

Take you choice and install the one you want.

Then create your vm and install xp.

zvacet is correct about splitting your ram between the host and guest systems but wrong that it halves your memory, you can allocate whatever you want to your guest system, probably a minimum of 256 megabytes for XP.

Read more at virtualbox.org

---

### Post by roshanjose on 2009-03-01
actually i have installed XP in other disk...the only problem is that i want it to use XP while using ubuntu

---

### Post by howefield on 2009-03-01
> **roshanjose said:**
> actually i have installed XP in other disk...the only problem is that i want it to use XP while using ubuntu

That is what Virtualbox allows you to do, run XP inside a window running on top of your Ubuntu.

Search for a video on youtube to show you how it looks. There are tons of them.

[http://www.youtube.com/watch?v=lmlvK7a8bJQ](http://www.youtube.com/watch?v=lmlvK7a8bJQ)

---

### Post by roshanjose on 2009-03-01
vow thank you... 

i am checking it out...

I am mainly using XP because I am facing problems with flash. I have installed flash plugins. 

When i watch a youtube video... i can watch it only once...i can't move the scrollbar to watch it again.. if i move the scrollbar..then it gets stuck..



Are there any html sites that i can read so that i can learn hoe to use this virtualbox

---

### Post by howefield on 2009-03-01
The virtualbox website is virtualbox.org

and this ubuntu page has some good screenshots of how to setup a virtual machine. Scroll down past the text to see them. (although they are a bit dated now, but should give you enough of an idea)

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by roshanjose on 2009-03-01
whats the difference  between the OSE and PUEL version....Which one is better

---

### Post by howefield on 2009-03-01
I'd say the PUEL version is best, from the point of view that it supports USB, the OSE doesn't but here is the list of extras in the PUEL version, from the virtualbox website,...


> Closed-source features ¶

The following list shows the enterprise features that are only present in the closed-source edition. Note that this list may change over time as some of these features will eventually be made available with the open-source version as well.

    * Remote Display Protocol (RDP) Server 

    This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

    * USB support 

    VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

    * USB over RDP 

    This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

    * iSCSI initiator 

    VirtualBox contains a builtin iSCSI initiator making it possible to use iSCSI targets as virtual disks without the guest requiring support for iSCSI.

    * Serial ATA controller 

    Like a real SATA controller, VirtualBox’s virtual SATA controller operates faster and also consumes less CPU resources than the virtual IDE controller. Also, this allows you to connect more than three virtual hard disks to the machine.

---

### Post by roshanjose on 2009-03-01
can i get more info about adding a Hard Disk with XP as virtual image in ubuntu

---

### Post by theozzlives on 2009-03-01
I use the PUEL version and am quite happy with it. I got XP and Windows 7 running in it. Never tried the OSE version.

---

### Post by roshanjose on 2009-03-01
where can i download the PUEL version from??

---

### Post by bela42 on 2009-03-01
Take a look at this very old blog post: [http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

It is referring to VirtualBox 1.5.x though, so it may or may not apply to 2.1.x

Also, the virtual machine does most likely show a much different hardware to your already installed Windows and you will face the same problems if you would move your Windows hard drive into a different computer.

Its much easier to just install Windows into a new virtual disk, you may even use your existing license, since the VBox isn't running at the same time as your "real" Windows.

---

### Post by zvacet on 2009-03-01
@ **roshanjose**

I think that you are looking for something like [this.]("http://ubuntuforums.org/showthread.php?t=380699&highlight=vmware+server+hard+drive")I don´t know is that possible with VB.

---

### Post by Linux000 on 2009-03-02
There is a way that you can mount a real hard disk as a virtual machine, a tutorial is in the VirtualBox fourms, unfortunately I have no clue where it is. one thing you have to do is to go into a terminal and type

sudo su

it will prompt for a password, type the one you choose at install time.

then type

cd /dev

then

chmod 777 /dev/sdb

finally type

ls -al sdb

it should return something like this

brwxrwxrwx 1 root disk 8, 16 2009-03-02 16:41 sdb

this should give you all privileges on your other hard drive, when you make the image (you might have to do that to the image itself also)

Hope it helps

---

