---
title: "Raid is easy"
date: 2016-01-09
forum: Hardware
---

### Post by lile001 on 2016-01-09
Forget about all the documentation you will read here about RAID.  Raid is easy.  You don't have to do it during Ubuntu install.  You don't need a bunch of obscure settings.  Heck you don't even need a command line prompt.  

First - Ubuntu official documentation [here]("https://help.ubuntu.com/community/Installation/SoftwareRAID") says raid cards are very expensive. Folks on this forum will echo "Raid cards are expensive".    [This card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815124152") costs $19US.  I suppose [sarcasm] that they are used to those $1 PCs they send to third world schoolchildren if $20 is expensive[/sarcasm]  Cheap!  

Second, [the documentation]("https://help.ubuntu.com/community/Installation/SoftwareRAID") goes on and on about software RAID.  FUGHETTABOUTDAT.  You don't need any kind of software RAID or fake RAID or mdadm if a hardware raid card costs as much as two starbucks lattes.  Buy the card.   

Hardware installation of this card is straightforward. [EVEN I CAN DO IT]("http://www.louiselyonsauthor.com/wp-content/uploads/2015/10/homer-simpson-doh-400x288.jpg").   Bolt in two identical hard drives, plug in the power and plug a SATA cable from the drives to the card.  
A prudent Ubunt-ite would first check the SMART data on both drives to make sure they are any good.  I will not explain that procedure here as it is well covered elsewhere. 

Second, you will notice in the boot sequence that the ASM card now has its own BIOS page when booting. It shows you have two separate hard drives installed and they are not RAID. I went past this page several times scratching my balding head.  If you pay attention it says CNTRL-R = RAID Setup in fine print at the bottom of the screen.  Next time you boot (missed it, didn't ya?)  press Control-R at the right time to set up the RAID hardware card.  

The RAID setup menu says something like "No RAID installed"  - select that to configure it.  

Select RAID 1 (this mirrors the two disks you installed, making them one with twice the redundancy but half the total capacity.  2 1TB disks = 1 TB total RAID capacity)  which is what most people mean when they say RAID (YMMV)  

Press enter to accept
esc to leave menu
esc to continue boot

You will notice you now have a new, single, 1TB hard disk (or whatever size you installed).  

Continue to the DISK utility to enable SMART reporting,  format it, create a partition (this is on a PLUS button for some reason, it took me a while to find it because I was looking in menus)  partition it as EXT4 (unless otherwise noted)  and mount it somewhere. 

 Voila' you have a RAID array without going to the terminal prompt once.  

This worked for me on a DELL T5500 with Ubuntu 14.04LTS already installed.  Please comment if you've tried similar cards and let us know any tips. I'll let this thread stay open for a while then close it.

---

### Post by weatherman2 on 2016-01-09
While RAID (mirror) is useful and even essential for certain scenarios, for the average user it is probably overkill.  Hard drive failure, which RAID mirror protects against, is only one risk to your data.  RAID does nothing to protect you against file system corruption, accidental erasure, or (if a Windows system ever has access to the data over a network) malicious corruption by malware.  Anyone with a RAID mirror should also have a separate, reliable backup system such as additional offline drives, another server, or backup online.

---

### Post by lile001 on 2016-01-10
Yep, ditto all that stuff, I've got offsite backups and so on.  BUT I don't agree that RAID is overkill, for my needs ( I run a business on my computer and I need that data to be reliable).  

I'm just surprised that I could not find any documentation that says this works in Ubuntu, ( and did find documentation that says otherwise)  so I thought I should document it myself.

---

### Post by QIII on 2016-01-10
You have found a solution that works with this hardware in your case.  This does not mean that your solution is applicable to all situations, nor does it mean that other answers found on the Forums are invalid.

Please bear in mind that you are making sweeping assumptions based on a sample size of one.

---

### Post by CharlesA on 2016-01-10
The card you mention is limited to RAID 0 and RAID 1 and PCI-e x 1. What would you do if you needed to run RAID 5 or 6?

I made the mistake of getting one of those "cheap" RAID cards that didn't have a driver built into the kernel. DKMS does not work very well and having to compile the module from scratch after DKMS fails is just lovely. The best part of the card I had was that the kernel modules only supported 2.4 and 2.6 kernels. If I wanted to use it on a 3.x kernel, I had to hack up the code for the build environment. It was a painful lesson, but something that crops up on these forums every so often.

Point being - RAID might be "easy" if you bother to do your research and get something that will work for your environment.

Do not discount software raid and mdadm. What happens if your RAID card dies and there is no replacement? Do you need to rebuild your array from scratch and restore from backups or are you able to get another card and *hope* it detects the array and allows you to recover?

---

### Post by SeijiSensei on 2016-01-10
"Serious" RAID cards cost about $100 or more.  The ones that use [SAS]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022629&IsNodeId=1&bop=And&Order=PRICE&PageSize=90") are well-supported in the Linux kernel.  I wouldn't choose any other hardware RAID option on a server.

---

### Post by lile001 on 2016-01-16
*[COLOR=#000000]"Serious" RAID cards cost about $100 or more. The ones that use [/COLOR][SAS]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607%20600022629&IsNodeId=1&bop=And&Order=PRICE&PageSize=90")[COLOR=#000000] are well-supported in the Linux kernel. I wouldn't choose any other hardware RAID option on a server.[/COLOR]*

Perhaps so, siejisensei, however I am not running a server, I am running a desktop machine, and the $20 card I bought *seriously* works (that's a joke, don't take it seriously).  I don't know what features one finds in a serious card, I am sure they are awesome, but this was *good enough*.  Let's call this a *good enough* solution, for my 2c I wish I knew about it previously.  

Since I previously beat my head bloody against a wall trying to set up fakeraid earlier, and this card was a breeze, I thought the post would be worth it.    YMMV

Well, since I could not for the life of me get fakeraid to work at all, after a few weeks of posting on these forums and trying lots of suggestions, the fakeraid option isn't much use for my system and skill level.  Yes I bothered to do my research, read the Friendly Manual, spent a few weeks posting back and forth with helpful experts on thsi forum, and no I could not make fakeraid work after heroic effort.   I bought a Dell machine that did RAID 1 under windows - no amount of coaxing would allow that RAID to be recognized under Linux.  Go figgur.  

If the card dies, well, I will use my online remote backup to recover.  No problem, just bother.  Raid 1 is all I need, if you need something more robust, then get an expensive card with more options.    My point is, with my skill level (not great) I found this to be trivial compared to what I endured trying to set up software RAID.  Hopefully others will find this useful.

> **QIII said:**
> You have found a solution that works with this hardware in your case.  This does not mean that your solution is applicable to all situations, nor does it mean that other answers found on the Forums are invalid.

Please bear in mind that you are making sweeping assumptions based on a sample size of one.

Nor do I believe that other answers are invalid, except the statement in Official Ubuntu Documentation "RAID CARDS ARE EXPENSIVE".  That is no longer true, there are cheap RAID cards now,  and if I could figure out how to edit that page I would do so.  Someone else did edit that in the last few days, so don't bother looking it up.   

I am making the sweeping assumption that my experience which directly contradicted what I found on the Official Ubuntu Documentation for Fakeraid (don't look it up - someone changed it a few days ago) might be useful for the next poor sucker that comes along and can't make fakeraid work either.  I think that's a valid thing to post here, don't you?     Leave some breadcrumbs for the next guy.

---

### Post by weatherman2 on 2016-01-16
> **lile001 said:**
> I bought a Dell machine that did RAID 1 under windows - no amount of coaxing would allow that RAID to be recognized under Linux.  Go figgur. 

Not a surprise - I would never expect a proprietary Microsoft RAID to be supported in Linux.

> If the card dies, well, I will use my online remote backup to recover.  No problem, just bother.

Me too - which is the reason I don't even waste my time with RAID anymore.

If your data is that mission critical to the point where you MUST have RAID 1 and refuse to do it as a software RAID, I'd be buying a spare RAID card at the same time as a backup.  I have setup software RAID in Linux before and don't quite understand why it was so difficult for you - I suspect it wouldn't be for most people.

---

### Post by lile001 on 2016-01-16
> **weatherman2 said:**
> Not a surprise - I would never expect a proprietary Microsoft RAID to be supported in Linux.



 I have setup software RAID in Linux before and don't quite understand why it was so difficult for you - I suspect it wouldn't be for most people.


Microsoft proprietary RAID doesn't work in Linux - YOU HEARD IT HERE FOLKS!  I wish someone had told me this 4 years ago when I was trying to make it work.   

Don't understand why it was difficult either.  Maybe it is just on Dell, or this particular Dell, but it was a fool's errand.  I just want someone else in my same situation to be able to find this thread and maybe find an easy out for something that might otherwise not be easy.

---

### Post by CharlesA on 2016-01-17
> **lile001 said:**
> Microsoft proprietary RAID doesn't work in Linux - YOU HEARD IT HERE FOLKS!  I wish someone had told me this 4 years ago when I was trying to make it work.   

Don't understand why it was difficult either.  Maybe it is just on Dell, or this particular Dell, but it was a fool's errand.  I just want someone else in my same situation to be able to find this thread and maybe find an easy out for something that might otherwise not be easy.

You mean using dynamic disks in Windows, right? That type of thing rarely transitions well due to the way MS handles it on their end, unfortunately.

However, if you are using fakeraid set up in the BIOS, that is handled differently - Windows has their own driver and it is possible Linux does as well, but I'm not sure how well they translate between the two. In my experience, if you have an array running on Windows, it will need to stay with Windows. Same with Linux. That just seems to be how it is - different tech that isn't compatible with each other.

---

