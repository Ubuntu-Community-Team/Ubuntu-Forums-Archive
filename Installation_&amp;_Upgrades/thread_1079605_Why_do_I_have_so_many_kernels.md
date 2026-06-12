---
title: "Why do I have so many kernels?"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by lesliek on 2009-02-24
I'm using Ubuntu version 8.04.

I'm also using kernel version 2.6.24-16.

If I look at the Grub menu, I'm not invited to use any kernel other than that.

However, when I search my files, I see that I have files relating, not only to kernel 2.6.24-16, but to many later kernels, the latest of which is 2.6.24-23.

Shouldn't I be using the latest? Is there some step I should've been taking as each subsequent kernel was installed to get it to be my working kernel?

Thanks for reading this,

Leslie

---

### Post by kestrel1 on 2009-02-24
Yes, you should be using the latest kernel.
You could edit your grub menu to enable you to boot to the latest kernel, although that is normally carried out automatically when the kernel is upgraded. This step must have been missed during an upgrade.

---

### Post by lesliek on 2009-02-24
Thanks for your quick reply, kestrel1.

I'm afraid something fundamental must be wrong, because the step was missed for 2.6.24-17 through to 23!

I'm sorry that I don't know enough to express myself properly, but could this be related to the fact that upgrading the kernel would've stopped something else from working, say some module built for the -16 version, and so the upgrading was automatically prevented (even though the downloading wasn't)?

Thanks again,

Leslie

---

### Post by hellsgator on 2009-02-24
try installing startup-manager from add/remove applications. it will allow you to chose the right kernel and set it as standard.

---

### Post by lesliek on 2009-02-24
Thanks for replying, hellsgator.

Unfortunately, StartUp-Manager simply reproduces the options in the Grub menu. They do not include any other kernel than the one I'm presently using.

Thanks again,

Leslie

---

### Post by kestrel1 on 2009-02-24
It is possible, but there could be another reason.
From what I recall the last time my kernel was upgraded I was asked a question (forget the wording) but basically it asked if I want to change the Grub menu.
If you post the output from the following command I should be able to tweak your grub menu to enable bothe kernels, just in case there is a problem with the newer one:
```
gedit /boot/grub/menu.lst
```

---

### Post by lesliek on 2009-02-24
I remember that question now that you mention it and I must've been answering it each time in a way that's led to my present situation. I'm not sure why I would've answered it that way--could it have been a default answer?

Anyway, when I look at menu.lst, I find in it in part:

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,1)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

Then, when I go to /boot, I find sitting there all of the later vmlinuz-2.6.24-xx-generic and initrd.img-2.6.24-xx-generic files.

Would it be sufficient to copy the two items I've set out above, paste them in above the existing two, change "16" to "23" wherever it appears in the new entries and then save menu.lst?

Or is there more to it?

Thanks very much for your help, kestrel1.

---

### Post by kyphi on 2009-02-24
First check which kernel you are really using:

```
ls /boot
```

then

```
sudo apt-get update
```

You should be using kernel 2.6.24-23

---

