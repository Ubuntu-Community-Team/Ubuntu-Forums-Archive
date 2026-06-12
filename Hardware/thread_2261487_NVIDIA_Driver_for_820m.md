---
title: "NVIDIA Driver for 820m"
date: 2015-01-19
forum: Hardware
---

### Post by soumoks on 2015-01-19
Hi, I recently upgraded my lenovo z50-70 623 model laptop running ubuntu 14.04 64-bit with kernel [COLOR=#000000]3.13.0-44-generic to [/COLOR]3.16.0-29-generic because of some issues with openCV using the command
```

sudo apt-get install linux-generic-lts-utopic

```




openCV runs without an issue after the kernel update however I now have a new issue.

The display doesn't turn on after resuming from suspend, no backlight nothing. The system seems to have resumed from suspend however the display remains black.
I am assuming this is due to the display driver. I am currently using the default Nouveau display driver as I experienced freezing issues with the additional driver provided by ubuntu ,a "nvidia  binary driver v331.113 " .
Can anyone guide me on installing the correct drivers for my card or any other solution to this issue?

Thanks

---

### Post by soumoks on 2015-01-20
People,any help ?
is it ok if I try installing the latest driver from this site? 
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Or is there an easier method with a ppa?

Thanks

---

