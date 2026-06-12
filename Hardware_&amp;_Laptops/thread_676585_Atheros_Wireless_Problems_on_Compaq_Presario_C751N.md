---
title: "Atheros Wireless Problems on Compaq Presario C751NR"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by lcubanito on 2008-01-23
Been working on trying to get wireless working on this Presario with the Atheros 5600EG Wireless Card.  I've tried the NDISWrapper solution but still cannot get it working.  Anybody have any suggestions?

---

### Post by pearljam145 on 2008-01-24
I got this running with ndiswrapper. I downloaded the Atheros drivers **(version 6.0.3.85) ** from [Atheros.cz]("http://www.atheros.cz/download.php?atheros=AR5006EG&system=1"). Make sure you get the version 6 and not version 5. Version 5 did not work for me. Version 6 is the second link from the top. Hope this helps.

---

### Post by pearljam145 on 2008-01-24
Btw [here]("http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/") is a tutorial I used to install the driver

[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

---

### Post by lcubanito on 2008-01-24
I tried both v5 and v6 driver.  Still can't get it working.  Thanks anyway.

---

### Post by pearljam145 on 2008-01-24
I have exactly the same laptop and ndiswrapper worked quite well for me. Anyway let me know if I can help in anyway.

---

### Post by lcubanito on 2008-01-24
> **pearljam145 said:**
> I have exactly the same laptop and ndiswrapper worked quite well for me. Anyway let me know if I can help in anyway.

Ok, I don't like to give up easily.  I had tried so many different things that had gotten frustrated and was not acting with a level-head.  The last configuration I had tried had gotten me the furthest, since it at least recognized the hardware.  I got rid of the 5.x driver and reloaded the 6.x driver and guess what......It worked.  I'm happy it's finally working.

One more thing, I noticed that the signal strength seems to be a bit weak.  With Vista, I was getting 100%.  With Ubuntu, I hover around 56% in the same location.  Have you noticed this?

I remember this happening to me on a different laptop under Vista.  I replaced the driver and got better signal strength.  Guess I'll keep my eyes open for updated drivers.

In any event, Thanks for your help!!

---

### Post by pearljam145 on 2008-01-25
Great, Yeah, I too noticed that the signal strength is a little poor. Also the wireless seems to drop once in a while. Unfortunately the default Atheros driver doesn't seem to work. In case you come across updated drivers do let me know.

---

### Post by pearljam145 on 2008-04-15
I had quite a bit of trouble with ndiswrapper (wireless drops after restarting, general instability). I ended up using madwifi instead. See instructions [here]("http://www.fedoraforum.org/forum/archive/index.php/t-184661.html"). Works much better now. Now if I can get suspend to work reliably :(

---

