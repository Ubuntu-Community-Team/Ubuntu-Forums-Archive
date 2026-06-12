---
title: "EEE 1000 Series - How is the support? I'm thinking of buying one."
date: 2009-05-07
forum: Hardware
---

### Post by Repgahroll on 2009-05-07
Hello, first of all, sorry my poor english :(...

I want to buy a netbook to work, because I travel a lot and always have to access my emails from public computers.

I've been searching a lot and i found that the better options nowadays are the Asus EEE 1000 series, because Acer support in my country is very poor, (I used to have an AOA and they took about 2 months to repair a simple 'single key bad contact problem' inside warranty) and I bet MSI support is just as poor as Acer's one. The other manufacturer's, like Dell, HP, LG, Samsung, etc. has expensive or ""bad"" hardwares. So, i'm almost decided. EDIT -> I'm talkin'bout the 1000/1000H/1000HA, can't afford an 1000HE :(.

BUT, I don't know about the Linux (Ubuntu) support for such hardware, one of the most important aspects to me is the battery life time, because i don't have where to charge it most part of the time, and the second aspect is the Linux support, i want everything working, bluetooth, ethernet, wi-fi, wcam, mic, speakers, usbs, card readers, i want to buy a bluetooth mouse, i have to print on a lot of different printer (ubuntu support them all PnP), i also plan to connect it on an external monitor and speakers sometimes.

I know that the MSI Wind battery life is poor on Linux compared to Windoze XP, and i don't know if such thing also happens with the EEEs.

Maybe I should wait a little longer. What do you think?

Is the shorter battery life issue on Winds a "Linux" fault?

Thank you very much!

---

### Post by e.j. on 2009-05-08
I have the 1000he and everything 'just works'. Install eee-control and you can even control the cpu speed and toggle bluetooth, wifi, the camera and the card reader.

My battery life is great, 6.5-7 hours light internet, but the 1000he has a better battery than the other 1000 series computers. Ubuntu seems to do fine with the battery though.

I would imagine you'd have the same experience with any of the 1000 series.

You can find lots more info here: [http://forum.eeeuser.com/](http://forum.eeeuser.com/)

---

### Post by Repgahroll on 2009-05-09
Thank you!

Do you get such battery life using wi-fi? And do you get the same battery life running Windoze?

Right now the 1000HE is 30% more expensive than 1000HA, so i wonder if it's a better deal to wait a little and buy an 1000HE.

I thought the battery life of 1000HE series was 9,5h....

Thanks, and sorry my english.

EDIT: eee-control = eee-applet? I only found eee-applet in the official repos, and the description there is similar to your description of eee-control.

---

### Post by Jota37 on 2009-05-11
Hi,

eee-control is not in the repositories, you have to download the package directly from the author's website instead.

Here's the address:
[http://greg.geekmind.org/eee-control/]("http://greg.geekmind.org/eee-control/")

There are links to the .deb versions for Ubuntu close to the top of the page, at least now.

---

### Post by Jota37 on 2009-05-11
Now, on to the experience with the 1000HE, which I got about 6 weeks ago: it is great. :)

After getting it for my trip back home, I first installed Easy Peasy 1.0 (later upgraded to 1.1) on it, which was very nice. I kept XP on a small 10 GB partition, just in case, and it was a good idea, because the wireless modem at my parents home abroad would not work except in XP. At least I got tired of trying to mess with it and gave up. There are reports on line of people able to make that modem work in Linux (it's a Giant D310). I also installed 2 GB of RAM, removing the original 1 GB that came with the Eee, since that cost only $15 and is an easy way to make any computer perform much better.

Just after getting back to the USA, Jaunty was out, so I wiped the HD and installed 9.04 Ubuntu Netbook Remix on it. It works great, and I get about 6 hours battery -- most of it using wireless Internet. Some of the special keys only work after installing eee-control, and you have to set them up yourself (through eee-control preferences). Easy Peasy had it all already set up "out of the box". Apart from that, they are very similar, looks almost identical.

You can use Ubuntu, even the Netbook Remix, in Classic Desktop mode. But to me the classical mode is not good in such a small screen, with a lot of wasted space in the middle. The netbook mode uses space much more efficiently. That said, some software like the GIMP (image editor) do not work well in the "netbook mode", because of the several dialog windows.

WiFi worked nicely from the beginning, as did card reader, and the fn keys for screen brightness, volume, audio mute, external monitor switch, and maybe some others I'm forgetting now. It suspends are awakes fine, too, which I had heard was a sticking point in Linux in the past (this is my first laptop, although I've been a Linux user for 8 or 9 years). Webcam/mic and sound worked very well too, as did Skype using those. I have used Bluetooth mouse with it, but one of those that use a USB dongle.

Now, why the 1000 HE instead of 1000 HA, for me:
- faster wireless (N instead of G)
- better keyboard
- longer battery life

That's my experience with this little, wonderful laptop. I hope it helps.

---

### Post by Repgahroll on 2009-05-12
Thank you very much Jota37!!

Just one last question: Do you get the same battery life on XP?... 1000HE has a 'nominal' battery life of 9.5h...

Anyway, i'm now decided to wait a little longer and get one of these 1000HE.

Thanks.

---

### Post by Jota37 on 2009-05-13
Repgahroll,

> **Repgahroll said:**
> 
Just one last question: Do you get the same battery life on XP?... 1000HE has a 'nominal' battery life of 9.5h...


Well, I did not use it a lot in XP, just to access the net sometimes when on vacation. But I seem to remember that XP estimated about one hour more of battery life than Ubuntu does. I never really timed either one of them to see whether the estimates were accurate at all to begin with. I managed to get a good day out of it though, e.g. at the airport for some 6 or 7 hours, I used the Internet a lot, and although I did not use it continuously, it lasted for the whole day.

The "nominal" battery lives manufacturers give are always a bit optimistic... I guess they turn screen brightness way down, put CPU in "poewrsave" mode only, turn off WiFi... Who knows... :)

Anyway, the price difference between the HA and HE is quite small, as far as prices listed on Amazon were when I got mine... Something like $60, maybe?

Good luck!

---

### Post by Repgahroll on 2009-05-13
Thank you! I think it's better to buy one with Windows and duel-boot Ubuntu, because of compatibility problems, and the price is almost the same. (at least in my country)

But if i really notice that the battery life is that better on Windows (>1 hour), i think i'll use Windows most part of the time, at least while travelling.

Thank you very much!

---

### Post by Chronon on 2009-06-08
The only rough bit I am seeing is trouble waking up.  After hibernating it will often have 2--5 false starts (wakes up but hibernates immediately) before it will finally wake up.

I have had a couple of freezes with screen corruption, but I can't reproduce it reliably.

---

