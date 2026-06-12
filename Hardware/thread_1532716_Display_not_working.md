---
title: "Display not working"
date: 2010-07-16
forum: Hardware
---

### Post by nearo on 2010-07-16
Hello,

I recently bought a new Sony Vaio VPC-Y21s1e. Everything is working correctly except the touchpad and the screen. This thread is about the screen issue.

When I turn on the laptop I can see the bios and grub, then I see the Ubuntu logo for a few seconds and finally the screen turns black. The backlight is still turned on. When I connect an external screen the laptop will automatically 'mirror' the screen. According to the 'monitor preferences' menu the laptop's screen is detected and is being mirrored by the external monitor. I tried other resolutions etc but it's still not working.
I tried to disable acpi, "acpi=off"
Even ctrl-alt-f1 does not work with the build in display, but only on the external screen.

Ubuntu 10.04 32-bit
Tried OpenSuse 11.3 (more recent kernel etc, but not working either)
Intel SU5400
Intel HD Graphics

attached files: lspci and xorg's log.

---

### Post by Ray Hamilton on 2010-07-18
Do you know whether you have an Intel graphics card?  If so, this worked for me:

[http://ubuntuforums.org/showthread.php?t=1530105](http://ubuntuforums.org/showthread.php?t=1530105)

---

### Post by nearo on 2010-07-18
I do have an Intel card, graphics HD.
I tried your solution but unfortunately it doesnt work.

Thanks for your help though.

---

### Post by nearo on 2010-07-31
gabelstapler (I can not send you back a direct message): I have attached an external screen for the time being. I think it's best to report a bug and hope it will be fixed in 10.10.

---

### Post by nearo on 2010-08-06
I did not find a solution for this problem, however, I found a solution for the problems with the touchpad on this Vaio. Boot with the kernel parameter i8042.nopnp and your touchpad will work. Unfortunately multitouch is not (yet) supported. 

If anyone knows a (possible) solution or an open bug report on the problem with the display, please let me know by posting a reply.

---

### Post by utilitytrack on 2010-08-06
to **nearo**

Don't worry, I think that all will work properly. But I should say that laptops from SONY it's generally bad choice with respect to Linux.

Please post on forum (attachments it's inconvenient)
```
uname -r
```
and
```
$ lspci -nn
```
also
```
# cat /var/log/kern.log
```

Edit:
Now I exactly can say that your problem caused by buggy i915 kernel module. May be it already fixed (in 2.6.35, try to look in git), and in this case you should will to upgrade the kernel. Prepare yourself to this.

PS
Read this thread: [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg808097.html]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg808097.html")

---

### Post by nearo on 2010-08-06
uname -r
2.6.32-21-generic

See attachments for the output of the other commands.

Did this from a fresh ubuntu 10.04 live usb. Problem still exists in an up to date 10.04 install.

---

### Post by nearo on 2010-08-08
Unfortunately, this bug is not the same as the one you mention.
1. According to the bug report the problem is solved in 2.6.35rc6, I tried Ubuntu 10.10 alpha 3 which has an even newer kernel and the problem still exists.

2. "Starting X failed and froze the whole machine (flashing LEDs).". X does not fail. I can attach an external monitor as a workaround. Internal monitor is detected correctly, backlight is turned on and off when I enable or disable the screen. It does show grub, and it shows some text during boot when i disable quiet boot. However, after a few seconds nothing is displayed anymore but the backlight is still turned on. Using the vesa-driver does not help, internal display remains black.

---

### Post by chrislang on 2010-08-13
Hi Nearo, I've also got a sony viao VPCY21s1e and I've got exactly the same problem. I've tried lots of different things without success. Just thought I'd let you know that it's not just you....

---

### Post by nearo on 2010-08-15
tried 10.10 daily, still the same problem.

---

### Post by alpera on 2010-08-16
Hello,

I was thinking to purchase a y21s1e also because of the light weight and battery life. what is your suggestion? this bug gonna solved later, should i wait or go for a netbook? thanks much.

---

### Post by nearo on 2010-10-08
If you want to run Linux, you should buy another laptop.

---

### Post by gabriel_celeste on 2011-01-14
Hi,

I was also thinking about purshase this laptop and I found this tutorial:[http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e]("http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e").

---

### Post by gabriel_celeste on 2011-01-14
Hi,

I was also thinking about purshase this laptop and I found this tutorial:[http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e]("http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e").

---

### Post by chrislang on 2011-02-01
Has anyone successfully used this tutorial? 

[http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e](http://askubuntu.com/questions/19027/ubuntu-on-the-sony-vaio-vpcy-21s1e)

I installed alternate amd64 ubuntu 10.10 using a CD. Everything went OK, except "Network configuration failed". After installing, I booted the computer but only got a text log in - no graphics. 

I used "sudo vi /etc/default/grub" to edit out the "nomodeset" bit. But the links to the 2010-12-24 snapshot of 2.6.37rc3 don't work any more. 

I've found these:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-01-27-natty/linux-headers-2.6.38-997-generic_2.6.38-997.201101270909_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-01-27-natty/linux-headers-2.6.38-997-generic_2.6.38-997.201101270909_amd64.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-01-27-natty/linux-headers-2.6.38-997_2.6.38-997.201101270909_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-01-27-natty/linux-headers-2.6.38-997_2.6.38-997.201101270909_all.deb)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-01-27-natty/linux-image-2.6.38-997-generic_2.6.38-997.201101270909_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-next/2011-01-27-natty/linux-image-2.6.38-997-generic_2.6.38-997.201101270909_amd64.deb)

But I don't know how to download or install these from a command line. And I've no idea whether these are the correct packages to install.

I feel like I'm nearly there, but I'm now stuck.

---

