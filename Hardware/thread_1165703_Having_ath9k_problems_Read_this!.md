---
title: "Having ath9k problems? Read this!"
date: 2009-05-20
forum: Hardware
---

### Post by kdorf on 2009-05-20
This has been killing me forever, and I've finally got (what looks to be thus far) a solution. To start, I'll describe my problem exactly:

I've got an AR928X wireless card as identified by `lspci`. When there was a lot of data to trasmit, the card would drop the connection **frequently**. Even when there wasn't much data it would almost be guaranteed to drop at least every 10 minutes.

This problem was made better by using WICD, but it still happened from time to time. Plus I don't like WICD as much as NetworkManager. =)

In any case, here's the solution. I'll make this a list of terminal commands as that's where you have to go to make install anyways. If you fear the terminal then just follow along and you should be fine.

```
sudo su -

apt-get install build-essential

wget [http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)

tar -xjf compat-wireless-2.6.tar.bz2
(The folder that is extracted may have a different name, if in doubt, type compat-wireless- and hit tab for autocomplete)

cd compat-wireless-2009-05-20

make && make install
```

At this point if you reboot things should be working. If you're a little brave, though, you can try (as per instructions)

```
make unload (to unload your wireless driver)
modprobe ath9k (to reload the ath9k wireless driver)
```

Then give it a second and it should be working.

Please keep in mind that I haven't yet had a chance to extensively test this but I've noticed two things so far: large transfers that have always, without fail, caused a problem before are no longer an issue after several tests AND transfer speeds are five times faster than before (more on par with my actual connection speed).

I hope this is of help.

---

