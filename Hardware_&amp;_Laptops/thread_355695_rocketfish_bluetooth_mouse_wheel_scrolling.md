---
title: "rocketfish bluetooth mouse wheel scrolling"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by sargeras on 2007-02-07
Hi everyone,

I just picked up a Rocketfish Bluetooth USB mouse.  It has 3 buttons + the scroll option, but scrolling does not work.  I have tried setting the Z-axis mapping, however, it did not help.  I have searched this forum and tried many other approaches, but to no avail.  A little more information:  all other mouse buttons work (left, right, center click), I am not using a bluetooth connection (there is a USB/bluetooth adapter that comes with it), I am on an alienware 5700mx laptop, below is the mouse configuration section of my current xorg.conf.  One final piece of information:  if I run "xev", the buttons all provide a "key code", but not the scrolling.  I suspect that the wheel "action" is not even being detected, thereby preventing button mapping from being successful

Any help would be much appreciated, thanks.

xorg.conf
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "6 7"
EndSection

---

### Post by InvaderSteve on 2007-02-22
I'm experiencing the same problem.  Any leads would be greatly appreciated.

---

### Post by Alex&amp;Linux on 2007-07-22
Me too.
Really sweet keyboard!
I dont think messing with X11's input section will help with this, as it seems the problem may be related to the actual bluetooth USB adapter, and the lack of driver for it!

Ive sent a letter to Rocket fish about this, and feel free to do the same!

---

### Post by BrooksOfSheffield on 2007-08-14
I was having the same problems.  Luckily, I actually have 2 different bluetooth dongles - the one that came with the Rocketfish keyboard/mouse combo, and one that I had purchased separately a few months ago (just a generic iogear dongle from Walmart).

When trying to get the scrollwheel going on the Rocketfish dongle, the only way I could get the keyboard and mouse to associate at all was to hold down the button on the end of the dongle after putting both keyboard and mouse into discovery mode.  They would associate with the dongle and I'd have basic keyboard functionality and 2-button mouse functionality.

No amount of hcitool or hidd dinking could get my scrollwheel to register.  Tried XEV, nothing.

Then, I had this brainstorm and swapped out bluetooth adapters.  Using the non-rocketfish adapter, all I had to do was:

sudo gedit /etc/bluetooth/hcid.conf

Added:

```
device mac_address_here {
     name "Rocketfish Wireless Keyboard";
     auth enable;
     encrypt enable;
 }
 
 device mac_address_here {
     name "Rocketfish Mouse";
 }
```

sudo gedit /etc/default/bluetooth

and edited the HIDD section to be:

```
HIDD_ENABLED=1
HIDD_OPTIONS="--master --connect mac_address_for_keyboard --connect mac_address_for_mouse --server"
```

Voila!  Scrollwheel automagically works.

HTH.

---

### Post by SpectralDesign on 2007-08-28
Brooks,

that certainly looks easy, but how do you get the device MAC addresses?

As above, I get nothing from such inquiries as:

hcitool scan
sudo hidd --search
hcitool dev

lsusb shows three lines related to broadcom low-cost bluetooth, but still no MACs...

Any tips appreciated!

---

### Post by BrooksOfSheffield on 2007-09-03
Much to my shame, I must admit - I booted into XP and got the MAC from the hardware properties.

I'm sure with enough work and/or research I could've gotten it to give me the MAC addresses from a terminal, but I was lazy and frustrated.

---

### Post by cantscroll on 2007-11-22
So does the above solution work with the included dongle or is a different dongle the only way to go? If so, what is the difference between these dongles? I've found the scroll wheel to work fine with the included dongle in Windows, and with the built in bluetooth on a Mac.

PS Did the dongle you used have Linux drivers?

---

### Post by BrooksOfSheffield on 2007-11-27
With the rocketfish dongle I could get basic keyboard and mouse functionality.  No scrollwheel and no multimedia buttons.  Using an IOGear GBU220 (which apparently has drivers builtin to Feisty and Gutsy at least) the above fixes made the extra keyboard keys and the scrollwheel work.

Those fixes didn't make any of the extra features work with the rocketfish dongle.  Which I've discovered to be a huge annoyance when I wanna boot into windows.  Have to plug in a wired keyboard to access the grub menu, because the IOGear dongle doesn't associate with keyboard at power-on like the Rocketfish one does.  :(

---

### Post by moyofalaye on 2007-11-29
Man thanks for the help. Please please please, if you can find away for the rocketfish dongle to work (the scroll wheel and media features) please let us know. 

Im guessing you also picked up the keyboard form bestbuy during blackfriday. 

thanks again.

---

### Post by BrooksOfSheffield on 2007-11-29
Actually, I picked it up back in August when it was on sale for $50...  it's part of my HTPC rig, so having keyboard and mouse from the couch is pretty essential.

