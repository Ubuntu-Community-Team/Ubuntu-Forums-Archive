---
title: "[PARTIAL-SOLUTION] HP/Compaq Laptops (and others) with Changing MAC Address"
date: 2010-02-07
forum: Hardware
---

### Post by SteveDhalai on 2010-02-07
Hey,

This is a simple tutorial to provide a partial fix for people who are having problems with HP/Compaq Laptops like me.

The laptops look like this:
[img]http://h10010.www1.hp.com/wwpc/images/emea/compaq-presario-f700-notebook-pc_400x400.jpg[/img]

Often have the same stickers, AMD Processors and Nvidia graphics cards along with the same outer shell. They can have either HP or Compaq Branding.

**About the Problem**
These laptops seem to have a design flaw which after around a year (ironically when the guarantee is up) they start to overheat. This causes to a lot of problems including sometimes random restarts when the laptop gets too hot. The worst problem I've had so far is that something happens to the Ethernet Port and/or motherboard which **makes the Ethernet card stop giving the OS a Mac Address, causing you to have an ever-changing mac in linux**

**Why am I posting this?**
I've had this problem, **it causes the ethernet card to be rendered as "not working" in windows**. There also seems to be a lack of information about this on the net yet there are **a lot of forum topics with people with this problem, with no solution posted, this includes here on ubuntuforums**

**The Solution**
**This is only a partial solution, not an absolute fix**

1. The first thing you're going to notice is that Ubuntu makes up a random mac address but because of this you get a new instance of "Auto Eth" therefore everytime you boot up you're connected to Auto Etc x*number of starts eg Auto Eth 20. For some people this would be fine but as I lived in halls I can't have a changing mac address and some people wouldn't like one either.

2. You'll find in /etc/udev/rules.d/70-persistent-net.rules that all of these are listed with Random mac addresses. We need something persistent eg we need it to ALWAYS be Auto Eth 0 so we can edit the mac address later. The solution to this is to:

Edit /etc/rc.local by typing this in terminal
```
sudo gedit /etc/rc.local
```

Add the following 2 lines to the file (anywhere before exit 0)
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules
sudo touch /etc/udev/rules.d/70-persistent-net.rules
```

This will ensure that we always have eth0 as the connection (ubuntu will recreate the file on deletion starting the cycle from fresh eg instead of eth24 we always have eth0).

3. We still have the problem of a random Mac Address and for this I have only a part solution.

Somewhere (perhaps in your documents) you need to make 2 "Launchers" or "Shortcuts" the first one doing this:
```
sudo ifconfig eth0 down hw ether THEMACADDRESSYOUWANT 
```

And the second one doing this:
```
sudo ifconfig eth0 up
```

You need easy access to them, this is up to you, you can put them on the desktop or in a dock if you like. Personally I keep them next to the clock panel with some icons I found. Make sure you know which one is which, label the first with 1 and the second with 2.

4.Everytime you login you need to press these 2 Launchers. First press the first one and wait until you're told you're disconnected, then press the second one. You will now be connected to the internet and using the Mac Address you wanted/need to be using.

**Hope this has helped somebody**

---

