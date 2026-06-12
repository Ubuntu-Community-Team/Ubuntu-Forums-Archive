---
title: "root not able to create directory in /media"
date: 2011-05-28
forum: Hardware
---

### Post by dhwani on 2011-05-28
I am facing an unusual problem. Even if I switch to root, I am not able to create a folder under /media.

The system details
Ubuntu 11.04
Kernel 2.6.38-8-generic
File system - ext4

on hardware

Acer Aspire One D260
Intel Atom Processor N450
1 GB Memory

The following is a log of what I do to verify the problem

sk@ADAMBAR:~$ 
sk@ADAMBAR:~$ su
Password: 
root@ADAMBAR:/home/sk# cd /
root@ADAMBAR:/# ls -al
total 112
drwxr-xr-x  23 root root  4096 2011-05-22 16:00 .
drwxr-xr-x  23 root root  4096 2011-05-22 16:00 ..
drwxr-xr-x   2 root root  4096 2011-05-22 00:35 bin
drwxr-xr-x   3 root root  4096 2011-05-22 01:06 boot
drwxr-xr-x   2 root root  4096 2011-04-22 00:54 cdrom
drwxr-xr-x  19 root root  4080 2011-05-28 11:14 dev
drwxr-xr-x 142 root root 12288 2011-05-28 11:15 etc
drwxr-xr-x   3 root root  4096 2011-05-14 20:26 home
lrwxrwxrwx   1 root root    32 2011-05-22 00:50 initrd.img -> boot/initrd.img-2.6.38-8-generic
lrwxrwxrwx   1 root root    33 2011-04-22 01:07 initrd.img.old -> boot/initrd.img-2.6.35-22-generic
drwxr-xr-x  19 root root 12288 2011-05-22 00:43 lib
drwx------   2 root root 16384 2011-04-22 00:50 lost+found
drwxr-xr-x   2 root root     0 2011-05-28 11:14 media
drwxr-xr-x   2 root root  4096 2011-05-22 16:04 mnt
drwxr-xr-x   2 root root  4096 2010-10-07 21:26 opt
dr-xr-xr-x 160 root root     0 2011-05-28 16:44 proc
drwx------  27 root root  4096 2011-05-27 22:30 root
drwxr-xr-x   2 root root 12288 2011-05-22 00:42 sbin
drwxr-xr-x   2 root root  4096 2010-05-09 21:24 selinux
drwxr-xr-x   2 root root  4096 2010-10-07 21:26 srv
drwxr-xr-x  12 root root     0 2011-05-28 16:44 sys
drwxrwxrwt  15 root root  4096 2011-05-28 12:23 tmp
drwxr-xr-x   2 sk   sk    4096 2011-05-22 16:00 usb1
drwxr-xr-x  11 root root  4096 2011-04-22 11:30 usr
drwxr-xr-x  15 root root  4096 2011-05-22 00:02 var
lrwxrwxrwx   1 root root    29 2011-05-22 00:50 vmlinuz -> boot/vmlinuz-2.6.38-8-generic
lrwxrwxrwx   1 root root    30 2011-04-22 01:07 vmlinuz.old -> boot/vmlinuz-2.6.35-22-generic
root@ADAMBAR:/# cd /media
root@ADAMBAR:/media# ls -al
total 4
drwxr-xr-x  2 root root    0 2011-05-28 11:14 .
drwxr-xr-x 23 root root 4096 2011-05-22 16:00 ..
root@ADAMBAR:/media# mkdir usb0
mkdir: cannot create directory `usb0': Permission denied
root@ADAMBAR:/media# 

I am not new to Ubuntu. I have been using it since last 3 years. But this is a bit weird. Because of this I am not able to auto-mount flash drives. Disk Utility shows the plugged in flash drive but clicking on mount volume pops up the following error.

    Error creating moint point: Permission denied

I have checked the forums and found similar problems but they were mostly permission issues. Here root has the permissions and the chmod is also set properly yet I am not able to create the folder.

I have seen the same problem in ubuntu 10.10 as well on the same machine. 10.10 works just great on another Acer laptop that I have.

Any suggestions are most welcome. Thanks in advance.

---

### Post by ajgreeny on 2011-05-28
Have you really setup a root account, as it is disabled by default in ubuntu.

Try ```
sudo mkdir /media/usb0
``` from your user terminal.

---

### Post by dhwani on 2011-05-28
Hi 

Thanks for the reply.

I have setup the root account and i use it from the terminal.

I had tried the same using sudo as well. I can create directories any where else. For instance i can create an alternative location for mounting like /usb1 when logged in as root. The problem seems to be just under /media.

Does this sound like a bug?

---

### Post by coffeecat on 2011-05-28
Let's look at the permissions of the media directory:

```
ls -l / | grep media
```

---

### Post by dhwani on 2011-05-29
The permissions on the media directory are as follows

```
drwxr-xr-x   2 root root     0 2011-05-28 11:14 media
```

Pardon me ... but I have given this detail in my first post. There are other details as well. Please let me know if I should repost the same for convenience.

Thanks for the responses. By the way I have just converted my brother to a Ubuntu user and this problem is holding him from being a comfortably happy user. :-(

thanks
dhwani

---

### Post by coffeecat on 2011-05-30
My apologies for missing that in your first post. I was wondering if the /media directory had somehow become read-only, but clearly not.

The problem, as you say, is that you can't create directories within /media. You say you get the error message "Error creating moint point: Permission denied" when you try to automount a flash drive. Have you, by chance, installed the application "usbmount"? It interferes with the USB automounting functionality of the GUI desktop and many people have regretted installing it. It's designed for GUI-less systems. I can't see that it would prevent the creation of directories in /media, but it does seem to do weird things in desktop systems. If you do have usbmount installed, uninstall it and see if that makes any difference.

---

### Post by dhwani on 2011-05-31
I had installed usbmount as part of trying out many things. So I removed it using the following command

```
sudo apt-get remove usbmount
```

I restarted the system to be double sure. But still I am **not able to** create a directory under /media as root or via sudo. 

Are there any additional packages related to usbmount that also need to be removed that apt-get wont remove automatically?

Thanks for the continued help.

---

### Post by garvinrick4 on 2011-05-31
This is a new install of 11.10 and this is the sudoers file below:
And all works well as shown below: Take a look at your /etc/sudoers
```
gksudo gedit /etc/sudoers
```# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults    env_reset    
                         
# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo    ALL=(ALL:ALL) ALL

#includedir /etc/sudoers.d

----------------------------------------------------------------------------------------------
rick@rick-HP:~$ sudo mkdir /media/test
[sudo] password for rick: 
rick@rick-HP:~$ cd /media
rick@rick-HP:/media$ ls
data  home  test
rick@rick-HP:/media$
####Try using sudo -i in Ubuntu to get into root instead of the su or su -#####
             Line Above is just information I noticed.

---

### Post by dhwani on 2011-05-31
Hi

I am able to sudo many other things including making another directory outside my home like the following

```
sudo mkdir /usb0
```

This means the sudo should be working fine. I don't have the machine with me right now hence I am not able to check the sudoers list. I will check and post back.

I will also check the sudo -i option and post back.

But the queer problem is that I am able to create directories every where else **but not under /media.**

thanks

---

### Post by garvinrick4 on 2011-05-31
What does yours look like: Something has got to be wrong with /media then.
```
rick@rick-HP:~$ cd /
rick@rick-HP:/$ ls
bin    dev   initrd.img      lib32       media  proc  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lib64       mnt    root  srv      usr  vmlinuz.old
cdrom  home  lib             lost+found  opt    sbin  sys      var
rick@rick-HP:/$ ls -la
total 132
drwxr-xr-x  23 root root  4096 2011-05-27 00:37 .
drwxr-xr-x  23 root root  4096 2011-05-27 00:37 ..
drwxr-xr-x   2 root root 12288 2011-05-27 00:30 bin
drwxr-xr-x   3 root root  4096 2011-05-28 18:58 boot
drwxr-xr-x   2 root root  4096 2011-04-10 18:37 cdrom
drwxr-xr-x  20 root root  4640 2011-05-30 22:04 dev
drwxr-xr-x 135 root root 12288 2011-05-30 22:34 etc
drwxr-xr-x   3 root root  4096 2011-04-10 18:38 home
lrwxrwxrwx   1 root root    32 2011-05-27 00:37 initrd.img -> boot/initrd.img-2.6.39-3-generic
lrwxrwxrwx   1 root root    32 2011-04-10 18:40 initrd.img.old -> boot/initrd.img-2.6.38-8-generic
drwxr-xr-x  21 root root  4096 2011-05-27 19:04 lib
drwxr-xr-x   4 root root 20480 2011-05-27 00:27 lib32
lrwxrwxrwx   1 root root     4 2011-04-10 18:35 lib64 -> /lib
drwx------   2 root root 16384 2011-04-10 18:34 lost+found
drwxr-xr-x   5 root root  4096 2011-05-30 21:41 media
drwxr-xr-x   4 root root  4096 2011-05-16 17:54 mnt
drwxr-xr-x   2 root root  4096 2011-04-10 00:46 opt
dr-xr-xr-x 158 root root     0 2011-05-30 13:29 proc
drwx------  11 root root  4096 2011-05-27 20:23 root
drwxr-xr-x   2 root root 12288 2011-05-30 19:55 sbin
drwxr-xr-x   2 root root  4096 2011-03-21 01:35 selinux
drwxr-xr-x   2 root root  4096 2011-04-10 00:46 srv
drwxr-xr-x  13 root root     0 2011-05-30 13:29 sys
drwxrwxrwt  13 root root  4096 2011-05-30 22:55 tmp
drwxr-xr-x  12 root root  4096 2011-04-16 12:09 usr
drwxr-xr-x  15 root root  4096 2011-04-10 01:03 var
lrwxrwxrwx   1 root root    29 2011-05-27 00:37 vmlinuz -> boot/vmlinuz-2.6.39-3-generic
lrwxrwxrwx   1 root root    29 2011-04-10 18:40 vmlinuz.old -> boot/vmlinuz-2.6.38-8-generic
rick@rick-HP:/$ 

