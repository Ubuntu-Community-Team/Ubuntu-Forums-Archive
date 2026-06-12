---
title: "Install Ubuntu on a Dell latitude with PCMCIA CD drive"
date: 2006-09-30
forum: Hardware &amp; Laptops
---

### Post by Lynswin on 2006-09-30
I am having a big problem, I cannot even run the live cd as my Dell Latitude Csx will not boot from the attached PCMCIA Cd drive (I seem to remember having similar problems when trying to install Win xp a couple of years ago but I cannot remember how I overcame it!).

I have an internal HDD, and external floppy and a PCMCIA CD Rom drive. I have the most up to date BIOS version and I have tried setting the boot sequence to CD Drive and also PCMCIA but the drive is never 'visible' until windows has started. I also tried using Smart Boot Manager but again, the drive was not 'visible'. I have the drivers for the PCMCIA CD drive on a floppy disc but I am not sure if this is of any use!! As soon as windows is up and running the drive is visible and works great (and I have also cheked that the Ubuntu CD is OK as it runs fine on my desktop).

I have read a few methods on Google but these generally involve removing the HDD from the laptop (which is not really an option for me) or they are written so that only someone with a PHD in computer science can understand!!

If anyone can give me a straightforward, step by step guide on how to do this I would be very grateful. I would like to initially run both Windows and Ubuntu with a view to eventually uninstalling Windows if I find that Ubuntu can do everything I need it to.

Any help is gratefully appreciated

Thanks

Lynda

---

### Post by Jussi Kukkonen on 2006-09-30
This is a little tricky... Not because the whole process is so difficult, but because AFAIK no-one's packaged it nicely like other install options (let's face it, it's not the most popular way to install Ubuntu). I wouldn't hold my breath waiting for an easy install option if you can't boot from the CD... One thing you could try is [http://instlux.sourceforge.net/](http://instlux.sourceforge.net/), I have no idea how stable it is though.

I'll give you an idea how it could be done the hard way.  This is not a step-by-step guide, and there may be other ways too... There are two things needed if the computer won't start from the CD:
[LIST]
[*]**Copy the CD image to hard drive**
This can be probably be achieved with a live-floppy, like  TomsRtBt: [http://www.toms.net/rb/](http://www.toms.net/rb/)
[LIST]
[*]create a partition for the image on the hard disk (this can be the future Ubuntu partition), e.g. ext3 filesystem
[*]mount the CD, copy the image to the new partition
[/LIST]
[*]**boot from the copied image**
This can probably also be done with the live-floppy I mentioned, by making the floppys boot loader load the image on the hard drive. Can't help with that though, because tomsrtrb uses lilo and not Grub, and I know nothing about lilo.
[/LIST]

---

### Post by Lynswin on 2006-09-30
Hi.

Many thanks for the reply. I like the sound of the second option (booting from an image from the hdd) but unfortunately I don't know about partitioning drives and you have lost me with the talk about an image file (sorry, I have always done everything through windows and although I know windows very well when it comes to anything more technical I am a bit lost - unless someone can talk me through things step by step!!)

I am going to have a look at the instlux option though as this sounds like it may work for me.

Best wishes & thanks again

Lynda

---

### Post by Lynswin on 2006-09-30
I have had another go at this using Instlux and it looked as though it was finally working but unfortunately it got to the start of setting up and said it couldn't find cdrom or something ........grrrrrrr.

I have had another idea - would it be possible to install an older version of Ubuntu (or any other os) from a floppy disk and then upgrade to Ubuntu? As soon as I have an OS up and running the pcmcia seems to work fine.

Any more help would be appreciated.

Thanks
Lynda

---

### Post by mastersync on 2007-06-30
I have the same problem. How do this turn out ?

Sorry for necroposting.

---

