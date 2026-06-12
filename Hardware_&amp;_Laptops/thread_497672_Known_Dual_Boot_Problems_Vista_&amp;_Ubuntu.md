---
title: "Known Dual Boot Problems: Vista &amp; Ubuntu"
date: 2007-07-10
forum: Hardware &amp; Laptops
---

### Post by tgbrowning on 2007-07-10
Machine:  HP Pavilion dv2000

Folks, I'm in a kind of pickle here. I bought a laptop for my duaghter and installed Ubuntu on it, setting up a dual boot Vista/Ubuntu (Edgy).  I first repartitioned the hard drive under Vista, rather than waiting to do it under Ubuntu. Everything seemed to go okay. In the process of updating Edgy, something blew out and Ubuntu died on my. No idea what, except I got a long set of error messages that ended with the disconcerting phrase "kernal panic". 

I'm not entirely certain how reassure an OS, so I figured on reinstalling Ubuntu.  

Did so, changing the partition slightly when I did, using Ubuntu's partioning program during the install.  

Window Vista died a horrible death.  

I decied to drop back a couple of squares and resintall Vista via the factory restore.  It seemed to work okay. About a third of the way through setting up Vista (post install -- setting up the wireless network adapter, killing unwanted programs, that sort of thing) and Vista died again. 

This time, the factory restore didn't work. Period. It froze solid, no matter what I tried.

Decided enough was enough -- cursing Vista in three languages -- I went to what I had originally thought to do -- bought a copy of Windows XP and installed it.  Mucho problems doing so and told it to repartition everything. After a LOT of problems (the CD was spitting out read errors here and there) got an install.  Sort of. Ran into HUGE roadblock with Windows XP not recognizing a lot of the hardware.  But the partitioning seemed to be okay.  

But I couldn't get the hardware issues fixed. XP wouldn't run far too many things.

I read in the forums that Vista seemed to go nuts become of boot - order problems. The only reasonable option I had left was to try the factory restore again, which I did.

Worked. Evenually. Had some problems but I did manage a clean install. The machine is back up and running just like it had been running, before I started this mess.

Now, I'd like to install Ubuntu, again, but I'm a bit leery of doing so.  

Has anyone made any sense out of the problems that Vista has, sometimes, with dual booting? What I've gleaned from the forums is that it appears -- appears, mind you -- that Vista is okay [COLOR="Red"]if you set up the partition under Vista, first, and do NOT mess with it during the install.[/COLOR]

