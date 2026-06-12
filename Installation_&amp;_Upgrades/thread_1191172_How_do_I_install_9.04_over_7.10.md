---
title: "How do I install 9.04 over 7.10?"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by Arthur_D on 2009-06-18
I wanted to install Ubuntu 9.04 with a CD on top of 7.10.
I tried to edit the partitions manually, and chose the ext3 filesystem to get reformatted. Everything looked fine until I rebooted, and there was the old 7.10 entries in GRUB, and I could start it, though I got a hangup after loading the desktop.

What in the world did I wrong?

BTW, I'm dual-booting Ubuntu and XP.

---

### Post by merlinus on 2009-06-18
Can you post results of

```

sudo fdisk -l

```

whilst running from the live cd?

---

### Post by Arthur_D on 2009-06-18
> **merlinus said:**
> Can you post results of

```

sudo fdisk -l

```whilst running from the live cd?
Yeah, I'll do that later, because it is on my sister's computer, and it's kinda late here.
But I thought I could post some more details. After installing 9.04 with the CD, I got a window saying that GRUB couldn't be configured, and that it was a critical error. Then I tried, using the Live CD, [the steps for recovering GRUB after a Windows install_._]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start")
That didn't help, so I came here to ask. Thanks for the quick response; will post the result of sudo fdisk -l tomorrow.

---

### Post by merlinus on 2009-06-18
OK, and whilst you are at it, see if you can mount your ubuntu partition and post /boot/grub/menu.lst.

---

### Post by Arthur_D on 2009-06-19
Sorry, we're going on a vacation, 6 days or so, therefore my sister wanted to wait with this.
Will come back in 6-7 days or something like that with the info you asked for.
Just saying so you don't think I ask for something, and then does no effort for getting the info you need.

Any other suggestions meanwhile are of course appreciated. :)

---

### Post by Arthur_D on 2009-06-27
Never mind, just used a GParted Live CD and deleted the partition, and then let the 9.04 installer create a new one.

Thanks for your interest. :)

---

