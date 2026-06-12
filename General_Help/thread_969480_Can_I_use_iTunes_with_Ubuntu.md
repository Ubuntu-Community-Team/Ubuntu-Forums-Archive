---
title: "Can I use iTunes with Ubuntu?"
date: 2008-11-03
forum: General Help
---

### Post by fullerama on 2008-11-03
Brand new to Ubuntu. Also brand new to iPhone. (I know, where have I been...).  I have found that one needs to access iTunes to get Apps and other downloads. Is it possible to install iTunes on Ubuntu?

If not, is there some sort of bridge between iTunes and some other program that will facilitate getting iTunes on the computer?

Seems you need iTunes to sync everything on the iPhone. Any help will be greatly appreciated.

---

### Post by Rainstride on 2008-11-03
> **fullerama said:**
> Brand new to Ubuntu. Also brand new to iPhone. (I know, where have I been...).  I have found that one needs to access iTunes to get Apps and other downloads. Is it possible to install iTunes on Ubuntu?

If not, is there some sort of bridge between iTunes and some other program that will facilitate getting iTunes on the computer?

Seems you need iTunes to sync everything on the iPhone. Any help will be greatly appreciated.

Rhythmbox Music Player does pretty much the same exact thing for the most part, and it has ipod support so you should be able to use your iphone with it.

---

### Post by fullerama on 2008-11-03
Thanks, Rainstride. I'll try that.

---

### Post by rbmorse on 2008-11-03
I haven't found a way to do this that doesn't involve jailbreaking the iPhone and therefore invalidating it's warranty.

What does work (mostly) for me is to run an XP virtual machine under VMware and install iTunes into that. VirtualBox may work, too, but in either case it needs to be able to handle USB devices that hotplug. 

The mostly part is that I cannot restore an iPhone from iTunes that has been backed up on a VMware virtual machine.  Everything else works pretty well.

---

### Post by jpoRS on 2008-11-03
Does this help?

[URL="http://ubuntuforums.org/showthread.php?t=957403"]LINK
[/URL]
Good Luck,
jim

---

### Post by skydiver|goose on 2008-11-03
sorry about your iphone purchase, hopefully you can get something that works well to replace it soon

in the mean time, VMWare, WINE, or CrossOver will allow you to run itunes in ubuntu. I'd recommend WINE. You'll do:

```
sudo apt-get install wine
```

then go to the apple website, download the itunes installer, and once it's downloaded right click and open with WINE

good luck mate

---

### Post by prometheus1981 on 2008-11-03
> **skydiver|goose said:**
> sorry about your iphone purchase, hopefully you can get something that works well to replace it soon

in the mean time, VMWare, WINE, or CrossOver will allow you to run itunes in ubuntu. I'd recommend WINE. You'll do:

```
sudo apt-get install wine
```

then go to the apple website, download the itunes installer, and once it's downloaded right click and open with WINE

good luck mate

You can also go to [http://www.winehq.org/](http://www.winehq.org/) for more information, but I would try to install wine in sudo first. I have WinXP on dual boot because when I tried wine, for some reason, iTunes ran worse than in Windows (Hard to belive huh?)

---

### Post by fullerama on 2008-11-03
Thanks to all for your responses. Even Skydiver!  Hey, the iPhone was the wife's idea. I like bright, shiny objects just as much as the next guy, so I got one, too.

We'll mark this as "solved", I guess. I just helped the wife figure out how to sync her phone on her Windows computer. I'll address my personal iTunes issues for Ubuntu at a later time. There's a lot of other stuff at a higher priority for me right now.

Thanks again!

---

### Post by huanix on 2008-11-16
Just as a follow up, iTunes 8 will not run in Ubuntu under wine (as of 1.1.8 ). I spent an ugly weekend trying to get it to work with limited success: 
[http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/](http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/)

The option that most people seem to be taking (for true sync) is running iTunes in a Windows XP virtualbox; there are still some bugs in the current Virtualbox (2.0.4) that should be fixed in a future release (2.10), in the mean time, this script will fix things:
[http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/](http://www.huanix.com/2008/11/03/fixing-usb-on-virtualbox-to-allow-iphone-sync-with-an-ubuntu-host-running-windows-xp/)

If you haven't purchased an iPhone yet, the Google G1 is looking like an exciting alternative - though I haven't tried it myself!

Edit: The bugs were successfully fixed in VirtualBox 2.0.6.

---

### Post by HotCupOfJava on 2008-11-16
You may also try running an older version of itunes under WINE. See [http://www.oldapps.com/itunes.htm](http://www.oldapps.com/itunes.htm)

That should work. I prefer WINE for running Windows applications.

---

### Post by fullerama on 2008-11-17
Huanix: I tried "urging" the wife towards a G1, but all her friends have iPhones, blah, blah, blah...after the warranty is up I'll jailbreak mine and have some fun.

HotCup: Yes, I had seen that solution. I have a lot going on right now, so I'm just going to wait on this phone sync issue. It's working pretty well for me now without any syncing.

Thanks for the updates.

---

### Post by huanix on 2008-11-17
i definitely encourage you guys to try with everything you've got to compile wine in a way that will run iTunes 8, but I don't think a simple solution will work. I've worked with most of the past 12 wine releases looking for things that did work, and those that didn't; all I ended up with was the ability to recognize that a device exists. if you want to get together and share ideas i'd be glad to meet you on a wiki or irc.

As I've been telling the internet for a week or so, the closest i could get was by using wine 1.0.1 with 5 maarten lankhorst patches (usb), and 1 ea durbin (itunes 8 ) patch. I could roll these patches into a script to run on the source, but no one has $inclined$ me in that direction. I believe the next logical step is to use a windows program called orca to strip the itunes 8 of its extra installation packages and still leave a usable program.

Here is iTunes 8 running under Wine showing a pod attached:
[http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/](http://www.huanix.com/2008/11/12/itunes-8-running-in-wine-recognizes-ipod/)

My thing is that i generally work in the direction that paypal contributions come from, and right now that direction is the virtualbox fix-  presumably because it works.

---

### Post by fullerama on 2008-11-17
After my initial attempt at a WINE installation of iTunes, I decided it's way beyond my ability right now. Still very much a nube in Ubuntu.

After I upgraded to 8.10 over the weekend, I do notice that Ubuntu now recognizes my iPhone when I plug in with USB. I was able to extract some photos from it, but that's all the time I had this morning to experiment.

Again, thanks to all you knowledgeable people for passing along the fruits of your labor.  It really means a lot to know you are out there ready to help.

I'm going to put the iTunes issue aside for now and try to get my audio sounding good. Wow, Ubuntu should really address that in an upcoming release. It's a real mess in there.

---

### Post by huanix on 2008-11-22
I posted the newest version of the script, it will now detect and install the correct version of Virtualbox-2.0 (by adding the repository to your sources) and create a correct /etc/fstab listing for usb - that will assign the usb to the vbox group thanks to tauchris.

[www.huanix.com/2008/11/22/itunes-8-running-in-virtualbox-20-allows-usb-sync-with-iphone-and-ipod-touch/](http://www.huanix.com/2008/11/22/itunes-8-running-in-virtualbox-20-allows-usb-sync-with-iphone-and-ipod-touch/)

---

### Post by huanix on 2008-12-04
For anyone that's still following this thread, I did set up a wiki to keep track of our ability to sync iPhones and iPods from within linux. It's here:

[http://www.huanix.com/sync-in-linux](http://www.huanix.com/sync-in-linux)

---

### Post by jpoRS on 2008-12-05
Thanks for the wiki huanix, I will definately keep it in mind for when this thread inevitably comes around again.

---

