---
title: "Help choosing a laser printer?"
date: 2016-03-16
forum: Hardware
---

### Post by ncage on 2016-03-16
I'm in the need for a new laser printer and need some advice. The printer must, of course, be "highly" compatible with linux in that its not a pain to setup :). I was looking at the Brother HL-L2340DW [http://www.amazon.com/Brother-HL-L2340DW-Monochrome-Wireless-Printing/dp/B00LZS5EEI/ref=sr_1_1_m?s=office-electronics&ie=UTF8&qid=1458148116&sr=1-1&keywords=laser+printer ]("http://www.amazon.com/Brother-HL-L2340DW-Monochrome-Wireless-Printing/dp/B00LZS5EEI/ref=sr_1_1_m?s=office-electronics&ie=UTF8&qid=1458148116&sr=1-1&keywords=laser+printer") but i heard that there was some issues getting it working with linux. I noticed the brother has linux drivers. Are the issues most likely related to the fact that you can't connect the printer to Ethernet and most likely the printer would be connected wirelessly? If thats the case i could opt for the Brother HL-L2360DW instead. That adds another $40 to the price and otherwise the printers seem to be identical. 

Whatever printer i choose needs to have automatic duplexing. I also, as stated above, want a laser printer (no inkjets). I don't really need color. Any advice would be appreciated.

---

### Post by him610 on 2016-03-16
> i heard that there was some issues getting it working with linux. I noticed the brother has linux drivers. Are the issues most likely related to the fact that you can't connect the printer to Ethernet and most likely the printer would be connected wirelessly?

You need to go back to whom you heard about the issues getting it work in Linux to determine exactly what the issues are.
Indeed, Brother does have Linux drivers on its website, Be sure to choose the correct drivers (deb). Pay attention to the instructions.
If you are concerned about connecting wirelessly, then buy one with a wired connection; although, a wireless connection should pose no problems. 

When your PC communicates with the printer over your local network it only sees the IP address of the printer, it doesn't care whether it is wired or wireless. 
You might consider assigning a static IP address to the printer when you configure it.
It looks like a decent printer. Good luck.

---

### Post by jaarvidsen on 2016-03-17
i have a samsung ML-2160 laser printer, its worked flawlessly with ubuntu/mint for about 3 years now, dont even have to do ANYTHING to make it work, just plug it in, turn it on and a little notofication appears saying 'configuring printer' or something like that and a few secs later its ready to use. dont know if all samsungs are like that but this one is

---

### Post by Edison_James on 2016-03-17
I use a Brother DCP7030 myself, no color just priner, scanner, no complaints.
You do have to download the drivers from the Brother site. This article explains how.
[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)

If you go that route, it is important to follow the instructions in the link given, not the instructions on the Brother Site, as they don't work.:)

---

### Post by kurt18947 on 2016-03-18
> **jaarvidsen said:**
> i have a samsung ML-2160 laser printer, its worked flawlessly with ubuntu/mint for about 3 years now, dont even have to do ANYTHING to make it work, just plug it in, turn it on and a little notofication appears saying 'configuring printer' or something like that and a few secs later its ready to use. dont know if all samsungs are like that but this one is

I have both Brother & Samsung MFDs. The Brother is pretty easy using Brother's installer script. The Samsung ML-2870 using wired ethernet was even easier as jaarvidsen said. I am using Ubuntu Gnome and find the default printer manager pretty sparse. I install the package "system-config-printer" if it's not already there. That offers more control and options. I believe "system-config-printer" is included by default in Xubuntu and possibly Lubuntu. To install the Samsung I just tell the app to find network printers. The Samsung shows up. I ask it to install and a few seconds later I get a message "printer installed". The scanner function also works without further tweaking.

---

