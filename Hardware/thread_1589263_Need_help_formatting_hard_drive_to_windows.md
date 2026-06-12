---
title: "Need help formatting hard drive to windows"
date: 2010-10-06
forum: Hardware
---

### Post by lobinetech on 2010-10-06
I am trying to install a new hard drive on a laptop I am servicing but the laptop wont find the HD when i tried to install windows on it,bought replacements and I am getting the same issues.I want to intsall ubuntu on the drive so i can be able to use the HD utility to format it to windows so I can also install windows on it
the laptop is 
Sony Vaio VGN-NR430E
Please how do I go about this
Like ubuntu so far

---

### Post by trundlenut on 2010-10-06
What version of windows?

---

### Post by leclerc65 on 2010-10-06
Gparted will format anything and it's free.

---

### Post by lobinetech on 2010-10-06
> **trundlenut said:**
> What version of windows?
 windows 7
> **leclerc65 said:**
> Gparted will format anything and it's free. 
thanks,will look at it but if i cant find the HD on the laptop how do i use it,ohh,with ubuntu?

---

### Post by Morbius1 on 2010-10-06
If you installed a new HDD and Window or Ubuntu can't find it then your problem isn't in the OS it is in your BIOS. Boot to your BIOS and see if the hard drive is even recognized as being present.

---

### Post by lobinetech on 2010-10-06
> **Morbius1 said:**
> If you installed a new HDD and Window or Ubuntu can't find it then your problem isn't in the OS it is in your BIOS. Boot to your BIOS and see if the hard drive is even recognized as being present.
 ubuntu found it but when i tried to install windows it wouldnt

---

### Post by lobinetech on 2010-10-06
now i ahve ubuntu installed and went to disk utility and said disk is healthy,so How do I formatt it to be able to install windows on it.
pls help

---

### Post by trundlenut on 2010-10-06
It does sound like there could be some sort of driver issue with Windows which is preventing it recognising the drive.

---

### Post by lobinetech on 2010-10-06
found out how to formatt it but still wont let me,it said it was mounted(sorry I am new to this)then i when i tried to unmount it it says it can only be unmounted from root

---

### Post by Morbius1 on 2010-10-06
Because you'll be formatting over the partition that holds the software that's being used to format the partition.

I don't remember if the Ubuntu LiveCD has gparted already installed and operational but if it does then you could do it from that.

Or you can download Parted Magic which has gparted plus a whole lot more. Every Linux user and every mulibooter should have in their tool chest: 
[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

---

### Post by lobinetech on 2010-10-06
just downloaded and about to try it out,thank you

---

### Post by leclerc65 on 2010-10-06
Gparted iso can be downloaded from [here]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/").
You can burn it to a CD then use the CD to boot, instead of using the one in Ubuntu.
But as Morbius1 said, it's probably the Bios setup you need to tinker with.

---

### Post by lobinetech on 2010-10-06
> **leclerc65 said:**
> Gparted iso can be downloaded from [here]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/").
You can burn it to a CD then use the CD to boot, instead of using the one in Ubuntu.
But as Morbius1 said, it's probably the Bios setup you need to tinker with.
 really new to thinkering with stuff like that and i am learning a big deal,hoiw do i change the bios settings?
on my screen when i press F2 i see the bios but no where to edit
and yipeeeeeeeeeeeeeeeeeee,i think i got it,allowing me to install windows,used pmagic to format and will see what happens
thanks a great deal

---

### Post by lobinetech on 2010-10-06
working perfectly,tyhanks to everyone for the contribution

---

### Post by claven123 on 2010-10-22
I was told not to install windows AFTER an installation of linux. Is this correct?

---

### Post by leclerc65 on 2010-10-24
You have to know how to recover the Grub, so it's easier to install Windows before Ubuntu.

---

