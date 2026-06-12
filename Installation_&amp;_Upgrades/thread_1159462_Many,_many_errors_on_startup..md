---
title: "Many, many errors on startup."
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by LiteralKaiser on 2009-05-14
Whenever I boot, I watch a flood of text scroll by. I can still boot fine though. Any help (getting rid of them)?

Here is /var/log/kern.log is showing: [http://pastebin.com/f35ce2391](http://pastebin.com/f35ce2391)
[SIZE="1"]
Crap, I posted this in the wrong area.[/SIZE]
[SIZE="1"]
Could someone move this to the correct area?[/SIZE]

---

### Post by khelben1979 on 2009-05-14
> **LiteralKaiser said:**
> Whenever I boot, I get a considerable amount of errors. I can still boot fine though. Any help (getting rid of them)?

Here is /var/log/kern.log is showing: [http://pastebin.com/f35ce2391](http://pastebin.com/f35ce2391)
[SIZE="1"]
Crap, I posted this in the wrong area.[/SIZE]

I don't see any errors, but I do see that it generates a lot of output ("maybe" a bit too much). I believe that you need to change to another kernel which is configured up in a different way to get reduced output at boot up.

---

### Post by LiteralKaiser on 2009-05-14
> **khelben1979 said:**
> 
[QUOTE=LiteralKaiser;7280067]Whenever I boot, I watch a flood of text scroll by. I can still boot fine though. Any help (getting rid of them)?

Here is /var/log/kern.log is showing: [http://pastebin.com/f35ce2391](http://pastebin.com/f35ce2391)
[SIZE="1"]
Crap, I posted this in the wrong area.[/SIZE]

I don't see any errors, but I do see that it generates a lot of output ("maybe" a bit too much). I believe that you need to change to another kernel which is configured up in a different way to get reduced output at boot up.[/QUOTE]

I doubt it's that [the kernel], this started happening after I left a disk with Knoppix on it in my drive, and it booted. I tried Knoppix out for a while, and then the errors came on the next boot. Since then, I've upgraded the kernel twice, to linux-image-2.6.27-11-generic and then to linux-image-2.6.27-14-generic.

How would I do that?

---

### Post by Spinitch on 2009-05-14
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] **after installing Jaunty ERROR city** 
im not so new to ubuntu but still a newbie and could really use the help,after i installed the new Jaunty 9.04 i rebooted after an update and now all iget when i boot right after the boot/grub/menu.lst are error messages repeating about 200 tries saying my root/dev failed or no such file or directory and leaves me in busy box after it gives up waiting for root device...ive tried every sudo trick i know (which isnt very much) and all the forum help i could find and im going to pull my brain out through my nose in a min as nothing has worked for me even trying from the live cd, if anyone is having this problem or a solution i would be forever in your dept im a photographer and all my work is on there and my newbie mistake was forgetting to back up my files :sad:( yes i know i know bad SPIN i will try to list the errors ive been getting hopefully will make it easier to help with my issue thank you everyone 


ata3.00: status: DRDY ERR
ata3.00 error: UNC
end_request:I/O error,dev,sdb,sector131
EXT3-fs:cant read group descriptor 7

mount:mounting /dev/disk/by-uuid/9f5cd2cd-413a-4ab0-95a-6408a0c80820 on /root failed:invalid argument

mount:mounting/dev on /root/dev failed: no such file or directory

mount:mounting/sys on /root/sys failed: no such file or directory

mount:mounting/proc on /root/proc failed: no such file or directory

Target filesystem doesnt have /sbin/init. no init found.try bypassing init=_bootarg.

---

### Post by khelben1979 on 2009-05-15
> **LiteralKaiser said:**
> How would I do that?

Look inside the synaptic package manager for Linux kernels to see what they got. Or... compile your own.

---

### Post by LiteralKaiser on 2009-05-15
> **khelben1979 said:**
> 
[QUOTE=LiteralKaiser;7281120]
[QUOTE=khelben1979;7280368]
[QUOTE=LiteralKaiser;7280067]Whenever I boot, I watch a flood of text scroll by. I can still boot fine though. Any help (getting rid of them)?

Here is /var/log/kern.log is showing: [http://pastebin.com/f35ce2391](http://pastebin.com/f35ce2391)
[SIZE="1"]
Crap, I posted this in the wrong area.[/SIZE]

I don't see any errors, but I do see that it generates a lot of output ("maybe" a bit too much). I believe that you need to change to another kernel which is configured up in a different way to get reduced output at boot up.[/QUOTE]

How would I do that?[/QUOTE]

Look inside the synaptic package manager for Linux kernels to see what they got. Or... compile your own.[/QUOTE]

I doubt it's that [the kernel], this started happening after I left a disk with Knoppix on it in my drive, and it booted. I tried Knoppix out for a while, and then the errors came on the next boot. Since then, I've upgraded the kernel twice, to linux-image-2.6.27-11-generic and then to linux-image-2.6.27-14-generic.

---

### Post by khelben1979 on 2009-05-16
I have read more in detail what you have written this time and I hope that you understand that your files on this harddrive isn't lost even though it will never boot up your Linux system again (if this is the case).

You can access all your important files if you insert another harddrive and installing Linux on it and then mounting this harddrive from there. Then you can access everything and nothing shall be lost, unless... there is a serious hardware fault with the harddrive which I know nothing about, but then you always have [SpinRite]("http://en.wikipedia.org/wiki/Spinrite").

---

### Post by LiteralKaiser on 2009-05-16
> **khelben1979 said:**
> I have read more in detail what you have written this time and I hope that you understand that your files on this harddrive isn't lost even though it will never boot up your Linux system again (if this is the case).

You can access all your important files if you insert another harddrive and installing Linux on it and then mounting this harddrive from there. Then you can access everything and nothing shall be lost, unless... there is a serious hardware fault with the harddrive which I know nothing about, but then you always have [SpinRite]("http://en.wikipedia.org/wiki/Spinrite").

I'm not talking about losing my data at all, I was just describing what I think caused the problem. (Using a Knoppix Live CD)

---

