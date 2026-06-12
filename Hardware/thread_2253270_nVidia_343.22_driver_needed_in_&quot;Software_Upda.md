---
title: "nVidia 343.22 driver needed in &quot;Software Updater&quot;"
date: 2014-11-18
forum: Hardware
---

### Post by jon_williams on 2014-11-18
It took a while for nVidia 331.38 to be added to the 'Additional Drivers ' section of 'Software Updater' for GTX 7xx cards, and since the new GTX 9xx series needs, for example, 343.22 (or above), when can this be expected to be added there (as I require the proprietary driver)?
I know there are other methods to getting the nVidia drivers in*, but these are often painful (I know, I've tried!) - so a no-mess approach is desperately needed to make use of the Maxwell cards.

(* the easiest other way is via xorg-edgers, but this package does not include the OpenCl part of the driver, which I need)

---

### Post by Pilot6 on 2014-11-18
There is opencl package in xorg-edgers. It conflicts with existing one.
Do this

```

sudo killall nvidia-persistenced
sudo apt-get purge nvidia*
sudo add-apt-repository  ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-343
sudo add-apt-repository -r ppa:xorg-edgers/ppa

```

And you will have nvidia 343.22 with opencl too.

---

### Post by jon_williams on 2014-11-19
This [thread](https://foldingforum.org/viewtopic.php?f=80&t=26981) on the official Folding@Home forum suggests that there is still something not right with the xorg-edgers package which necessitates the proprietary nVidia 343.22 driver in order to run Folding@Home.

---

