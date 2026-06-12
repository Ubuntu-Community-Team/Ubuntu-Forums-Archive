---
title: "Accessing ubuntu files from windows."
date: 2008-10-25
forum: General Help
---

### Post by Yoadee on 2008-10-25
Hi all, I have installed Ubuntu on Partition "D:" but when I try to access the files I have downloaded from windows I don't find them. The only thing that is in the "D:" drive is the ubuntu installation. 

I have downloaded some files with Transmission that I need to use on my Windows, any help would be appreciated. 

Sinercly, Yoadee.

---

### Post by sethvath on 2008-10-25
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by Yoadee on 2008-10-25
Didn't help me at all. I need a way to access the files. I don't see how that helps me doing it.

---

### Post by sethvath on 2008-10-25
Are you trying to access the files you downloaded with transmission on ubuntu FROM windows? Or the other way round. Read your first and third sentence, they mean 2 different things. 

To access your windows files FROM ubuntu, mount your windows partition first. Refer to this tutorial [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by EmaRsk on 2008-10-25
> **Yoadee said:**
> Didn't help me at all. I need a way to access the files. I don't see how that helps me doing it.

There you can find a driver to install on your windows that makes you capable to mount and access an ext2/ext3 partition from windows. (You have to open the control panel and configure it to mount the right one with the letter you want.)

But you also said:

[quote=Yoadee]The only thing that is in the "D:" drive is the ubuntu installation. [/quote]

from which I understand that you actually CAN see the files in the ubuntu partition (correct me if I'm wrong). Then the problem is only to find where transmission has put your files, but that depends on your settings.

Workaround #1: use a usb stick or other kind of removable media
Workaround #2: do the reverse, and copy your files to the windows partition from within ubuntu

---

### Post by cloud-e on 2008-10-25
Hi Yoadee,

I had this very issue tonight. Essentially what you are trying to do is get Ubuntu to read/write to your Windows NTFS partition. Firstly let me give you my pastebin link so you can see the steps I underwent. [http://paste.ubuntu.com/62431/](http://paste.ubuntu.com/62431/)

The very first thing you will want to do is open terminal and type sudo fdisk -l. Like so.

1) applications>accessories>terminal
2) sudo fdisk -l

*Keep Terminal open

This should ask you for your pw, just type your pw. The output in terminal will be all the partitions that Ubunutu can see. Here you will look for any NTFS partitions you will need to mount in order to access them. FOR EX. you type sudo fdisk -l and it gives you /dev/sda1 and or /dev/sdb2. You may have multiple NTFS partitions. Make a note of the NTFS partition. We will come back to that soon.

Next inside terminal paste the following: sudo apt-get install ntfs-3g ntfs-config ntfsdoc ntfsprogs

These are your NTFS apps that will help Ubuntu access those said partitions.  Like so.

3) sudo apt-get install ntfs-3g ntfs-config ntfsdoc ntfsprogs

Now what we need to do is create a directory for Ubuntu to associate the NTFS partitions and give yourself permissions to the directory(ies)

4) sudo mkdir /media/sdxx

*replace the xx values for the output you received from step 2

5) sudo chmod ugo+rw /media/sdxx

*replace the xx values for the output you received from step 2

6) sudo gedit /etc/fstab

After this command you will open the /etc/fstab here you will need to add the NTFS partition(s) that Ubuntu needs to mount for access.You will need to add the following to that text file at the bottom. 

/dev/sdxx  /media/sdxx ntfs-3g defaults 0 1

Next attempt to mount the NTFS partition with sudo mount /dev/sdxx

7) sudo mount /dev/sdxx

***if you receive the following output in Terminal following step 7:

Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:
Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.
Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda1 /media/sda1 -o force Or add the option to the relevant row in the /etc/fstab file: /dev/sda1 /media/sda1 ntfs-3g force 0 0

You must complete the following step in Terminal: sudo mount -t ntfs-3g -o force /dev/sdxx /media/usb

(Step Eight) sudo mount -t ntfs-3g -o force /dev/sdxx /media/usb


Hope this works!



Message from our father:

Hello netlanders,
Due to a project I'm working on (in minix), I'm interested in the posix
standard definition. Could somebody please point me to a (preferably)
machine-readable format of the latest posix rules? Ftp-sites would be
nice.

---

