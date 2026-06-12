---
title: "4k@6p resolution on 19.04"
date: 2019-07-05
forum: Hardware
---

### Post by numbawon on 2019-07-05
I'm having a problem getting my device outputting 4k properly . 

I'm running 19.04, I am running on a NUC6iKYK ([https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc6i7kyk.html](https://www.intel.com/content/www/us/en/products/boards-kits/nuc/kits/nuc6i7kyk.html)). I have the [http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) repo, and have taken updated from there. I have in the past on other OSs  (arch linux, and Windows) gotten 3840x2160@60 work perfectly. The screen I have is an LG 55UF6450-UA ([https://www.lg.com/us/tvs/lg-55UF6450-4k-uhd-led-tv](https://www.lg.com/us/tvs/lg-55UF6450-4k-uhd-led-tv)). In the past I've been able to get (on 18.xx builds) I've been able to get 3840x2160@30hz but not yet gotten @60 yet, but on the latest install when I switch to those 2160@30 all I get is a blue screen. 

get-edid | parse-edid gets me : ([https://pastebin.com/ivsS8yfw](https://pastebin.com/ivsS8yfw)). 

I've also dpkg-reconfigure phigh xserver-xorg after getting later drivers, to no affect. And for completeness lspci | grep VGA outputs 00:02.0 VGA compatible controller: Intel Corporation Iris Pro Graphics 580 (rev 09)

I've also swapped and tested the hdmi to known good and tested 4k capable devices.

---

