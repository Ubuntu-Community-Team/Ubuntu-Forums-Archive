---
title: "Not Able To Install NVIDIA Drivers"
date: 2009-02-09
forum: Installation &amp; Upgrades
---

### Post by bjnueva8623 on 2009-02-09
Seems like I've tried everything. When I go to **System>Administration>Hardware Drivers** there are three options (versions 173, 96, and 177). I've tried them all but all that happens is a small window pops up (downloading and installing driver) but it disappears quickly without a "changes applied" message. 

I found this [website]("http://boncey.org/2008_11_29_nvidia_drivers_in_ubuntu_8_10_intrepid_ibex") with a possible explanation. I tried that but receive this message: 

[B]E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root? [/B]

Anyone know what the problem is?

---

### Post by taurus on 2009-02-09
You need to include a **sudo** in front of those commands since you need root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bjnueva8623 on 2009-02-09
> **taurus said:**
> You need to include a **sudo** in front of those commands since you need root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

So basically, I'd have to type "sudo" before the command?

```
sudo apt-get install linux-headers-2.6.27-7-generic
```

Like that? Just making sure.

---

### Post by taurus on 2009-02-09
> **bjnueva8623 said:**
> So basically, I'd have to type "sudo" before the command?

```
sudo apt-get install linux-headers-**2.6.27-7-generic**
```

Like that? Just making sure.

Yes, sudo and then the command, apt-get.  Make sure you are running that kernel version though, 2.6.27-7-generic.

```
uname -a
```

---

### Post by bjnueva8623 on 2009-02-10
> **taurus said:**
> Yes, sudo and then the command, apt-get.  Make sure you are running that kernel version though, 2.6.27-7-generic.

```
uname -a
```

Everything went well (thanks a million for "uname -a" thing), here's what I got. 

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-177[/B]

Where can I find that nvidia package? I tried the hardware drivers again and got the same results as before.

---

### Post by taurus on 2009-02-10
Maybe you don't have enough repos enable in /etc/apt/sources.list.  Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by bjnueva8623 on 2009-02-10
Wait, never mind. This time the installation window showed up and after initially thinking it was stuck, it finished loading after I left it alone for a while. I was thrown off because everything else seems to load ridiculously fast in Ubuntu. 

Thanks a lot for your help. Everything looks great now, except the bottom panel seems to have disappeared and the font size has decreased dramatically. Any idea what could be up? I'm actually having trouble reading what I type.

EDIT: I restarted the system and the size is back to normal. Everything is good now. Thanks you.

---

### Post by taurus on 2009-02-10
Maybe you need to play with the resolution.  Look in System -> Preferences -> Screen Resolution or System -> Administration -> NVIDIA Display Settings.

---

