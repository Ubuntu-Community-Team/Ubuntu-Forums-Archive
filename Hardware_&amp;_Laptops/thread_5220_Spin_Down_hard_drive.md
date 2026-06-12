---
title: "Spin Down hard drive"
date: 2004-11-16
forum: Hardware &amp; Laptops
---

### Post by Viro on 2004-11-16
How do I get my hard drive in my notebook to spindown? I've added the following to my /etc/hdparm.conf file

> /dev/hda {
	io32_support = 1
	dma = on
	spindown_time = 36
	apm = 255
}


If it helps, I'm running ReiserFS and I've heard somewhere that ReiserFS doesn't allow your hard drive to spin down.

---

### Post by rbrimhall on 2004-11-17
I'm pretty sure that "laptop-mode" which is in the 2.6 kernels and enabled on Ubuntu spins down the HDD. Mine seems to spin down when idle for a few seconds and spins up when I am doing something. The script is in /usr/sbin/ and is called laptop-mode... maybe taking a look at it will help you out.

---

### Post by Viro on 2004-11-17
That looks promising. How do I ensure that it gets run all the time at boot up?

Edit: Before I forget, what filesystem are you running? Is it Reiser or ext3?

---

### Post by rbrimhall on 2004-11-17
I'm using reiser... I get a "starting laptop mode" after "Checking battery state" during boot-up right before GDM loads. It only starts when I am unplugged from AC... Pretty sure the one of the acpid scripts load this up (/etc/acpi)...

---

### Post by dare2dreamer on 2005-03-03
by default, laptop-mode is enabled. You can have a look at /etc/default/laptop-mode for details on how to turn it on or off. Reiserfs will prevent laptop-mode from working, as it needs nearly constant access to the drives to do its thing.

Assuming you are running ext3 partitions, you might have a look at /usr/share/doc/laptop-mode for more details on setting your spindown_time to something appropriate.

To overcome the problem of laptop-mode only working when on battery, I simply went into the bios on my laptop and told it to power manage the drives and screen regardless of whether or not it was on a/c power. Failing that option, you can run laptop-mode manually as root when needed:

```
sudo laptop-mode start|stop
```

---

### Post by dodok1 on 2005-03-03
I am not sure for Reiser, but for ext3 I had to set *noatime* in the mount options to disable periodic writes to disk.

---

### Post by dare2dreamer on 2005-03-04
The noatime option is a good idea for any partition under linux. All it does is turn off the regular writing of file access times to the partition in question, a bit of info no application really uses and is generally gleaned from looking at timestamps anyway.

Using the option seriously cuts down on pointless random disk accessing.

---

### Post by mohaham on 2005-04-16
i have tried setting the hard-drive spindown_time to something appropriate in laptop-mode...
but couldnt succeed...
need some help here please...

---

