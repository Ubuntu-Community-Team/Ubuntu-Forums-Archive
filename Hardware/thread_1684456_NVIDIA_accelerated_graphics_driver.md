---
title: "NVIDIA accelerated graphics driver"
date: 2011-02-09
forum: Hardware
---

### Post by beerandskittles on 2011-02-09
Hi all,

I have just successfully installed Ubuntu 10.10, with everything working great.

Previously I had tried Mint Linux, installing the 'NVIDIA accelerated graphics driver' under Additional Drivers. This lead to the pc booting to the command prompt (not loading the GUI). Trying 'startx' indicated that xserver couldn't load.

I'd like to attempt this driver install under Ubuntu, however I'm concerned it'll fail again & that I won't be able to get into the GUI.

Can someone please tell me what I need to do if this drivers fails like before so that I can restore the original graphics driver / setup and access the GUI?

Thanks!

Ash

---

### Post by beerandskittles on 2011-02-09
As feared my Ubuntu install won't boot after applying the NVIDIA driver.

No login prompt is shown.

One message on the screen is:

Not starting jetty - edit /etc/default/jetty and change NO_START to be 0 (or comment it out).

Can someone please tell me how to boot into safe mode and revert the graphics driver back? :confused:

---

### Post by gufide on 2011-02-09
did you install it through jockey-gtk? If not, it can make errors... try to remove it using 
  ```
sudo sh "name of the file" --uninstall
``` then reboot

to boot in safe mode just go in "Ubuntu with linux ... (recovery)"

---

