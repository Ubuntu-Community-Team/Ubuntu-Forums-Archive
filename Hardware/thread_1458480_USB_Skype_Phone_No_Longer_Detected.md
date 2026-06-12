---
title: "USB Skype Phone No Longer Detected"
date: 2010-04-20
forum: Hardware
---

### Post by rykel on 2010-04-20
Hi,

My USB Skype Phone (as an audio input/output) was detected and working fine under Karmic and up to Beta 1 of Lucid.

However, it is no longer detected.

I would like to file a Launchpad bug report so that the developers concerned can do something about it.

May I know which Launchpad page should I make a report like this, and what information do I need to include?

Thank you!

---

### Post by khelben1979 on 2010-04-20
[Bugs in Ubuntu]("https://bugs.launchpad.net/ubuntu")

If you intend to report bugs by using the Ubuntu launchpad.net you need to create an account with them first, click on report a bug on the page and you get to their log in page.

---

### Post by rykel on 2010-04-24
I have a Launchpad account, but I do not know where to file a report like what I want.

The USB Skype Phone in question is a knockoff product that looks like the phone from IPEVO. (see picture)

Ubuntu has successfully detected it as an Audio Device until one of the Lucid update caused Ubuntu to fail to detect it anymore.

I need to use the phone. Can you please advise?

---

### Post by khelben1979 on 2010-04-24
Hmm.. give an output from how the system identifies your usb phone and make sure it's connected:
```
lsusb
```

Then I'll look at for starters.

---

### Post by rykel on 2010-04-24
> **khelben1979 said:**
> Hmm.. give an output from how the system identifies your usb phone and make sure it's connected:
```
lsusb
```

Then I'll look at for starters.

Hi,

This is what I got...

[B][INDENT]$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/INDENT][/B]

Other than the USB phone, nothing else is attached via USB.

---

### Post by khelben1979 on 2010-04-24
From what you posted I can't see that your mobile phone is detected. Filing a bug report to the Ubuntu developers might speed up the process in getting this fixed, other than that, I don't know what you should do.

Of course, reinstalling is also an option and then you can turn off automatic updates and only apply updates to your system which you are certain of what they are.

---

### Post by rykel on 2010-04-24
> **khelben1979 said:**
> From what you posted I can't see that your mobile phone is detected. Filing a bug report to the Ubuntu developers might speed up the process in getting this fixed, other than that, I don't know what you should do.

Of course, reinstalling is also an option and then you can turn off automatic updates and only apply updates to your system which you are certain of what they are.

Thanks!

Interestingly, the red lights do still blink upon inserting the phone into the USB port as expected. Would you have a link where I can click on to file this bug report?

btw, this phone is fairly popular and common in Asia, as it looks cool and is waaaay cheaper than the IPEVO one. Which probably came from the same factory in China anyway. hehee   :P

---

### Post by khelben1979 on 2010-04-25
I would recommend you get an Ubuntu launchpad account by clicking on register in the right top of the screen from [this webpage]("https://launchpad.net/ubuntu").

Once you have a launchpad account you can file a bug report in there, but before you do so, you should check if others have had the same problem as you by searching through: [Questions for Ubuntu]("https://answers.launchpad.net/ubuntu").

---

### Post by fparri on 2011-04-12
I've got this same phone. Anyone can use it, especially using the dialpad and menu buttons, too? :)

---

### Post by rykel on 2011-04-12
Unfortunately the phone buttons and menus do NOT work on Ubuntu, although it can be used as a speaker and microphone. I have thrown away the phone and no longer uses it with the PC. Anyway, with Android, iPhone and Symbian mobile phones, we can now have a handsfree, cordless Skype phone, so who needs those stinky, Linux-UNfriendly USB phones??    :)

---

### Post by fparri on 2011-04-13
I partly agree. It's true that Skype works with most smartphones on market, but sometimes it's useful to have a USB-powered Skype Phone connected all the time to our PC. Think of office :)

Pity nobody developed linux-drivers for these devices... :(

---

