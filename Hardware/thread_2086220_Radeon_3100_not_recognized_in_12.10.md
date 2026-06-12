---
title: "Radeon 3100 not recognized in 12.10"
date: 2012-11-20
forum: Hardware
---

### Post by stonefuzz on 2012-11-20
Hi there,

I'm new to Ubuntu and I've just installed Ubuntu 12.10 in my Satellite L300D-20Z.
It has a ATI Radeon 3100 graphics card, but in the system properties it appears has an unknown device.
Is the drivers missing? How can I install them?

Thanks, cheers!

---

### Post by QIII on 2012-11-20
Unfortunately, ATI has moved that card (all HD 2XXX - 4XXX models and prior) to a legacy driver support branch and the driver does not support X Server 1.13, which is used by Ubuntu 12.10.  Actually, the non "HD" models went to legacy in 2008 or so.

You can do one of the following short of buying an HD 5XXX card or newer if your card is an HD 3100 series:

1.  Use Ubuntu 12.04.1 LTS and the ATI 12.6 driver.

2.  Use the default open source Radeon driver installed by default with Ubuntu.

3.  Use someone's PPA with scripts to downgrade X Server to 1.12 and install an older driver.

The utility of #3 is only transient and eventually you will be so far behind X Server and the latest driver that something will break when you upgrade to a future release of Ubuntu.

If your card is the older Radeon series (that is, not HD, but I think yours is in the HD family even if not labeled as such), your only option is the open source Radeon driver Ubuntu uses by default when installed, no matter what version of Ubuntu you install.

There is nothing Canonical or any other distributor can do.  Unless ATI reconsiders its driver support model, this is simply how it is.

---

### Post by Yellow Pasque on 2012-11-21
> Is the drivers missing? 
No. The open-source driver is used by default. The sysinfo program has a bug where it doesn't recognize the video card. It's nothing to worry about.

---

### Post by stonefuzz on 2012-11-21
Thanks for your replies.

Yes, I guess my card is one of the HD series (although the laptop specifications doesn't say so).

The question that I have now is if I should choose option #1 or #2.
I mainly use my laptop for basic things like surf the web, listen music and watch some movies/TV series. Also, I have the need to work with RAW image photographs and do some editing (using Gimp, maybe).

Is this doable with the default Radeon drivers (option #2)?
Or should I have the proper graphic card drivers and go for option #1?

Thanks and regards

---

### Post by QIII on 2012-11-21
Since you already have Ubuntu 12.10 installed, I'd work with the open source driver for a while and see if it suits your needs.  That might be easier than the hassle of installing 12.04.

If you run into heat problems, there are remedies.

---

### Post by stonefuzz on 2012-11-21
Ok, I'll use 12.10 with the open source drivers and see if that works for me, thanks for the advice.

In fact there was a time, while using ubuntu, that the system shutdown entirely with no previous notice. It never happened before while using win7. Can this be related? (you mentioned heating problems...)

Thanks and regards

---

### Post by QIII on 2012-11-21
It may be that heat was a problem.  It occasionally happens with the Radeon driver.

You can install lm-sensors and gkrellm for a quick way to monitor.

I'm on my cell right now and can't add links, but each should be covered in the community wikis.

---

### Post by stonefuzz on 2012-11-22
Last night the laptop shutdown twice, while using it on my lap. It heats a lot more in that condition but it never happened before while using Win7.
I did not had the chance to install the applications you recommended but I will do so as soon as possible.

I wonder if i can get this thing controlled and steady or if I just have to stop using Ubuntu in my laptop (It would be a shame since I'm starting to like it a lot). :confused:

Thanks again, cheers

---

### Post by QIII on 2012-11-23
You can try jupiter,  which has some power management tools to keep things cool and extend battery life.

---

### Post by stonefuzz on 2012-11-23
Thanks for all the advices given. I've been busy, so I hadn't the chance of trying them out.

I don't know if I got something right here: If I change to 12.04.1 LTS will I still have those heating problems?

Thanks!

---

### Post by Yellow Pasque on 2012-11-23
> **stonefuzz said:**
> If I change to 12.04.1 LTS will I still have those heating problems?

If you use the same open-source radeon driver, then yes. However, switching to 12.04 will allow you to use the proprietary fglrx/Catalyst Linux driver, which should make power consumption/heat better.

---

