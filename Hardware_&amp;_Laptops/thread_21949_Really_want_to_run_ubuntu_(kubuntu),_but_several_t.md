---
title: "Really want to run ubuntu (kubuntu), but several things I need a hand with."
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by madscience on 2005-03-24
I have a relatively new laptop (purchased Dec 2004).  It's a [Toshiba M30-001](http://www.toshiba.ca/web/specifications.grp?lg=en&section=1&group=1&product=2390&part=2652).  I bought this laptop knowing that linux might be a little tricky to get running, but I still have high hopes.  There are several good guides to installing linux on various Toshiba M30 models, but none for my specific model, and some of the fixes don't seem to help out on this machine.  Specifically, the problems I'm still having, and the fixes I've tried (unsucessfully) follow:

GRUB hanging at "GRUB" prompt:  I'm stumped as to what's causing this.  I tried passing pci=noacpi to the kernel, as was suggested on IRC, it didn't help.  At this time I'm using LILO with the "compact" option enabled, and this seems to be acceptable.  This one's a "Does anyone have a clue?" question, more than anything else.

Keyboard "bouncing" and delayed input:  I've tried passing psmouse.rate=40 and psmouse.proto=imps2 to the kernel at boot, as others with this issue on Toshiba indicate it's a problem with the synaptics touchpad.  This didn't do anything.
I've set Option "XkbDisable" "on" in xorg.conf and this fixed the "bouncing" problem, but there is still occasionally a delay when inputting using the keyboard.  Any other suggestions would be more than welcome, as this is one of two deal-breakers for running linux on this machine.  I'm aware that recompiling the kernel after tweaking some settings may work, but this seems like shooting a fly with an elephant gun.  If no one can come up with an easier solution, I may go ahead and do it, but only if I can get everything else running.

WiFi connection dropping out often, and not seeing all available networks:  As noted in the link above, this machine has an intel pro/wireless 2200bg miniPCI card.  It does work OOB, but I've noticed that the connection drops frequently and unexpectedly.  Usually a "ifdown eth0" followed by "ifup eth0" fixes it, but not always.  As noted in other posts, I've tried installing all the latest updates, but it's still happening.  Also, using kde wireless, not all available networks are listed.  In my apartment building, there are 7 wireless networks seen when in windows.  Two of these are unencryted, unprotected networks.  One of these is mine, with MAC address filtering.  Occasionally, ubuntu will only see one or another of the unencrypted networks, for no apparent reason.  This is very annoying, because my network is 802.11g, with a fileserver I need access to.  The other unencrypted network (which it tends to find more often) is my neighbors, and is only a 802.11b

Hibernate, and S3:  This is the other deal-breaker on this machine.  I had high hopes that at least hibernate would work, and in fact I did manage to get the machine to hibernate and wake up once.  Every other time I've tried hibernate, the machine will seem to freeze with a small (640x480ish?) gray square in the middle of the LCD when I try to wake it up.  Hibernate also seems to take about 4 to 5 times longer to shut the machine down than it does in windows.  Is there any configuration I can try for this?  Standby and suspend for the machine don't seem to work *at all*, and if anyone has suggestions, fire away.  I don't consider standby or suspend critical, however.  I've noticed people blaming the nvidia driver for this on other sites, and if it came down to it, I'd choose 3d acceleration.

I know that's a lot to look at, and I'm aware of the following sites and have looked at them previously:

[http://www.uni-koblenz.de/~tenshi/tosh/](http://www.uni-koblenz.de/~tenshi/tosh/)
[http://w3.ualg.pt/~paneves/Linux%20on%20a%20Toshiba%20M30%20Laptop_en.html](http://w3.ualg.pt/~paneves/Linux%20on%20a%20Toshiba%20M30%20Laptop_en.html)
[http://www.jeanpierre.de/m30/](http://www.jeanpierre.de/m30/)
[http://www.marcsaric.de/m30_linux1.html](http://www.marcsaric.de/m30_linux1.html)
[http://julian.coccia.com/blog/index.php?p=68&more=1](http://julian.coccia.com/blog/index.php?p=68&more=1)
[http://www.kraus.tk/installnotes/toshiba-m30/toshiba-m30.htm](http://www.kraus.tk/installnotes/toshiba-m30/toshiba-m30.htm)

At this point, I've fled back to windows.  If anyone can give me a few pointers, I'd really appreciate it.  The only other question I have for everyone is about an external Hauppage WinTV USB2 tuner I have and whether it's possible to get running in linux.

---

### Post by jerome bettis on 2005-03-26
the ipw2200 card does that.  it's a driver issue, and they're working on fixing it.  i wrote a little script that takes down the network, unloads / reloads the module and brings the network back up.  i put an icon for this on my panel so it only takes a second to get it back.  normally this doesn't happen very often at all, but some days it happens quite frequently.

i wouldn't worry about suspend to ram yet.  it's unlikely that you'll get it working, but if you check the wiki there's a few things you can try.  acpi is still under active development.  try again in about 3-6 months.

for hibernate, you can use software suspend 2:  [http://swsusp.sf.net](http://swsusp.sf.net) .  it works great for me every time, and it's just about as fast as windows hibernate.  however, you will have to recompile the kernel after applying their patch.

the usb tv tuner should work i think.

---

