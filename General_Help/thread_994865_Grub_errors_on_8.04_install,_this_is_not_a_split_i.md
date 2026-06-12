---
title: "Grub errors on 8.04 install, this is not a split install, only have ubuntu installed"
date: 2008-11-27
forum: General Help
---

### Post by patrickberry on 2008-11-27
Hi all,

I have a work pc that that only has 8.04 installed. No hd partitions.

I get a mix of grub error 18 and 15 every so often when i switch in.

It does not happen always, just sometimes.

All the info I have been able to find refers to ubuntu installs in combination with another OS. This is not my case.

Is there a simple way to clean up my grub errors? I am not a techie, just a guy trying to work on his pc.

cheers in advance
Patrick

---

### Post by caljohnsmith on 2008-11-27
Since the Grub errors are not consistent, you might have a hardware problem. How about at the Grub menu, choose the "memtest86+" option and let that run for a while to see if it finds anything wrong with your RAM. Also I would recommend checking your HDD's health to see if that is an issue. If you don't have a CD that came with your HDD, you can download the [Ultimate Boot]("http://www.ultimatebootcd.com") CD and run HDD diagnostic tests using that. Let me know how that goes.

---

### Post by patrickberry on 2008-11-27
Hi,

thanks for the response,

I have tried running the memorytest thing, but that takes hours!!,

I will let it run all night tonight and see what happens,

I have gotten into my pc using the .iso live cd thing, and just told it to run fomr installed version ...

Its my work pc, not a mess around machine, so its kind of important to feel I am working in a safe OS/hardware mix environment.

cheers
patrick

will report back tomorrow.

---

### Post by 10barhead on 2008-12-10
I'm in the same boat give or take. Have single install of Hardy Heron 8.04.1 on hard drive and get error 15 every time I start up. This is my third day at trying to fix it just so I can get in there to harvest my files and address book before I either go for a complete re-install, fire it out the window or just buy a new laptop and curse the day I ever was tempted to .......But anyway, any ideas? BTW, I'm not a techie either, so, any answers in just plain English please.
I can boot up from install disc but can't get into the hard drive from that and I'm not sure what to do from Terminal or how to tweak whatever from install process.

Thanks.

---

### Post by caljohnsmith on 2008-12-10
10barhead, do you get the Grub error 15 before seeing a Grub menu, or before seeing the text "Press ESC to see menu", or do you get the error after selecting Ubuntu in the Grub menu? How about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by 10barhead on 2008-12-10
Hello there CalJohnSmith,
thanks for reply. When I switch the machine on, the only thing I see is Grub Error 15. I haven't seen any menu or esc option at all.

Will go to Terminal now and let you know what I get back shortly.

---

### Post by 10barhead on 2008-12-10
Hello again,
here is the output of sudo fdisk -lu

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    75168134    37584036   83  Linux
/dev/sda2        75168135    78140159     1486012+   5  Extended
/dev/sda5        75168198    78140159     1485981   82  Linux swap / Solaris

---

### Post by 10barhead on 2008-12-10
Now I'm a bit baffled, sorry, but I'm don't know what to enter for the next part -sudo xxd -l 2 -p /dev/sda. I didn't think I was right but I tried it like this anyway

ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sda1
0000
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-10
10barhead, how about instead doing:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. Reboot, and let me know if you still get the Grub error 15.

---

### Post by 10barhead on 2008-12-10
Thanks,
so far this is what I have:

grub>
       root (hd0,0)

grub>
      setup (hd0) 
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub>

Now I'll proceed to the quit stage and let you know -that is if I can still see the outcome as I mightn't see any more once I enter quit.

---

### Post by 10barhead on 2008-12-10
Ok,entered quit, which brought me back to initial terminal window, then I rebooted. Same story, Grub stuck on error 15. Hmmm....

---

