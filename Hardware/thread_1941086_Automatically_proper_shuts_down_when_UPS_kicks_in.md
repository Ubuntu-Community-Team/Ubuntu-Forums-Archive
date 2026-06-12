---
title: "Automatically proper shuts down when UPS kicks in"
date: 2012-03-14
forum: Hardware
---

### Post by Arqillions on 2012-03-14
Hey guys,

Im looking for a UPS brand/model that can automatically proper shuts down my CPU when UPS kicks in.

Any idea how i can do this?

Can i just buy any UPS and set something in Ubuntu?

or

This idea will make my life a living hell?

Thanks in advanced :)

---

### Post by VH-BIL on 2012-03-15
Check out:

[http://remus.rutgers.edu/~petechen/linux/UPS.html](http://remus.rutgers.edu/~petechen/linux/UPS.html)
and
[http://archive09.linux.com/feature/128099](http://archive09.linux.com/feature/128099)

---

### Post by trundlenut on 2012-03-15
I have a couple of APC upss that work great with apcupsd but I believe that some of the newer models are not compatible with the apcupsd, thanks to some changes made by APC.

apcupsd notifies you when the power fails/returns and gives you a graceful shutdown as required (you can configure it) and you get a simple web interface to check the status of the ups too.

See [here]("http://www.apcupsd.org/") for the apcupsd website

---

