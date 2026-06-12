---
title: "attempting to install ethernet controller driver..."
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by Nachtkriecher on 2009-06-05
hello ubuntu forums. i had a (Ubuntu 6.06.2 LTS) server's network card die in a lightning storm, and am trying to install a new one. here's what i got so far.

bought a new network card, and put it in. when i did lspci i got two ethernet controllers, "Intel Corporation [82541PI and 82545GM] Gigabit Ethernet Controller"

i googled those numbers and found these:
[http://www.intel.com/design/network/products/lan/controllers/82541pi.htm](http://www.intel.com/design/network/products/lan/controllers/82541pi.htm)
[http://developer.intel.com/design/network/products/lan/controllers/82545gm.htm](http://developer.intel.com/design/network/products/lan/controllers/82545gm.htm)

since the 82541PI website had no software section, i downloaded the linux* driver for the 82545GM (not the preboot), put it on a cd, and then on the server, 'cp /cdrom/e1000-8.0.9.tar.gz /home/myusername'

i then unpacked the tar, changed to src directory, and ran make install, all per the readme instructions: [http://downloadmirror.intel.com/9180/eng/README.txt](http://downloadmirror.intel.com/9180/eng/README.txt)

it told me this:
Makefile:71: *** Linux kernel source not found in any of these locations:
Makefile:72:
Makefile:73: *** Install the appropriate kernel development package, e.g.
Makefile:74: *** kernel-devel, for building kernel modules and try again. Stop.

I thought i was doing pretty well until i hit that. any clues?

---

### Post by DBrocks on 2009-06-05
Plug and play is not supported? What's your kernel version?
EDIT: Looks like you will have to compile the driver into your kernel. I'm at school right now, and your text file is blocked by my firewall. :/ I'm heading home in a few, and I'll be back.

---

### Post by Nachtkriecher on 2009-06-05
ifconfig only gives the local configuration.

edit: perhaps it should be noted i skipped the rpm part of the readme instructions:

> To build a binary RPM* package of this driver, run 'rpmbuild -tb
<filename.tar.gz>'.  Replace <filename.tar.gz> with the specific filename
of the driver.

NOTE: For the build to work properly, the currently running kernel MUST
      match the version and configuration of the installed kernel sources.
      If you have just recompiled the kernel reboot the system now.

      RPM functionality has only been tested in Red Hat distributions.


---

### Post by DBrocks on 2009-06-05
I edited my post above too. :p I believe you willl have to recompile your kernel. I'll be back in about half an hour whilst I walk home from school.

---

### Post by Nachtkriecher on 2009-06-05
haha wow i was really confused for a moment there.

my kernel version is 2.6.15-54-server

i really hope i dont have to recompile.... it's not my server, i work for my university, and honestly im a linux noob.

---

### Post by DBrocks on 2009-06-05
Alright well I'm home now :p And I think I have a solution to your problem. You will NOT need to recompile your kernel. If you open the Makefile in the src directory of the driver, and scroll down to line 72 or so, you will see a list of directories. What that list is, is a list of directories to search for the linux kernel headers (used for compiling). I even tried making/installing the same driver on my server, and I got the exact same error. No biggie though, all you have to do is punch this in exactly as it's typed:

```
sudo apt-get install linux-headers-$(uname -r)
```
"uname -r" gives the exact number of the Kernel version you are using. This basically takes out the possibility of screwing up your number, as this has to match perfectly. 

Then try the make install again.

---

### Post by Nachtkriecher on 2009-06-05
i was all excited and was ready to try what you said, unti li remembered... since my server doesn't have internet access i can't do apt-get!

---

### Post by DBrocks on 2009-06-05
Okay well we can fix that. Sorry, i totally forgot you don't have internet access. :o  Post output of 
```
uname -r

```

Linux headers exist in tar.gz's also. Ill see if i can find one.

---

### Post by Nachtkriecher on 2009-06-05
```
uname -r
```
yields
```
2.6.15-54-server
```

---

### Post by mocoloco on 2009-06-05
Not trying to get you off track, but you are aware that 6.06 support ends this month?  It would probably be a good time to upgrade to 8.04 LTS before troubleshooting too much. It's possible you're issue may be solved already in the newer versions.
From my experience upgrading directly from 6.06 to 8.04 goes remarkably smoothly.

---

### Post by Nachtkriecher on 2009-06-05
yes, well, i was aware it is old, not aware that support ends this month, but we will be moving everything to a new server very soon, but we have some things we need to get off it first, and my superiors decided the best way to do that would be to get a new network card *shrug*

---

### Post by DBrocks on 2009-06-05
Sorry to double post, but do you have another working ubuntu box with cd-rw drive lying around? AptOnCd would help get the headers on there.

---

### Post by Nachtkriecher on 2009-06-05
yes, that's how i got the driver on there to begin with. i have not heard of AptOnCd though.

edit: i installed aptoncd and and running it and it doesn't have the package you specify in the list, and i dont see a way to look for more.

---

### Post by DBrocks on 2009-06-05
Alright well I found an alternative. You need two files: [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-54_2.6.15-54.76_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-54_2.6.15-54.76_i386.deb)      and this one:    [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-54-server_2.6.15-54.76_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-54-server_2.6.15-54.76_i386.deb)

Put them on a CD and bring them to your server. Now run 

```

sudo dpkg -i linux-headers-2.6.15-54_2.6.15-54.76_i386.deb

```

Hopefully this should complete successfully. Now do

```
sudo dpkg -i linux-headers-2.6.15-54-server_2.6.15-54.76_i386.deb
```
Headers are now on your server. 
(I tried this and it worked. You should be okay with this)

---

### Post by Nachtkriecher on 2009-06-05
already dl'd the second one, was unsure about dependencies, thanks...

running your commands...

---

### Post by jnw222 on 2009-06-05
seem to need linux-headers or linux-source

---

### Post by DBrocks on 2009-06-05
Yeah the second one depends on the first one. I had to scratch my head for a few minutes figuring out the deps, then I remembered you needed the generic before the server.

---

### Post by Nachtkriecher on 2009-06-05
hmmm.... getting really close.. thanks so much so far...

i ran make install and it screwed up on some permissions thing so i ran sudo make install, and it was good for a while and then it said
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode

i thought hopefully it was nonconsequential, but i did the rest of what it said as close as i could.....

ifconfig still gives just the local.

/lib/modules/2.6.*****/kernel/drivers/net contained no file named e1000.ko, but it did contain a directory with a file called e1000.ko, so i ran all the commands the readme said to on that. insmod never worked, it said something about the file not existing or being a directory or something.

also, i dont understand why the readme says to specify an IP, wont i be given one by my ISP?

---

### Post by DBrocks on 2009-06-05
Okay good, we have the driver installed, now to get it to be included in the kernel. For some reason that e1000.7.gz didnt work for me either. I ignored it, and I was fine. It's basically just a man page for it. Not too important for a driver.

Try running:

```
sudo rmmod e1000
```This deletes any existing modules for the e1000 (IMPORTANT).

```
sudo insmod /var/lib/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.ko
```This inserts the new driver module.

It's asking you for an IP because each computer on a network gets a unique IP. If you are running a server, its probably a static IP. If you are not sure which IP to use, ask a head-honcho what he/she wants :D:D

EDIT: What I think you did was run the modprobe e1000 followed by insmod e1000. In the README, it said to choose one method, but I'm going with insmod, because it worked for me.

---

### Post by Nachtkriecher on 2009-06-05
i also have AIM - it's my forum username without "her" at the end

edit: oops, didn't see your reply

---

### Post by Nachtkriecher on 2009-06-05
so insmod didn't fail this time, (im sure i tried all that before)

ok, so now i need to do the ifconfig eth0 <IP>?

---

### Post by DBrocks on 2009-06-08
Solved. We worked it out on AIM. If anyone else needs help on this, send me a PM.

---

