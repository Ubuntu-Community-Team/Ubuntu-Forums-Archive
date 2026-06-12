---
title: "Dell Latitude E5510 unusable as native Ubuntu laptop"
date: 2011-02-11
forum: Hardware
---

### Post by tsr2 on 2011-02-11
I have a brand new Dell Latitude E5510 (a Core i3 variant) as a new work machine. I started out by experimenting wiith a Linux Mint (Debian Edtion) Live CD. This only gave me a grey screen CTRL-ALT-F1, CTRL-ALT-BACKSPACE, etc. had no visible effect.

I loaded up an 10.04 release candidate CD and got a very nice desktop, unfortunately I then installed all the updates, after which I was back to the grey screen :(. Reinstalling a "clean" 10.04RC without reformatting, to save time got me "restricted graphics".

I started again with a reformat this time, upgraded directly to Maverick Meerkat and I was straight back to the grey screen ](*,)

I don't have a vast amount of time to dedicate to getting this running, so I think I'm probably going to have to abandon the idea of a native installation and install under Win7 and Virtualbox :sad:

---

### Post by jpl888 on 2011-02-11
I'm sorry you are having trouble. Looks like a graphics driver problem, we could do with some more detail like the model of graphics card you have?

If you don't know it off the top of your head you can run "lspci" from a terminal and tell us what it is from that.

We will then be able to give you options.

Perhaps you could try downloading a 10.10 CD and install that.

Generally Dell laptops are well supported by Ubuntu, my feeling is that you have an Nvidia or ATI graphics card and that the root of the issue is related to the use of the proprietary driver.

---

### Post by tsr2 on 2011-02-11
> **jpl888 said:**
> I'm sorry you are having trouble. Looks like a graphics driver problem, we could do with some more detail like the model of graphics card you have?

If you don't know it off the top of your head you can run &quot;lspci&quot; from a terminal and tell us what it is from that.

When I posted that I was unable to get to any kind of terminal to run lspci, so I couldn't really post any details. I have now managed to boot into an older kernel (2.6.32-21), so I can now give you the lspci output (attached).

---

### Post by jpl888 on 2011-02-11
It's an Intel chip. When you booted from the older kernel did you get proper graphics then?

---

### Post by tsr2 on 2011-02-11
> **jpl888 said:**
> It's an Intel chip. When you booted from the older kernel did you get proper graphics then?

The graphics seem just fine with the 2.6.32 kernel.

---

### Post by jpl888 on 2011-02-11
What version is the newer kernel?

---

### Post by tsr2 on 2011-02-11
> **jpl888 said:**
> What version is the newer kernel?

It's kernel 2.6.35-25.

---

### Post by jpl888 on 2011-02-11
Try the oldest Maverick kernel (2.6.35-22) i.e. 

```
sudo apt-get install linux-image-2.6.35-22-generic
```

---

### Post by tsr2 on 2011-02-11
> **jpl888 said:**
> Try the oldest Maverick kernel (2.6.35-22)

It's playing silly buggers. I've installed that kernel, but I don't seem to be able to get it to give me a choice. As soon as the BIOS screen disapears I press ESC several times. I get a flash of the Ubuntu splash screen, and a couple of flashes of a cursor, then on to the blank screen of death.

---

### Post by jpl888 on 2011-02-11
Use shift instead of escape.

---

### Post by tsr2 on 2011-02-11
> **jpl888 said:**
> Try the oldest Maverick kernel (2.6.35-22)

Finally got into 2.6.35-22. I got a flash of a message (could not load /path/to/modules.dep) and I'm back at the grey screen.

---

### Post by jpl888 on 2011-02-11
Try the latest 2.6.35 mainline kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

If it doesn't work try 36 37 and 38.

---

### Post by tsr2 on 2011-02-12
> **jpl888 said:**
> Try the latest 2.6.35 mainline kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

If it doesn't work try 36 37 and 38.

Thanks for all the help, I've spent a day and a half on this, when I was hoping to do something productive and I can't spend any more time on it. I've tried 32, 35 and 38. The only one that "worked" was the original 32 off the 10.04RC. I've now got a set up with Maverick Meerkat installed, but booting the old 32 kernel. That works sufficiently for now. I don't think suspend works, but I can live without that for the time being.

I'll try new kernels occasionally, when I have time and motivation, but I'm not holding my breath waiting for one that will work on that machine.

---

### Post by jpl888 on 2011-02-12
You're welcome.

Yeah you have the right idea, stick to what works, just bear in mind there is a very slim chance that kernel could be hacked.

I'd say if you wait until Natty is released and then try that you may have more joy.

---

### Post by tsr2 on 2011-02-14
> **jpl888 said:**
> You're welcome.

Yeah you have the right idea, stick to what works

Sadly it's locked up solid twice today, so I have to conclude that it's not viable. I'm just putting Windows 7 on there and Linux is just going to be a guest OS, although it is the OS I will be mostly working in. ](*,)

---

### Post by jpl888 on 2011-02-14
It's just struck me that although this is probably an Intel graphics driver issue it could equally be a hardware problem.

I suppose if you are getting problems and lock ups in Windows 7 it will tell you that.

BTW I had half a mind to suggest a BIOS update earlier and looking at the download page for the E5510 there is a BIOS update from December (A07) which contains a video BIOS update and is labelled urgent. 

[http://support.euro.dell.com/support/downloads/download.aspx?c=ie&cs=iedhs1&l=en&s=dhs&releaseid=R288375&SystemID=LAT_E5510&servicetag=&os=W732&osl=en&deviceid=22283&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=429060](http://support.euro.dell.com/support/downloads/download.aspx?c=ie&cs=iedhs1&l=en&s=dhs&releaseid=R288375&SystemID=LAT_E5510&servicetag=&os=W732&osl=en&deviceid=22283&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=429060)

If you haven't managed to get Windows 7 back on there we can still update the BIOS from Ubuntu. Just let me know and I will get you a link to the hdr file.

Best of luck with it.

---

### Post by tsr2 on 2011-02-14
> **jpl888 said:**
> It's just struck me that although this is probably an Intel graphics driver issue it could equally be a hardware problem.

I suppose if you are getting problems and lock ups in Windows 7 it will tell you that.

BTW I had half a mind to suggest a BIOS update earlier and looking at the download page for the E5510 there is a BIOS update from December (A07) which contains a video BIOS update and is labelled urgent. 

[http://support.euro.dell.com/support/downloads/download.aspx?c=ie&cs=iedhs1&l=en&s=dhs&releaseid=R288375&SystemID=LAT_E5510&servicetag=&os=W732&osl=en&deviceid=22283&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=429060](http://support.euro.dell.com/support/downloads/download.aspx?c=ie&cs=iedhs1&l=en&s=dhs&releaseid=R288375&SystemID=LAT_E5510&servicetag=&os=W732&osl=en&deviceid=22283&devlib=0&typecnt=0&vercnt=5&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&source=-1&fileid=429060)

If you haven't managed to get Windows 7 back on there we can still update the BIOS from Ubuntu. Just let me know and I will get you a link to the hdr file.

Best of luck with it.

The possibility that it's hardware had occurred to me. I'm assuming that it's not at this stage, but will reconsider that, if there are problems under Windows.

The BIOS identifies itself as A07, so I assume it's up to date.

---

### Post by jpl888 on 2011-02-14
Yep that's the right one.

If you still get problems in Windoze it may be worth a reflash before you send it back.

---

