---
title: "Suspend/Resume with EeePC 1025C"
date: 2013-05-29
forum: Hardware
---

### Post by sunglassesjoe on 2013-05-29
Hey everyone!

So, I've just installed Xubuntu on my EeePC 1025c Flare and everything is working fine except for the fact that the graphics are broken whenever it wakes from suspend.  I've been searching the forums and Google for quite some time now and can't seem to find a fix to this specific problem--plenty of tutorials on how to install the drivers, but that is not the problem.

Any help would be greatly appreciated.  Thanks!

---

### Post by sunglassesjoe on 2013-05-30
[SIZE=3][FONT=arial]I finally found something that worked.  This should work with any of the Intel Cedarview or Cedar Trail adapters. 
 I created the file: 
[COLOR=#333333]    /etc/pm/config.d/gma500 

with the contents: 
    ADD_PARAMETERS='--quirk-vbestate-restore'[/COLOR][COLOR=#333333].[/COLOR][/FONT][/SIZE]

---

### Post by divirtual on 2013-09-28
Thanks for this tip to helping to restore the screen of the eeePC 1025C after suspend.   A long time ago, I had followed the directions at [http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/](http://blog.uninstall.it/2012/06/05/kubuntu-12-04-on-asus-eeepc-1025c/) to get a working resolution.  Now, with your help, I can tell my wife to just suspend and resume, rather than having to shutdown and restart each time.

---

### Post by Rob Sayer on 2013-11-02
I may be a little late here but I use an acer netbook with cedarview gpa and I should share my experience here.

Generally I'll stick to the lts release (ie. 12.04) but it's not always a good idea.  Like with gma3600 machines.

If you search 12.04 cedarview you'll get a ton of links pointing you to a non canonical ppa that has a kernel driver patch for gma3600.  This will work, but more or less, but it will also hold you to an older version of the kernel.  Which tends to introduce other problems.

It's not even necessary for 12.04.  That patch was moved upstream into the 12.04 kernel.  If you do a 12.04 install, just keep running update until you're damn sure you have everything.  Then install fron Additional Drivers.

This is one of those times where you do a search and the vast majority or results is the wrong one.  Worse, the right way to do it in 12.04 is much easier.

However, that kernel patch that was moved upstream wasn't that good.  They didn't get a decent version of it until 13.04.  It's *way* better, and 13.10 is better still.  I didn't have to modify the grub config file to get brightness control.  First time ever for me on an acer machine ...

I don't know what wireless adapter your asus has, but the broadcom 4313 (actually 4727) in my acer netbook works better than ever now with the open source driver bcrmsmac driver.  That's also a first.  That's a persnickety little wireless adapter in linux ... it feels like I picked a netbook with the 2 least well supported hardware items in linux, but it works fine now in 13.10.  Just another example.

Personally I prefer to use the long term support version ... I installed 13.10 with a separate partition for /home since I'm now in a 9 month update cycle for this machine ... but the lts isn't always the best choice.

---

