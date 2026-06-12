---
title: "Compaq CQ56 Synaptic touchpad sticks horizontally"
date: 2011-04-30
forum: Hardware
---

### Post by BROBOCOP_FTW on 2011-04-30
I recently bought a Compaq CQ56: 

[http://www.bestbuy.com/site/Compaq+-+Presario+Laptop+/+AMD+V-Series+Processor+/+15.6%22+Display+/+2GB+Memory+/+250GB+Hard+Drive+-+Basic+Black/1271897.p?id=1218245812097&skuId=1271897&st=cq56&cp=1&lp=1](http://www.bestbuy.com/site/Compaq+-+Presario+Laptop+/+AMD+V-Series+Processor+/+15.6%22+Display+/+2GB+Memory+/+250GB+Hard+Drive+-+Basic+Black/1271897.p?id=1218245812097&skuId=1271897&st=cq56&cp=1&lp=1)

and installed Ubuntu 10.10. It works fine for the first few minutes, but eventually the Synaptic touchpad sticks horizontally (in other words, I try to move the cursor around, but it only goes up and down on the screen). 

I have tried installing:

```
gsynaptics
xserver-xorg-input-synaptics
```

but nothing has changed.Thanks in advance.

---

### Post by ZombieApocalypse on 2011-09-18
I'm experiencing the same thing on my new Compaq CQ56 using Kubuntu 11.04. Did you find a solution? At the moment I'm using an external mouse.

---

### Post by Tandem78 on 2012-01-31
> **ZombieApocalypse said:**
> I'm experiencing the same thing on my new Compaq CQ56 using Kubuntu 11.04. Did you find a solution? At the moment I'm using an external mouse.

Guys, I had the same problem and I think I have the solution, or at least a fix. See [http://en.wikipedia.org/wiki/Touchpad](http://en.wikipedia.org/wiki/Touchpad) - the problem is that the virtual ground effect is inadequate - it probably depends on factors like weather, relative humidity and so on.  Just moisten your fingertip or touch the frame of the VGA socket on the side with your left hand.   
 In Win7 the Synoptics driver have options to adjust the sensitivity, I have no idea if they have any effect under ubuntu.

---

### Post by ZombieApocalypse on 2012-02-01
> **Tandem78 said:**
> Guys, I had the same problem and I think I have the solution, or at least a fix. See [http://en.wikipedia.org/wiki/Touchpad](http://en.wikipedia.org/wiki/Touchpad) - the problem is that the virtual ground effect is inadequate - it probably depends on factors like weather, relative humidity and so on.  Just moisten your fingertip or touch the frame of the VGA socket on the side with your left hand.   
 In Win7 the Synoptics driver have options to adjust the sensitivity, I have no idea if they have any effect under ubuntu.

Thanks for the info. I shall give those suggestions a try.

---

