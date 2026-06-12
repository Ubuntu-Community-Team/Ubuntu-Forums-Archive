---
title: "laptop battery help"
date: 2008-09-19
forum: General Help
---

### Post by phoenix_snake on 2008-09-19
Hi, I recently installed linux on my dell inspiron 1525 and have only got three things left to do is configure my broadcam wireless, conexant modem and battery life.

Before I get on to the network stuff I noticed my battery life has decreased from around 4.5 on Vista to 3 on ubuntu.

Is it alright to assume its reporting the wrong time cause Vista itself never gives an accurate figure either? Is it possible for it to decrease cause of a change in OS?

thanks

---

### Post by holiday on 2008-09-19
Just a hunch - you could try draining the battery out on Ubuntu and then recharging it all the way up in Ubuntu. You'll have to adjust your power settings to let Ubuntu run on a low battery, and it's a good idea to let the battery leak out for a few hours. Just let you laptop sit on its dead battery.

I'm not!! an expert but I find a recalibration often helps.

---

### Post by stickmangumby on 2008-09-19
Different Operating Systems can require different amounts of power. Some are more efficient than others.

However, I'd do what holiday suggests - for an OS to get an accurate idea of battery life it often needs to run the battery down to nothing.

---

### Post by phoenix_snake on 2008-09-19
so that means I let it drain out and then plug it in on charging while its of and ubuntu should be fine?

---

### Post by phoenix_snake on 2008-10-03
I just tried ubuntu again after a long break but this time I am on the 8.10 beta and the battery life is way better.

---

### Post by kosmiciatakuja on 2008-10-03
Also, if you are into tweaking stuff in /sys and /proc you can jump to [http://lesswatts.org](http://lesswatts.org) and follow the guides there, they're usually pretty informative (and long...). 

And, if you are into conserving power, 'powertop' utility is a must! 
```
sudo apt-get install powertop
``` and then later you run it via ```
sudo powertop
```

I'm not sure if that tool requires an Intel processor but because it was written by Intel guys then it might as well do - you have been warned ;)

---

### Post by phoenix_snake on 2008-10-03
> **kosmiciatakuja said:**
> Also, if you are into tweaking stuff in /sys and /proc you can jump to [http://lesswatts.org](http://lesswatts.org) and follow the guides there, they're usually pretty informative (and long...). 

And, if you are into conserving power, 'powertop' utility is a must! 
```
sudo apt-get install powertop
``` and then later you run it via ```
sudo powertop
```

I'm not sure if that tool requires an Intel processor but because it was written by Intel guys then it might as well do - you have been warned ;)
thanks for the advice and yes its an intel processor, :) I will try powertop, does this have a GUI cause some links I read while surfing have a lot of command line stuff :(

---

### Post by binbash on 2008-10-03
Dude you have to configure most things if you need more battery.I do not like default config files

---

### Post by vanessa on 2008-10-12
How can I disable the auto-sleep on critical battery mode so that I can drain my battery?
I can't find it on Power Management, and my computer went to sleep when the battery was at around 10%.

---

