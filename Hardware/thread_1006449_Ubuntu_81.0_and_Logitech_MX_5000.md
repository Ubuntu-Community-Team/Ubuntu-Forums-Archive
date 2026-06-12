---
title: "Ubuntu 81.0 and Logitech MX 5000"
date: 2008-12-09
forum: Hardware
---

### Post by nocknock on 2008-12-09
Hi friends.

I'd hope that with the new version of Ubuntu, it's solve the follows problem with keyboard and mouse (Logitech MX 5000). The problem:

No keyboard or mouse on boot Logitech MX 5000 Bluetooth.

I am having to unplug and replug my bluetooth USB stick that gives the signal to my Logitech keyboard and mouse each time i want to login to ubuntu.

I need help.

Thank you.

---

### Post by Skerit on 2008-12-13
I'd love to see this annoying bluetooth issue resolved.
I've bought this keyboard a year ago and still have to do this awkward workaround every bootup, it's ridiculous!

---

### Post by mewrei on 2009-01-14
Problem pertains to a setting in the Bluez config, specifically the HID2HCI setting.  Apparently the Bluetooth dongle included with the MX5000 isn't one of the supported models.

Easiest way to fix this is

```
gksudo gedit /etc/default/bluetooth
```

Then change the

```
HID2HCI_ENABLED=1
```

to

```
HID2HCI_ENABLED=0
```

Should work for you then

---

### Post by Skerit on 2009-03-04
That did the trick, thank you!

---

### Post by nocknock on 2009-03-06
Thank you, very much.

mewrei, you are the best.

---

### Post by ilfpmats on 2009-03-08
Hello,

I'm ubuntu and linux newbie. I work on a win xp with Logitech MX5000 Bluetooth Desktop (Mouse and Keyboard)
I installed ubuntu as a dual boot and was surprised how easy that works.

Now, if I choose ubuntu by startup, it arise a Login-Screen. I can't login. My Keyboard or Mouse is not recognized. How can I solve that? I see no way to open a shell - I can't even login. Should I buy a usb-wire-keyboard???

Thanks for your Help!

Roly

---

### Post by ilfpmats on 2009-03-09
sorry... It works. I don't know why - I uninstalled and installed again and suddenly, mouse and keyboard works.

---

### Post by justanotherbody on 2009-04-28
After you change HID2HCI_ENABLED=0 make sure you restart bluetooth

sudo /etc/init.d/bluetooth restart

---

### Post by Automat2 on 2009-11-29
quote=mewrei;6549339]Problem pertains to a setting in the Bluez config, specifically the HID2HCI setting.  Apparently the Bluetooth dongle included with the MX5000 isn't one of the supported models.

Easiest way to fix this is

```
gksudo gedit /etc/default/bluetooth
```Then change the

```
HID2HCI_ENABLED=1
```to

```
HID2HCI_ENABLED=0
```Should work for you then[/quote]

It must have changed on the 9.10 because I haven't got that file. If I type "gksudo gedit ..." a blank screen comes up. And yet I have connected both the keyboard and the mouse via BT.

---

