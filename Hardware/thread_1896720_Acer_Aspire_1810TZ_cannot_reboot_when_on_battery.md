---
title: "Acer Aspire 1810TZ: cannot reboot when on battery"
date: 2011-12-17
forum: Hardware
---

### Post by gamon on 2011-12-17
I have a strange problem with my Acer Aspire 1810TZ: when I reboot from windows everything works fine, but when I want to reboot from Ubuntu (but this is tested also with Xubuntu and even Arch Linux, both live and installed versions) the system shuts down correctly, but then 2 things can happen:
1) if the pc is on AC power, the screen goes blank for 3-4 seconds, then the pc shuts down (the power led turns off, the fan and hdd both stop), and then, after about 2 seconds, it restarts and boots normally (note that when rebooting from windows the pc never shuts down, i.e. the power led never turns off and so on)
2) if the pc is on battery, the pc just shuts down, and I have to turn it back on manually with the power button.
I've also updated the BIOS, thinking it could be its fault, but to no avail.
Do you guys have some ideas how I can fix this problem?
Thank you!!

---

### Post by devtry on 2012-07-17
Hi, gamon!

I know that this is an old post, but I hope you will read my answer.
My computer is an Acer Aspire 1810TZ too; a couple of months ago I compiled and installed linux kernel 3.2.1 on Ubuntu 11.04: I then observed exactly your problem as you have described it.

Alessandro Menti helped me on Ubuntu Questions ([https://answers.launchpad.net/ubuntu/+source/linux/+question/186088](https://answers.launchpad.net/ubuntu/+source/linux/+question/186088)) to figure out what was the problem.
It is a kernel bug introduced with the 3.x.x series.

If you are using a 32-bit Ubuntu you can modify the GRUB configuration file and add "reboot=b" as a parameter to be passed to the kernel at boot time. This resolves the problem.

I've also reported the bug on launchpad ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/964687](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/964687)); there you can find a patched kernel by Leann Ogasawara. Unfortunately no one fixed this bug in the official Ubuntu kernel or in the upstream Linux kernel.

I was really busy when I reported the bug, so I could not fix it myself (I don't even know if I can do it now) and I could not report the bug upstream (to the Linux developers) beacause I needed some free time to do it.

Now I have some spare time and I can deal again with this problem.

Please let me know if you read this message; I'll let you know when I report the bug upstream or I have any kind of news!

Thanks!

---

### Post by gamon on 2012-07-18
Hey devtry, thank you for answering!

To be honest, I too fixed this issue kind of a month ago, although using "reboot=efi", and if I hadn't forgotten this thread, I'd have updated it :wink:

I've read the reports you've linked (I happen to be from Italy too ^^ ), and I strongly agree this bug should be submitted upstream: if you do, I'll try to find the time to help somehow if needed!

Thanks again, let me know of any news :P

EDIT: I've been able to retrieve the sources that led me to the "reboot=efi" solution, here they are for reference:
* [http://askubuntu.com/questions/89015/acer-aspire-one-d257-laptop-doesnt-restart](http://askubuntu.com/questions/89015/acer-aspire-one-d257-laptop-doesnt-restart)
* [http://www.expertcore.org/viewtopic.php?f=20&t=3009](http://www.expertcore.org/viewtopic.php?f=20&t=3009)
* []("http://askubuntu.com/questions/26601/new-computer-hangs-on-shutdown-reboot-how-to-troubleshoot")[http://askubuntu.com/questions/26601/new-computer-hangs-on-shutdown-reboot-how-to-troubleshoot](http://askubuntu.com/questions/26601/new-computer-hangs-on-shutdown-reboot-how-to-troubleshoot) (this one actually proposes "reboot=bios" as you do)

---

### Post by devtry on 2012-07-19
Hi gamon, thank you for your quick reply!

I think that your piece of information could be very useful to fix the bug, thanks! Now we have two similar but different solutions, and that is good.

The world is small, or so it seems: same country, what a coincidence!

Thank you for the links: very useful!

Yes, I think I will report the bug upstream, but first of all I'll try to find out when the bug/regression was introduced (using the git bisect tool) and it will take some time. I'll let you know when I have some results.

Thank you for your helpfulness!

---

### Post by gaussian on 2012-12-30
Just to report that this thread solved this issue on my Aspire 1810T (not TZ) using 64-bit 12.04. I used reboot=b command line option. 

And I was thinking it was a hardware failure :)

---