### Post by caljohnsmith on 2008-12-10
OK, next try:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
ls -lR /mnt/boot
```
Note "-l" is a lowercase L, not a one.

---

### Post by 10barhead on 2008-12-10
Here goes...

ubuntu@ubuntu:~$ sudo /dev/sda1 /mnt
sudo: /dev/sda1: command not found
ubuntu@ubuntu:~$ ls -l /mnt
total 0
ubuntu@ubuntu:~$ ls lr /mnt/boot
ls: cannot access lr: No such file or directory
ls: cannot access /mnt/boot: No such file or directory
ubuntu@ubuntu:~$ 

...am I doing this correctly I wonder?

---

### Post by 10barhead on 2008-12-10
Here goes...

ubuntu@ubuntu:~$ sudo /dev/sda1 /mnt
sudo: /dev/sda1: command not found
ubuntu@ubuntu:~$ ls -l /mnt
total 0
ubuntu@ubuntu:~$ ls lr /mnt/boot
ls: cannot access lr: No such file or directory
ls: cannot access /mnt/boot: No such file or directory
ubuntu@ubuntu:~$ 

...am I doing this correctly I wonder?

---

### Post by 10barhead on 2008-12-10
Getting a bit late here for me now so I'll come back tomorrow. Thanks for all the help so far. Good night.

---

### Post by patrickberry on 2008-12-11
Hi there,

I get around the problem with having the live cd in the cd reader when i switch on the pc.

i then choose to load from the hard drive. It works for me. No idea why, just does.

---

### Post by 10barhead on 2008-12-11
Thank you patrickberry,
sadly,  it didn't work for me though. I got cd drive open, put in the installation disc (-is this the same as "live" cd?), switched on, but still stuck at Grub stage 1.5 with error 15.

---

### Post by caljohnsmith on 2008-12-11
How about trying the commands I gave in post #12 again, but please either copy/paste them if you can, or try to avoid typos if you have to type them in by hand. You missed the "mount" part of the command in your post #13, which is why it didn't work. How about giving that another shot and let me know the results.

---

### Post by 10barhead on 2008-12-11
Hello again caljohnsmith,
my apologies for that error. I've redone as you suggested, pasting the whole lot in in one go. Here's the output:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 already mounted or /mnt busy
mount: according to mtab, /dev/sda1 is already mounted on /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 16
drwx------ 2 root root 16384 2008-12-09 13:36 lost+found
ubuntu@ubuntu:~$ ls -lR /mnt/boot
ls: cannot access /mnt/boot: No such file or directory
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-12-11
According to the output you posted, something must have gone wrong while installing Ubuntu, because the main Ubuntu sda1 partition only has a "lost+found" folder right now, nothing else. I would recommend reinstalling, and let me know if the installer reports any errors during installation. If you would like a good step-by-step guide for installing Ubuntu, how about giving this a try:

[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html) 

Let me know how that goes.

---

### Post by achase79 on 2008-12-11
I read somewhere else that it may be a corrupted partition table.

---

### Post by 10barhead on 2008-12-11
Cheers,
I thought that might be the case. Hmmm...is it possible to do this without losing all my files, email address book and so on?

---

### Post by caljohnsmith on 2008-12-11
> **10barhead said:**
> Cheers,
I thought that might be the case. Hmmm...is it possible to do this without losing all my files, email address book and so on?
You could try looking in the "lost+found" directory by doing:
```
sudo mount /dev/sda1 /mnt
gksudo nautilus /mnt
```
And browse the "lost+found" folder to see if there is anything in it. If not, probably the only way to get back your files would be to use a program like "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")", but you will need a drive with as much space as your sda1 partition for photorec to put all the recovered files in. Also, it's a lot of trouble trying to sort through all the thousands of files that photorec will recover to find what you want. I would only use photorec if you really need your files desperately, but it's up to you of course.

---

### Post by 10barhead on 2008-12-11
Files are desperately needed so I'll try photorec and then go far a reinstall. I have an external drive that should do the job, I hope. Thanks again for all your help. I'll post back with the end of the story.

---

### Post by silverglade00 on 2008-12-11
I got the same error before. Turns out I had my iPod plugged in and it messed up the partition ordering. Unplug iPod and reboot fixed it. Any external drive might do it, flash drive, jump drive, external cd drive, etc.

---

### Post by silverglade00 on 2008-12-11
.

---

