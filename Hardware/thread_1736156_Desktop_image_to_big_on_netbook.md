---
title: "Desktop image to big on netbook"
date: 2011-04-22
forum: Hardware
---

### Post by Max Ward on 2011-04-22
I recently got a netbook from a friend. It had a broken and old version of ubuntu on it so I decided to make a usb drive with ubuntu 10.10 and write over the old ubuntu version. Everything was fine (i managed to boot from the usb fine) until I selected install ubuntu from the live usb menu, after I did this I just saw lots of coloured line moving up the screen. I looked up the problem on google and found that I could try and set nomodeset at the live boot screen. This worked however the screen was way to big for the monitor so that I could not see the full desktop, and whenever I try change the resolution I just lots of scrabled graphics until it reverts back to the old resolution. I managed to install ubuntu thinking I might be able to update the graphics drivers from the update manager but when I installed all the updates I still had the same problem of the desktop being to big to fit on the monitor. What can I do?  :confused:

---

### Post by linuxyogi on 2011-04-22
Mention the graphics hardware details of that netbook & may be people can help.

Just Google for it. I guess you will find the specs.

---

### Post by Max Ward on 2011-04-22
I found the hardware detail but it doesn't name what graphics it has it just says onboard it and I can find the graphics specification anywhere.

Model	 Elonex Webbook NB1
Lid Colour	 Black
Operating System	Linux Ubuntu
Processor Type	 Via C7-M
Processor Speed	 1.6 GHz
RAM Size	 512 MB
RAM Technology	 DDR II SDRAM
Hard Drive Capacity	 80 GB
Hard Drive Interface	 SATA
Screen Size	 10.2
Screen Type	 WXGA
Optical Drive	 No Optical Drive
Graphics	 On board
Networking	 Adapter On board, RJ45
USB Ports	 3
Wireless LAN	 g/b
Keyboard	 UK

---

### Post by KegHead on 2011-04-22
Hi!

My neighbor had a problem with his monitor.
 
Worked out his monitor had a borked connection at his mobo.

Does your netbook have any history?

KegHead

---

### Post by Max Ward on 2011-04-22
No the old ubuntu os on it used to work fine no problem

---

### Post by KegHead on 2011-04-22
Hi!

Your specs look ok.

Just an idea:

Try to install your iso again on your usb stick.

It's worked for me.

KegHead

---

### Post by snowpine on 2011-04-22
Welcome to the forums Max! There is a Search feature at the top right of the page, you can use to find other Elonex users who are having the same problem.

For example:
[http://ubuntuforums.org/showthread.php?t=1148184](http://ubuntuforums.org/showthread.php?t=1148184)

Hope that helps you troubleshoot the problem, since I am not familiar with this hardware myself, I can't do anything except point you in the right direction. Good luck! :)

---

### Post by linuxyogi on 2011-04-22
You can try reinstalling as sugested or you can get info about you graphics hardware by installing 

hardinfo

```
sudo apt-get install hwinfo
``` ```
hwinfo -gfxcard
```

---

### Post by Max Ward on 2011-04-22
Ok I have got a bit further I found the grapics chip name and found the driver however the driver says it only works on ubuntu 9.04 however I tried to install it on 10.10 which ended up in ubuntu stating in a command prompt, I unistalled the driver and got a GUI back does this mean I will have to use 9.04

---

### Post by linuxyogi on 2011-04-22
> **Max Ward said:**
> Ok I have got a bit further I found the grapics chip name and found the driver

So what is it ? Why didn't mention it here?  May be someone can help.


> **Max Ward said:**
> does this mean I will have to use 9.04

Using 9.04 is not an option. It is no longer supported.

See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

_**Mention your graphics hardware.**_

---

### Post by Max Ward on 2011-04-22
the graphics chip is "VIA Technologies, Inc. CX700/VX700 [S3 UniChrome Pro]" and here is the driver site [http://linux.via.com.tw/support/downloadFiles.action](http://linux.via.com.tw/support/downloadFiles.action)

but as I say it only supports 9.04

---

### Post by Max Ward on 2011-04-22
I think 9.04 is my only choice

---

### Post by linuxyogi on 2011-04-22
Okay, try this

open a terminal & type ```
sudo displayconfig-gtk
```
Now try to adjust the resolution of your monitor there

If by any chance you don't see the correct resoution , select "openchrome" as driver

Finally **save** the configuration.

I did this a long time ago. I am not sure if this will work.

But there is no harm in trying.

---

### Post by Max Ward on 2011-04-22
displayconfig-gtk doesn't work
I get:
sudo: displayconfig-gtk: command not found
but thanks anyway

---

### Post by linuxyogi on 2011-04-22
> **Max Ward said:**
> I think 9.04 is my only choice

If nothing works move to some other distro. Using 9.04 is not at all a sensible decision  from a security point of view.[-X

---

### Post by linuxyogi on 2011-04-22
Try this [http://crunchbanglinux.org/](http://crunchbanglinux.org/)[]("http://www.google.co.in/url?sa=t&source=web&cd=1&ved=0CCYQFjAA&url=http%3A%2F%2Fcrunchbanglinux.org%2F&rct=j&q=crunchbang&ei=o8uxTdGiD4G3twfU3viMDA&usg=AFQjCNESSEiLpa8ddWQlgxjCrZoNlrI2JA&cad=rja")

---

### Post by Max Ward on 2011-04-22
with another distro wont I have the problem I had originally havng to start the install with nomodeset?

---

### Post by snowpine on 2011-04-22
Don't give up, Max! I just typed "openchrome" in the Search box at the top right of the page and got hundreds of hits. You are on the only person in the world with this graphics chip; somewhere on these forums is the solution! :)

I also did a Google search for "ubuntu openchrome" and this was the first result, maybe it will help? [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by linuxyogi on 2011-04-23
Just try to learn how to configure the Xserver. Previously there was displayconfig-gtk for this purpose but now it seems they have removed it.

Five years back I used to use a  PC with VIA Graphics. What I have learned from my experience is that VIA "just works" in Linux. Nothing more. While you get accelerated graphics with most Intel Chips out of the box. And in case of Nvidia & ATI there's both open source & proprietary drivers available.

Because there are so many better solutions available out there, the Linux community don't really care about VIA graphics anymore (I think). Probably that's why not many people responded to your thread. 

The main culprit here is VIA itself. They should have co operated with the Linux community in developing drivers. 

IMHO, in future stay away from VIA.

---

### Post by dandnsmith on 2011-04-23
Just reviewing this thread makes me wonder if you're going down the right path.
I think I can infer that you can boot from a USBstick, and that you've picked 10.04 but not the netbook version.
Why not get a live version of the netbook Ubuntu 10.04 onto USB and boot from that. Look at the results and see whether it's doing the screen part properly (after all, that is what you asked about) - if it it you can install from there.
The netbook version is specifically designed to work with the smaller netbook screens, ans so far these have stood me in good stead.
I caution against a later version than 10.04, as things started changing, and some people had problems.

---

### Post by Max Ward on 2011-04-23
I have tried other disrubutions and netbook versions now I always get the same problem. The driver I download seems not to work at all. I tried pluging the notebook into an external monitor today and the display on the netbook corrected itself slightly I could see the entire bar at the top however the desktop image was still far to long also after I rebooted it went back to how it was before. Is there no way of changing the screen orientation (like you could with old CRT monitors)?

---

