---
title: "Samsung R410 &amp; Ubuntu 10.04"
date: 2010-05-21
forum: Hardware
---

### Post by Eestlane on 2010-05-21
Samsung R410 seems to be popular laptop in some areas, so this topic might be a good place to share the compatibility issues.

Seems the r300 drivers don't support Kernel-modesetting on Radeon Xpress 1250, so when trying to install Ubuntu 10.04, be sure to set nomodeset in installation preferences (iirc it was Other Options). Also, before first boot click E on the Ubuntu item and add "nomodeset" (without the quotes) to the same line where "splash" is written to (just separate it with space), then press ctrl+x to boot. If you are in Ubuntu you should [add it permanently]("http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture").

Another issue I had was that installation kind of failed, because no gdm was started. However the failed install happened when I used "try Ubuntu" and in there install. Later I used "install ubuntu" from the boot menu and then it went smoothly.

I installed it without swap partition and don't want to add one, so hibernate won't work (maybe there are some other hacky workarounds). The bad thing is, suspend also doesn't work, but I doubt it has anything to do with swap, so I have yet to find the answer.


That's it for now, maybe someone finds this topic when googleing.


**UPDATE: After trying all the different drivers to get KMS working I found out it was actually kernel fault. Updating the Linux kernel to latest 2.6.35 RC1 and KMS worked! However, it seems wifi didn't work then for some reason, but I'll test that again later.**

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/558378](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/558378)
Works with 2.6.32-24 too (I'm using x64)

---

### Post by Eestlane on 2010-08-11
**1. Fix recognition of Fn button**

```
gksu gedit /lib/udev/rules.d/95-keyboard-force-release.rules
```
Add R410 to Samsungs models list ( | is separator and asterix is probably regex-like any characters).
> ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="*N130*|*N140*|***R410*|***SR70S/SR71S*|*Q210/P210*", RUN+="keyboard-force-release.sh $devpath samsung-other"

```
gksu gedit /lib/udev/rules.d/95-keymap.rules
```
Add R410 to Samsungs models list
> ENV{DMI_VENDOR}=="[sS][aA][mM][sS][uU][nN][gG]*", ATTR{[dmi/id]product_name}=="*NC10*|*NC20*|*N130*|*SP55S*|*SQ45S70S*|*SX60P*|*SX22S*|*SX30S*|*R59P/R60P/R61P*|*SR70S/SR71S*|*Q210*|*Q310*|*X05*|*P560*|***R410*|***R560*", RUN+="keymap $name samsung-other"

```
gksu gedit /lib/udev/keymaps/force-release/samsung-other
```
And make sure it looks like this:
> # list of scancodes (hex or decimal), optional comment
0x82 # Fn+F4 CRT/LCD
0x83 # Fn+F2 battery
0x84 # Fn+F5 backlight on/off
0x86 # Fn+F9 WLAN
0x88 # Fn-Up brightness up
0x89 # Fn-Down brightness down
0xB3 # Fn+F8 switch power mode (battery/dynamic/performance)
0xF7 # Fn+F10 Touchpad on
0xF9 # Fn+F10 Touchpad off



**2. Fix brightness to be triggered from software not hardware**
```
gksu gedit /usr/share/hal/fdi/information/10freedesktop/10-laptop-panel-hardware.fdi
```

After this part:
> <device>
    <match key="info.category" string="laptop_panel">:
add:
> 
<!-- For Samsung -->
      <match key="/org/freedesktop/Hal/devices/computer:system.hardware.vendor" string="SAMSUNG ELECTRONICS CO., LTD.">
        <match key="/org/freedesktop/Hal/devices/computer:system.hardware.product" contains_outof="R410">
          <merge key="laptop_panel.brightness_in_hardware" type="bool">false</merge>
        </match>
      </match>

You might need to restart.

Now that Fn button and brightness probing works Fn+ArrowUp and Fn+ArrowDown should change screen brightness (panel applet might not work as intended though, but I doubt you need it, Fn+F5 backlight toggle also doesn't work however seemed to work when using [voRia's samsung tools]("http://www.voria.org/forum/viewtopic.php?f=3&t=296")).

---

### Post by Eestlane on 2011-04-08
Everything works quite perfect out-of-box with 11.04, don't do anything.

---