### Post by lesliek on 2009-02-24
Thanks very much for your reply, kyphi (and g'day).

I'm sure I'm using 2.6.24-16, despite having many later versions in /boot, for the reason kestrel1's identified. The output of dmesg confirms that I'm using it.

kestrel1 suggested editing menu.lst and I think I understand how to do that, though I asked for confirmation about it in a post that probably crossed with yours.

As I mentioned in it, I already have the files for 2.6.24-23. The problem is that they're sitting there doing nothing until menu.lst is edited.

Would running update in those circumstances achieve anything useful, like asking me again the question I've been answering wrongly in the past each time I installed a later kernel version?

Thanks again,

Leslie

---

### Post by kestrel1 on 2009-02-24
Do the above first, but if you still have 24-16 then put the below in your menu.lst file: ```
## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-23-generic
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.24-23-generic
```

To do this I would suggest the following ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```
Then ```
sudo gedit /boot/grub/menu.lst
```
Paste the above in the appropriate place in the menu.lst file & save it.
Reboot & press esc to enter the grub menu, unless you see the menu normally & select the 24-23 kernel & see how you go. It can be changed to default later if it works OK.
What you said is right, but there is no real need to have both of the lines duplicated at this point. You only want to see if the kernel works first. You can add the second option later on once you establish that your system is happy with the newer kernel.

---

### Post by kyphi on 2009-02-24
Don't forget to
```
sudo update-grub
```

...and g'day to you too, lesliek.

Re the part of the question dealing with "removal" of old kernel modules, these can be removed via Synaptic.

---

### Post by lesliek on 2009-02-24
Well, the -23 kernel version works satisfactorily, so I'll now proceed as I proposed earlier.

I'm assuming that making the entry for that version first in the list will make it the default.

Also, I'd like to delete everything relating to kernel versions from -17 to -22 inclusive.

I don't see how there can be any harm in that, since I've never used any of them anyway.

Thanks very much for all your help, kestrel1. Everything you said was very clear (as well as being correct!).

Leslie

---

### Post by scouser73 on 2009-02-25
Here is a tutorial for removing obsolete kernels; [http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/")

---

### Post by lesliek on 2009-02-25
Thank you very much for the reference, scouser73.

I now have installed only the -16 and -23 versions of 2.6.24. The first is the one I'd been using until today and the second is the latest and the one I'm now using.

Thanks again,

Leslie

---

### Post by kestrel1 on 2009-02-25
> **lesliek said:**
> Well, the -23 kernel version works satisfactorily, so I'll now proceed as I proposed earlier.

I'm assuming that making the entry for that version first in the list will make it the default.

Also, I'd like to delete everything relating to kernel versions from -17 to -22 inclusive.

I don't see how there can be any harm in that, since I've never used any of them anyway.

Thanks very much for all your help, kestrel1. Everything you said was very clear (as well as being correct!).

Leslie

Yes putting it first in the list will work or if you go near the top of your grub menu.lst file you should see an entry that says default & is set to '0'. If you set this to the kernel you want to boot from that would also work.
If your menu has:
```
## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, kernel 2.6.24-23-generic
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=B4148F7C148F3FFA loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.24-23-generic
```
The kernel you want to boot is the third in the list, but as default is set to '0' you would want to make the default '2'
Hope that makes sense.
I would also suggest copying the second in the list (Recovery Mode) & changing that to look at the 24-23 kernel & set it below you 24-23 boot.

---

### Post by jjpcexpert on 2009-02-25
Make way! This is something to do with wubi.

---

### Post by lesliek on 2009-02-25
I went with parachuting the two -23 entries in on top of the two -16 entries, because I don't know whether changing the default number from 0 will cause problems next time I answer the question on a kernel upgrade about changing menu.lst.

Thanks again

Leslie

---

### Post by kestrel1 on 2009-02-25
> **jjpcexpert said:**
> Make way! This is something to do with wubi.
lesliek, are you running Ubuntu via Wubi?

---

### Post by lesliek on 2009-02-25
Yes, I am. The computer came with Windows pre-installed and it seemed easier to get Ubuntu going with Wubi than to do partitioning. (I wanted to save Windows so that I could be sure to be able to use the internal dial-up modem that came with the machine, if necessary.) I was able in the Windows control panel to make Ubuntu the default OS, so that the presence of Windows doesn't bother me and I have had to use the internal dial-up modem in Windows a few times.

Does the fact that I'm using Wubi mean that any newer kernel versions will have to be added to menu.lst manually regardless of how I answer the question about menu.lst on upgrade?

---

### Post by kestrel1 on 2009-02-25
Not ever done a wubi install, but it looks like this may be the case.
Now that you have the new kernel set to load can you do the:
```
ls /boot
```
& just make sure it is loading.

---

### Post by lesliek on 2009-02-25
Here's what ls /boot shows:

abi-2.6.24-16-generic             initrd.img-2.6.24-23-generic
abi-2.6.24-23-generic             initrd.img-2.6.24-23-generic.bak
config-2.6.24-16-generic          memtest86+.bin
config-2.6.24-23-generic          System.map-2.6.24-16-generic
grub                              System.map-2.6.24-23-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-23-generic

But here's what dmesg shows:

[    0.000000] Linux version 2.6.24-23-generic (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:13:11 UTC 2009 (Ubuntu 2.6.24-23.48-generic)

So I don't THINK there's any question. I'm using the new version and Wubi hasn't affected Grub, which is operating as it suggests on its face.

---

### Post by kestrel1 on 2009-02-25
OK, I think I have woken up now. My brain must have been somewhere else when I said about using the ls command. This will only list the contents of the boot folder.
To check for your kernel version you can go to the following: System -> Administration -> System Monitor & click on the System tab. This will tell you the Kernel version. I think it is in the same place on 8.04, I am currently on 8.10. If you have a problem with that I will have to check when I get home in about 5 hours.

---

### Post by lesliek on 2009-02-25
The System Monitor in 8.04 is in the same place as in 8.10 and shows the same thing as dmesg does--I'm using the most recent kernel. So all is well and Wubi hasn't prevented in some way the manual editing of menu.lst from taking effect.

---

### Post by kestrel1 on 2009-02-25
Thats is good news. Just keep an eye out if you get another kernel upgrade, you might just want to check that the menu.lst file is up to date.

---

