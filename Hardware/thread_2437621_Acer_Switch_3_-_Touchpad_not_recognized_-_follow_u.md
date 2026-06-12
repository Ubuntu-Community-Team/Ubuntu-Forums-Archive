---
title: "Acer Switch 3 - Touchpad not recognized - follow up"
date: 2020-02-26
forum: Hardware
---

### Post by waldert on 2020-02-26
Please see thread '**Acer Switch 3 - Touchpad not recongnised**' at [https://ubuntuforums.org/showthread.php?t=2403167](https://ubuntuforums.org/showthread.php?t=2403167)

The thread was unfortunately closed - but there's one important open question ... how to get the touchpad multitouch working i.e. two-finger-scrolling

After playing around for month I was given the opportunity by accident.

After installing mint-19.3-xfce (build on ubuntu 18.04) on my Acer Switch-SW312-31 I only had to follow the procedure of **turblety** (#2 in thread):

  ```
## blacklisting module hid_rmi:
  $ sudo gvim /etc/modprobe.d/hid.conf
  ## and add as only line:
  blacklist hid_rmi

## then load module hid_multitouch
  $ sudo gvim /etc/modules-load.d/hid.conf
  ## add
  hid_multitouch
```

after updating to kernel 5.3.0-40-generic #32~18.04.1-Ubuntu SMP and making it permanent via:

```
$ sudo gvim /etc/init.d/touchpad_script 

  #!/bin/sh
  echo 3 06cb 81a7 3 | sudo tee /sys/module/hid_generic/drivers/hid\:hid-generic/new_id

$ sudo chmod +x /etc/init.d/touchpad_script
``` 

Now restart and your touchpad should work, two-finger-scrolling included  
(if you activate 'mouseclicks with touchpad' in your touchpad-preferences)

Thanks to Turblety

---

