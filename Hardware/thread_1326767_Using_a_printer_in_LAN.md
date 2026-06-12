---
title: "Using a printer in LAN"
date: 2009-11-14
forum: Hardware
---

### Post by Alcareru on 2009-11-14
Hi there.

I'm not very familiar with printing/printer issuses in linux as I just bought my very first own printer a couple of days ago. I managed to get the printer sort of working. As of currently I'm having problems trying to install it on my desktop machine. I think I could get it working if I'd install the newest HPLIP (3.9.10) and plug the printer in by USB and after it's been recognized it should work without wire as well.

But the thing is this, to me it seems I already have all the information that should ever be needed. The model is f4580 and it's located at 192.168.1.60 and the required ports 191 192 9100 are open. So I'm just thinking that there must be a place where I can put this information and that's it. What else there is to "install"? The only hp-utility that seems to work as expected is hp-mkuri. Then again I don't know what to do with the uri :)

So as an bonus, could someone tell me whats the deal with that uri? Also some more bonus points will be rewared for an explanation of what's the difference between hp-mkuri and hp-makeuri? They sound like they should do the same thing, but the latter gives error for me and the first one gives some sort of a uri to my printer.

P.S. I might need to update to newest HPLIP anyways because afaik support for f4500-series just came out and the older 3.9.3 available on repos for ubuntu 9.04 might just not cut it. But let's ignore that fact for now.

---

### Post by IcarusR on 2009-11-14
Personally I've always used CUPS for network printing. [URL="www.cups.org"]www.cups.org[/URL
Should be in the repositories.
That said, as you say your printer is supported by 3.9.10 not 3.9.3 so I'd try getting the latest version.

---

### Post by Alcareru on 2009-11-15
> **IcarusR said:**
> Personally I've always used CUPS for network printing. [URL="www.cups.org"]www.cups.org[/URL
Should be in the repositories.
That said, as you say your printer is supported by 3.9.10 not 3.9.3 so I'd try getting the latest version.

Yes I believe I have cups installed. It is required by HPLIP afaik. Any quick tips on how to get it working with that? 

EDIT: In short it seems to be that I have to point my browser to localhost port 631 and set up some stuff there. But what about scanning (I'll try this later today)? It's an all-in-one multipurpose device so it's a scanner as well.

---

### Post by Alcareru on 2009-11-16
Cups its self was installed but pointing firefox to localhost:631 gave no results. After that I tried to update to the newest HPLIP version with the binary distributed by hp. Everything seemed to work nice and well. It even automatically downloaded some missing packages, but after that it failed claiming cups is missing. Then I realized what was the problem. It's not that cups isn't installed, but that I've of course disabled the service for I have had no printer. So after restarting the service, cups site works just great. Regardless of that I decided to finish installing the up-to-date HPLIP and try if the standard hp installation process would work. And it did. Now that all dependencies were met and cups was running all I had to do was to give it the ip-address and jet-port (dunno what it is but left it for default and it worked). Now the printer works and is found by cups and hp-tools. Also scanning works.

So I'm all good for now. Hope these babblings of mine will be found useful by someone struggling with same sort of problems. If not... well it was nice talking to me :) (and to you too IcarusR)

P.S. I've bumped into one small annoyance. I'm not sure how much of problem it will be in real printing tasks but at least the cups test page prints too right. The number scale on the right side is not fully visible but is printed off the paper. And I have calibrated the printer already several times so that can't be it.

P.P.S.
I think I figured that one out too. The printer is just fine. It's the test page that's "flawed". The test page is designed for(/by) North American people and uses the "letter" size. Here in Finland and (in most other places?) we use the standard ISO paper sizes. The equivalent of "letter" is A4 but the sizes vary a bit. (US letter) 216 × 279 compared to (ISO 216 A4) 210 × 297.

---

### Post by Alcareru on 2009-11-17
Just as a finla nail to the coffin. The test page isn't "flawed". It prints just fine as long as you've configured HPLIP/cups to use correct paper size.

---

### Post by finnbakk on 2009-11-17
Having problems: Not possible to connect to printer on windows box in the same LAN as my obuntu 9.10 box.
System hangs for some minutes and refuses to go further when begin to search for printer in the windows network group. This was no problem in Ubuntu 9.04 etc.
And no problem connecting to the same printer from a Fedora 11 box in the same LAN.

---

### Post by Alcareru on 2009-11-18
> **finnbakk said:**
> Having problems: Not possible to connect to printer on windows box in the same LAN as my obuntu 9.10 box.
System hangs for some minutes and refuses to go further when begin to search for printer in the windows network group. This was no problem in Ubuntu 9.04 etc.
And no problem connecting to the same printer from a Fedora 11 box in the same LAN.
How can another computer on LAN block another one from connecting to a third one? Unless of course the route goes through that computer and ports are being blocked..

---

### Post by freechelmi on 2009-12-02
> **Alcareru said:**
> 

But the thing is this, to me it seems I already have all the information that should ever be needed. The model is f4580 and it's located at 192.168.1.60 and the required ports 191 192 9100 are open. So I'm just thinking that there must be a place where I can put this information and that's it. What else there is to "install"? The only hp-utility that seems to work as expected is hp-mkuri. Then again I don't know what to do with the uri :)

hello , just a question aside : 

Did the HP setup GUI allowed you to setup the IP adress/WPA ssid & pass ? 

thks

---

### Post by Alcareru on 2009-12-09
> **freechelmi said:**
> hello , just a question aside : 

Did the HP setup GUI allowed you to setup the IP adress/WPA ssid & pass ? 

thks

Funny, as you you mentioned that, I realized I don't remember defining the encryption method that the printer uses for it's wlan connection at any point. But I must have done it at some point for how else could it have access to my LAN? Some time has passed now, but the only possible scenario is that, I have specified those things when I first tried that the printer works from my laptops windows partition.

So to answer your question. I don't know if it's possible to set those things up with the linux setup tool.

Also as I now am here once again writing to this SOLVED :) thread, I might add that I do have one complication. The printer does not wake on lan or something like that. So every time I want to print something I need to walk up to the printer and restart it. If I won't, I'll get some sort of communication error and nothing gets printed.

---

### Post by Alcareru on 2010-05-11
So just to update this information a bit. As of currently the new ubuntu 10.04 aka Lucid Lynx has hplip version 3.10.2 by default. There for installing and using this printer is possible out of the box. In case you run into errors like:
error: Unable to find hp-toolbox on PATH.
That is only due to the fact that your actually trying to open the HP device manager GUI application. AFAIK it's in no way needed and you can just as well rely only on cups but in case you want it just type in terminal:
sudo apt-get install hplip-gui

---

