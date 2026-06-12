---
title: "Lenovo X200 tablet - power consumption"
date: 2010-03-01
forum: Hardware
---

### Post by nikosm on 2010-03-01
Hello,

I am about to buy the Lenovo X200 tablet and was wondering if Lenovo's excellent power management will be available with Ubuntu's kernel (say 2.6.31-19 or newer). Is the power management of a Laptop brand-specific or OS-specific? If the latter, is there any comparison of how well the drivers in the kernel perform to Window's (Lenovo's (?)) drivers?

Thanks for any hints.

Nikos

---

### Post by six30two on 2010-03-01
I believe they're OS specific. The OS is written in a conventional language that we can understand that interprets commands into an assembly language - the language that the hardware speaks. Since all OSes are written a little differently, what they say in assembly is a little different.

As far as a comparison... beats me :)

---

### Post by nikosm on 2010-03-01
six30two, thanks for the fast answer!

Actually there is this very old comparison between some OS's, showing them to be all similar on an R52, but I guess it doesn't say so much about the status today.

[http://www.phoronix.com/scan.php?page=article&item=880&num=2]("http://www.phoronix.com/scan.php?page=article&item=880&num=2")

Nikos

---

### Post by desmane on 2010-03-01
both, I own a x200 and the power consumption on regular use is similar, but once you are trying to waste less watts, you're definitely better off in windows because of the drivers (it does undervolting, or instead of spinning up the fan it reduces power if you want to), settings are much better to control. sad but true :) but not using windows nevertheless..

check out powertop to reduce power consumption, there is also a "laptop mode" in linux (google for it), turn off your wireless radio when you dont need it and disable DRI (3d effects) check out [http://www.lesswatts.org/](http://www.lesswatts.org/)

---

### Post by nikosm on 2010-03-01
Thanks a lot desmane, I will look into that!

---

### Post by desmane on 2010-03-01
sorry, to answer your question: 

without wlan, display brightness=lowest and no application running (idle) with a 9cell: 

windows=11h
linux=9h

I have 3d effects on. Surfing, working (normal use) and full brightness, I get 0,5h to 1h less compared to windows

---

### Post by nikosm on 2010-03-01
> **desmane said:**
> sorry, to answer your question: 

without wlan, display brightness=lowest and no application running (idle) with a 9cell: 

windows=11h
linux=9h

I have 3d effects on. Surfing, working (normal use) and full brightness, I get 0,5h to 1h less compared to windows

That gives me an idea of what to expect.

You have been very helpful, thanks a lot!

Nikos

---

