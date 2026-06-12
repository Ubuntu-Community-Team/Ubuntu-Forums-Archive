---
title: "Using mobile as a HSDPA modem?"
date: 2009-01-03
forum: Hardware
---

### Post by Benchamoneh on 2009-01-03
Does anyone know how I would go about getting my laptop on the internet using my existing mobile phone? I own a Sony w910i with unlimited internet as part of my contract (it's on o2). I've paired the device with my laptop but I'm not sure how to go about using it as a 3G/HSDPA modem instead of a dial up modem. Can anyone help?

---

### Post by Benchamoneh on 2009-01-05
Ok I've done a bit more researching on this topic and found a [guide]("http://www.astahost.com/info.php/Mobile-Broadband-Ubuntu-Bluetooth_t19728.html") that describes this process. The only problem is that this method requires the use of the 'bluez-pin' package, which as far as I can tell is no longer included in the repos for Hardy (not sure why). Does anyone know where I can get hold of this package? Thanks

---

### Post by nitintutlani on 2011-07-15
> **Benchamoneh said:**
> Ok I've done a bit more researching on this topic and found a [guide]("http://www.astahost.com/info.php/Mobile-Broadband-Ubuntu-Bluetooth_t19728.html") that describes this process. The only problem is that this method requires the use of the 'bluez-pin' package, which as far as I can tell is no longer included in the repos for Hardy (not sure why). Does anyone know where I can get hold of this package? Thanks

Search for bluez-simple-agent for alternate implementation to pairing bluetooth devices. Ref: [http://manpages.ubuntu.com/manpages/natty/man1/bluez-simple-agent.1.html](http://manpages.ubuntu.com/manpages/natty/man1/bluez-simple-agent.1.html)

---

