---
title: "Can Linux kill your laptop's HDD? Question returns."
date: 2012-05-23
forum: Hardware
---

### Post by originalred20 on 2012-05-23
Hi all!

I saw a Linux magazine cover, where it said: "Optimizing linux for laptops". I couldn't afford to buy it, so I started searching the internet. First I found this [http://hardware.slashdot.org/story/07/10/30/1742258/ubuntu-may-be-killing-your-laptops-hard-drive  ]("http://hardware.slashdot.org/story/07/10/30/1742258/ubuntu-may-be-killing-your-laptops-hard-drive")
It's a very long discussion, but here you can find an article which explains a lot:
[http://lwn.net/Articles/257426/](http://lwn.net/Articles/257426/)

Anyway, as you can see it's like five year old, so I was wondering - where are we today? Is it somehow fixed? Does ubuntu recognize laptops or whatever? What has changed since then?

regards

---

### Post by idoitprone on 2012-05-23
> **originalred20 said:**
> Hi all!

I saw a Linux magazine cover, where it said: "Optimizing linux for laptops". I couldn't afford to buy it, so I started searching the internet. First I found this [http://hardware.slashdot.org/story/07/10/30/1742258/ubuntu-may-be-killing-your-laptops-hard-drive](http://hardware.slashdot.org/story/07/10/30/1742258/ubuntu-may-be-killing-your-laptops-hard-drive)
It's a very long discussion, but here you can find an article which explains a lot:
[http://lwn.net/Articles/257426/](http://lwn.net/Articles/257426/)

Anyway, as you can see it's like five year old, so I was wondering - where are we today? Is it somehow fixed? Does ubuntu recognize laptops or whatever? What has changed since then?

regards


[LIST]
[*]"*Unix was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things.*" – [Doug Gwyn]("http://en.wikipedia.org/w/index.php?title=Doug_Gwyn&action=edit&redlink=1")
[/LIST]
nuff said


the hardware will be fine

---

### Post by goaliedude3919 on 2012-05-23
That is a pretty excellent quote. 

Just make sure you don't edit something that you don't know what it does. If you don't know what something does, research it before modifying it. As long as you do that, you should have no problems with Linux.

---

### Post by Yellow Pasque on 2012-05-23
> As might be guessed, the problem is not Linux-specific either, with both Mac OS X and Windows laptop users reporting high load cycle counts as well.

The answer is to keep an eye on load cycle count and reduce or turn off disk power management if it's a problem.

The biggest example of this problem I've seen reported lately is with Western Digital disks using the "Intellipark" feature, which aggressively parks the head every 8 seconds, where Linux tends to read or write to the disk every 10-15 seconds. That leads to a lot of load cycles. I know the Caviar Green series uses Intellipark, and maybe some other WD drives too.

---

### Post by lukeiamyourfather on 2012-05-23
Linux doesn't kill laptop hard disk drives. Overly aggressive power management settings kill laptop hard disk drives which is the case with any operating system.

---

### Post by originalred20 on 2012-05-23
yeah, the Doug Gwyn quote is sexy, but I'd rather know if ```
 hdparm -B 254 /dev/sda
``` is the right solution? Has anyone tried it yet? 

It's kinda important, because I had PATA disc once and it died shortly after installing ubuntu on it (I don't know what was the actual reason), so I want to take precaution, before I install Ubuntu on my brand new laptop.

I'm also asking if in new Ubuntu releases this problem is "magically" fixed?

---

### Post by 3Miro on 2012-05-23
The article is from 2007, this is 10 versions of Ubuntu ago and I can't even count how many versions of the kernel. Are you guys sure this is even remotely relevant anymore?

---

### Post by originalred20 on 2012-05-23
> **3Miro said:**
> The article is from 2007, this is 10 versions of Ubuntu ago and I can't even count how many versions of the kernel. Are you guys sure this is even remotely relevant anymore?

Exactly my question.

---

### Post by jmore9 on 2012-05-23
I been using various linuxes since caldara linux came out.  The only time i believe linux killed a hard drive was 4 years ago and i was using a laptop drive in my desktop.  I had extra one so why not ?  Turns out the autopark feature works just fine in a desktop as if in laptop.  After being on for about 3 weeks it started making metal contact noises and then clicking and then stopped completely.

Ohter than that time i have not have 1 drive fail.  And there were a couple of time i reformated a drive (IDE) about 6 times in a row trying to get an intall to work.

Now i have had the bearings start to go bad , you get the high pitch squeal and grinding noise on start up and shut down.  Had a couple of them.  Used them also till they gound to a stop.

---

### Post by jjiggens on 2012-05-23
actually this issue was present before 12.04 went LTS, but has been patched since then. 

However it appears that default apm_battery = 128 which does not allow the disk to spin down at all on battery now.

Changing it to 127 in /etc/hdparm.conf and setting the spin down time to = 36 will allow your disk to spin down after 3 min, which is not too aggressive and will allow spinning down to save battery whilst not worrying about damaging your hard disk after prolonged use.

YOur results may vary though as some users report soem weird spin up and down issues still when setting the spin down time less aggressively.

> This bug was fixed in the package hdparm - 9.37-0ubuntu4
 ---------------
hdparm (9.37-0ubuntu4) quantal; urgency=low
   * debian/hdparm-functions, debian/95hdparm-apm: set our spindown policy
    back to -B128 instead of -B127.  Too many drives misbehave too badly
    with this setting, possibly leading to drive failure.  We should revisit
    this once we understand why people's drives are spinning back *up* so
    frequently.  LP: [#952556]("https://bugs.launchpad.net/bugs/952556").


---

### Post by lukeiamyourfather on 2012-05-23
> **3Miro said:**
> The article is from 2007, this is 10 versions of Ubuntu ago and I can't even count how many versions of the kernel. Are you guys sure this is even remotely relevant anymore?

I've been using Ubuntu and Fedora on my ThinkPad X61 for almost five years without issue so my guess is things have been sorted out.

---

### Post by 3Miro on 2012-05-24
I thought we are talking about shrinking the life-expectancy of the HDD by a year or two, an HDD doesn't die in a few months. I have been using Linux exclusively for over 4 years now and with multiple desktops HDDs as well as laptops I have had only one HDD death. That particular HDD was something that I purchases used for 10 dollars and then I abused the crap out of it (constantly moving large files to/from it), after about 6 months the 10-dollar HDD died.

If you are worried that Linux will kill your HDD in a few months, you are wrong. This doesn't happen.

---

### Post by originalred20 on 2012-05-24
> **jjiggens said:**
> actually this issue was present before 12.04 went LTS, but has been patched since then. 

However it appears that default apm_battery = 128 which does not allow the disk to spin down at all on battery now.

Changing it to 127 in /etc/hdparm.conf and setting the spin down time to = 36 will allow your disk to spin down after 3 min, which is not too aggressive and will allow spinning down to save battery whilst not worrying about damaging your hard disk after prolonged use.

Great answer, thanks!
So to sum up:  on Ubuntu 12.04 the ```
 hdparm -B 254 /dev/sda
``` isn't necessary, but it's still worth to do the apm=battery thing, am I right?

When you look at this thread title and go back to the article I linked in my first post, you will see, that this is/was general operating systems issue on laptops. We all try different distros, so I'd appreciate, if you shared your knowledge about this, when it comes Linux family in general.

---

