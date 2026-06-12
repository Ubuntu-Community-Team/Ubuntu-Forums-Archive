---
title: "Lack of Space on Eee PC 900"
date: 2008-08-04
forum: Hardware
---

### Post by flautim on 2008-08-04
I bought an Asus 900 **_Linux _**but quickly realised I´d made a mistake as my progammes wouldn´t load!  I bought an ordinary Windows XP disk and loaded this and of course had the same problem as a guy on a previous thread - lack of space.

Is there a special version of Windows for the Eeepc or is it simply a case of deleting as much as poss once it´s loaded?  Certainly by using Firefox I´ve been able to delete Explorer so have also got around 500mb "spare".

At the moment I´m using a pendrive for programs and files but if I can get hold of a larger SD card that would be preferable I think.

Anyone got any suggestions or advice please?

---

### Post by TenPlus1 on 2008-08-04
Have the package manager delete .deb files after installation, this will also clear the packages on the hard-drive already which will save you a LOT of space...

Plus, you could uninstall the crap you dont need/want/use...

---

### Post by flautim on 2008-08-04
:-) Thanks for the ideas.  Will certainly give the first one a try.  I de-crapped when I put XP on - I did think that far!!!  First idea sounds very good - never heard of those files before.  Thanks very much.

---

### Post by RedPandaFox on 2008-08-05
How big was your eeepc hd? Im running an eeepc 701 with 2gb ssd with XP installed and a 4gb 701 with XP, and can run both with Ubuntu will all the programs I need to install. You sure its the 900 you bought?

---

### Post by tact on 2008-08-05
Hey there...

Depending on where and when you bought your eeepc 900, getting the linux version may not have been a "mistake" at all.   There was a time when the XP version shipped with only 12GB SSD whilst the linux version of the same eeepc shipped with 20GB SSD for the same price.  (Thus making it a smart move to buy the linux version even if you wanted to run XP in the end - only issue is you'd have to install XP yourself).

When I bought an eeepc for my wife's limited net uses I bought the linux version (comes with xandros linux) and I wiped it off and installed full ubuntu.  No problems with space -  I think she has about 12GB freespace (and thats with a few movies on the SSD already).

The boxed set I bought came with an install CD for both xandros linux and WinXP.  Did your's not come with the CD's?  

Lastly - it looks like (?? am I reading you right?)  you are looking for advice on how to install WinXP on your eeepc.  

Not sure why you ask that question in the ubuntu linux forums?  I would have thought any WinXP forum, or any eeepc forum would be more appropriate.

Good thing this bunch at ubuntu forums are a friendly bunch.  :)   I see some have already given some advice.   I cannot really help with getting XP installed - I assume that the XP cd that comes in the eeepc box just installs a custom version.   

Also if it helps here is where you will find the eeepc forums:
[http://forum.eeeuser.com/index.php](http://forum.eeeuser.com/index.php)

---

### Post by tact on 2008-08-05
If you wanted to know about installing ubuntu onto an eeepc 900 this is what I did:
- the eeepc 900 I bought comes with 20GB of storage available, it is split across two SSD modules - one 4GB and one 16GB

I wanted to use the space as best as possible.  It would have been nice if I could put the operating system "/" on the 4GB SSD and everything else on the 16GB SSD.  But whilst its possible (with a lot of trimming) to fit the "/" file system into 4GB - I prefer to not trim, and have some spare space in there.  So for my peace of mind I like my root partition to be about 9GB size - which, of course, will not fit onto the 4GB SSD.

So...  after surveying a system I use every day and have heaps of extra software installed on -  I found that "/usr" runs a bit over 3GB.   So I put that on the 4GB SSD.

Then the rest "/" and "/home" etc..  all went onto the 16GB SSD.

I have since figured this is not at all the best way to do it.  Its ok.  But not best.  What I am planning to do soon is start over...  and use LVM (logical volume manager) to combine both the 4GB and 16 GB SSD's into one 20GB logical volume.  That way there will be no wasted space and no need to find something to fit perfectly into the 4GB SSD and not be afraid it will need more space in the future.

---

### Post by flautim on 2008-08-05
Hi All

Thanks for all the helpful info.

Why did I write on this ubuntu forum?  Because somehow or other it came up in a search and seemed like a good place to ask the question!

Yes I´m sure it´s te Eee pc 900 cos it says it on the underside!

At the moment I`m "stuffed" because I had a burglary at home at the weekend and the charger was nicked so I can´t use the Eee.  I´ve a new charger being sent to me, at which time I´ll come back and take note of what you´ve all kindly written and see what I can do to make my system sleeker.

Thanks again.
Flautim

---

### Post by vp100 on 2008-08-22
Hi Flautim,
you can get 4Gb and 8GB, an even a 16Gb SD card on ebay, some come with card reads.
As for operating system, you can cut it down, to save space, or use a utorrent to download one that been done already.

---

### Post by vp100 on 2008-08-22
Hi Flautim,
you can get 4Gb and 8GB, an even a 16Gb SD card on ebay, some come with card reads. same price as 1Gb or 2Gb in the shops.
As for operating system, you can cut it down, to save space, or use a utorrent to download one that been done already.

---

