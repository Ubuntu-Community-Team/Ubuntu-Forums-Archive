---
title: "Remote control on Gutsy"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by zhimsel on 2007-12-31
I'm looking to buy a remote control to control music, video, etc (possibly with Amarok or Elisa). Does anyone know of any good remotes that work stably with Linux/Ubuntu? I would like to make sure before I buy anything.

---

### Post by cyrus_the_virus on 2008-01-04
Hi,

My brother has one of these remotes that are interpreted as an USB mouse/keyboard by the os, so it works out of the box. I would recommend one of those.  You can control the mouse with it and it as some keys like play/pause etc  I've tested it in ubuntu 7.10 and it works out of the box. I don't know the brand of it (I think it's brandless). My brother got it from ebay in china. 

I use a pinnacle PCTV remote control with the receiver connected to the serial port with LIRC.
It took a while to get it working (I would not recommend this if your new to linux) but with lirc you have little bit more freedom in assigning keys to functions. So some keys work differently in different applications.

Good luck!
Marty

---

### Post by zhimsel on 2008-01-04
> **cyrus_the_virus said:**
> Hi,

My brother has one of these remotes that are interpreted as an USB mouse/keyboard by the os, so it works out of the box. I would recommend one of those.  You can control the mouse with it and it as some keys like play/pause etc  I've tested it in ubuntu 7.10 and it works out of the box. I don't know the brand of it (I think it's brandless). My brother got it from ebay in china.
Is there any name I could search for it by? Like a model number or something?

> **cyrus_the_virus said:**
> I use a pinnacle PCTV remote control with the receiver connected to the serial port with LIRC.
It took a while to get it working (I would not recommend this if your new to linux) but with lirc you have little bit more freedom in assigning keys to functions. So some keys work differently in different applications.
I'm not new to Linux, but I wanted to avoid having to configure LIRC. I hear it can be a pain. If necessary, I would use it. Is there a USB version of this remote? I know LIRC is iffy with USB, but I don't remember if my motherboard has a serial port. (I'm not at home right now).

---

### Post by cyrus_the_virus on 2008-01-05
Hi,

This is the one my brother has:
[http://cgi.ebay.com/PC-Windows-Media-Player-Remote-Control-USB-IR-Receiver_W0QQitemZ230205035895QQihZ013QQcategoryZ51086QQssPageNameZWDVWQQrdZ1QQcmdZViewItem]("http://cgi.ebay.com/PC-Windows-Media-Player-Remote-Control-USB-IR-Receiver_W0QQitemZ230205035895QQihZ013QQcategoryZ51086QQssPageNameZWDVWQQrdZ1QQcmdZViewItem")
I searched for *'ir media control'* on ebay
The description says it only works with windows but that's not true. As I said before, it behaves like an usb mouse/keyboard so you can program the keys in System->preferences->Keyboard shortcuts.The big round button will let you control the mouse.

I would recommend one of these. Setting up lirc is not easy and by using this one you can avoid that.

Good luck
Marty

---

### Post by Salazar666 on 2008-02-21
Hi,

My problem is a little bit different. I already have a pinnacle PCTV remote, but my new PC doesn't have a serial port. So I'm not sure whether I should buy a USB/Serial converter or a "ir media control" that zhimsel mentioned.

@zhimsel: if the remote of your brother acts like a keyboard/mouse, which keys are assigned to the IR-buttons? Is it like "you press the <Play>-button on your remote control and it sends <Ctrl>-<P> to the (whole) Desktop"? Or does it send commands like the media keys on modern keyboards (something like "XF86AudioPlay"?

---

