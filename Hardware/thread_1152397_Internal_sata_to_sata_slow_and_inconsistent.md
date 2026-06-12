---
title: "Internal sata to sata slow and inconsistent"
date: 2009-05-07
forum: Hardware
---

### Post by fibbsjc on 2009-05-07
I've got three drives in my tower and all of them are sata.  I'm often transferring files or directories back and forth between them and some of the files are rather large.  The problem I always have is that the transfer rate is so slow, on average its 13M/s.  This is very frustrating because they are internal drives and not USB connected.  It further frustrating because once in a blue moon it'll tranfer at 85M/s.  I get very excited when I see this but want to know why it can't achieve transfer rates like that on a regular basis?  Is there some settings for this that I should know about?  Is ext3 (which they have all been formated to) not good at transfer?

Any thoughts or advice would be very welcome.  Sorry if this has been adressed before, I looked but couldn't find any threads.

---

### Post by logos34 on 2009-05-07
you can test them with

sudo hdparm -tT /dev/sda

what fstab mount options are you using? (relatime is the fastest)

---

### Post by fibbsjc on 2009-05-07
I'm not sure, whatever the default mount method is (in case you haven't picked up on it I'm a complete no nothing as of yet).  I don't have them permanently mounted-that is to say they show up in nautilus and mount anew every time I boot up and click on the drive for the first time.  I'm guessing that has something to do with it (I'll slap the back of my head on your behalf), but that honestly never occurred to me.  I'll check that out when I get off work and then school myself on fstab mounting (I tried it in the past and failed miserably, so have been putting that off).  I hadn't realized that there were different ways to mount a drive that could effect its performance like that.

So to recap:  I'm a dumb a** and you have been very helpful.  Thank you for your patience.

---

### Post by logos34 on 2009-05-07
gksudo gedit /etc/fstab

but if the transfer times are that low, there some other issue

---