```Link:
[http://www.go2linux.org/command-ls-file-permissions](http://www.go2linux.org/command-ls-file-permissions)
Your field 8 in /media should be 4096 and yours is 0 I believe:
There is a start.

---

### Post by dhwani on 2011-05-31
The same directories listing for me is posted in the first post. I don't see anything visibly odd with the /media directory.

My kernel is older than yours and my system has ext4, if at all that could make any difference.

thanks.

---

### Post by garvinrick4 on 2011-05-31
What about the link I gave you and field 8 is it 0 bytes or 4096 bytes in /media
[http://www.go2linux.org/command-ls-file-permissions](http://www.go2linux.org/command-ls-file-permissions)

---

### Post by garvinrick4 on 2011-05-31
If it is still at 0 then I have read it is corrupted and has to be fsck. (Should be 4096) (you show 0 in your post.)
Put in a live cd or from another install and run:
```
sudo e2fsck /dev/sd[COLOR=Red]xy [/COLOR] 
```x being your drive and y being your partition such as sda1 or sda5 whatever your install is.
## Cannot run fsck on a mounted drive.

---

### Post by dhwani on 2011-05-31
I am so sorry I had missed the link in your earlier post. I mistook it to be part of your signature :-(

Yes that definitely is a start. In fact I had doubted that it could be a corrupt file system issue and had run 
sudo fsck by booting from a USB drive. But it had given that the file system is ok.

All the same it definitely looks that all is not ok in the file system. I will try the e2fsck command and post back the status. But that may take a few days since the machine is not with me right now.

In the mean while thanks a lot for all the help.

---

### Post by dhwani on 2011-06-03
Hi

I got hold of the Acer Aspire now and tried the suggested steps as below. fsck reported that the file system is clean. After booting from a USB drive i did the following ...
```

