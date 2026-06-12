---
title: "Wlan0 not working w/ ndiswrapper (bcmwl5.inf)"
date: 2005-03-15
forum: Hardware &amp; Laptops
---

### Post by noamsml on 2005-03-15
I have just install hoary on my laptop. I usually use ndiswrapper for my WLAN. after installing ndiswrapper, the drivers, and doing ndiswrapper -m,  I copied an /etc/netwok folder I had on the CD which was known to work with debian sarge. it did not work, for some reason dhclient would fail.

moreover, while on debian iwlist wlan0 scanning would return our wlan, on hoary it said it could not find anything.  I then tried removeing ndiswrapper-utils and installing ndiswrapper from source, which caused a whole mess. I then reinstalled ubuntu and tried the same thing but edited /etc/network/insterfaces manually instead of copying it, which did not work either.

what should I do?

---

### Post by lao_V on 2005-03-15
Have you tried using the DriverLoader from Linuxant? I found it extremely easy to install and use. [Try it]("http://www.linuxant.com/driverloader/?PHPSESSID=5115e097f2114f241f5bdff5f3d192c8"), you might like it

---

### Post by munki on 2005-03-15
I've got ndiswrapper runnning with bcmwl5 :)

In your ndiswrapper config file, edit the line (something)radio and change the value from 1 to 0.

0 means power on the chipset
1 means power off the chipset

Don't ask why it's default setting is 1, but it was here... 

Just change the "1" to "0" on the radio-thing in /etc/ndiswrapper/config , reboot the machine and the light will glow on your wlan card :)

If you got some problems message me, and I will answer it later.

---

### Post by andyk on 2005-03-15
i use the same drivers for my compaq presario wifi card.  i too had it up and running and then after some upgrades it went haywire.  i tried copying backup copies of the original folder with no luck.  i ended up going in to apt and uninstalling ndiswrapper completly along with the bcmwl5 inf and sys files and then reinstalling ndiswrapper from scratch.  it worked with no problems.  don't know about editing config file, as i never had to do it with ubuntu.  i've had to in other linux distros (Suse namely)

good luck,

andy

---

### Post by telmo on 2005-03-15
I have it working (the same driver) on Hoary, if this is your case, just download the source file from sourceforge and install it using make and make install instead of just make install. This works perfectly for me.

If your using Warty, just browse the forum a little and you'll find a thread i made with this solution.

---

### Post by noamsml on 2005-03-15
[QUOTE=munki]I've got ndiswrapper runnning with bcmwl5 :)

In your ndiswrapper config file, edit the line (something)radio and change the value from 1 to 0.

0 means power on the chipset
1 means power off the chipset

Don't ask why it's default setting is 1, but it was here... 

Just change the "1" to "0" on the radio-thing in /etc/ndiswrapper/config , reboot the machine and the light will glow on your wlan card :)

If you got some problems message me, and I will answer it later.[/QUOTE]
thank you, it worked!

---

### Post by munki on 2005-03-15
Off cause it did ^^

---

### Post by andyk on 2005-03-15
so are you trying to gloat ? ;)  Kidding.  Although I didn't know about the whole "off and on" thing, so thanks.  Learn something new everyday...

andy

---

### Post by munki on 2005-03-16
[QUOTE=andyk]so are you trying to gloat ? ;)  Kidding.  Although I didn't know about the whole "off and on" thing, so thanks.  Learn something new everyday...

andy[/QUOTE]

I did neither, but since I couldn't get the light glow on my wlan I got angry  :twisted: so I started to fool around, and zapping through config files, and saw that line.. then I 'googled' it, and found some information :) 

ndiswrapper works really fine.

---

### Post by yippy on 2005-03-17
[QUOTE=andyk]i too had it up and running and then after some upgrades it went haywire.[/QUOTE]
It breaks for me after kernel upgrades, I have to recompile and install ndiswrapper each time.  (I have amd64, so I've had to manually compile it)

---

### Post by Shaggy on 2005-03-22
Just wanted to hop in with another instance of the problem being fixed by changing the config file.

What I had to change was the "RadioState" perameter from 1 to 0, I know I had to change mine because when I installed the driver ndiswrapper said it was changing the state from 0 to 1.  This was with the default ubuntu deb that was installed.

---

### Post by Feenix3k on 2008-04-20
Be sure to blacklist bcm43xx. I too had troble with bcmwl5.inf, but the laptop was loading bcm43xx. Once it was blacklisted it worked fine.  Also this guide gave me the information I needed to solve my bcmwl5.inf problems.  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

