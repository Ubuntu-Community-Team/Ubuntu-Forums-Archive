---
title: "Touchpad frozen after system suspend/standby"
date: 2010-10-02
forum: Hardware
---

### Post by Faylcon on 2010-10-02
I have a Gateway notebook with Synaptic Touchpad and Ubuntu 10.10 Release Candidate. In this version of Ubuntu (and the previous 2 I have tried) the cursor freezes after closing the lid and hibernating/suspending/standby the computer.  Any ideas on how to get the touchpad to wake up automatically?

---

### Post by wowshailen on 2010-10-12
My screen is frozen here. After a wake up, the pwoer LEDs are on, but the screen is off. Basically, everything is frozen, since I can't get any response by pressing random keys on the keyboard etc.

Only way to get back to ubuntu is a power reset.

I am using Uubntu netbook edition 10.10 on a Samsung NC10 (N450 processor).

It is annoying that Ubuntu has such big problems.

---

### Post by cecilx22 on 2010-10-18
Please try to keep replies towards helping others with their problems rather than add to the list of things the thread is trying to deal with.  This sort of reply will tend to make a thread with a specific topic devolve into a wide, general, and less helpful thread.

> **wowshailen said:**
> My screen is frozen here. After a wake up, the pwoer LEDs are on, but the screen is off. Basically, everything is frozen, since I can't get any response by pressing random keys on the keyboard etc.

Only way to get back to ubuntu is a power reset.

I am using Uubntu netbook edition 10.10 on a Samsung NC10 (N450 processor).

It is annoying that Ubuntu has such big problems.


On a side note, my Dell XPS16 is having the same trouble.  If anybody has any ideas on what to take a look at, what logs to dump, etc, please let me know and I'll look into it!

Thanks!

---

### Post by cecilx22 on 2010-10-18
Do you, by chance, have an external mouse?

I have a Logitch external mouse, and when listing input devices after suspend (with touchpad not working), I get this (along with other devices, none of which are a synaptics touchpad):

```
I: Bus=0003 Vendor=046d Product=c525 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1a.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/input/input24
U: Uniq=
H: Handlers=mouse0 event8 
B: EV=17
B: KEY=ffff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c525 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1a.1-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.1/input/input25
U: Uniq=
H: Handlers=kbd event9 
B: EV=1f
B: KEY=837fff002c3027 bf00444400000000 1 f848b27c000 667bfad9415fed 8e000000000000 0
B: REL=40
B: ABS=100000000
B: MSC=10

```

Seeing it twice like that is odd...

---

### Post by Laykun on 2011-01-26
I have this exact same issue. Dell XPS 16, Logitech external Mouse (Logitech MX AIR). Has anyone ever found a fix for this?

---

### Post by jhawkjsu on 2011-02-22
I was Googling the problem and came across this thread. The touchpad on my XPS 16 freezes after suspend/standby, too. Has anybody come across any fixes?

---

### Post by SlickT10 on 2011-03-17
I have the same problem as the OP. I have a Gateway MX6650/MA2A Computer with the same problem. Any light on this subject? It's pretty important since I can't have an external mouse all the time and It makes the computer unusable to always have to restart or shutdown completely.

---

### Post by toomanymatts on 2011-03-21
bump.  Same issue on a Dell Vostro v13.  Ubuntu 10.10.  Anyone, anyone?

---

### Post by lillem4n on 2011-05-10
Same on my V13 Vostro... have anyone filed a bug? Where do you do that, and how?

---

### Post by kstella on 2011-05-10
I have a similar problem with my MSI Wind U100, but I'm using 11.04. After suspend, when I power up again, the screen is black. The mouse  cursor appears after a while, and I can move it, but the screen stays black. Another time, the whole computer froze; couldn't move my mouse or type.

---

### Post by Faylcon on 2011-05-10
I did find a solution to this (it also works in 11.04). As root, navigate to and edit /etc/default/grub.  Change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset" to solve the problem.

---

### Post by eladn on 2011-05-13
> **lillem4n said:**
> Same on my V13 Vostro... have anyone filed a bug? Where do you do that, and how?

I have the exact same problem on my V13. I think this bug is what you are looking for: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86820)

---

### Post by theWrkncacnter on 2012-01-31
> **Faylcon said:**
> I did find a solution to this (it also works in 11.04). As root, navigate to and edit /etc/default/grub.  Change the line:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset" to solve the problem.

I experience this issue too (ALPS pointing device, ubuntu 11.10). Any explanation on why this method works / what it does?

---

