---
title: "Questions about ubuntu."
date: 2008-07-20
forum: General Help
---

### Post by w7gsh on 2008-07-20
Hello all:
            I just installed and updated Ubuntu on my computer and I can connect to the internet using the External modem I just bought,the modem I got is a Trendnet TFM-560x.It is actually ubuntu studio that I have.So far I like it alot,much better than windows,but I have a some questions about it,that i hope someone can answer here are the details of the pc I have.
Dell Dimension 4400
Pentium 4 1.6
512 megs ram
80 gig hard drive
Dial Up internet
Sound Blaster audigy sound card


Is there a Device Manager and if so how do I get to it?
My internet connection is super super slow any ideas?
No audio?


If anyone has any ideas or tweaks I would appreciate it.

                                                   Thanks
                                                        Gary

---

### Post by Vivaldi Gloria on 2008-07-20
Welcome to ubuntu. I suggest you learn a couple of things before you do anyting.


**1)** Installing Programs. For this use

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.


**2)** Learn the basics of a terminal from

[https://help.ubuntu.com/8.04/basic-commands/C/](https://help.ubuntu.com/8.04/basic-commands/C/)

This is important because quite a bit of help in this subforums requires you to enter commands in a terminal. You start a terminal from

Applications > Accessories > Terminal 

or press Alt+F2 and start

```
gnome-terminal
```


**3)** About your audio. Try opening a thread in hardware & laptop forums. Also include the results of the commands

```

aplay -l
lspci | grep Audio
```

you get in a terminal. 


**4)** There isn't a device manager included. I remember seeing one called sysinfo in synaptic. Search & install it. But there are a lot of commands you can use in terminal: see the below post.


**5)** About your internet speed. I don't know why it is slow. May be this could help. Start firefox and enter "about:config" in the adress bar. Enter "IPv6" in the filter bar to find the entry "network.dns.disableIPv6". Then double click the entry to make its value false. Restart firefox. If this doesn't work then you may consider opening a separate thread for it.

---

### Post by Vivaldi Gloria on 2008-07-20
There are a number of (terminal) commands that give general info about your hardware:

```
lshw
hwinfo
dmidecode
```

If any of these are not installed then search & install them using synaptic.

Preferably use these (and the ones at the end of this post) with sudo:

```
sudo lshw
```

etc. (Sudo gives administrative rights.)

These spit out so much info that it may be better to save the output into a text file:

```
sudo lshw > info1.txt
sudo hwinfo  > info2.txt
sudo dmidecode  > info3.txt
```

Start by using the short versions

```
sudo lshw -short
sudo hwinfo --short
```

They have flags to restrict the output to certain hardware. For example

```
sudo lshw -class system
```

gives a basic info and motherboard. To learn more about these flags see their man pages:

```
man lshw
```

etc.

Some other commands:

```
lspci (Lists PCI devices including Audio, VGA, Ethernet etc.)
aplay -l (sound info)
uname -a (kernel info)
lsusb (list USB devices)
ls /dev/disk/* -lah (disk info)
fdisk -l (disk info)
df -h (disk usage info)
free -m (memory info)
cat /proc/swaps (swap file/partition info)

```

and the list goes on and on.

---

### Post by mattze on 2008-07-20
hardinfo is a nice devicemanager.

install it via ```
sudo apt-get install hardinfo
``` or synaptic.

---

### Post by ~Nightingale~ on 2008-07-20
Welcome to the Ubuntu experience, you WILL enjoy your stay.:KS

---

### Post by hansdown on 2008-07-20
Welcome w7gsm.

---

### Post by Vorian Grey on 2008-07-20
I agree, hardinfo is nice.

Welcome aboard, w7gsm.

---

