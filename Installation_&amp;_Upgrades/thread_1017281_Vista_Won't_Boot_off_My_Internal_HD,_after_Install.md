---
title: "Vista Won't Boot off My Internal HD, after Installing Mint 6 on my External HD"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by bazbazbaz on 2008-12-20
Hi,

I have searched far and wide and have not found a solution to my specific problem, even though lots of posts have come real close.

**First, here is my goal:** I want to install Ubuntu on my external 750gb usb drive and leave Vista on my internal 120gb laptop HD _AND_ for Ubuntu to load only when my external drive is plugged in and on, but Vista to load when my external drive is unplugged or off. I don't want Vista or its partition to have any concept whatsoever of my external drive or grub. I don't want to choose Vista from some sort of boot list or anything like that.

**Here is where I got:** I successfully install Mint 6 on my external drive and made sure to switch grub's location in "advanced" during the install to "sdc" (i think) rather than the default "sd0" (i think). When I rebooted, things didn't work perfectly, there was a grub "error 17 partition not found" but I fixed it by editing /boot/grub/menu.lst and now I am happily typing this from my future primary OS - Mint!

**The problem:** When my external HD is unplugged Vista does not load and I only get the word "GRUB" on a black screen. There are no options or any keys to type, all I can do is ctrl+alt+delete to reboot. Now what is strange is that I specifically told grub to be on my external hd. Why is it showing up on my _internal_ disk at all? I really wanted my internal disk to remain untouched and oblivious to what I was doing.

**Thoughts:** I think I need to restore my Vista MBR. I tried booting from the Vista CD and choosing the option to fix boot (or something like that) but that didn't solve it, and I can't seem to run commands such as fdisk /mbr or fixmbr off of the vista command-line. 

What do you suggest?

Thank you very much!

---

### Post by caljohnsmith on 2008-12-20
How about trying the following commands from the Vista CD command line:
```
bootrec /fixmbr
bootrec /fixboot
```
See if that's enough to get Vista booting again, and if not, let me know what happens when you try booting Vista.

---

### Post by infamous-online on 2008-12-21
Did you turn the pc off, and unplug the windows harddive and then tried and install ubuntu on the external?

Remember if you try to install ubuntu on your machine with the windows os installed the grub will override the windows MBR and therefore you'll be forced to re-install windows if ubuntu goes down. So, be sure to keep the boot loaders seperate of one another. 

That way when you're running windows, ubuntu won't mess it's settings and vice versa. However what that external drive windows won't see it unless you use disk management. Hope this helps.

---

### Post by bazbazbaz on 2008-12-21
@caljohnsmith: Thank you man, that worked perfectly! I am surprised I didn't bump into this in all my searching....

@infamous-online: I probably should have done that but it's a pain in the butt to unplug a laptop drive, so I thought if I was extra careful and specified exactly where I want grub to go that it wouldn't stray. It seems that it does anyway - or perhaps I overlooked something...

@everyone: I love the Ubuntu community! So helpful, so unpretentious, so quick to answer - awesome!

Thanks guys...

---

