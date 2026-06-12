---
title: "How to setup up HDAPS protection and ubuntu 8.10 with your IBM thinkpad"
date: 2008-12-21
forum: Hardware
---

### Post by pardasaniman on 2008-12-21
Hello everyone... 

First, I must apologize, I cannot write a nice tutorial for this.. I've exhausted myself trying to figure this out.

Description of what I did:
OK, so for starters, I went to [http://permalink.gmane.org/gmane.linux.drivers.hdaps.devel/1393](http://permalink.gmane.org/gmane.linux.drivers.hdaps.devel/1393) , and patched my kernel using using the excellent how to-at [http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/](http://blog.avirtualhome.com/2008/10/28/how-to-compile-a-custom-kernel-for-ubuntu-intrepid/) .  
Fortunately, you needn't compile your own kernel.. you can just use my deb.  

step 1: go [here]("http://www.megaupload.com/?d=E83IY78L"), download & install the linux-image deb.
then install the linux-header deb I've included in this post

reboot into your new kernel

at this point, you should see a file /sys/block/sda/device/unload_heads

step 2
Then go to [http://sourceforge.net/project/showfiles.php?group_id=1212&package_id=171579](http://sourceforge.net/project/showfiles.php?group_id=1212&package_id=171579) and downloaded tp_smapi-0.40 .  Basically, extract the package, and then do a 
"make install HDAPS=1"

It will tell you if it worked OK.  type dmesg to verify

step 3 If all is well, go install from synaptic hdapsd and hdaps-utils... we'll have to butcher those... hdapsd will not work out of the box... **hdaps-gl at the command prompt should work at this point**!

step 4
Then, I went to [http://www.zen24593.zen.co.uk/hdaps/](http://www.zen24593.zen.co.uk/hdaps/) and downloaded and compiled the latest hdapsd
**do a **
gcc [http://www.zen24593.zen.co.uk/hdaps/hdapsd-20081004.c](http://www.zen24593.zen.co.uk/hdaps/hdapsd-20081004.c) -O hdapsd

**you should be able to do this **
sudo hdapsd -d sda -s 15 -a -v -y  
and see accelerometer readings note the -y... you may not need it.. but I did.

OK, you're almost there, copy the hdapsd you just created overtop of the old one from the ubuntu deb, and put it in /usr/sbin/hdapsd

and then, lastly, we need to modify the old hdapsd init script, because the old one won't work... toss in the hdapsd.txt file overtop of the one in /etc/init.d  (be sure to remove the .txt extension)  .. It will only work if your laptop's disk is /dev/sda

and if you're lucky, you might be able to replicate my success.

You'll probably find [http://www.zen24593.zen.co.uk/hdaps/gnome-hdaps-applet-20081204.tar.gz](http://www.zen24593.zen.co.uk/hdaps/gnome-hdaps-applet-20081204.tar.gz) useful for monitoring the state of your disk within gnome...  it has a self explanatory install file.

Good luck!  Again, sorry I haven't put more up... I hope a more capable person can gain something from this and put together a more useful how to... perhaps maybe some deb package including tp_smapi?


**sigh**   At least it's better than the time I had to realize that I'd have to make a modification to the hdaps kernel module (and then I did) to get this to work.

---

### Post by uljanow on 2009-01-05
There is a backport[1] of hdapsd (1:0.0.20081004-1) for intrepid available.


[1]https://launchpad.net/~ssakar/+archive

---

### Post by xepe on 2009-01-05
thanks a lot!!!
i had little trouble compiling the applet but i think i made it.
I have a problem, when i run "sudo hdapsd -d sda -s 15" and move the thinkpad, i get:

write: Operation not supported
Mon Jan  5 18:07:36 2009: parking
write: Operation not supported
write: Operation not supported
read(/sys/block/sda/device/unload_heads): Operation not supported
write: Operation not supported
Mon Jan  5 18:07:37 2009: un-parking

and the applet never changes state, is this ok?

thanks for all!

---

### Post by bonfire89 on 2009-01-19
"then install the linux-header deb I've included in this post"

Where is the linux-header deb?


by the way, thanks for this post, I have been trying to get this to work for over a year.

---

### Post by KennyChen on 2009-01-21
> **bonfire89 said:**
> "then install the linux-header deb I've included in this post"

Where is the linux-header deb?


by the way, thanks for this post, I have been trying to get this to work for over a year.

The "linux-header deb" is at the end of the #1 post.
I have been trying for a long time too

---

### Post by KennyChen on 2009-01-21
Hi everyone,
I have a problem.I have installed the tp_smapi package.And now I can control my battery by using tp_smapi.
But when I type "dmesg" to verify.I found someting wrong.
```

[   20.149669] thinkpad_ec: thinkpad_ec 0.37 loaded.
[   20.153050] tp_smapi 0.37 loading...
[   20.153191] tp_smapi successfully loaded (smapi_port=0xb2).
[   20.182128] hdaps: initial mode latch is 0x01
[   20.182237] hdaps: setting ec_rate=250, filter_order=2
[   20.182456] hdaps: device successfully initialized.
[   20.182516] input: ThinkPad HDAPS joystick emulation as /devices/virtual/input/input9
[   20.212148] input: ThinkPad HDAPS accelerometer data as /devices/virtual/input/input10
[   20.240114] hdaps: driver successfully loaded.

```

It is "tp_smapi 0.37" not "tp_smapi 0.40"
Why?:(

---

### Post by bonfire89 on 2009-01-22
> **KennyChen said:**
> The "linux-header deb" is at the end of the #1 post.
I have been trying for a long time too

lol oh my, I missed that, it is so seldom that a file is attached like that. Thanks!

---

### Post by TobiWan88 on 2009-01-24
Worked great thanks;)

---

### Post by albertomagana on 2009-01-31
In Point #4 will be (assuming that you have the .c source on the same folder)

gcc -o hdapsd hdapsd-20081004.c

maybe its too easy and clear, but for the noobs..

---

### Post by TobiWan88 on 2009-02-05
Has anyone tried the 2.6.27-11 kernel? Do I have to patch it?

Edit: I tried it. Without patch it does not work, but the above procedure still works!

---

### Post by pardasaniman on 2009-02-09
> **xepe said:**
> thanks a lot!!!
i had little trouble compiling the applet but i think i made it.
I have a problem, when i run "sudo hdapsd -d sda -s 15" and move the thinkpad, i get:

write: Operation not supported
Mon Jan  5 18:07:36 2009: parking
write: Operation not supported
write: Operation not supported
read(/sys/block/sda/device/unload_heads): Operation not supported
write: Operation not supported
Mon Jan  5 18:07:37 2009: un-parking

and the applet never changes state, is this ok?

thanks for all!

Does /sys/block/sda/device/unload_heads exist?

---

### Post by xepe on 2009-02-09
yes, /sys/block/sda/device/unload_heads does exist, and i get the same messages over and over again T_T .

---

### Post by zhwu on 2009-02-19
Great post, thanks for sharing! But I can't make it work on my X61 because I'm running 64bit version of Ubuntu 8.10... Hope somebody there will make an update for this before I figure out how to patch kernel 2.6.27-12 on my own.

---

### Post by zhwu on 2009-02-21
Finally I got a change to work on it, now I have the kernel(2.6.27-12.28) patched, compiled and installed successfully. hdaps-gl works now, but I can't get the /etc/init.d/hdapsd work for the following error:
 * Not starting hdapsd: /sys/block/sda/queue/protect does not exist, please read /usr/share/doc/hdapsd/README.Debian

Anyone got the same issue?

---

### Post by zhwu on 2009-02-21
Well, after several modifications to the /etc/init.d/hdapsd, now it works :)
Basically I just switched to /sys/block/sda/device/unload_heads...

---

### Post by pardasaniman on 2009-04-17
Right... I totally forgot that I may have had to do that!!

---

### Post by John Baptist on 2009-07-15
I have an older ThinkPad (T41p) that supports HDAPS but I couldn't get it working under Ubuntu, even after following these directions. The problem is that the disk interface is obsolete and it doesn't report to the OS that it supports head parking. The result is that hdapsd couldn't write to the unload_heads file in /sys and as a result the drives didn't get stopped, even though everything was apparently loaded.

Then I read this: [http://www.mjmwired.net/kernel/Documentation/laptops/disk-shock-protection.txt](http://www.mjmwired.net/kernel/Documentation/laptops/disk-shock-protection.txt)

So, to deal with my situation, hdapsd supports a -f flags. This flag tells it to send a special -1 to unload_heads which forces the kernel module to try to park the heads, even if it thinks it can't. If you start hdapsd with the -f flag, everything works!

You can add the -f flag to hdapsd by editing the OPTIONS line in /etc/init.d/hdapsd

Hope this helps!

---

