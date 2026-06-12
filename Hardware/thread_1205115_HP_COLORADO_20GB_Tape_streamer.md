---
title: "HP COLORADO 20GB Tape streamer"
date: 2009-07-05
forum: Hardware
---

### Post by MarioFromBelgium on 2009-07-05
Hi,

just put in a HP COLORADO 20 GB Tape Streamer(this is an IDE-device) in my UBUNTU 8.01
I just cannot get it to work

from terminal

administrator@server01:/$ sudo mt -f /dev/ht0 status
[sudo] password for administrator: 
mt: /dev/ht0 is not a character special file

wathever I try I always get that error

I know that the Tape-drive ius recognised in the Bios and I believe also UBUNTU has recognised it when I run dmesg, the streamer is mentioned a few times:

[    8.506167] scsi 0:0:1:0: Sequential-Access HP       COLORADO 20GB    4.01 

Now I don't know what this line means but I'm worried about the word scsi...it is an IDE-device.

What can I do to find out what is it that is not working?

---

### Post by marvin81 on 2010-03-14
Hello!

I have just nearly the same problem. My IDE-Travan-Streamer is not even recognized by the system (Kubuntu 9.10). Do you have any idea how I can get this fixed?

The tape drive is on the secondary IDE controller as a slave drive. Is there any way for a direct access?

Thanks for your help!

Cheers! :popcorn:

---

