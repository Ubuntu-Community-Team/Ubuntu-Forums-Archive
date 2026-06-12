---
title: "Is my laptop dying?"
date: 2009-06-23
forum: Hardware
---

### Post by hotstepperk on 2009-06-23
As the title suggests, im worried that my laptops starting to die on me. I was wondering if there are any tools (preferably graphical) that could test all the hardware on my laptop and let me know if its faulty, and if so how the problem may be resolved.

One more thing- is it normal for ubuntu to overwork one processor while the other does barely nothing on a duo core comp? this is slightly worrying to me as i feel it may cause the first processor to be overworked and may be the root of my problems.

---

### Post by rob2uk on 2009-06-23
What symptoms, other than one core working harder than the other, make you think its on its last legs?

---

### Post by xtjacob on 2009-06-23
Is your operating system 32-bit or 64-bit?

---

### Post by aesis05401 on 2009-06-23
Firstly, have you checked for standard resource hogs on the machine?

For instance - when I have the 'gnash' plug-in enabled for Firefox it completely monopolizes CPU1 on my machine whether or not FF is using it for anything.  

Additionally, there are certain processes that do not normally show under the GUI process manager that may be killing your performance.  

One of the worst cases I have ever seen involved someone's inadvertant experiment with snort.  The user was unaware that snort was still running on their machine, and it did not show in the gnome process manager (at least not with this user's config settings), so the process was eating all the resources in sight and the user believed their machine was dying.

Opening a terminal and typing : 'sudo top' will display a root level process manager.  If you see a process in there that is monopolizing your resources a little research sould get you back to normal.

1. What is the resource hogging process?
2. Do I need to be running this process?

If you find something that should be killed then use the 'kill' command in conjunction with a process ID (# in PID column on 'top' display): ie: 'sudo kill 4618' would kill the firefox process on my machine as '4618' is the PID assigned to FF according to my 'top' readout.

If there is no resource hog then the trouble shooting will get a little more in-depth.

Edit: I should mention you exit 'top' by hitting ctrl+c.

---

### Post by hotstepperk on 2009-06-23
well, of late the hard-disk seems to be making some weird noises, some of my ram appears to mysteriously missing (about 20MB) and the fan keeps switching on and off when in low use then should i start something resource hungry it sounds awful- like it hitting on something or is slightly loose in there.

---

### Post by khelben1979 on 2009-06-23
[Hardware diagnostics with open source tools - Linux.com]("http://www.linux.com/archive/articles/55366").

---

### Post by rob2uk on 2009-06-23
> **hotstepperk said:**
> well, of late the hard-disk seems to be making some weird noises, some of my ram appears to mysteriously missing (about 20MB) and the fan keeps switching on and off when in low use then should i start something resource hungry it sounds awful- like it hitting on something or is slightly loose in there.

Backup NOW!

Sounds like your hard disk is VERY much on it's way out

---

### Post by hotstepperk on 2009-06-23
> **rob2uk said:**
> Backup NOW!

Sounds like your hard disk is VERY much on it's way out

Wow. thats encouraging to know. any way I can test my hard-disk for integrity? i've js installed smart-tools but im not sure how to use it, more accurately how to tell if there's a problem with it or not! 

@ xtjacob: I'm using 32 bit jaunty

@ aesis05401: I've just run the 'sudo top' command and it says that Xorg is hogging up 50% of the cpu, firefox about 20% and the rest at 1's and 0's. should It be that high?

---

### Post by rob2uk on 2009-06-23
> **hotstepperk said:**
> Wow. thats encouraging to know. any way I can test my hard-disk for integrity? i've js installed smart-tools but im not sure how to use it, more accurately how to tell if there's a problem with it or not! 

@ xtjacob: I'm using 32 bit jaunty

@ aesis05401: I've just run the 'sudo top' command and it says that Xorg is hogging up 50% of the cpu, firefox about 20% and the rest at 1's and 0's. should It be that high?

There are ways and means of doing it, but testing stresses the disk more than normal usage, and if it's already on it's way out... well, you get the idea

---

### Post by hotstepperk on 2009-06-23
> **rob2uk said:**
> There are ways and means of doing it, but testing stresses the disk more than normal usage, and if it's already on it's way out... well, you get the idea

I suppose. Though I'm saving up to get one of them gateway FX laptops, probably around December, meaning this one needs to see me till then! Besides, this has seen me through quite abit, so I figure if its fixable, I should try and make it work.

---

### Post by hotstepperk on 2009-06-23
> **khelben1979 said:**
> [Hardware diagnostics with open source tools - Linux.com]("http://www.linux.com/archive/articles/55366").

Thanks for the link. I'll give Memtest86+ a try later tonight.

---

### Post by aesis05401 on 2009-06-23
> **hotstepperk said:**
> @ aesis05401: I've just run the 'sudo top' command and it says that Xorg is hogging up 50% of the cpu, firefox about 20% and the rest at 1's and 0's. should It be that high?

Many processes will spike very high on the CPU scale, but typically don't stay high.  Xorg is routinely the #2 CPU hog on my machine over time, but at any given time it is usually pretty low on the CPU usage.

You can get a good picture of what is happening overall by looking at the load averages that are posted in the upper right corner of the 'top' header.

I agree with other posters that the audible symptoms you are noticing may suggest impending harddrive failure.  If this is the case, don't start running diags until you have backed up everything that is important to you - and then take a look at what a solid disk analyzer says about the HDD.

If it looks like disk death for sure, you may want to look into an external USB drive enclosure.  While this will not give the same performance as an internal drive, it will get you through to your new laptop you are saving money to buy - and will be a nice peripheral device going forward.  Whenever I have HDD concerns the first thing I do is snap an image onto one of my external USB drives - takes a lot of stress off my mind and is a pretty cheap solution.

Worst case scenario you run Ubuntu from your external drive for a few months.

---

### Post by hotstepperk on 2009-06-23
> **aesis05401 said:**
> Many processes will spike very high on the CPU scale, but typically don't stay high.  Xorg is routinely the #2 CPU hog on my machine over time, but at any given time it is usually pretty low on the CPU usage.

Worst case scenario you run Ubuntu from your external drive for a few months.

I suppose. The processor loads have dropped significantly now that I've closed songbird and transmission. So much for multimedia multitasking! The hard-disk noise isn't as bad, but the more I multi-task, the more audible it gets. Its a slow, slow death...

---

### Post by aesis05401 on 2009-06-23
Out of curiosity, what are the specs on your machine?  

I still use a Toshiba Tecra from the late nineties as a portable diagnostic terminal, but wouldn't even try running a modern desktop on it.  In fact, it took a lot of work to even get Linux running on it IIRC ;)

---

### Post by hotstepperk on 2009-06-23
> **aesis05401 said:**
> Out of curiosity, what are the specs on your machine?  

I still use a Toshiba Tecra from the late nineties as a portable diagnostic terminal, but wouldn't even try running a modern desktop on it.  In fact, it took a lot of work to even get Linux running on it IIRC ;)


Mine isn't as old- although i've got an ancient Toshiba somewhere in the house as well, cant remember what model it is, need to look it up. Im using a HP 530 | 120GB HDD | IGB Ram | Intel GMA 950 (hate Intel "graphics")

---

### Post by khelben1979 on 2009-06-24
> **hotstepperk said:**
> Thanks for the link. I'll give Memtest86+ a try later tonight.

You're welcome! Just made a quick google search on the matter.

---

