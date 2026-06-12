---
title: "PCMCIA combo card (USB &amp; Firewire) not working properly in Hardy"
date: 2008-11-11
forum: Hardware
---

### Post by fINTiP on 2008-11-11
I own an HP PCMCIA card with one USB port and one Firewire port. However, while it will charge my ipod, I cannot access my ipod from it- I also remember having a problem where a certain usb webcam would work for a moment after starting, and would glitch worse and worse until it was just cycling beyond recognition.

This seems to indicate that packets are being dropped through the USB. I think that the data getting worse on the webcam was an example of dropped data packets, possibly due to heat. Supporting that suspicion was that removing the card showed that it was, indeed, very hot. If anyone needs me to post a "dmesg" of what I get when I plug a USB drive in to it, I can do so.

I don't have anything to test the Firewire with right now, so no status on that.

About the card:

Here's what's printed on the back-
HP Product Number: PM098A#ABA rev 1.0- A
S/N: UMI[SIZE="6"][FONT="Courier New"]5302481[/FONT][/SIZE]
Web: [www.microinv.com/hp](www.microinv.com/hp)
Tech Support Phone: 1-866-314-7239
[FCC logo] Canada ICES-003 Part B
Model Number: UT-5271-1
Product of China

I cannot call the tech support phone because I'm in a foreign country, and the webpage doesn't exist. microinv.com does work, and they seem to have some similar products, but I didn't see how to use any information there myself.

Googling gave me sparse response, but I found these two potentially valuable bits:

The first is from [here]("http://osdir.com/ml/linux.kernel.firewire.user/2006-04/msg00002.html"), a guy talking about exactly the same card, and apparently the same problems...

Most of it is over my head, as I know very little about kernal development.

> Morpheus wrote:

    I am having trouble using a CardBus IEEE 1394/USB 2.0 adapter
    manufactured by HP (PM098A#ABA) under Debian/stable kernel 2.6.8-2-686.

...

    This used to work in older versions of the 2.4 kernel. 


With the same card?

    It seems that IEEE 1394 support regresses as kernel versions increase.


There were regressions during the 2.5/ 2.6 line of development but it is getting better. Try the latest stable release of the Linux 2.6 series, which is 2.6.16(.1). There were a lot of bug fixes since 2.6.8.

But before you update the kernel, make sure that ohci1394 is loaded with its default parameters, i.e. phys_dma=1.

When you install a new kernel, take care to keep the old kernel bootable. If it should be easier for you for some reason to install only 2.6.14.x or 2.6.15.x (e.g. because you can then use a source RPM of your distribution or if the installed userspace environment does not meet all requirements of the newest kernel), then try these and --- especially if you have an ALi based CardBus card --- also apply these patches: [http://me.in-berlin.de/~s5r6/linux1394/updates/](http://me.in-berlin.de/~s5r6/linux1394/updates/)

I can't guarantee though that the most recent driver sources indeed fix this particular problem. I saw login timeouts on two or three occasions during the last few months too when I connected devices after a reboot. Unloading and reloading of ohci1394 "fixed" it. I forgot to take note which driver versions were involved; however this may also be attributed to a somewhat buggy PCI 1394b card I have, or to the Prolific based enclosure which may have been the only one to stumble over this.

    I have searched the net and found a lot of people complaining about
    this problem,


If these people had ALi cards, then the problem is definitely fixed in 2.6.16. (Yes, it took this long.)

BTW, unless people complain _here_ or at bugzilla.kernel.org, driver problems will remain unfixed. (I will gradually start to watch distro bugzillas too as spare time permits.) Moreover, there are not many active 1394 developers and contributors, therefore bugs often cannot be diagnosed and fixed as fast as we like.
--
Stefan Richter
-=====-=-==- -=-- ----=
[http://arcgraph.de/sr/](http://arcgraph.de/sr/)


The second piece of info is that I found a driver for a combo card with exactly the same Model Number, but from a different company- since my card says "Product of China" on it, I don't doubt HP just slapped their label on it. The driver is [here]("http://www.unixtar.com.tw/p4.php"), near the top of the list, for model UT-5271-1.

It would be AWESOME if I could get this working, as my laptop (Dell C640) has only ONE usb port, and it's usb 1.1... moving gigs of music on my ipod 160gig is a several hours long process, and a huge pain- especially because the ipod usb plug barely fits, and has more than once come out of the plug, corrupting my data and forcing me to use floola's valuable restore function.

Any clues? Even telling me what kernel version I have in 8.4?

---

