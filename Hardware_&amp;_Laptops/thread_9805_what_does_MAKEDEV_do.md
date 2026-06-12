---
title: "what does MAKEDEV do?"
date: 2005-01-01
forum: Hardware &amp; Laptops
---

### Post by HankB on 2005-01-01
I'm working with digital video capture and found that I needed to create the /dev/raw1394 device node and manipulate its permissions before kino would connect to the video camera.

I thought that MAKEDEV would do the job if I just:
   cd /dev; MAKEDEV raw1394
but no error was reported and no /dev/raw1394 was created. (Using the -v option it printed the major and minor numbers and I used those to create the node using 'mknod') But I find that when I reboot the node is gone.

So I took a look at the code (MAKEDEV is a shell script) and saw that it does the work in a sub named makedev(). I turned on verbosity within the sub (set -x) and then added a 'pwd' to see where it was doing its work. The result is shown below:

root@toonsinator:/dev # /tmp/MAKEDEV raw1394
+ pwd
/.dev
+ '[' '' ']'
+ '[' '!' '' ']'
+ '[' '' ']'
+ rm -f raw1394-
+ mknod raw1394- c 171 0
+ chown root:disk raw1394-
+ chmod 0660 raw1394-
+ mv raw1394- raw1394
+ :
+ exit 0
root@toonsinator:/dev # ls raw1394*
ls: raw1394*: No such file or directory
root@toonsinator:/dev # ls -l /.dev/raw1394
crw-rw----    1 root     disk     171,   0 2005-01-01 11:58 /.dev/raw1394

It creates the node in /.dev and leaves it there. In fact, there are 220 entries in my /dev directory and 1430 in /.dev. (Wow!) So my questions are:

Is this how MAKEDEV is supposed to work?

If not, is there something I'm doing wrong?

How can I make /dev/raw1394 persist past the next reboot?

This is on an AMD64 system but FWIW I'm running into the same issue with /dev/md0 on a Debian 32 bit system. Both systems are running 2.6.8 packaged kernels.

thanks,
hank

---

### Post by wallijonn on 2005-01-02
cd /dev
sudo depmod -a
sudo modprobe raw1394

lsmod 

if raw1394 is listed, then

cd /etc
sudo gedit modules
(add raw1394 device to end of list)
(reboot)

---