ubuntu@ubuntu:~$ sudo fsck /dev/sdb2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
/dev/sdb2: clean, 170437/9773056 files, 17069901/39071744 blocks
ubuntu@ubuntu:~$ 

```

I further tried a few more things. From the USB boot I mounted the hard drive partition and deleted the media folder. After this I rebooted from the hard drive. But the media directory was back there with size 0. :-(

Is it possible that the start-up scripts may be setting up the media directory as a special directory, something similar to the /proc directory?

I will investigate this further and keep posting. Any more thoughts or suggestions would help.

Thanks.

---

### Post by dhwani on 2011-06-03
Finally it worked.

The problem was that as part of my own trials to make things work on 10.10, I had naively configured autofs on /media. When nothing worked on 10.10 I had upgraded it to 11.04. The configuration had remained the same after the upgrade and that was creating the special 0 size /media mount point managed by autofs.

This was preventing the normal operation of auto mounting in 11.04.

Thanks for all the pointers and suggestions. 

Learning from this is - **Don't just keep messing up your system by trying everything that is suggested on the forums. Each scenario in which something had worked for someone may be different. Do some research first.** :-(

---

### Post by supersom81 on 2012-01-28
First up, thanks! This is just what I needed.

Could you jot down the exact sequence of steps you followed to solve this problem?

I started having this problem right after I installed autofs; so it wasn't all that hard to guess what was causing the problem. So I removed autofs at the very outset. But that didn't help. That's when I started having doubts.

Your post inspired confidence to invest time in taking autofs off. So i stopped the service, removed autofs, commented out the relevant lines in auto.master and auto.sshfs and rebooted. It worked! 

Did yours start working the same way? I would suppose it should have started working as soon as I removed autofs. Any idea why that didn't happen?

---

