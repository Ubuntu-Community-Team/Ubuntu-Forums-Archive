---
title: "Need help setting up Verizon Novatel Wireless"
date: 2010-02-03
forum: Hardware
---

### Post by pizza-is-good on 2010-02-03
Hello there,

I have successfully installed Karmic on a co-worker's desktop (A Dell Vostro 220). There is some software that he wants to add, and of-course, there is all the updates to run. The problem is that we cannot connect personal computers (as in not owned by the company) to the network. He has a Verizon Novatel 3G card that we can use, but Ubuntu will not see it. A while back, I used a Sprint Sierra Wireless card on my laptop, and Ubuntu handled it better than windows.

We put in the card, and nothing will happen. I tried the set up wizard, but all that it does is put a "#777" in the number field.

That is the only way that we can connect to the internet, so we need to get it working. I'm sure that there is a way, so your experience will be appreciated.

Thanks,

~pizza

---

### Post by pizza-is-good on 2010-02-03
bump.

Anyone, any ideas or help?

~pizza

---

### Post by SoFl W on 2010-02-03
Okay, I will give pizza chance.

A couple of years ago at work we did get a Verizon card and linux working.  However I no longer work at that place and don't have access to the bookmarks.  I remember sites specifically for Linux and Verizon cards so try searching for Verizon and Linux.   (If you haven't already)  If I remember you did need to change some config files.

---

### Post by SoFl W on 2010-02-03
Other thoughts:

1) I know with some programs in Windows you need to set it up as a Sprint card and it works.   You might need to configure it as a Sprint card not as a Verizon card.

2) Have you considered getting a wireless router for the card?  (Example is a Dlink DIR-450)   The card plugs into the router and connects to the Internet.    The computer connects to the router as usual.  Sometimes this is easier and allows you to connect multiple machines/devices.

---

### Post by pizza-is-good on 2010-02-03
> **SoFl W said:**
> Okay, I will give pizza chance.

A couple of years ago at work we did get a Verizon card and linux working.  However I no longer work at that place and don't have access to the bookmarks.  I remember sites specifically for Linux and Verizon cards so try searching for Verizon and Linux.   (If you haven't already)  If I remember you did need to change some config files.

> **SoFl W said:**
> Another thought.

I know with some programs in Windows you need to set it up as a Sprint card and it works.

Have you considered getting a wireless router for the card?  (Example is a Dlink DIR-450)   The card plugs into the router and connects to the Internet.    The computer connects to the router as usual.  Sometimes this is easier and allows you to connect multiple machines/devices.

SoFl W,

Thanks for your reply.

I am still looking around for those sites. I had already tried prior to posting, but then again, it's always worth a second try.

I have not considered the router, since this will only be a one time deal to get the computer up with all the software that he wants, and up to date, and then just leave it off the internet indefinitely.

I'm a little unsure as to what you mean by setting it up as a Sprint card in windows...

---

### Post by SoFl W on 2010-02-03
I am wrong, it wasn't under Windows.  At work we used those Dlink DIR-450 routers for wireless cards.  In the configuration on the router itself we selected a Sprint card because the comparable Verizon card was not listed.  

I guess what I am saying is don't limit your search to just Verizon models.  Verizon and Sprint use the same network and a lot of the cards are the same.  You might be able to find help with configuring a comparable Sprint card.

---

### Post by pizza-is-good on 2010-02-03
OK, that's a good idea.

The thing that puzzles me tho is that I used a Sprint Sierra Wireless card on my ubuntu-laptop a few months back, and it worked without a problem...

I'll keep looking, and waiting to see if somebody has any other ideas or knowledge from experience.

But thanks for all your help SoFl W, and if you have any more ideas, please post them.

~pizza

---

### Post by pizza-is-good on 2010-02-03
I still haven't found anything...

Anyone else???:?

---

### Post by efflandt on 2010-02-04
It might help if you said which model Novatel 3G device you have.  I have a USB720 and all I had to do to get that to work is pick USA and Verizon from Network Connections and it simply worked (even from bootable iso on USB flash before I knew how to get Broadcom WiFi working).

But another poster mentioned a 760, and I have no experience with that.

---

### Post by pizza-is-good on 2010-02-04
> **efflandt said:**
> It might help if you said which model Novatel 3G device you have.  I have a USB720 and all I had to do to get that to work is pick USA and Verizon from Network Connections and it simply worked (even from bootable iso on USB flash before I knew how to get Broadcom WiFi working).

But another poster mentioned a 760, and I have no experience with that.

I'll find out today, for some reason I didn't copy the model # down, but I did copy the FCC ID and the IC.:lolflag:

~pizza

---

### Post by pizza-is-good on 2010-02-04
It's a USB760.

---

### Post by SoFl W on 2010-02-07
Pizza,

