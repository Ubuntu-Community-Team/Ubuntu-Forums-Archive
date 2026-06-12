---
title: "Mounting iPod touch?"
date: 2008-01-02
forum: Hardware &amp; Laptops
---

### Post by runemaste644 on 2008-01-02
Im wondering if i can use the regular mount command to mount my iTouch. I refuse to jailbreak it so i dont void the warranty. Pretty much all i need to know is what device it is in /dev/

---

### Post by blu3ness on 2008-01-02
just restore it and you'll have your warranty back, refusing to jailbreak iTouch is like refusing to use Linux! *gasp*

---

### Post by runemaste644 on 2008-01-05
well i at least want to charge it from linux; and if i had a mac, refusing to jailbreak wouldnt be refusing to use linux (Macs are bsd unix) and restoring my itouch would give me my warranty back? that makes no sense...

---

### Post by itsJim on 2008-01-07
> **runemaste644 said:**
> well i at least want to charge it from linux; and if i had a mac, refusing to jailbreak wouldnt be refusing to use linux (Macs are bsd unix) and restoring my itouch would give me my warranty back? that makes no sense...

What doesn't make sense? If you restore your ipod touch how are they ever going to know you jailbreaked yours? Hence you get your warranty back.

---

### Post by runemaste644 on 2008-02-21
ok i finally did jailbreak, but how do i mount it in feisty? Its being rather stubborn with me. And unless you can tell me how to charge it via ssh, i dont want to hear about ssh.

---

### Post by ntetreau on 2008-02-22
> **runemaste644 said:**
> ok i finally did jailbreak, but how do i mount it in feisty? Its being rather stubborn with me. And unless you can tell me how to charge it via ssh, i dont want to hear about ssh.

Hi, you made the right call jaibreaking your ipod touch.  Now you need to get it going with Linux, trust me, in the end it will work very well.  The only problem I can see is that you'll most probably need to upgrade your Feisty to Gutsy.  Once you've done this, it will charge via USB automatically.  Then you will install the package ipod-convenience as well as an updated libgpod which will enable you to sync music and album art via Amarok and gtkpod (not sure about rhythmbox). Once properly setup, there is no need for command line or playing with ssh directly.

When you're done with the update to Gutsy (shouldn't take more than an hour normally) you need to follow this wiki to the letter:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

if you have problems, you can search, read and post in this thread:
[http://ubuntuforums.org/showthread.php?t=588246](http://ubuntuforums.org/showthread.php?t=588246)

Good luck

---

### Post by runemaste644 on 2008-03-01
the problem is, that i cant upgrade to 7.10 or it will break my system

---

### Post by ntetreau on 2008-03-04
Sorry to hear that.  However, the bottom line is that to charge your touch in Linux, you will need the kernel driver which is not available to pre-Gutsy systems as far as I know.  Then, there is no way transfer music to it under linux unless your jailbrak it.  This does not void your warranty as long as you restore it using iTunes prior to seeking help from Apple.  You might be better to dual boot at the moment until you are able to upgrade.

---

### Post by bwang on 2008-03-04
How come upgrading will break your system?

---

### Post by stevensonfire on 2008-04-07
my itouch is jailbroken 
and when i 
ipod-touch-mount 
i get 
"iPod is not responding to pings at ipod.
Please set the environment variable IGNOREPING if you want to ignore this."


what am i suppose to do?

---

### Post by runemaste644 on 2008-04-12
> **bwang said:**
> How come upgrading will break your system?
i used wubi and then i cant use loopmounted virtual partitions if i upgrade

---

