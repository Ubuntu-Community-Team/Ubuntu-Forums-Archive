---
title: "unable to mount cd drive"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by jeremytaylor on 2006-06-14
Hi there, 
enjoying dapper but I have a problem with mounting cds/dvds.

When I attempt to mount I get the message:
Unable to mount selected volume, mount:special device /dev/scd0 does not exist.

I have an asus w3v laptop. I had to install a custom kernel to get it working which is probably the problem. I followed the instructions in the howto-tips&tricks [http://ubuntuforums.org/showthread.php?t=157560](http://ubuntuforums.org/showthread.php?t=157560)

My output from dmesg has a number of peculiar errors in but I don't know how to diagnose the problem. I've attached the output here. [ATTACH]11202[/ATTACH][ATTACH]11203[/ATTACH]

Hopefully someone can help me.
Jeremy

---

### Post by wahman143 on 2006-06-14
Hi Jeremy,
I perused your dmesg output and I've got a few ?'s for ya:

1.  can you post the output of 'lspci'?
2.  I'm curious why you are using 'mount /dev/scd' to get the cd-rom drive...if your HDD is sda(x) (where x is the partiton number), then logically your cdrom would be sdb (if it were a scsi/sata cd-rom).  

I think you may have the command input wrong, but I'd like to see the lspci output first.

Cheers,
Wah

---

### Post by jeremytaylor on 2006-06-14
Thanks for the reply, here's my lscpi output.[ATTACH]11206[/ATTACH]

/dev/sdb doesn't seem to exist either. I was actually just using the file browser to mount the drive not the command line but I haven't had much luck with that either.

jeremy

---

### Post by wahman143 on 2006-06-14
Cool - thanks.  

I'd take a look at hda, hdb, hdc, hdd as your optical drive - I say this b/c I've got a Dell D610 laptop with pretty much the same config as you, and although its Hard Drive is SATA, the optical is a regular IDE (also, I've only seen SATA opticals for desktops)...and it uses /dev/hdc as its node.

Cheers,
W.

---

### Post by brandt on 2006-06-15
Actually, I'm having the same problem.  /dev/scd0 is the correct device name.  Here is the listing from the fstab generated during install:

```

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

In my case, the node is generated and everything works fine under the stock 2.6.15-23, but isn't generated if I boot from my 2.6.16 kernel even though I used the same .config file.  I'm using a thinkpad z60t and according to [www.thinkwiki.org](www.thinkwiki.org), the problem is caused when ide and sata support are loaded in a particular order.  I tried to fix the load order but either I didn't do it correctly or it's not the solution.  I'd be interested to see if anyone else has any ideas.

---

