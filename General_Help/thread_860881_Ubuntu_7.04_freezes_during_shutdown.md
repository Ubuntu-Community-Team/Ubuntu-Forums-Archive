---
title: "Ubuntu 7.04 freezes during shutdown"
date: 2008-07-16
forum: General Help
---

### Post by jlownie on 2008-07-16
Hi everyone,

I am running Kubuntu with Ubuntu 7.04 on a Dell Aspire 5570Z laptop.  Every 3rd or 4th time I try to shut it down, it freezes up part of the way through the process, and I have to hold down the power button to switch it off.  Sometimes the partition that I'm running Linux on is not cleanly unmounted, and I have to run fsck to get it to start up.

There is nothing in /var/log, no messages in dmesg, and when I tried the command shutdown -h now > shutdown.log, the log file was completely empty.  So I have no idea what is causing the problem.  Sometimes the screen goes beserk, so I wonder if maybe the problem is related to the graphics drivers.

Can anyone help me get more information about the cause of the problem?  Is there some way I can switch on extra logging or something?  I don't know what I can do to narrow it down.

Thanks,

James

---

### Post by jlownie on 2008-07-23
bump.

---

### Post by jlownie on 2008-07-26
bump.

---

### Post by abrasax on 2008-07-30
I had the same problem. Only happened every time.
Try to boot with command

xforcevesa

It helped me. Graphics get worse but at least you can shutdown or restart. It can be a temporary fix until you set up graphics drivers properly.

---

### Post by jlownie on 2008-07-31
Thanks Abrasax.  I haven't noticed any graphics card problems, do you have any advice on diagnostic steps?  I suppose I can try installing the drivers again, or installing the latest ones if there are any.  

Now that I think about it, the drivers were chosen automatically when I installed Ubuntu.  Maybe I need to look at them more carefully.

- James

---

### Post by abrasax on 2008-07-31
Sorry, I'm also new to linux. I have no idea how to help you. I'm trying to install graphics drivers for my laptop and i'm not doing so well. If my advice helped you i'm glad, but that is the limit of my linux knowledge.

---

