---
title: "DVD ROM not detected"
date: 2010-03-10
forum: Hardware
---

### Post by drunkenbrawler on 2010-03-10
Hello everyone,
I've been using Ubuntu for some days now.
The problem i'm facing started recently. I have 2 DVD ROMs and I was able to use them without problem for a long time. But few days before i started my PC and the problem is that both the DVD ROMs are not detected. The tray comes out (i think that means Power supply is good) but the DVDs are not read.

I entered BIOS and saw that my Primary IDE master is showing no device and slave was showing some random sting of strange characters (i think usually this is some string of characters but these characters were not alphabets. They were symbols) I dont know what to do. I booted in windows but DVD ROMs are not detected there either. 

What should i do?
I have Ubuntu 9.10 and Windows XP.

---

### Post by khelben1979 on 2010-03-10
You can start with getting yourself a new IDE cable. It might help.

---

### Post by drunkenbrawler on 2010-03-10
hmmm. i'll try dat and post soon

---

### Post by Ferannia on 2010-03-11
Much worse here:

my cd/dvd drive _is_ recognized by BIOS; it clearly lists its name and a model number. When I insert for example the installation CD into the drive, it proceedes with installation menu, and everything is well. Obviously, the drive works and a cable is OK too.

However, it is _not_ recognized by Jaunty 9.04:
dmesg doesn't show a trace from the dvd. All dmesg shows is sda/sda1/sda2/sda3 where two HD reside and swap. Nothing else.

In /etc/fstab I have:
/dev/scd0    /media/cdrom0   iso9660,udf user,noauto,exec,utf8  0    0

Switching places udf<-->iso9660 of course didn't help. THe dvd drive is not recognized by the software in the first place.

There is also no more scd0 or sr0 in /dev. Missing completely.

Everything was well with this very same cd/dvd drive sometimes in October or November last year, Jaunty 9.04 too. I could watch movies, mount data cd, burn dvd on this system, etc...
And then, there was a certain automatic software update, via synaptic, and the dvd drive stopped working after that. Maybe I did something wrong unintentionaly. I am not sure, but I am 99% sure I didn't do anything nasty to the system.

Please, what are possible reasons the drive is not recognized by this software anymore, and how to fix it ?

Thank you.

---

### Post by khelben1979 on 2010-03-11
> **Ferannia said:**
> dmesg doesn't show a trace from the dvd. All dmesg shows is sda/sda1/sda2/sda3 where two HD reside and swap. Nothing else.

Maybe an kernel upgrade messed it up? Have you tried to downgrade to the previous Linux kernel provided by Ubuntu? (You should see it in Synaptic)

---

### Post by Ferannia on 2010-05-09
> **khelben1979 said:**
> Maybe an kernel upgrade messed it up? Have you tried to downgrade to the previous Linux kernel provided by Ubuntu? (You should see it in Synaptic)


It seems it was not only maybe. However, (re)installing in Jaunty restricted kernel modules, backported, previous kernel versions, my own compiled kernel too - nothing helped.

It all almost convinced me that maybe the DVD drive itself is dying.

After a clean installation Lucid Lynx, the drive works again, like new. God knows only what happened with the damned update in Jaunty.

---

### Post by khelben1979 on 2010-05-09
For future refence, you can always check in the log files what the Ubuntu update did to the system:
[URL="http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/"]
View log files in Ubuntu Linux[/URL].

---

