---
title: "ATI and GDM problem."
date: 2008-11-19
forum: General Help
---

### Post by fiendishfish on 2008-11-19
Hello,

Graphics Card = Radeon 9600
Monitor = IIYAMA 19"

Here it goes... I Installed the ' ATI Catalyst™ 8.11 Proprietary Linux x86 Display Driver' on my box and followed the installation instructions at:

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat811-inst.pdf]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat811-inst.pdf")

So the installation went well and it installed all the drivers, and then the guide asked me to run

 ```
/usr/X11R6/bin/aticonfig --initial
```

Which edits the xorg file etc to make the drivers work, I presume, so then I rebooted, and everything looks ok, but when GDM loads up, the monitor goes on standby and I can't do nothing, especially as my VT hotkeys don't work for some reason.

Can anyone think of a possible solution to this, I hear that if you edit the driver to 'vesa' in xorg it'll bypass the ati drivers, but how do I access xorg with a screen on standby, shall I run a liveCD?

I still would like to know if anyone knows how to fix the issue opposed to bypassing it. By the way I'm using VGA not DVI.


An example of someone ELSE who reported the bug here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/272877](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/272877)
Thanks

-fiendishfish

---

### Post by nikgare on 2008-11-19
Why don't you try what's sugested in the bug report?


> You can change the driver to "vesa by getting to a console by pressing Ctrl+Alt+F1 (or is it Alt+F1? I can't remember). Then shut down GDM by typing:

sudo /etc/init.d/gdm stop

Then you edit the file /etc/X11/xorg.conf with for example 'nano' by typing:

sudo nano /etc/X11/xorg.conf

There should be a "Device"-section that looks like this (there might be more lines of text between "Section" and "EndSection", but mine just looks like this when using the Intrepid Alpha 6 Live CD):

Section "Device"
 Identifier "Configured Video Device"
EndSection

In this section add a line with the text "Driver "vesa"". Doing so with the example above would make it look like this:

Section "Device"
 Identifier "Configured Video Device"
 Driver "vesa"
EndSection

Now start GDM again by typing:

sudo /etc/init.d/gdm start


---

### Post by fiendishfish on 2008-11-19
Sigh... Because that ceases to solve the problem, that will allow me to access X and such like, but won't allow me to use my graphics card drivers, I'm now on the shell and looking at all sorts of weird messages.

```
(WW) fglrx: No matching device section for instance (BusID PCI:1:0:1) found
```

I get that in GDM's log ^

Although if I add 1:0:1 as the busID in xorg.conf it gives the same message out, but for 1:0:0 instead, 1:0:1 comes up as secondary in dmesg, what does this mean?

Thanks for your response anyway dude!

-fiendishfish

---

### Post by nikgare on 2008-11-19
Why not install via Synaptic? - the package you need is xorg-driver-fglrx

---

