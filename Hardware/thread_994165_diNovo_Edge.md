---
title: "diNovo Edge"
date: 2008-11-26
forum: Hardware
---

### Post by cybertron3 on 2008-11-26
Does anybody know if there is an actual hardware between the diNovo Edge ([http://www.logitech.com/index.cfm/keyboards/keyboard/devices/192&cl=us,en](http://www.logitech.com/index.cfm/keyboards/keyboard/devices/192&cl=us,en)) and the diNovo Edge Mac Edition ([http://www.logitech.com/index.cfm/keyboards/keyboard/devices/4741&cl=us,en)?](http://www.logitech.com/index.cfm/keyboards/keyboard/devices/4741&cl=us,en)?)  I really like the keyboards and want to get one for my ubuntu media computer.  I've been using an apple USB keyboard with my system for a while... and the Mac edition is cheaper (by $20) on Amazon so is there any reason I would want the non-mac version?

---

### Post by mzabatta on 2008-11-26
i too want to know about the dinovo edge and 8.10 does the touchpad and all of the extra hotkeys work? id like to know before i shell out the money for it

---

### Post by theotherphil on 2008-11-30
> **mzabatta said:**
> i too want to know about the dinovo edge and 8.10 does the touchpad and all of the extra hotkeys work? id like to know before i shell out the money for it

I've just installed Ubuntu 8.1 on my desktop machine (dual boot with Vista) and I can confirm that the Dinovo Edge does indeed work once you have paired with it. The touchpad works as does the volume slider/ mute button out of the box. The other buttons I believe will need mapping.

A word of warning though, I haven't managed to get it to connect automatically yet but I thought of this and had auto login enabled which got me to the desktop where I can configure the bluetooth easily from the gui.

---

### Post by cybertron3 on 2008-11-30
Is that the regular diNovo Edge, or the Mac edition?

---

### Post by Plexor on 2008-12-16
I have the diNovo Edge and Intrepid 8.10.  It works upon first connection but then drops after a period of inactivity.  Additionally, it does not start when turning the computer on.  Anyone know how to get this keyboard to have a solid connection?

---

### Post by icedfusion on 2008-12-17
I have a a DiNovo Edge also. My keyboard worked fine in the previous release but does not work now when it gest to the login screen (its fine at boot).

The last thing I want to do is have to get up from my chair and have to plug the dongle in and out before it starts working - I may as well have a wired one!

However, saying all of that there is a work around that I read about but have now lost the link to the chap who posted it:


modify the file:
```

sudo gedit /etc/default/bluetooth

```

and change the line:
```

HID2HCI_ENABLED=1

```
to
```

HID2HCI_ENABLED=0

```

Note that this will have the side affect of disabling the bluetooth stack/dongles on your PC. As I do not use them on this particular machine with my DiNovo then this does not bother me.

Hope this helps someone.

Cheers

ice.

---

### Post by injate on 2009-01-17
> **icedfusion said:**
> 
have to get up from my chair and have to plug the dongle in and out before it starts working
```

sudo gedit /etc/default/bluetooth

```

and change the line:
```

HID2HCI_ENABLED=1

```
to
```

HID2HCI_ENABLED=0

```

Note that this will have the side affect of disabling the bluetooth stack/dongles on your PC. As I do not use them on this particular machine with my DiNovo then this does not bother me.

Hope this helps someone.

I just upgraded to xubuntu 8.10 from 8.04 (or maybe 7.10...not sure) and had this exact same problem.  after every reboot I'd need to unplug the USB bluetooth dongle and plug it back in to get it to detect the wireless DiNovo keyboard correctly.  This config change fixed it.  It's actually better than my old ubuntu version which would take a while for the keyboard to 'wake up' or I'd have to power/off on the keyboard.

Thanks ice.

---

### Post by yt_l9 on 2009-01-18
I actually just go a dinovo edge (pc edition) and I do love it but I'm having some trouble hotmapping the keys and I've found that using my turtle beach soundcard isn't as easy as I'd hoped.  The card is fine but I can't control the volume with that swipe adjuster on the keyboard.  What did you use to map your keyboard?  I've only been on linux for 6 months so I'm still relatively new to all this.  To circumnavigate the problem with login screen I just uninstalled Bluez.  You can edit what loads automatically if you'd like but I figured I'm not using bluetooth anyways so there isn't much of a loss for me.  The only other issue I've had is with the play/pause button.  I'll only play and not pause for me.  Other than those few issues I love this thing.  The range is incredible too.  I'm about 15 feet away and have yet to have a missed key that was the keyboards fault.

---

### Post by Ashrael on 2009-01-27
Does anybody know if there is a fix for the zoom keys and the fn activated keys? 

This seems to be a fix : 

[http://bugzilla.kernel.org/attachment.cgi?id=10848&action=edit](http://bugzilla.kernel.org/attachment.cgi?id=10848&action=edit)

but I have not had the chance to try it yet...

TIA!

---

### Post by Gp. on 2009-03-04
How is that patch applied>? (for the noob)

---

### Post by rcarlton on 2009-03-04
> **injate said:**
> I just upgraded to xubuntu 8.10 from 8.04 (or maybe 7.10...not sure) and had this exact same problem.  after every reboot I'd need to unplug the USB bluetooth dongle and plug it back in to get it to detect the wireless DiNovo keyboard correctly.  This config change fixed it.  It's actually better than my old ubuntu version which would take a while for the keyboard to 'wake up' or I'd have to power/off on the keyboard.

Thanks ice.

I have upgraded just like this and this solution does NOT work.  I have been looking for a solution to this for 2 weeks now since I upgraded.  This is a step backwards in functionality.

---

### Post by Oncle Ben on 2009-03-29
> **rcarlton said:**
> I have upgraded just like this and this solution does NOT work.

It works for me too - don't know why it doesn't for you, rcarlton.

Thanks, ice !
Ben

---

### Post by bellamr on 2009-08-04
> **icedfusion said:**
> I have a a DiNovo Edge also. My keyboard worked fine in the previous release but does not work now when it gest to the login screen (its fine at boot).

The last thing I want to do is have to get up from my chair and have to plug the dongle in and out before it starts working - I may as well have a wired one!

However, saying all of that there is a work around that I read about but have now lost the link to the chap who posted it:


modify the file:
```

sudo gedit /etc/default/bluetooth

```and change the line:
```

HID2HCI_ENABLED=1

```to
```

HID2HCI_ENABLED=0

```Note that this will have the side affect of disabling the bluetooth stack/dongles on your PC. As I do not use them on this particular machine with my DiNovo then this does not bother me.

Hope this helps someone.

Cheers

ice.

Thanks, your suggestion worked for me!

---

### Post by Chicanob12 on 2010-01-17
Has anybody bought the Mac Edition keyboard?  Does anyone know if it would work for Ubuntu Karmic 9.10.  Just wondering since the Mac edition is a lot cheaper than the regular one.  It looks the same, but I just want to be sure before I drop money on this.  Thanks in advance

Update:  I went ahead and bought the Dinovo Mac Edition and it works very well and right away on Ubuntu Karmic.  I have not turned off my pc to see if I can log in or anything but I'm sure i'll have the same difficulties as everyone else... lol.

---

### Post by Xobb on 2010-04-20
> **Chicanob12 said:**
> Has anybody bought the Mac Edition keyboard?  Does anyone know if it would work for Ubuntu Karmic 9.10.  Just wondering since the Mac edition is a lot cheaper than the regular one.  It looks the same, but I just want to be sure before I drop money on this.  Thanks in advance

Update:  I went ahead and bought the Dinovo Mac Edition and it works very well and right away on Ubuntu Karmic.  I have not turned off my pc to see if I can log in or anything but I'm sure i'll have the same difficulties as everyone else... lol.

I've got mac edition and it worked perfectly for me on Karmic. I even could log in. 

Is there any way to change the keyboard layout when connecting bluetooth keyboard. I switch the alt/win keys positions in keyboard settings, but would like to know if there is some way to automate it. If the input is from regular keyboard i want default settings, but when using dinovo edge the alt/win keys switch.

---