I installed ubuntu on my laptop and at the last minute took the laptop on a trip.  While I was at the airport I wanted to see how ubuntu, my laptop and access to the airport's free WiFi would work.  It didn't, but when I was booting my laptop I noticed there was a warning/error displayed for a second.  I checked the log files and found out the driver for my wireless card was not installed. When I had access to a wired connection I found [THIS]("http://ubuntuforums.org/showthread.php?t=759100") page and the drivers.

Check the logs and see if an error for the card is displayed, check the "/lib/firmware/" directory for the correct drivers.

---

### Post by pizza-is-good on 2010-02-08
SoFl W,

Thanks for that info. I have downloaded it all, and will try it tomorrow when I have access to that computer. It looks promising.
I will post again as soon as I can to let you know if it worked or not.

~pizza

---

### Post by zerubbabel on 2010-02-08
In the "Mobil Broadband" section of your device configuration, use:

Number: #777
Username: [email]1234567890@vzw3g.com[/email] (substitute your cell number)
Password: vzw

---

### Post by pizza-is-good on 2010-02-08
> **zerubbabel said:**
> In the "Mobil Broadband" section of your device configuration, use:

Number: #777
Username: [EMAIL="1234567890@vzw3g.com"]1234567890@vzw3g.com[/EMAIL] (substitute your cell number)
Password: vzw

That sounds like a good idea too, I'll give it a try tomorrow as well, but first, I have a question:

How do I find out the # of the card, or is it my co-worker's cell #?

Thanks,

~pizza

---

### Post by SoFl W on 2010-02-08
Unless I am wrong each card has its own cell number.  When my company used them the paperwork had the phone number listed along with the ESN  (Electronic Serial Number)  If you don't have access to the paperwork someone at Verizon might be able to help you using the ESN.

---

### Post by zerubbabel on 2010-02-10
> **SoFl W said:**
> Unless I am wrong each card has its own cell number.  When my company used them the paperwork had the phone number listed along with the ESN  (Electronic Serial Number)  If you don't have access to the paperwork someone at Verizon might be able to help you using the ESN.

Exactly. It's also on the statement you get from Verizon every month, or you can look at your Verizon account online and it will show you the phone number of your device.

---

### Post by pizza-is-good on 2010-02-11
> **zerubbabel said:**
> In the "Mobil Broadband" section of your device configuration, use:

Number: #777
Username: [EMAIL="1234567890@vzw3g.com"]1234567890@vzw3g.com[/EMAIL] (substitute your cell number)
Password: vzw

> **SoFl W said:**
> Pizza,

I installed ubuntu on my laptop and at the last minute took the laptop on a trip.  While I was at the airport I wanted to see how ubuntu, my laptop and access to the airport's free WiFi would work.  It didn't, but when I was booting my laptop I noticed there was a warning/error displayed for a second.  I checked the log files and found out the driver for my wireless card was not installed. When I had access to a wired connection I found [THIS]("http://ubuntuforums.org/showthread.php?t=759100") page and the drivers.

Check the logs and see if an error for the card is displayed, check the "/lib/firmware/" directory for the correct drivers.


Well, I tried both of the above, and nothing worked....

For some reason, it just won't do anything with the card.

I was monitoring the system log as I put the card in today, and it did something, I mean, that the log said things like 'USB device connected on port 2', 'broadcomm wireless USB detected' and so forth, but it did nothing to my network manager...

---

### Post by pizza-is-good on 2010-02-20
Well, we never managed to get the card working, so this thread is still open I guess, but just FYI, we found a loophole to the network rules, so as long as we didn't log in to the server, we could hook up an outside computer. Everything worked out OK.

Thank you for your help everyone anyways.

~pizza

---

### Post by Mach1US on 2010-02-22
This has worked for me flawlesly

[http://ubuntuforums.org/showthread.php?p=2048477#post2048477](http://ubuntuforums.org/showthread.php?p=2048477#post2048477)

---

### Post by jpl888 on 2010-02-22
I have a Novatel X950D and you have to eject the fake CD before the device will go into modem mode i.e. ```
eject sr0
```

Try running it manually from the command line and see if network manager picks it up. If it does I'll tell you how to modify the udev rules so it happens automatically.

---

### Post by Mach1US on 2010-02-22
This has worked for me flawlessly

[http://ubuntuforums.org/showpost.php?p=2048477&postcount=1](http://ubuntuforums.org/showpost.php?p=2048477&postcount=1)

---

### Post by pizza-is-good on 2010-02-25
> **Mach1US said:**
> This has worked for me flawlesly

[http://ubuntuforums.org/showthread.php?p=2048477#post2048477](http://ubuntuforums.org/showthread.php?p=2048477#post2048477)

> **Mach1US said:**
> This has worked for me flawlessly

[http://ubuntuforums.org/showpost.php?p=2048477&postcount=1](http://ubuntuforums.org/showpost.php?p=2048477&postcount=1)


That Worked!!!!!!!

I had to restart the computer before it worked tho.... But it did.

This Thread is SOLVED!!!!

---

