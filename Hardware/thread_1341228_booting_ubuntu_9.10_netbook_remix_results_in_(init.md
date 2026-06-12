---
title: "booting ubuntu 9.10 netbook remix results in (initramfs) after last upgrade"
date: 2009-11-29
forum: Hardware
---

### Post by kihitara on 2009-11-29
I have read some of the other threads on here to do with (initramfs) but a lot seems like a different language to me. Does someone speak Noob Language? Thanks.
 
I booted my netbook this morning and after the ubuntu logo got (initramfs) _ with no other message.
 
After forcing shutdown and restarting, it took me to a boot menu, where I chose the first option (standard startup in linux ubuntu). After a while, I got the following message:
 
[SIZE=3][FONT=Times New Roman]Loading please wait…[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/scripts/init-top/briltty: 19: grep: not found[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Gave up waiting for root device. Common problems:[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Boot args (cat /proc/cmdline)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Check rootdelay= (did the system wait long enough?)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Check root= (did the system wait for the right device?)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Missing modules (cat /proc/modules: Is /dev)[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]ALERT! /dev/disk/by-uuid/84b7f9ae-e9b3-44a5-8709-37f5bfb7d8e6 does not exist. Dropping to a shell![/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman](initramfs)[/FONT][/SIZE]
 
I then forced shutdown again, restarted and tried safe mode. Got a whole lot of other errors, but it ended with the same:
 

[SIZE=3][FONT=Times New Roman]Gave up waiting for root device. Common problems:[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Boot args (cat /proc/cmdline)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Check rootdelay= (did the system wait long enough?)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Check root= (did the system wait for the right device?)[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]-[/SIZE] [SIZE=3]Missing modules (cat /proc/modules: Is /dev)[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]ALERT! /dev/disk/by-uuid/84b7f9ae-e9b3-44a5-8709-37f5bfb7d8e6 does not exist. Dropping to a shell![/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman](initramfs)[/FONT][/SIZE]
 
I am running a Toshiba NB200. Help! Have I lost everything?

---

### Post by kihitara on 2009-11-29
I have since this morning decided to reinstall Ubuntu completely, after following the instructions of several "fixes" and none working. I have installed just the regular Ubuntu 9.10 (not the netbook remix), have done the update / upgrade via the command line, and it seems to reboot... but I do have to wonder how long it will work for this time. I had a stable install of Linux before. Does this mean I should just not do any updates? Because every time I've broken Ubuntu, it has been because of an update.

---

### Post by beloved88 on 2009-11-29
As a fellow noob, i have a similar sentiment.  Updating seems iffy as I've perused the forum and from my own experience.  I've found a good number of people that swear by LTS versions only.  I've come to the conclusion that "if it ain't broke, don't fix it." I've had the best luck with Jaunty, so i'm gonna stick with it till Lucid is released, even then, i'm giving it a good month or two until i switch over. Everything accept bluetooth seems to work atm, and it's not crucial that i get that fixed any time soon.

---

### Post by beloved88 on 2009-11-30
oh, and i also encountered the (initramfs) issue too, but it went away when i installed off of a LiveUSB made with ImageWriter instead of USB Startup Disk Creator...

---

### Post by cpttripzz on 2009-12-14
I had the same issue. I fixed this issue by chrooting into the old root directory

see this article [http://ubuntuforums.org/showthread.php?t=1156240]("http://ubuntuforums.org/showthread.php?t=1156240")

and then running sudo apt-get update; sudo apt-get dist-upgrade

Hope this helps everybody else with this problem.

---

### Post by marcasl on 2009-12-28
I had the same messages when booting to Ubuntu after Windows 7 auto-hibernated.

NB: I'm also using 9.10 netbook remix and GRUB 2!

Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules: Is /dev)
ALERT! /dev/disk/by-uuid/299284d2-0a19-4d89-8187-06ea0bb11807 does not exist.
Dropping to a shell!

That's right, from this shell I can look at the contents of the /dev/disk/by-uuid directory and see that ID is absent:
(initramfs) ls /dev/disk/by-uuid
...

I was able to repair this via the GRUB boot loader. 
When you see: 
" 'e' to edit the commands " 
you can hit 'e' and see the commands used by GRUB to boot Ubuntu.

You can also hit Ctrl-x to boot, after making any modifications here. I was successful after replacing the root directive on the line with the "linux" command (just before the final "initrd" command).

Note: I have Linux root (hd0,5) i.e. /dev/sda5 so I replaced:
root=UUID=299284d2-0a19-4d89-8187-06ea0bb11807 ro quite
with:
root=/dev/sda5 ro quiet

Then: Ctrl-x

That got Ubuntu to boot OK. Then I reconfigured GRUB 2 in the usual way:
$ sudo update-grub

Note: I don't know why, but the root directive is still using /dev/sda5 and not the original style root=UUDI=...., although I have not uncommented GRUB_DISABLE_LINUX_UUID=true in /etc/default/grub.

GRUB 2 obviously has a few surprises in store for us, yet ;)
& I still don't know why Windows 7 auto-hibernation caused the problem.

---

### Post by dtobias on 2010-06-29
> **marcasl said:**
> 
When you see: 
" 'e' to edit the commands " 
you can hit 'e' and see the commands used by GRUB to boot Ubuntu.

You can also hit Ctrl-x to boot, after making any modifications here. I was successful after replacing the root directive on the line with the "linux" command (just before the final "initrd" command).

Note: I have Linux root (hd0,5) i.e. /dev/sda5 so I replaced:
root=UUID=299284d2-0a19-4d89-8187-06ea0bb11807 ro quite
with:
root=/dev/sda5 ro quiet

Then: Ctrl-x



I followed these directions but when I hit Ctrl-x I got a black screen, nothing.  After restarting I saw that my root commands had not changed.  

I am using GRUB 1.97~beta4, could that be part of why this didn't work for me?

---

### Post by mikewhatever on 2010-06-29
It could well be that your root partition is not sda5. Check your /etc/fstab to find out.

---

### Post by dtobias on 2010-06-29
> **mikewhatever said:**
> It could well be that your root partition is not sda5. Check your /etc/fstab to find out.

When I pressed 'e' to make the change I found that it was sda1.  Is this something I need to change?

---

### Post by dtobias on 2010-06-29
This post suggests I might be missing my modules

[http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html](http://www.dedoimedo.com/computers/ubuntu-initrd-bug.html)

---

### Post by mikewhatever on 2010-06-29
So, if root is on sda1 in your case, did you use sda1?

---

### Post by dtobias on 2010-06-30
> **mikewhatever said:**
> So, if root is on sda1 in your case, did you use sda1?

Ahh, I understand your question now.

In the above instructions I used a 'sda1' instead of a 'sda5'.  After making the above change I got a black screen on the boot and after restarting everything went back to how it was.

---

### Post by TheAsarya on 2010-07-23
Hi, 

I had similar problems but now it's fixed my boot up time is ridiculous.

I just upgraded 9.10 to 10.04 on my NB200 netbook. I also had the "Gave up waiting for root device" problem. I solved this by using the previously provided solution replacing 

root=UUID=299284d2-0a19-4d89-8187-06ea0bb11807 ro quiet
with:
root=/dev/sda5 ro quiet

however, boot up time is now something like ten minutes (hence I thought the fix wasn't working the first few times). argh. I have run sudo update-grub, with no effect. I still have to edit the command at boot up to get it to boot at all and then have to wait ten minutes or so to get the login screen. Any help, mainly to fix the boot time, would be appreciated.

---