Periodically I switch back to the Rocketfish dongle and fight with it some.  So if I get any progress, I'll be sure to post about it.

---

### Post by moyofalaye on 2007-12-02
if this helps i figured out that the rocket fish keyboard needs to specifically use the widcomm bluetooth stack for the scrolling and the media keys to work.

I hope this helps

---

### Post by guitarguy987 on 2007-12-03
> **moyofalaye said:**
> if this helps i figured out that the rocket fish keyboard needs to specifically use the widcomm bluetooth stack for the scrolling and the media keys to work.

I hope this helps

Good to know, but is it working in Gutsy?  I can't seem to find anything about widcomm bt stack for Gutsy in these forums or anywhere else...  Looks like I might have to go out and get another adapter...

Thanks!

---

### Post by moyofalaye on 2007-12-06
I said that, so that the people who know how to do these things could help us who dont know.

I dont know if ubunto supports the widcom bluetooh stack. or even how to install it.

---

### Post by BrooksOfSheffield on 2007-12-07
After extensive searching for the past few months I've given up (at least temporarily) on a working widcomm stack in linux.  Broadcom has said that they're working on a linux version, but no telling how long ago that info was added to their website and whether or not it's accurate.

---

### Post by moyofalaye on 2007-12-09
Man me too :( , i have been trying to find anything on widcomm for linux. oh well.

---

### Post by BrooksOfSheffield on 2007-12-11
Right now the only real hope I have is that enough people get bluetooth keyboard/mouse combos that maybe in Hardy they work on getting a widcomm stack operating.

If there was enough need, there'd be drivers.  I mean...  sheesh.  I could make my wiimote work as a pointing device.  Kind of.


******
EDIT
******

Using the Rocketfish dongle, I'm able to manually get everything working.  If I can get it to automatically work, I'll post a howto!

---

### Post by moyofalaye on 2007-12-19
Man thanks. I will await.

---

### Post by fugazi41 on 2007-12-21
> **BrooksOfSheffield said:**
> Using the Rocketfish dongle, I'm able to manually get everything working.  If I can get it to automatically work, I'll post a howto!

I have that same keybord/mouse/dongle. It works but not the mouse wheel  scrooling.
Can you gives us some hints about you manual setup? Maybe we could help to automate it!

regards,

fugazi

---

### Post by MgNate on 2008-01-01
Well i bought my Rocketfish Mouse and Keyboard of black friday also! =] Cousin bought it for me since i waited with her ALL night. 

The thing about the stack is my devices do stack in linux, i used my bluetooth headset to test it out and it connected to my linux machine.

 I've been using windows for a few months until today because I've been playing so much WoW. But now i want to go with Linux. Any help would be great! Don't give up guys!

---

### Post by sacredmonk on 2008-01-02
The problem isn't the xorg.conf file. It's just that the mouse isn't pairing with your device. You get the same problem if you use the mouse unpaired in windows. The mouse gets recognized, and it works because it's automatically made to function with your dongle, without the need to pair. By pairing it however you ensure that it gets correctly read by the os. So basically, all you need to do is pair your mouse! Unfortunately, you will have to do this everytime at boot, because the pairing gets lost when you restart. The dongle may be unresponsive when you first boot into ubuntu, so you will have to reset the dongle with "sudo hciconfig hci0 reset". Once it's reset it will respond to the "sudo hidd --search" command. Of course, in order for it to find and automatically pair your mouse it has to be in discovery mode. You MUST execute the command immediately after you reset your dongle however, because if you do not, the dongle will once again become unresponsive, and you wont be able to pair the device unless you reset it again. After you finally do get the device paired, your wheel will work. I read online somewhere that you can set it to connect to the device on boot by editing a certain file, but I did not try it, and have forgotten where I read it. If I come across it again, I'll check it out and see if it works. For now I don't mind pairing the device manually as long as I get to use the scroll wheel. I can't live without it.!

---

### Post by BrooksOfSheffield on 2008-01-04
After much tearing of hair and gnashing of teeth, I've gone back to my IOGear dongle.  

To manually make it work, like previous poster said, all you have to do is 

sudo hciconfig hci0 reset

put your mouse/keyboard into discoverable mode

sudo hidd --search

