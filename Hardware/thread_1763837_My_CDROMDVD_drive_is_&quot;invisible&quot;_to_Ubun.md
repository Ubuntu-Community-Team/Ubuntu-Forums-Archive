---
title: "My CDROM/DVD drive is &quot;invisible&quot; to Ubuntu 11.04"
date: 2011-05-20
forum: Hardware
---

### Post by garylben on 2011-05-20
I just installed Ubuntu 11.04 on a rebuilt computer using an Asus P8P67 LE mb (new one with the B3 revision) and a Sandy Bridge Core i5 2500k cpu.

Installing from a CD failed. The OS "couldn't find a medium containing an OS," or words to that effect.  I tried a 10.10 install CD i'd used with success on my old PC.  It booted but bailed on that first step where it looked for a CD drive.  Couldn't find one.

I installed from a thumb drive.  Went OK.  However I still have no CD or DVD drive.  Nothing in /dev to suggest one exists. Nothing in any of the utilities I've checked either.  It seems to be as if it has been unplugged.  I'm dual boot with Win7 and everything, including the DVD/CD drive, is working just fine.  

Is this a Sandy Bridge issue, or perhaps some BIOS setting I haven't been able to find?  Anyone have any ideas of what I can to?  I'm quite new to Ubuntu, having just a few weeks of exploring 10.10 on my old PC before it's untimely demise.  

Any thoughts or help would be appreciated.  Thanks.

---

### Post by sidzen on 2011-05-21
some cdrom drives (especially multidrives) are incompatible.
your having to use usb stick to install is indicative of this probability.
have not had any problem with LG -  check compatibility database, to be sure.

Like -- [http://www.newegg.com/Product/Product.aspx?Item=N82E16827136236](http://www.newegg.com/Product/Product.aspx?Item=N82E16827136236)

Or go back to 10.04LTS, if necessary.

---

### Post by garylben on 2011-05-21
Thanks for the quick reply.  It did make me think.  I was locked into looking at the software or the MB/CPU combo. I wasn't really aware of hardware compatibility issues.

  I did download a firmware fix from Lite-on, and it didn't help.  I'm curious as to why I could use the same drive on my "old" computer to install 10.10 but now it fails with a different mb and cpu.  I'm not certain I could access the cd-rom with 10.10 after installing, however.  Just don't recall.  I use the CD rather rarely.  Any thoughts there?  

I'll also try some bios tweaks that talk about legacy systems and reduced capability attachments just to be sure.  

Thanks again.  Got me out of a thought process rut.

---

### Post by sidzen on 2011-05-24
I have yet to get a LiteOn to work with my flavors of Linux (so I gave up).  Also, I'm sticking with 10.04.

You're welcome &
Welcome!

---