Comments, anybody?  Suggestions (other than take two aspirin? 

Browning>>>

---

### Post by gpilkay on 2007-07-10
To be honest, I've always been leery of partitioning the hard disk, my duel-boot runs from two different drives, with Ubuntu booting first, then handling the bootup for everything else.  That way the Windows drive never is touched.

That likely isn't an option for lap-top installation.  Here's an article that may be able to give a more informed answer then I can:
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

It's a full tutorial.

---

### Post by tgbrowning on 2007-07-10
Thanks--I'll give it a look see. 

My problem is that I've got a streak of stubborn in me a mile wide. I detest having a computer thwart my plans for it. :)

Browning>>>

---

### Post by dabl on 2007-07-10
> **tgbrowning said:**
>  it appears -- appears, mind you -- that Vista is okay [COLOR="Red"]if you set up the partition under Vista, first, and do NOT mess with it during the install.[/COLOR]

Comments, anybody?  Suggestions (other than take two aspirin? 


That is what I read ....

My only experience is that I bought an e-machines PC with Vista pre-installed.  I was on a mission to set up an e-mail and Internet-searching machine for an elderly family member who has zero computer experience.  So, without ever booting Vista, the first time I powered it on I booted a GParted Live CD, and shrunk the Vista partition (the big one, not the recovery one), put a swap partition and an extended partition on it, and installed Kubuntu Feisty there.  Not dual-boot -- just Feisty. That was 6 weeks ago, and as far as I can tell there's no need for her to ever see or know that Vista is on that machine.  :guitar:

---

### Post by benjamin1254 on 2007-07-10
i see.. anyway in all of this i see one big bee stinger of a problem. Vista itself is a memory hog a compnet hog and when your downloading it will force feed the program downloading instead of letting everything pool nice and even... windows vista just wants to suck everything to one side or another when it comes to its resources. fiesty i have had nothing but love for! hence my reason of just giving up on vista all together untell they can come out with something less of a system hog. Fiesty i had just installed and like vista it went out and said this thing is here ... this is here... and this is here. But the only diffrence that i can see between the two OS' is the fact that windows hogs up resources and linux will use as much as it needs and run 110% more stabler. I would recommend just using ubuntu for a week and if by that time you dont see yourself reaching for the windows disk for some miss compatability let us know. I mean as of right now vista is just usefull sitting off in the corner tell everything is figured out or a better processor is made for vista spicificly.

---

### Post by tgbrowning on 2007-07-10
You're actually preaching to the converted. The ONLY reason I have windows on any of my personal machines is because my job requires me to use Microsoft Office -- I'm a programmer for Excel spreadsheet applications.

My daughter has no interest in PCs per se. She's strictly a user and the odds are that she will only really need Micrsoft Office.  There are some hardware issues however, since commercial DVDs have some problems under Ubuntu (no closed captioning as far as I've been able to tell) and the webcam built into the laptop is a bit new. There's not much chance it will work out of the box in Ubuntu.

My hope is that with a dual boot system, she'll see the performance differences as well as the various and many security problems she has with Vista and decide on her own to switch over to Ubuntu. She might not. But it will be her choice; I won't force her to go one way or the other.

Browning>>>

---

### Post by Scrib on 2007-08-07
I'm just about to buy a Pavilion dv2000. This will come pre instaled with Vista with no reinstal CD/DVD (as is the way these days). :lolflag:

I want to put Ubuntu on it as soon as I get it, but also want to keep Vista on it for a while (just in case something doesn't work in Ubuntu and I can test if it works under Vista to help me diag).

What is the best way to duel boot Ubuntu and Vista if Vista is pre installed? You mention pre partitioning it under Vista ? Is that using a third party app like Partition magic, or is that ability built into Vista now?

Or is it best to get the Ubuntu setup to repartition it? Or is it not possible?

Has anyone done this successfully before, and what was the best method? :confused:

---

### Post by dabl on 2007-08-07
What I read is that those who are successful use Vista's built-in disk partitioning utility to shrink the Vista OS partition (the big one, not the recovery one).  In other words, there is some disk partitioning utility in Vista, and you want to use that, not a third-party anything.

Then, once Vista is happy running in a shrunk partition, you boot your Ubuntu Live or Alternate CD, and you install Ubuntu in the partition that you freed up when you used Vista to shrink its partition.

I know that's real high-level, but that seems to be what is working.  Personally, I hope to never boot Vista!  :lolflag:

---

### Post by Scrib on 2007-08-07
OK cool - I'll give it a go when I get the new kit.

Hope I never need Vista either, I've settled on a laptop that has a built in webcam and TV card. If I can get those working (webcam should be ok, not so sure about he tv card though) i won't need Vista and will probably remove it when the next version on Ubuntu comes out - all being well.

---

### Post by dancavs on 2007-08-10
well i bought a new hp pavilion dv 2000 with vista about 3 months ago. i basically did (from memory exactly what has been described previously ... )

partitioned drive in vista using the help page on drive partitioning for guidance (it created a 20gb empty partition)
installed ubuntu feisty 7.04 in that partition from downloaded disk using 
[this]("http://www.psychocats.net/ubuntu/partitioning") page for general information on partitioning.

and it has been very stable. a few devices i have had to fiddle with to get working but so far everything i have tried to get working has been more or less successful.

the main problem i have now is what to use vista for ...

---

