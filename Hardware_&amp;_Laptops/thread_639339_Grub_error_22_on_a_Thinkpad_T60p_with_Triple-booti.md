---
title: "Grub error 22 on a Thinkpad T60p with Triple-booting OS (Ubuntu/XP_SP2/Vista_Business"
date: 2007-12-13
forum: Hardware &amp; Laptops
---

### Post by narutonakamura on 2007-12-13
Hi 

I just ran into a seemingly simple problem but with no apparent solutions that would also be uncomplicated. I am hoping some of you might be able to help and that this is the right forum to address this concern.

Until today, I had Ubuntu (version 7.10 or one version older than that), XP2 and Vista Business running on my T60p. When I had originally purchased the laptop, it came preloaded with Vista. On top of that, with a friend's help, I had installed Ubuntu and XP (SP2) in separate partitions, and Grub was doing the initial boot loading/OS selection. I had installed XP back then as I was a little skeptical about Vista’s compatibility with the older applications and wanted to keep XP just in case. However, barring a few exception, I found no big reason to switch back to XP (I’m sure if one gets into the nitty-gritty of it, XP will probably still turn out to be the better choice, but for my software needs, it doesn’t seem to matter). 

Anyhow, I recently decided to get rid of XP to get some extra HD space. The way my partitions were set up was (memory numbers approximates – don’t recall specifically):

5 GB                                   25 GB              50 GB             20 GB
ThinkPad Software            Ubuntu            Vista               XP

So I went into the Vista partition manager and simply deleted the XP partition and allocated that space to Vista – really bad idea. I wish it wasn’t so easy to do something as dangerous as that. It seemed a perfectly legible and innocuous thing to do back then – nothing blew up, no blue screens or anything. However, when I restarted my machine another time, I got the following error:

GRUB Loading stage 1.5

GRUB loading, please wait...
Error 15

My guess is that somehow, the partition table that GRUB uses is asking it to find XP at its previous location but since it cannot find it, it kind of chokes and locks up. Nothing works now. I can’t even press the blue ‘ThankVantage’ button to restore my system to a previous backup as GRUB interrupts before anything and doesn’t allow that sector of the HD to run. All I have access to is the system BIOS and all I can do with it is hardware diagnostics test (which I have done and it passed, so the hardware doesn’t seem to be corrupt at least). 

Unfortunately, I never burnt any kind of recovery disk or backup disk for my machine and such a thing didn’t come pre-packaged with it. And since my thinkpad was scheduled to automatically make daily backups, I didn’t feel I could ever be in a situation I wouldn't be able to recover from! Couldn’t have been more wrong! I called up IBM’s tech support and got the predictable response that they wouldn’t help me with this as I installed all these exotic OSes on my machine (I have a 3-yr full-service contract with them which is supposed to cover every other natural calamity otherwise). He said nothing can be done about my machine and that I will have to reformat it and loose the data, since I have corrupted that partition table. The only thing I could do is take it to a computer shop and have them probe my HD physically or do any one of those tedious and expensive procedures to recover the data and then re-format the machine. I don’t know how expensive the procedure is as yet (will find out tomorrow) but I find it hard to believe that nothing can be done about this problem in software and that one has to use the brute force method.

Of course, this is as far as I could take it myself, so I’m not really sure what else I can try. I did, in the mean time, upload a copy of the Ubuntu Live CD on my USB key, which I’m told I can use to restore GRUB by doing something fancy. I wouldn’t mind trying that but I’m very apprehensive as all this stuff (especially when it comes to Linux) seems a bit too alien to me right now and I don’t want to take a chance with my data. :(

If anyone on this forum might have an idea of how I can fix things, I would really appreciate it. If I find a solution in the mean time, I would be sure to share it with you as well.

Thanks a lot!

---

