---
title: "Ubuntu won't open old hard drive."
date: 2007-09-30
forum: Hardware &amp; Laptops
---

### Post by jtllogan on 2007-09-30
Hi,
I'm very new to Linux and Ubuntu. I just got a new computer and since I was fed up with Windows, I decided to try Ubuntu. I wanted to install my old hard drive into my new machine and Ubuntu will not let me view the files on the old hard drive. It is from a hp computer and the only thing that shows up is the hp recovery partition. Can anyone help me with this? I want to get my documents off of the drive and re- format it.

---

### Post by brad103 on 2007-09-30
Have you connected the drive as a secondary IDE connection?

See what you get when you run:
$ sudo cfdisk /dev/%%%
where %%% is the hard drive device name. Your primary drive may be hda, and your secondary could be hdb (or sda and sdb if you hava SATA drives)
Just select quit once cfdisk opens and you get the details.

---

### Post by jtllogan on 2007-09-30
My Primary drive is SATA Master and I have the old drive connected as IDE Master on the secondary IDE connection. 

I ran cfdisk and got:
FATAL ERROR: Cannot open disk drive

Any other suggestions?

---

### Post by brad103 on 2007-09-30
You'll get that error when it can't find the drive.

Try:
$ sudo cfdisk /dev/hda
and
$ sudo cfdisk /dev/hdb

How do you see the HP recovery partition? Does it appear on your desktop?

---

### Post by jtllogan on 2007-10-01
Tried it. Same result. Yes, I can see the HP recovery drive on desktop but the rest of the drive is off limits.

---

### Post by brad103 on 2007-10-01
Try the command

$ mount

This lists all currently mounted file systems. Look for your HP drive and see if you can get the correct /dev/%%% from there. Paste the output of the command here if you want.

Persevere with Linux, it's worth it :)

---

### Post by idkwot on 2007-10-01
> **brad103 said:**
> Try the command

$ mount

This lists all currently mounted file systems. Look for your HP drive and see if you can get the correct /dev/%%% from there. Paste the output of the command here if you want.

Persevere with Linux, it's worth it :)

what he said

---

