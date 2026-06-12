---
title: "ATi Radeon 9200 SE gives garbled video!"
date: 2008-06-25
forum: Hardware
---

### Post by Tamhvm on 2008-06-25
Hello Ubuntu users!

I'm kind of new to Ubuntu (never have installed it beyond curiosity), however I've been using Debian.

As I like to show the freedom-ness of Linux to my friends and coworkers, I requested a (small) batch of Ubuntu and Kubuntu CDs. The CDs arrived fine, however I thought that it would be nice to test Ubuntu in my desktop computer. My computer is quite modest, a *MSI K7 Ultra 2*, *AMD Athlon XP 2600+*, with 120 + 40GB hard disks, *512 MB RAM* and for video card I have a *ATi Radeon 9200 SE* video card.
I popped the Ubuntu CD into my DVD drive, and then it started loading, everything went perfectly until GDM loaded... Then I got this:
[IMG]http://i83.photobucket.com/albums/j315/tamhvm/UbuntuGarbled2.jpg[/IMG]
Yeah, it is the Ubuntu splash screen totally garbled! [SIZE="2"](sorry for the poor picture quality, I used my cell phone camera)[/SIZE] As you can see also, the mouse cursor sits ungarbled in the middle of the screen. With a bit of imagination, and eyes crossing you can see that Ubuntu logo in the middle.
After Ubuntu loads, you can see this:
[IMG]http://i83.photobucket.com/albums/j315/tamhvm/UbuntuGarbled1.jpg[/IMG]
You're right, this is Ubuntu's desktop. Garbled. Mouse cursor visible. Menus unreadable. Fortunately, the text console works perfectly, so I was able to [FONT="Courier New"]shutdown -r now[/FONT] nicely.

I'm very worried, this glitch is quite weird! I'm really considering to upgrade my video card, that's until I get money to get a nVidia one.

Thanks in advance for any insight in this problem!

---

### Post by Rocket2DMn on 2008-06-26
The LiveCD does not work for everybody since it has limited support for video drivers.  I suggest getting your hands on an alternate install cd which uses a text based installer, but is still easy to use.  You can download it from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) by checking the box at the bottom of the page.  ShipIt (or whoever you got the Live CDs from) may have alternate cds available, but I'm not sure.

---

### Post by Tamhvm on 2008-06-28
Well, I used the Alternate install CD, and installed it (damaging my other OS partitions in the way), and guess what??
It still doesn't works!! I got the same result, the same video problems...
I'm wondering, well, *maybe* the real solution is to get a new video card.
Someone at my local LUG told me to change the refresh rate in the Xorg configuration. He told me that maybe X is accessing a very high refresh rate, by the way showing a "snow" effect (a lack of features of my computer's display), however, when I arrived to the xorg.conf file, I didn't found any reference to Refresh rate or resolution whatsoever.
I have to remark also, that I tested yesterday using the Safe Graphics Mode option in Ubuntu Live CD gives me good video results (at least I can read, but no GL acceleration/CompizFusion whatsoever).

Thanks for reading my little rant and problem, and any insights will be due gratefully accepted!!

---

### Post by _ujin_ on 2009-08-23
Recently, found the same problem, installing ubuntu 9.04 on system with ECS K8-M800 M/B. Radeon 9200SE showed just the same picture. Reading the "radeon" man I found option "DisplayPriority". So the solution may be is to add string 
[FONT=monospace]
[/FONT]Option "DisplayPriority" "HIGH"

into xorg.conf in "Device" section

Hope, it helps

---

