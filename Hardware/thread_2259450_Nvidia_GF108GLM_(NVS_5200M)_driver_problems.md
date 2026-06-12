---
title: "Nvidia GF108GLM (NVS 5200M) driver problems"
date: 2015-01-04
forum: Hardware
---

### Post by jnorris2 on 2015-01-04
I have a Dell Latitude E6430 with Ubuntu 14.04 and it was freezing up after waking up from being suspended... so, I installed Nvidia's 340.65 driver, which resolved that issue, but now I have weird display issues where parts of the screen are intermittently bouncing around and not refreshing properly. What's the next option?

---

### Post by jnorris2 on 2015-01-04
Is there an older or alternate driver I can try?

---

### Post by papibe on 2015-01-04
Hi jnorris2.

What driver did you have installed before that?

I believe 340 is the one on the Nvidia web site isn't it?

I'd recommend trying the proprietary diver offered in 'Additional Drivers'. If that does not work for you, I'd recommend upgrading using the the swat ppa, or the xorg-edgers' ppa if tha latter doesn't work (see [here]("http://ubuntuforums.org/showthread.php?t=2223757&p=13028215#post13028215")).

I would let the driver from the Nvidia website as a last resort.

See [here]("http://ubuntuforums.org/showthread.php?t=2169638&p=12765972#post12765972") to get a clean start from a driver that's not working well.

Regards.

---

### Post by jnorris2 on 2015-01-04
Thanks for the reply... I'm a linux novice, but I was using the default (Nouvou) driver.

I just ran the following (from your link):

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates sudo apt-get update sudo apt-get upgrade
```

Which gave me this:

```
Removing nvidia-340 (340.65-0ubuntu1~xedgers14.04.1) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1757
dpkg: error processing package nvidia-340 (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-340
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm not sure what that means, or what to do next...

EDIT:
I changed back to the Nouveau driver, and ran the above again and the errors were gone... rookie mistake I guess. Is there anything else I should do after that upgrade? Or are we assuming that the Nouveau driver will work now? (sorry if these are dumb questions, it's all a bit confusing to me... I just want to know what to try next if the Nouveau driver keeps freezing at login).

---

### Post by jnorris2 on 2015-01-05
Nouveau froze at login again this morning waking up from 'suspend'... If Nouveau is a fail, and Nvidia's 340.65 (alleged driver for my graphics set) fails... what's the next option?

---

### Post by tokyobadger on 2015-01-05
> **jnorris2 said:**
> 

```
Removing nvidia-340 (340.65-0ubuntu1~xedgers14.04.1) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1757
dpkg: error processing package nvidia-340 (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-340
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm not sure what that means, or what to do next...

EDIT:
I changed back to the Nouveau driver, and ran the above again and the errors were gone... rookie mistake I guess. Is there anything else I should do after that upgrade? Or are we assuming that the Nouveau driver will work now? (sorry if these are dumb questions, it's all a bit confusing to me... I just want to know what to try next if the Nouveau driver keeps freezing at login).

[see my post at #7 ]("http://ubuntuforums.org/showthread.php?t=2258309&highlight=") - you need to kill the nvidia-persistenced process to complete the removal and/or upgrade of the nvidia proprietary drivers

You also need to install (after nvidia-3xx driver installation) ccsm (compizconfig-settings-manager)
```
sudo apt-get install compizconfig-settings-manager
```

Then run ccsm and follow the instructions in [this thread]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367") (again post #7)

[FWIW your card is supported by the latest 346.xx drivers so 340.xx should be fine](http://www.noobslab.com/2014/12/use-nvidia-graphics-drivers-in.html)

---

### Post by jnorris2 on 2015-01-05
Thanks Tokyobadger... I reinstalled the Nvidia driver, and installed CCSM... The flickering is still occurring, so I'm not sure what I did wrong. Here is, step by step, what I did...

1) I didn't have Nvidia persistenced (see my edit above) as I had switched back to Nouveau, so when I did this:

```
ps ax | grep persistenced
```

it only found the auto color one.
2) I then did this:
```
sudo apt-get purge nvidia-340 && sudo apt-get install nvidia-340
```

3) Next I did this:

```
sudo apt-get install compizconfig-settings-manager
```

4) I then restarted. At that point lspci -vnn | grep -i VGA -A 12 showed that I was again using the Nvidia driver, but now I'm back to flickering. What'd I do wrong? Is there something I'm supposed to change in Compiz?

---

### Post by tokyobadger on 2015-01-05
The instructions for using ccsm are in the second link (launchpad) and the instructions are coincidentally also in post #7; basically you run ccsm and go to the button Workarounds and from that list you check the option "force buffer paint redraw" (or similar - working from memory but it's clear in the link)

---

### Post by jnorris2 on 2015-01-05
Awesome thanks... I had a bit of reading comprehension fail on your first post, hence why I missed the second link. Thanks for all the assistance!

---

### Post by tokyobadger on 2015-01-06
No problem - glad you solved it

---

