---
title: "Gutsy and ATI Radeon 7000"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by DM was on fire! on 2007-12-15
I had a friend on another forum tell me that their computer was working with Gutsy and an ATI video card, and was running Compiz and Emerald.
However, after experiencing the problems I have on Dapper (crashes, lockdowns, the occasional log-out and get either taken back to GDM or a full screen command prompt), I *was* going to upgrade to Feisty because I heard it has good ATI support. Now that I've heard that, can anyone tell me if there are any incompatibility issues with an ATI Radeon 7000 and 7.10?
I don't wanna make the mistake of upgrading all the way to Gutsy, and then being stuck on Windows because I can't uninstall it or downgrade back to Feisty or all the way back to Dapper.

Thanks in advance. <3

P.S.: Since this would be my first time upgrading Ubuntu, I would assume that all the programs I have installed would stay on my hard drive, right?

---

### Post by DrMega on 2007-12-15
There is a problem with the Radeon 7000 in Ubuntu. Take a look at this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873")

...I'm afraid its a bit of a long thread, but if you scan down you'll see that on several occassions people thought they'd pinned it down only for it to pop up again.

---

### Post by DM was on fire! on 2007-12-15
> **DrMega said:**
> There is a problem with the Radeon 7000 in Ubuntu. Take a look at this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/16873")

...I'm afraid its a bit of a long thread, but if you scan down you'll see that on several occassions people thought they'd pinned it down only for it to pop up again.

Figures. I did have a NVIDIA video card in here but it burned up...and then I end up getting the problem child. XP

What does it mean where it says "fter disabling dri in Xorg.conf the system does not freeze anymore"? Do I disable the drivers and install the ones in Synaptic?

---

### Post by DrMega on 2007-12-15
> **DM was on fire! said:**
> Figures. I did have a NVIDIA video card in here but it burned up...and then I end up getting the problem child. XP

What does it mean where it says "fter disabling dri in Xorg.conf the system does not freeze anymore"? Do I disable the drivers and install the ones in Synaptic?

No, there is some obscure option in the fiile xorg.conf. It sets direct rendering (as opposed to software rendering). I'll see if I can find the references I used when this happened to me and post back later.

---

### Post by DrMega on 2007-12-16
To help find out if your display driver is giving you grief, you could temporarily change the driver to the generic MESA driver. Here's how.

1. Open a terminal (Applications menu / Accessories / Terminal )

2. Go to the directory where your x config files lives:

```
cd /etc/X11
```

3. Make a backup copy of xorg.conf

```
sudo cp xorg.conf xorg.conf.backup
```

4. Open xorg.conf in your favourite editor (I use gedit)

```
sudo gedit xorg.conf
```

5. Look for "SECTION SCREEN" and find that line that says DRIVER "ATI", and change ATI to MESA

6. Save your changes.

7. Restart X (CTRL+ALT+Backspace or you could always reboot).

Your other alternative is to boot Gutsy from the LiveCD and see how it gets along for a while before you decide whether to install it or not.

---

