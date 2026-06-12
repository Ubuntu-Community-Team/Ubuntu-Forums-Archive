---
title: "Macbook Pro 3.1 Touchpad Configuration - Jaunty"
date: 2009-04-30
forum: Hardware
---

### Post by lambengolmor on 2009-04-30
Hi everybody, I desperatly need help:

-I had an ubuntu 8.10 on my macbookpro 3.1, at installing time I had issues, but I managed to make the touchpad work trough manual editing of Xorg.conf

-I updated to 9.04

-Right click by two finger tapping ceased to work

-I tried everything (reenabiling my manual editing in Xorg.conf, translating that settings in an /etc/hal/fdi/policy/appletouch.fdi file etc...) but I got:
   A) right clicking but wierd moving mouse cursor
   ---> some other experiment
   B) NOT right clicking AND wierd moving mouse cursor.

Please, I just need a simple but working confturation (don't need middle click, iPod-like rotation and similar...)

Thanks a lot in advance

PS: in gdm mouse cursor behaves quite good, I don't have the possibility to right click in it though (I mean... I don't think I have areas where right-clicking could show any effect)

PPS: I followed some guide but none worked, nor was designed specifically for MBP 3.1 + Jaunty

---

### Post by all2ez on 2009-05-02
I haven't had time to try this yet but it looks good.  Please let us know if it works for you.

[http://deekayen.net/macbook-pro-31-jaunty-setup](http://deekayen.net/macbook-pro-31-jaunty-setup)

---

### Post by lambengolmor on 2009-05-03
I'm sorry, it didn't work for me, but it could just be that I didn't had a clean Jaunty installation.
In detail:

-mouse click works using mouse button (left click with button, right click with two fingers on pad + button)
-mouse cursor still doesn't move diagonally (it just goes down/up and then left/right: same issue I found [here]("http://ubuntuforums.org/showthread.php?t=493758&page=7"))

Thanks anyway for help!

---

### Post by lambengolmor on 2009-05-03
Sorry, that's stupid, but I edited /etc/hal/fdi/policy/appletouch.fdi just after posting and now works quite fine (but the funny cursor movement remains)

this is my appletouch.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>

    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">1</merge>

        <merge key="input.x11_options.TopEdge" type="string">0</merge>
        <merge key="input.x11_options.LeftEdge" type="string">0</merge>
        <merge key="input.x11_options.RightEdge" type="string">1100</merge>
        <merge key="input.x11_options.BottomEdge" type="string">800</merge>

        <merge key="input.x11_options.FingerLow" type="string">15</merge>
        <merge key="input.x11_options.FingerHigh" type="string">25</merge>
        <merge key="input.x11_options.TapButton1" type="string">1</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">0</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>

        <merge key="input.x11_options.MinSpeed" type="string">0.5</merge>
        <merge key="input.x11_options.MaxSpeed" type="string">2.0</merge>
        <merge key="input.x11_options.AccelFactor" type="string">0.15</merge>
        <merge key="input.x11_options.VertScrollDelta" type="string">20</merge>
    </match>
  </device>
</deviceinfo>
```

---

### Post by LogonJasirl on 2009-10-21
> **all2ez said:**
> I haven't had time to try this yet but it looks good.  Please let us know if it works for you.

[http://deekayen.net/macbook-pro-31-jaunty-setup](http://deekayen.net/macbook-pro-31-jaunty-setup)

Following the steps in the linked page. I get the following error when trying to add the software source. 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8DB7F87A2B97B7B8

Any ideas? Cheers!

---

### Post by all2ez on 2009-10-21
Not totally sure but you might wanna try this to get the key:

[http://ubuntuforums.org/showpost.php?p=6650442&postcount=11](http://ubuntuforums.org/showpost.php?p=6650442&postcount=11)

---

