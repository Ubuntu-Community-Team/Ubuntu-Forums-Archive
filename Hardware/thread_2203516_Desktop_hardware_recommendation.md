---
title: "Desktop hardware recommendation"
date: 2014-02-03
forum: Hardware
---

### Post by jbsmith05 on 2014-02-03
I want to start self-teaching myself shell scripting so I was going to start by installing Ubuntu on a new machine. I've used Ubuntu before on spare laptops but those have been sold so I have nothing laying around that I could use.

I'm hoping to get some recommendations of a small (a cube size or smaller), Cheap (hopefully $100 or less), low-power (as in doesn't use a lot of power) linux box that I could use for this purpose. Below is what I would be doing initially.

a) It would be an always on machine - so not sure if Ubuntu Server is required or not? 
b) I'll be learning shell scripting that would be scheduled via cron 
c) First script would be rsync/lftp/etc to automate incremental backups from a remote host 
d) Would be run headless - all other machines in the house are Mac's so I'll need to be able to remote in 
e) Needs to be able to connect to my Synology NAS

Thank you!

---

### Post by varunendra on 2014-02-06
> **jbsmith05 said:**
> I'm hoping to get some recommendations of a small (a cube size or smaller), Cheap (hopefully $100 or less), low-power (as in doesn't use a lot of power) linux box

Is the ARM platform a considerable option for your purpose? If yes, take a look at [**Raspberry Pi**]("https://en.wikipedia.org/wiki/Raspberry_Pi") ([Amazon Link]("http://www.amazon.com/s?ie=UTF8&page=1&rh=i%3Aaps%2Ck%3ARaspberry%20Pi")), or [**BeagleBone Black**]("http://beagleboard.org/Products/BeagleBone%20Black") or even relatively more powerful [**Odroids**]("http://com.odroid.com/sigong/blog/blog_list.php?bid=138").

I haven't used any of them personally, but from what I have read about them, I think they can do everything you listed. Very cheap for what they can do, ridiculously low powered and dead silent/cool/stable. Just don't expect any heavy computing or a lot of data storage from them, unless you are willing to compromise with USB storage.

---

### Post by matt53 on 2014-02-06
I agree with varunendra here, but i would like to add that you don't need ubuntu server for this. There are a few other options, but most are going to be over $100

---

### Post by jbsmith05 on 2014-02-07
I looked at the raspberry pi but the thing I don't like (don't want to do) is build an enclosure for it.  Is there some premade things for that?

Also for that price I was looking at the cubox-i [http://cubox-i.com/](http://cubox-i.com/)  for slightly more than a raspberry pi it sounds like it would meet my needs...???

---

### Post by varunendra on 2014-02-08
> **jbsmith05 said:**
> I looked at the raspberry pi but the thing I don't like (don't want to do) is build an enclosure for it.  Is there some premade things for that?
Of course there is, offered as a bundled package as well as separately available, in plenty of designs : 

[http://www.ebay.com/sch/items/?_nkw=raspberry+pi+enclosure&_sacat=&_ex_kw=&_mPrRngCbx=1&_udlo=&_udhi=&_sop=12&_fpos=&_fspt=1&_sadis=&LH_CAds=](http://www.ebay.com/sch/items/?_nkw=raspberry+pi+enclosure&_sacat=&_ex_kw=&_mPrRngCbx=1&_udlo=&_udhi=&_sop=12&_fpos=&_fspt=1&_sadis=&LH_CAds=)

> Also for that price I was looking at the cubox-i [http://cubox-i.com/](http://cubox-i.com/) for slightly more than a raspberry pi it sounds like it would meet my needs...???
Don't have any idea about this one. But apart from the "Infra Red for Remote Control" feature, doesn't look superior in any way. On the contrary, looks less flexible to me in comparison to both Raspberry Pi and BeagleBone.

---

