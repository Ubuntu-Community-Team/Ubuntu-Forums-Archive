---
title: "Sound card replacement problem."
date: 2009-07-06
forum: Hardware
---

### Post by Confused Computer User on 2009-07-06
Hi,

It's been a while since I posted something on this forum, but here goes.

I have A computer that I have dual-booted, Windows and Ubuntu (using the grub Loader. I have Ubuntu 8.04 with the latest updates.

About me:
Not too keen on command lines and I don't have a lot of Linux experience.

Problem:
I have an old computer. I used Linux and windows side by side on it and it ran well. The only issue was that Ubuntu did not recognize the sound card. I had a much older computer on which the sound card was recognized. So I decided to switch the two. Now these sound cards are almost identical to a fault. Same brand, same model I believe but I can't really tell. I pulled out the problem sound card and plug-ed in the one that was supposed to work. 
The computer started off fine, I got to the grub loader, chose Linux and a few seconds later I get an error message that the system panicked or something.
I tried booting into windows but this goes as far as the loading screen and then the computer reboots. 
I placed the original sound card but the same thing happens. :mad:

I am sure that I'm doing something wrong.

N.B.:
This is an old computer. I don't have an install cd nor a way to back it up. the info on it has been saved but the issue is that I don't know what to do.

Please help.

Any suggestion is appreciated, but please allow a gracious amount of time for reply. I am not able at the moment to spend too much time on this.

---

### Post by elitenoobboy on 2009-07-06
"chose Linux and a few seconds later I get an error message that the system panicked or something."

Being more specific here would really help.

Both of the OS's failing to boot after restoring the original hardware makes it sound like a hardware problem. Will it boot off of a live cd?

---

### Post by Confused Computer User on 2009-07-07
The error message I get is as follows:

[ 31.813276]   DS: 007b   ES: 007b   FS: 00d8   GS: 0000   SS: 0068
[ 31.813340]   Process swapper (pid: 0, ti=c041e000 task=c03eb3a0 task.ti=c041e000)
[ 31.813407]   Stack 00000000  c03f6480  000000b0  00000000  00000001 00000001  d3416800  c04279f5
[ 31.813796]             00000010  d1402580  00000500  d3416820  00000007 00000101  00000120  d3416000
[ 31.814180]             00000110  d1400003  00000000  00000093  00000001 00000008  00000007  d1402568
[ 31.814563]  Call Trace:
[ 31.814650]    [<c04279f5>] huft_built+0x325/0x630
[ 31.814767]    [<c04282c5>] inflate_fixed+0x15/0x1b0
[ 31.814880]    [<c0428393>] inflate_fixed+0xe3/0x1b0
[ 31.814991]    [<c0428b35>] unpack_to_rootfs+0x6d5/0x950
[ 31.815102]    [<c0428dca>] early_populate_rootfs+0x1a/0x60
[ 31.815214]    [<c0423a55>] start_kernel+0x315/0x3b0
[ 31.815323]    [<c0423130>] unknown_bootoption+0x0/0x1e0
[ 31.815435]    =======================
[ 31.815469]  Code: 1f  84  00  00  00  00  00  89  c6  fa  0f  1f  84  00  00  00  00  00  90  64  a1  08  80  47  c0  8b  6c  87  70  8b  5d  00  85  db  0f  84  8a  00  00  00  8b  45 0c  <8b>  04  83  89  45  00  89  f0  50  9d  0f  1f  84  00  00  00  00  00  66  83  7c
[ 31.817920]    EIP: [<c018eae4>] __kmalloc+0x64/0x110 SS:ESP 0068:c041fe90
[ 31.818105] ---[ end trace ca143223eefdc828 ]---
[ 31.818175]  Kernel panic – not syncing: Attempted to kill the idle task!



Now if I press any key nothing happens. Yet I see at the bottom of the screen the cursor flashing steadily.

When I use the Linux (Ubuntu) live CD I get a similar problem.

... (this is representative of the lines of code I’ve skipped)
 
[ 38.519401]    [<c0421130>] unknown_bootoption+0x0/0x1e0
[ 38.519511]    =======================
[ 38.519572]  Code: 4f  df  90  90  90  90  90  90  90  90  89  d0  e9  09  ff  ff  ff  89  f6  8d  bc  27  00  00  00  00  57  56  89  c6  53  8b  4  20  <8b>  10  85  d2  0f  84  72  01  00  00  89  f0  ff  d2  89  c3  85  db  0f  84  b7
[ 38.521992]    EIP: [<c01a5548>] alloc_inode+0x8/0x1b0 SS:ESP 0068:c041de78
[ 38.522203] ---[ end trace ca143223eefdc828 ]---
[ 38.522276]  Kernel panic – not syncing: Attempted to kill the idle task!

I also tried Puppy Linux live CD and this gave a similar message more or less.:mad:

---

### Post by Confused Computer User on 2009-07-10
Any suggestions?:confused:

---

### Post by markbuntu on 2009-07-10
You could be a little more forthcoming with specific hardware information if you want help with your hardware.

Anyway, put the original card back in so you can boot up, post us some more specifics about your hardware, and we will se what we can do for you.

---

### Post by Confused Computer User on 2009-07-10
> **markbuntu said:**
> You could be a little more forthcoming with specific hardware information if you want help with your hardware.


I'll look in to it and try to find out as much as possible. This is an old machine not a custom machine. I'm not sure about the brand of the sound card but I will look and post back.

> **markbuntu said:**
> 
Anyway, put the original card back in so you can boot up, post us some more specifics about your hardware, and we will se what we can do for you.

I have placed back the old card in. The error messages I posted earlier are what I got with the original card in.

Please give me more time with this issue. I will be able to post back in a few days.

Thank you markbuntu and elitenoobboy for your replies.

---

### Post by Confused Computer User on 2009-08-14
Hello all,

It turns out a few days turned into a few weeks. I hope you are still willing to help me. New info on the issue.

The computer is a HP Vectra VL 6/400 Ser.8. 
You can visit this site for exact details concerning the desktop
[http://partsurfer.hp.com/cgi-bin/spi/main?sel_flg=partpic&pic_flg=part&stype=W&partnum=D5899-69001&HP_model=D5882T&model=&whichpic=%3F&template=main](http://partsurfer.hp.com/cgi-bin/spi/main?sel_flg=partpic&pic_flg=part&stype=W&partnum=D5899-69001&HP_model=D5882T&model=&whichpic=%3F&template=main)

Apart from this I have another thing.
I have removed the original sound card and booted the computer without a sound card. Linux failed at first however Windows loaded. After that I tried Linux once more and it loaded. This is some progress, At least it's working.

What are your suggestions?

Thank you in advance for your understanding and I apologize for not posting sooner.

---

### Post by Confused Computer User on 2009-08-14
> **Confused Computer User said:**
> Hello all,

It turns out a few days turned into a few weeks. I hope you are still willing to help me. New info on the issue.

The computer is a HP Vectra VL 6/400 Ser.8. 
You can visit this site for exact details concerning the desktop
[http://partsurfer.hp.com/cgi-bin/spi/main?sel_flg=partpic&pic_flg=part&stype=W&partnum=D5899-69001&HP_model=D5882T&model=&whichpic=%3F&template=main](http://partsurfer.hp.com/cgi-bin/spi/main?sel_flg=partpic&pic_flg=part&stype=W&partnum=D5899-69001&HP_model=D5882T&model=&whichpic=%3F&template=main)

Apart from this I have another thing.
I have removed the original sound card and booted the computer without a sound card. Linux failed at first however Windows loaded. After that I tried Linux once more and it loaded. This is some progress, At least it's working.

What are your suggestions?

Thank you in advance for your understanding and I apologize for not posting sooner.

Update to the Update.
Now I get the same messages as the above posts with and without the sound card. I don't get it anymore. I was happy it was working without the sound card and now this doesn't work anymore.:(

---

### Post by Confused Computer User on 2009-08-17
Any one??? :confused:

---

### Post by elitenoobboy on 2009-08-18
> Linux failed at first however Windows loaded. After that I tried Linux once more and it loaded. 
Now I get the same messages as the above posts with and without the sound card. I don't get it anymore. I was happy it was working without the sound card and now this doesn't work anymore


It sounds like a hardware problem, especially if linux is only successfully loading some of the time without making changes to the computer. Does windows load successfully everytime you try it? If ubuntu does load up, does it experience any instability? What happens when you try booting from the live cd? You mention not having a live/install cd in your first post. If this is still the case, I recommend burning a new one and trying that.

A quick google of the error message seems to indicate that it could be related to faulty ram. Try letting the memory tester from grub run through a couple of loops and see if anything comes up from there. You also might want to try reconfiguring and/or reseating your ram modules.

---

### Post by Confused Computer User on 2009-08-19
Thank you for the reply elitenoobboy.

I'll answer each of your points one at the time.

> **elitenoobboy said:**
> It sounds like a hardware problem, especially if linux is only successfully loading some of the time without making changes to the computer.
That is not it. It loaded once and then every successive reboot, it failed producing the same error as listed in my previous posts.

> **elitenoobboy said:**
> If ubuntu does load up, does it experience any instability?
None that I was aware of. I only opened OO and it worked well.
Problem was when I restarted it got to the log on screen were I left there because I had another issue to attend to. When I got back it was frozen/non-responsive.

> **elitenoobboy said:**
> Does windows load successfully everytime you try it?
Same as with Ubuntu. It loaded but after Ubuntu froze and I had to hard reboot it wasn't working anymore. I get to the windows loading screen but then it restarts every time.

> **elitenoobboy said:**
> What happens when you try booting from the live cd? 
Same as when I tree to boot ubuntu from the Hard Drive.

> **elitenoobboy said:**
> You mention not having a live/install cd in your first post.
I said "install cd" by which I was referring to the CD that comes with the computer (the cd that allows you to restore to factory defaults. 

> **elitenoobboy said:**
> A quick google of the error message seems to indicate that it could be related to faulty ram. Try letting the memory tester from grub run through a couple of loops and see if anything comes up from there. You also might want to try reconfiguring and/or reseating your ram modules. 
I will follow your suggestions and post back tomorrow if not in a week. 

Thank you again for the reply.:)

---

