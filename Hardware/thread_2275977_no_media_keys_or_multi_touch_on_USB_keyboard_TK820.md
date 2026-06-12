---
title: "no media keys or multi touch on USB keyboard TK820"
date: 2015-04-29
forum: Hardware
---

### Post by theonlyandy on 2015-04-29
Ahoj all together.

I'm a proud owner of a Logitech TK820 keyboard with multi touch pad &#8211; or I was?

After buying it it worked out of the box, also multitouch, which is implemented nicely in Gnome 3.

At some point it stopped working, though:
**My multimedia keys wouldn't work any more, also multi touch is limited to 2 fingers for scrolling up and down.**

I found some related forum posts, but none came close to my problem.

*showkey* doesn't recognize any keypress for the multimedia keys.

And in */proc/bus/input/devices* I'm having **2 entries** for that keyboard:

```
I: Bus=0003 Vendor=046d Product=4102 Version=0111
N: Name="Logitech TK820"
H: Handlers=sysrq kbd event5
[&#8230;]
I: Bus=0003 Vendor=046d Product=4102 Version=0111
N: Name="Logitech Wireless All-in-One Keyboard TK820"
H: Handlers=mouse3 event18
```

Additionally I'm seeing weird pointer jumps which I didn't have before and sometimes a key gets stuck (not physically of course).

Any help would be appreciated.

---

### Post by dino99 on 2015-04-29
is it with upstart or systemd ?  dmesg/syslog/xorg.0.log might have logged something about it i suppose

---

### Post by theonlyandy on 2015-04-29
Thx, despite some warning I found this:

> (EE) Logitech Wireless All-in-One Keyboard TK820: Read error 19

---

### Post by trag on 2015-05-04
I have used Logitech BT keyboards with the same sketchy results,things improved after I installed their unified driver.
 [COLOR=rgba(0, 0, 0, 0.8)][FONT=Roboto Slab]sudo add-apt-repository ppa:daniel.pavel/solaar[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.8)][FONT=Roboto Slab]sudo apt-get update && sudo apt-get install solaar[/FONT][/COLOR]

[COLOR=rgba(0, 0, 0, 0.8)][FONT=Roboto Slab]Those using GNOME Shell should swap the last command for:[/FONT][/COLOR]
[COLOR=rgba(0, 0, 0, 0.8)][FONT=Roboto Slab]
sudo apt-get update && sudo apt-get install solaar-gnome3
Good luck
tragic[/FONT][/COLOR]

---

### Post by theonlyandy on 2015-05-04
Thanks guys.

I installed solaar, but I don't think it's coming with any drivers, no?
It's just a managing software.

Nothing changed, despite rebooting and re-pairing my keyboard. Still no media keys or multi touch.

dmesg is giving me:
> [  104.560733] input: Logitech TK820 as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.5/4-1.5.4/4-1.5.4:1.2/0003:046D:C52B.0003/0003:046D:4102.0006/input/input20
[  104.565250] logitech-hidpp-device 0003:046D:4102.0006: input,hidraw2: USB HID v1.11 Keyboard [Logitech TK820] on usb-0000:00:1d.0-1.5.4:1
[  112.467847] logitech-hidpp-device 0003:046D:4102.0006: HID++ 2.0 device connected.
[  112.548112] input: Logitech Wireless All-in-One Keyboard TK820 as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.5/4-1.5.4/4-1.5.4:1.2/0003:046D:C52B.0003/0003:046D:4102.0006/input/input21
b

And it's systemd btw.

Thanks for more tips.

---

### Post by theonlyandy on 2015-06-23
So &#8211; suddenly it is working again. Maybe an update fixed it?

I only have 1 entry for my keyboard now:

```
I: Bus=0003 Vendor=046d Product=4102 Version=0111
N: Name="Logitech TK820"
&#8230;
H: Handlers=sysrq kbd mouse1 event5 
```

So I'm happy, sorry I can't provide any more insights.

---

### Post by theonlyandy on 2015-09-30
Unbelievable!

On [my Stack overflow question]("http://askubuntu.com/questions/615869/media-keys-and-multitouch-not-working-with-tk820") somebody found out a reason for the missing multitouch:

**Fn+Left Click toggles Multitouch on/off.**

For the missing media keys I still don't know the reason.

---

