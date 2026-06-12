---
title: "DELL Dimension 9200 and HP DeskJet 960C"
date: 2017-02-02
forum: Hardware
---

### Post by rcoleman.88 on 2017-02-02
Hello forum.

I've already been lurking around this forum for a few days and finally decided to register. Hopefully I will get some advice to solve my problem. At first, just to let you know, I'm just an average user and I haven't been using Ubuntu for a long time myself. So please bare that in mind.

A few years back I upgraded my parents old DELL Dimension 9200 to Win7. Now they were pestering me to upgrade to Win10. Personally I don't like MS Win that much and I doubt that Win10 would run smoothly on this old machine. Furthermore I heard so many bad things about Win10, especially recent updates resetting different configurations like the browser etc., so I decided not to do so.

Instead, since I have been using Ubuntu for a while, I decided to install the Mate Desktop (16.04.1 LTS) on my parent's computer. So far everything is good. I mean they are just using it to surf the internet, watching some silly (YouTube) videos and some basic text processing. So in my opinion there was no need to buy an new computer. The old one is still sufficient.

Anyway. Now I came across an issue and I just can't solve it. My parents still own an old printer which they bought used online a while ago. It's an old [HP DeskJet 960C]("http://www.for-sale.ie/hp-deskjet-960c") and I just can't get it to work. So can anyone please give me some advice? My parents are quite impatient when it comes down to these things. So any help is highly appreciated.

Ron.

---

### Post by howefield on 2017-02-02
> **rcoleman.88 said:**
> It's an HP DeskJet 960C and I just can't get it to work.

What have you tried ?

As far as I can see that printer should work out of the box as long as you have HPLIP installed. 

The package hplip-gui might make it easier.

```
sudo apt-get install hplip-gui
```

---

### Post by rcoleman.88 on 2017-02-02
Thanks for the fast reply.

> **howefield said:**
> What have you tried ?

As far as I can see that printer should work out of the box as long as you have HPLIP installed. 

The package hplip-gui might make it easier.

```
sudo apt-get install hplip-gui
```

I got the hplip ([http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)) and followed the installation instructions. Then I connected the printer. Nothing.
Resart, connected the printer again. Nothing.

Maybe I'll try the GUI. Thanks for the hint.

Otherwise I would just try to un- and reinstall hplip.

The printer should be alright. It was working before.

---

### Post by pdc on 2017-02-02
welcome to the Ubuntu forums: so the printer is connected by a usb cable to the computer? 

often folks that use ubuntu use the terminal to ask questions of the system about what is happening ... but if you find the folder that is called PRINTERS, do you see an icon there for the HP? (that would suggest to me it is installed ........)

If you have LibreOffice installed; to write letters; and you create a new page, and then click on the Print button, do you see a setting for the HP Deskjet?

It may seem daunting if you are new to ubuntu, but if you find the terminal in your system: the icon for it looks like a TV screen ......... and if you paste this command into it 

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

....... instead of control v like in most programmes you need an extra finger so it is control shift v .......... if you do that, is the HP listed? If that is too daunting then just type > [COLOR="#FF0000"]lsusb[/COLOR] in the terminal ... that is asking your computer to **LIST** the **USB** devices that are connected .........

 ...........if you are on a roll, can you copy the result and paste it back here?

___________________________-

If the Deskjet is listed there, then HP in their advice [http://hplipopensource.com/node/332#printing2](http://hplipopensource.com/node/332#printing2) say paste this command > [COLOR="#FF0000"]hp-check -t[/COLOR] and then > [COLOR="#FF0000"]hp-check[/COLOR]

---

### Post by rcoleman.88 on 2017-02-02
Thanks pdc!

I'm new to Ubuntu but after a few months I already know about the basics (Terminal, packages, dependencies etc.). But I'm still learning. ;)

I did the checks you described. Thanks for providing the commands! I didn't know them.
It looked like there was an issue with one of the dependencies. I don't know why because I used the automatic installer.

So I manually (re-) installed the missing (or corrupted?) package (libjpeg) via sudo apt-get install, did a reboot and connected the printer again. After that it got recognized by the system. And now it is working.

Thanks for your help!

Ron.

---

### Post by pdc on 2017-02-03
well done Ron! You are doing well to getting to use the terminal etc: sort of like doing your own oil and battery water checks!! It is nice when it all works

Glad it is all working;

---

### Post by rcoleman.88 on 2017-02-03
Yeah. But it's not that easy after using WIN for a long time. Especially tracing down problems. But luckily there's a great community.

---

