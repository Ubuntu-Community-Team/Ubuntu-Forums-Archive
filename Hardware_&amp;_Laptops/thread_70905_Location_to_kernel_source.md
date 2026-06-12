---
title: "Location to kernel source"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by stefanborremans on 2005-10-01
Hello,

I need to install the zd1211 driver. And to install the driver I need to locate the kernel source. Where can I find it in ubuntu?

Tnx

---

### Post by mlomker on 2005-10-01
After you install the package you'll find it as a file in /usr/src.

```

su
apt-get install linux-tree
cd /usr/src

```

Use the **ls** command to get the filename.  I'm going to use mine in this example:
```

tar jxvf linux-source-2.6.10.tar.bz2
ln -s linux-source-2.6.10 linux

```

---

### Post by stefanborremans on 2005-10-01
Okay, that worked for me.

The next step is to execute a command named: make clean

But if I execute the command, it says

make : command not found

---

### Post by mlomker on 2005-10-01
```

sudo apt-get install build-essential

```

---

### Post by stefanborremans on 2005-10-01
Apart from the ubuntu website, where can I check which kernel version I'm using?

The ubuntu wiki: [https://wiki.ubuntu.com/zd1211wifi](https://wiki.ubuntu.com/zd1211wifi)

says that I need to download linux-headers-2.6.10-5-386

But there is no one like that with apt-get, only 2.6.12-8 and 2.6.12-9.

Which one do I need?

---

### Post by mlomker on 2005-10-02
> Apart from the ubuntu website, where can I check which kernel version I'm using?


The linux-tree package downloads the proper kernel headers automatically.  You can use the **uname -r** command from a terminal to see what kernel you are running.

---

### Post by az on 2005-10-02
[QUOTE=stefanborremans]Hello,
I need to install the zd1211 driver. And to install the driver I need to locate the kernel source. Where can I find it in ubuntu?
Tnx[/QUOTE]
You do not need the full source.  Just install the linux-headers and you are good to go.


The linux-tree is the full source.

So, for hoary it would be for example:

linux-headers-2.6.10-5-386

---

### Post by stefanborremans on 2005-10-02
In mean time I discovered that my ubuntu version allready had the zd1211 module on board, I only needed to load it.

But I was wondering why I get the following mistake when I did a **make clean**. 

root@ubuntu:/home/stefan/Desktop/zd1211# make clean
make -C /home/stefan/Desktop/zd1211/src/modules-2.6.12 clean
make: *** /home/stefan/Desktop/zd1211/src/modules-2.6.12: Onbekend bestand of map (Unknown file or folder).  Stop.
make: *** [clean] Fout 2

---

### Post by NemanjaM on 2005-10-07
Hello! I have a similar problem.

I got a tip from another forum to install source kernel. I did this following your instructions but it made source for kernel version 2.6.10-5 and my source is 2.6.10-5**-386**.

How do I install kernel source for my version?

---

### Post by mlomker on 2005-10-07
That is the right one.

---

### Post by evsoul on 2005-10-27
Is there anyway to obtain the source from the cd or install? I have to install a VPN client to get on the wireless here, and I cannot install the VPN client without the kernel source. catch 22 for me I guess. heh

evsoul

---

### Post by 1veedo on 2005-11-06
i'll start my own thread

---

### Post by Yarbo on 2007-11-11
This looks like an old thread, but I am attempting to do something similar with Gutsy...

```
sudo apt-get install linux-tree
```

Does not work... it outputs:

```
$ sudo apt-get install linux-tree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-tree

```

---

### Post by primorec on 2008-01-18
sudo apt-get install build-essential

and then

./configure
make 
sudo make install

---

