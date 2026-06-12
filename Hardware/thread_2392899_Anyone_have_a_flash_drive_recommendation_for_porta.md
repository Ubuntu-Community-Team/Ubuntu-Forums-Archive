---
title: "Anyone have a flash drive recommendation for portable full install?"
date: 2018-05-26
forum: Hardware
---

### Post by herqulees on 2018-05-26
I've searched on and off for a flash drive that can handle 100+MiBps read **and **write, doesn't get so hot it'll burn you, is made of metal not plastic, and at least 128GB size. Basically what a flash drive should be before profit margins come into play. Portable SSDs are ruled out due to size and needing a cable. I haven't had much luck and was wondering if anyone had any recommendations?
Kind request: please stay on topic, no how flash drives aren't meant for this, just get a portable ssd and remove the cable, etc.

---

### Post by sudodus on 2018-05-27
Maybe these links will help you. You may not get all the way to your specs but maybe you find something that works for you. Fast USB 3 pendrives tend to get hot and they may not be quite as fast as you want, at least not after you have used them some time. A drive that can use discard alias trim would be best, there are a few such USB pendrives, for example Mushkin and Kingston DT Workspace. (I have no own experience of Mushkin, but the specs look good. 'Peak 4k write' can be important.)

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

[usb.userbenchmark.com](http://usb.userbenchmark.com/)

---

### Post by herqulees on 2018-05-27
> **sudodus said:**
> Maybe these links will help you. You may not get all the way to your specs but maybe you find something that works for you. Fast USB 3 pendrives tend to get hot and they may not be quite as fast as you want, at least not after you have used them some time. A drive that can use discard alias trim would be best, there are a few such USB pendrives, for example Mushkin and Kingston DT Workspace. (I have no own experience of Mushkin, but the specs look good. 'Peak 4k write' can be important.)

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed]("https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed")

[usb.userbenchmark.com]("http://usb.userbenchmark.com/")

Those are a couple awesome links that I have no idea why I didn't find myself. The Mushkin Ventura Ultra is clearly top of its class against everything else but I can't find it anywhere online. No one is even selling a used one on eBay. I went further down the list (by 4KiB write speed) and found the Corsair Flash Voyager GTX. The 128GB model is only $83 with same day delivery on Amazon [https://www.amazon.com/gp/product/B079NVJPKV/](https://www.amazon.com/gp/product/B079NVJPKV/) so I've ordered it and will play with it later today then upload some speed tests from various computers, operating systems, and speed test programs.
It is something I'll end up carrying with me every day with a full Ubuntu install. I use it mainly as an alternate OS on my company laptop. Luckily I have a cool IT department that could care less what I do when I boot from an external drive since the internal drive is encrypted and we don't deal with confidential info anyways. So instead of carrying two laptops (mine being a heavy bulky MSI gaming laptop) I just reboot to my own OS when I'm done at work while on the road. Then I can play Intel GPU and Linux friendly Steam games.

---

### Post by C.S.Cameron on 2018-05-27
I think Ubuntu now mostly runs in RAM when installed on a flash drive.
I'm not sure how significant USB3 is when running in RAM.
My favorite drive for full installs is an 8GB Kingston Traveler USB2 drive that I have been using as a booter for about 10 years now. It is indestructible.
I also have been using for about 2 years now, a Lexar 128GB USB3 Ultra. It never seems to boot usb3 though. Originally I had a Persistent system on it but it went corrupt with massive fragmentation so I changed to Full install about a year and a half ago.

Both are plastic body drives with metal inserts.

---

### Post by herqulees on 2018-05-27
Well Ubuntu Forums really has died off since the last time I was really on here a couple years ago. Thanks though sudodus for the links. I just got the 128GB Corsair Voyager GTX USB 3.1 in the mail and everything is pretty amazing so far. I installed Corsair SSD Toolbox and enabled overprovisioning (set to 8GB leaving 111GB after formatting) then ran CrystalDiskMark 6. Attached is the benchmark. Now I'll get to work installing Ubuntu 18.04.
[ATTACH=CONFIG]279886[/ATTACH]

---

### Post by sudodus on 2018-05-28
I'm glad I could help :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

