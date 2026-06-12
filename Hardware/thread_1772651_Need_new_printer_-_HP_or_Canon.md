---
title: "Need new printer - HP or Canon ?"
date: 2011-05-31
forum: Hardware
---

### Post by oygle on 2011-05-31
Time to throw out the old HP 810c desktop printer. Was looking at some Canon and HP printers today, and need to know what would be the better printer, out of either HP or Canon.

The 'problem' with my scanner has been drivers, so I need to know, if the new printer **WILL** _definitely_ work on Ubuntu.

1. HP is cheaper per page for printing, and that is a concern, so I'd go for HP, IF it is going to work 100%

2. 2 Ubuntu computers - 64 bit 10.04 LTS and a 32 bit, version after 10.04 ??  Both computers are ASUS motherboards, if that makes any difference.

3. Have a router with wireless printer function, so can go wireless, but might be better to stay with USB.

Here are the models I have been looking at:

_HP_

Estation CQ140A
Premium C310A  CN503A
B210A CN216A
Premium C410A  CQ521A
B110A   CN245A
Pro 8500
Deskjet 2050  HPD0205
OJ 7500A

_Epson_

Artisan 835  C11CA73401
Workforce  623  C11CA70401
NX420  C11CA80401
Workforce  325  C11CBD8401

If someone can advise please.

Regards,

Oygle

---

### Post by dFlyer on 2011-05-31
My vote is for the HP. Make sure you install hplip-gui from the archives.

---

### Post by oygle on 2011-05-31
Wow, Gary, that was quick. Thank you.  :)

I went to the HP site, entered one of the model numbers in (C310A), and the drivers section actually has Linux there. Clicked on that, and it showed the [HP Lip Open Source site]("http://hplipopensource.com/"). So, that confirms your advice. I would use Ubuntu Synaptic package manager though to install that GIU you mentioned.

Looks good. :D

---

### Post by oygle on 2011-06-01
I thought I could choose any model, but it seems it is best to go to [HP-LIP recommended printers]("http://hplipopensource.com/hplip-web/recommended.html") and see what support is available for each one.

The minimum HPLIP version is 3.10.9 , whilst Synaptic tells me that version 3.10.2-2ubuntu2.2 is available. So it seems I have to install from the HPliP site, rather than from package manager.

---

### Post by I'mGeorge on 2011-06-01
Go for a HP. Most of HP printers come with drivers for linux on the installation disks while Canon printers usually don't come with native drivers so their support under linux is worst. Sure you can find open source drivers for Canon also , but there's a catch as open source drivers might not sustain all the functions of your printer and usually it's better to buy something that comes with native support for linux so you will have less head aches when installing it and using it afterwards.

---

### Post by Ziadance on 2011-06-01
Hello All,
I've just got my *hp* photosmart B110a home & I'm having difficulties setting it up.  

The disk that comes with it doesn't play on my laptop, so I went to [www.hp.com/support](www.hp.com/support) and followed all the instructions.  I downloaded what I thought was the driver but that isn't opening either.. 

any suggestions, thanks

---

### Post by I'mGeorge on 2011-06-01
> **Ziadance said:**
> Hello All,
I've just got my *hp* photosmart B110a home & I'm having difficulties setting it up.  

The disk that comes with it doesn't play on my laptop, so I went to [www.hp.com/support](www.hp.com/support) and followed all the instructions.  I downloaded what I thought was the driver but that isn't opening either.. 

any suggestions, thanks

the file you've downloaded, what extension does it has ?

---

### Post by oygle on 2011-06-01
Thanks 'I'mGeorge', seems HP is the go. I meant to have the thread title as "Need new printer - HP or Epson ?" , but put 'Canon' instead.  :oops:

Anyway, I have settled for a [HP Photosmart Premium e-All-in-One Printer - C310a (CN503A)]("http://h10010.www1.hp.com/wwpc/au/en/ho/WF06b/18972-18972-238444-410635-410635-4023238-4023242.html?jumpid=reg_R1002_AUEN")

---

### Post by Ziadance on 2011-06-01
> **I'mGeorge said:**
> the file you've downloaded, what extension does it has ?

Hi thanks for the quick reply,
Maybe I should have mentioned I'm a complete beginner.  Extension?

hplip-3.11.5(2).run

Does that answer the question
Z

---

### Post by oygle on 2011-06-01
Are [these instructions]("http://hplipopensource.com/hplip-web/install/install/index.html") what you need ?

---

### Post by I'mGeorge on 2011-06-01
> **Ziadance said:**
> Hi thanks for the quick reply,
Maybe I should have mentioned I'm a complete beginner.  Extension?

hplip-3.11.5(2).run

Does that answer the question
Z

yes it does. In a terminal try this
```

cd /path_to_hplip-3.11.5(2).run
chmod a+x hplip-3.11.5(2).run
sudo sh hplip-3.11.5(2).run

```

That should be all

---

### Post by marios88 on 2011-06-01
I would definitely go with HP, over the years i have never had a driver problem

---

### Post by Ziadance on 2011-06-01
I've found it now, thanks all x

---

### Post by jacob2012 on 2011-06-01
Canon is not good at all because you must turn on the printer from time to time. However for the waste of ink for each ignition, it is a harsh reality. This is surprising that with equal amount of ink, HP prints more pages than all its competitors. But as HP ink is very expensive, the cost of use remains high.

---

### Post by oygle on 2011-06-06
Thanks everyone for your help. I chose the HP C310a, installed hplip-gui, had to go to the latest version of Ubuntu to do that, but well worth it.

Am able to do everything within Ubuntu that the printer can do, so this is really great.

Thanks,

Oygle

---