allegedly you can do [this]("http://ubuntuforums.org/showthread.php?t=586105") to make it work (the only thing they've added is putting hidp into /etc/modules) but it doesn't work for me.

---

### Post by moyofalaye on 2008-01-13
thanks man. Even though im posting this late.

---

### Post by Daga on 2008-02-08
> **BrooksOfSheffield said:**
> To manually make it work, like previous poster said, all you have to do is 

sudo hciconfig hci0 reset

put your mouse/keyboard into discoverable mode

sudo hidd --search

I tend not to talk on these forums because my distro of choice is Slackware, but that worked great! Sorry the reply is a month late or so...

With only one keyboard, I typed "hciconfig hci0 reset;sleep 10;hidd --search" (This is why I'm a bad Ubuntu user. I love to be able to be root occasionally. If you are on Ubuntu, you may need to adjust that line a little). It gave me ten seconds to hit the "connect" buttons on the keyboard and mouse. Didn't even have to restart Xorg for the media keys and scroll wheel to work.

Thanks!

---

### Post by BrooksOfSheffield on 2008-02-11
> **Daga said:**
> I tend not to talk on these forums because my distro of choice is Slackware, but that worked great! Sorry the reply is a month late or so...

With only one keyboard, I typed "hciconfig hci0 reset;sleep 10;hidd --search" (This is why I'm a bad Ubuntu user. I love to be able to be root occasionally. If you are on Ubuntu, you may need to adjust that line a little). It gave me ten seconds to hit the "connect" buttons on the keyboard and mouse. Didn't even have to restart Xorg for the media keys and scroll wheel to work.


The only problem is that you have to do that on every boot.  At least with *buntu.  Not sure about Slackware.

---

### Post by zonkytonk on 2008-05-20
so uh, anyone able to suggest how to get ubuntu (hardy) to recognize the rocketfish dongle at all? (ubuntu newb here)

---

### Post by Endolith on 2008-05-20
> **zonkytonk said:**
> so uh, anyone able to suggest how to get ubuntu (hardy) to recognize the rocketfish dongle at all? (ubuntu newb here)

My Rocketfish keyboard has worked just fine with the USB dongle since before Hardy.  My mouse worked, too, but moved erratically last time I tried it.  I've been using a different wireless mouse that I like better.

---

### Post by ectospasm on 2008-05-21
I got this working in Hardy with "sudo hciconfig hci0 reset;sleep 10; sudo hidd --search".  Any way of automating this, either through an init script, or...?  I think it could at least go into rc.local, except for the fact that you've got to time it with the connect buttons on the mouse and keyboard.

Anyone know how we could force the keyboard and mouse to go into pairing mode, through some signal sent through the dongle?

---

### Post by Endolith on 2008-05-21
> **ectospasm said:**
> Anyone know how we could force the keyboard and mouse to go into pairing mode, through some signal sent through the dongle?

Aren't there instructions on how to do that by pressing the button on the dongle?  Maybe there are different models being talked about here.

---

### Post by ectospasm on 2008-05-22
> **Endolith said:**
> Aren't there instructions on how to do that by pressing the button on the dongle?  Maybe there are different models being talked about here.

That would require user intervention, which makes automatic detection impossible, and hence the init script (or whatever) would fail.

Incidentally, I do have a pairing button on the dongle, and on the mouse and keyboard, but if I have to press those to get them paired, it's a PITA, IMO.

---

### Post by Endolith on 2008-05-22
> **ectospasm said:**
> Incidentally, I do have a pairing button on the dongle, and on the mouse and keyboard, but if I have to press those to get them paired, it's a PITA, IMO.

Yes, those are the right buttons.  I only had to pair them once, and I can use the keyboard with Windows, Linux, GRUB, and so on without any configuration.

---

### Post by BrooksOfSheffield on 2008-06-08
> **Endolith said:**
> Yes, those are the right buttons.  I only had to pair them once, and I can use the keyboard with Windows, Linux, GRUB, and so on without any configuration.

But do your multimedia keys and scrollwheel work?  That's the real issue that everyone is having.  It's no problem to get basic functionality, but life without scrollwheel is life not worth living.

For the record:  I've upgraded to Hardy and still no automatic love for the Rocketfish dongle.

---

### Post by stoomaroo on 2008-07-20
Quick one bud....how did you pull the MAC address out of your Windows config? (Control panel, etc....)

---

### Post by Endolith on 2008-07-20
> **BrooksOfSheffield said:**
> But do your multimedia keys and scrollwheel work?  That's the real issue that everyone is having.  It's no problem to get basic functionality, but life without scrollwheel is life not worth living.

I don't know; I only use the keyboard.  I rarely use the computer so it's not something I ever bothered to figure out.

---

### Post by BrooksOfSheffield on 2008-07-21
> **stoomaroo said:**
> Quick one bud....how did you pull the MAC address out of your Windows config? (Control panel, etc....)

After you set up the keyboard and mouse in Windows, click the bluetooth icon in your system tray, do Show Bluetooth Devices.  Your keyboard and mouse will show up in the resulting window.  Click one and select properties, gives you the MAC of that device.

If you're running Hardy and have a different adapter than the rf-btapdt that came with the set, you can put the devices into discoverable mode and add them through the tray icon in Gnome.  Hardy has definitely made some leaps forward in bluetooth usability.  Now I'm hoping they get drivers for the rocketfish adapter (so that it doesn't have to be manually started whenever it's used).

---

