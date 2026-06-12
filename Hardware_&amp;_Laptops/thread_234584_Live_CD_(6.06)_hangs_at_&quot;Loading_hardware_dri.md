---
title: "Live CD (6.06) hangs at &quot;Loading hardware drivers&quot; - Vaio Z505R"
date: 2006-08-11
forum: Hardware &amp; Laptops
---

### Post by rrnwexec on 2006-08-11
I am having an issue using the Live CD (6.06). I am attempting to boot from a Sony Vaio pcg-z505r notebook with external CD-ROM drive (CD51/A) without success. This is a PCMCIA based drive. 

I've noticed a couple of things:

1) In order to get as far as "Loading hardware drivers..." I had to enter a Boot option as follows:
[INDENT][FONT="Courier New"]   ide2=0x180,0x386[/FONT][/INDENT]
If above line is not entered as a Boot option, the boot process fails early and hard.

2) Once I get as far as "Loading hardware drivers..." the system appears to disable the CD-ROM momentarily (I see the Power & Busy indicators on the CD-ROM go dark, then Power lights up again), but no further access to the drive occurs. After about a minute or so i get:
[INDENT][FONT="Courier New"]  Loading hardware drivers...      [fail]
  [4295081.351000] Buffer I/O error on device hde, logical block 10267
  [4295081.351000] Buffer I/O error on device hde, logical block 10268
  [4295081.352000] Buffer I/O error on device hde, logical block 10269[/FONT][/INDENT]
  .... (many more messages similar to above)

I suspect that a hardware driver is loading (or trying) that tramples CD-ROM I/O just long enough to screw things up... just a hunch.

Any tips or pointers appreciated. 

Thanks in advance,
Randall.

---

### Post by aiki_mllr on 2006-08-12
Similar issue, similar machine.  
PCG-Z505JS with PCGA-CD51.  

Similar I/O complaints, in addition, SQUASHFS complaining about sb_bread failure to read a block, can't free a cache block, can't read an inode, and a nice hard freeze at that point.

I'm grabbing the alternate ISO now to see what I can do with a text install, but my skills are rusty to nonexistent.  Last time I played with Linux it was RH 4.1 or so.

I'll let you know the outcome.  In the meantime, this is an interesting link for Linux (specifically RH) on the Z505 series, though I'm sure you've seen it already:

[http://www.foogod.com/z505-linux/](http://www.foogod.com/z505-linux/)

Cheers,
d.b.

---

### Post by aiki_mllr on 2006-08-13
Yup, went with the alternate iso so I could have a text interface.  Install went smooth and flawlessly.  There was no need to tweak anything at all in the install, defaults all the way.

I've got some tuning I'll want to do, but I'm quite impressed at the performance so far.

Posting now from the Z505JS.  M'wife is happy--the 5-year-old dot-com spoils laptop that had been sitting in the closet unused has new life for her.

G'luck on your install,
d.b.

---

### Post by rrnwexec on 2006-08-28
Good to hear that it worked :)

BTW, which iso did you end up using? I would like to dust off my z505r and give it another go.

Thanks in advance,
Randall.

---

### Post by aiki_mllr on 2006-08-28
I used the ubuntu-6.06.1-alternate-i386.iso.  Still trying to work out some madwifi issues (no WPA, network-manager not regcognizing the card, though if I throw my wireless router wide open & hard code the SSID on the laptop, it connects fine).

The wife, though, thinks I'm the best thing since buttered toast as she has the reasonably fast old laptop with no ties to Billy Gates.

G'luck to you, and drop a line if you need a hand--it'd be great to get that Z505R of yours going.  I'm sold on Ubuntu.

---

### Post by rrnwexec on 2006-08-30
d.b. Thanks very much for the helpful advice. The alternate iso worked great. Burned it to a CD and booted from the Sony drive flawlessly.

Torrent link is here for those who come after us:
[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso)

I used the OEM install which is exceptional in that it creates a temporary account that can be used to configure all the settings, and then be removed with a single command so the first boot will be flawless for a new user. Great idea.

One issue I am seeing is the sound on the z505r seems to have an issue: clicking noises, lots of them. Did you experience this? If so, know any workaround? (I've temporarily disabled ESD support in Gnome to get around it, but that's less than ideal as I need sound).

Also, the memory stick slot needs to be disabled in BIOS otherwise the system will kick out a bunch of errors about hdc at boot time.

I'm using the built-in (wired) ethernet for network, which also worked flawlessly. However, I am looking for a USB wifi (802.11b/g) dongle that is supported without having to load any special drivers or perform other kernel magic tricks. Suggestions?  (I'll open a thread in networking forum too.)

Thanks again.

Cheers,
Randall.

---

