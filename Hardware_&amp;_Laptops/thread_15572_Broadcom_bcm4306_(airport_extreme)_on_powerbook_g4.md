---
title: "Broadcom bcm4306 (airport extreme) on powerbook g4"
date: 2005-02-15
forum: Hardware &amp; Laptops
---

### Post by paer on 2005-02-15
Hi,

First of all: I apologize if I seem to be rude in any way due to cultural or lingual problems - this is not my mother tongue.

I've used both gentoo and yellow dog linux on my powerbook (dualbooting with mac os x) but recently I decided to give ubuntu a shot. I tried the live cd (hoary current, built feb 4th), and everything looks smooth (as I knew it would - I've been using ubuntu warty for a while at my desktop system now...).

I remember searching the web for the broadcom driver for my airport extreme back when I where playing with gentoo, and I recall reading a lot of postings about drivers not existing for ppc-linux. Now it has gone a while since first linux install on my powerbook, so I was hoping this driver-absence would have changed. But it doesn't seem so. :o(

Ubuntu hoary live identifies my card correctly as an bcm4306 wireless card (802.11g), as I can see in Desktop->Administration->Device Manager. Still it doesn't do anything to launch it, and I can't see any modules (doing lsmod) that seem to have anything to do with bcm. iwconfig tells me that there are no wireless extensions on any of my network interfaces (lo, eth0, sit0 - whatever that is).

I've been searching the web (google) and the ubuntu forums for bcm4306 to see if there is any updated information since I last read about it, but what I can see is that there actually been some break-through on x86 ([http://ubuntuforums.org/showthread.php?t=14662&highlight=bcm4306](http://ubuntuforums.org/showthread.php?t=14662&highlight=bcm4306) <-- ndiswrapper seems to work) and on ppc with openBSD ([http://ubuntuforums.org/showpost.php?p=54130&postcount=4](http://ubuntuforums.org/showpost.php?p=54130&postcount=4)). This doesn't tell me anything about what I should do to make it work on my powerbook under Ubuntu, so please - if anyone knows anything more, tell me! Is there at all any way to get wifi to work with my airport extreme under ubuntu, and if it is: how do I do it? Any point in any direction will be helpful!

Thanks.

---

### Post by BigIslandVegan on 2005-02-18
I have been wondering about this too.  Here at the university it's uncommon to get a wired connection, certainly since they have invested in the wireless network recently.

The lack of hardware support for Airport Extreme makes Linux a non-option for me right now.  Wish I could use it and bluetooth with the T-Mobile unlimited internet service via the Motorola V600.  I wonder how long it would be till I am able to sit in the car and access the net with bluetooth and be at the university and use the wireless all from the PowerBook G4 12" 1GHz.

Hmm, just wondering  :-) 

Thank you all for your volunteer work and getting it to this point!

---

### Post by zenwhen on 2005-02-19
When Broadcom releases the specs for the hardware, drivers can be developed. If they do not, drivers cannot surface. This is not the fault of the Ubuntu or kernel devs, and nothing can be done until consumers demand the ability to use their hardware with any OS they please.

---

### Post by chascon on 2005-04-27
I entirely agree with zenwhen.  And to get you apprised of why yuo should demand specs an code read:

"the broadcom chipset used by apple 
for the airport extreme is also used in the Linksys WAP54G wifi access point 
... which runs under linux. This of course means there is a kernel module that 
drives the chip, and thus that either Linksys or Broadcom have code some 
driver for it. It makes me angry to think they would have gone that far and 
stopped there without considering their customers who care about running linux 
on their apple hardware."
[http://lists.debian.org/debian-powerpc/2004/02/msg00445.html](http://lists.debian.org/debian-powerpc/2004/02/msg00445.html)

and 

"A few months ago, I wrote to the kernel list describing the
relationship between Linksys (now business unit of Cisco Systems),
their WRT54G 802.11g wireless home gateway, and Linux. At the time,
we had recently discovered that the WRT54G was using a great deal of
software made available under the GPL, but was not giving credit to
the authors, or providing the source as required by the GPL.

After a bit of public pressure, Linksys posted their "GPL Code Center"
[1], where they claim that "the GPL source code contained in this
product is available for free download" [2]. Shortly after the code
center was made available, a group of developers pointed out to
Linksys that their source code, particularly their Linux kernel code,
was incomplete.

Previously, it was thought that the WRT54G source releases had only
neglected to include the source code for the various kernel modules
used to run the ethernet and wireless interfaces. However, at this
time, it is clear that the kernel proper of the WRT54G itself has had
functionality added to it. This functionality is not present in the
kernel code that Linksys has provided at their "GPL Code Center".

That is to say, there is code STATICALLY LINKED with the Linux kernel
running this device that is not present in the source download. This
code seems to be shared between the Broadcom ethernet and wireless
chips. It appears to be primarily responsible for configuring the
Sonics' SiliconBackplane and handling DMA transactions for both
devices."
[http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html](http://www.ussg.iu.edu/hypermail/linux/kernel/0309.3/0904.html)

---

### Post by ssam on 2005-04-27
on x86 it might be possible to get this to work using ndiswrapper and the windows driver, but i dont think there is anyone working on anything similar for powerpc.

sit0 is a ipv6 over ipv4 tunnel. you may find that turning ipv6 off speeds up the internet a bit,i think there are instructions in the wiki or on ubuntu guide.

if you have a powerbook you might want to find a pcmcia card. i find a cisco aironet 340 works very nicely in linux. it is recognised 'out of the box' you just need to tell it the ssid and to use dhcp in the network preferences.

i was lucky enough to buy a 15 powerbook one week before the aluminiums arrived, i was slightly anoyed at the time, but it has the original airport, which works well in linux.

good luck

sam

---

### Post by fromtheflames on 2005-10-15
[Check this out](http://ubuntuforums.org/showpost.php?p=412981&postcount=2)

---

### Post by Digitallysick on 2005-10-25
call me crazy, but if osx is based on linux, and it works with the airport extreme, couldn't someone convert code for use with unbuntu? seems like it would not be that hard to do

---

