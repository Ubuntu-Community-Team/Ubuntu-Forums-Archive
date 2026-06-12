---
title: "xp-pen g430 drivers"
date: 2016-06-06
forum: Hardware
---

### Post by methana on 2016-06-06
I recently installed Ubuntu 16.04 (before that I used Windows) and I can't get my drawing tablet to work.
I saw that in Ubuntu there are Wacom drivers pre-installed, but nothing about this tablet.
I tried installing drivers for windows trough wine, but it does not work.
Is there is a chance for me to still use this tablet? Because I really don't want to buy a new one.

---

### Post by PinkShinyRose on 2016-11-19
Are you still interested in using it? I don't own the tablet so I cannot try, but an aliexpress review dated 30th of october mentioned they got it to work with [this]("http://permalink.gmane.org/gmane.comp.kde.devel.bugs/1588362").

EDIT: I'm still not sure if people read this, but since it was rather annoying to find this out I'm editing my post, just in case. I bought the tablet too and got it to work on Linux Mint 17.3-mate-64bit with the Yakkety 4.8 kernel. It's not ubuntu, but should be sufficiently similar to Trusty for this to work in Ubuntu.

I got it to work by:
1. Compiling and installing the wizardpen driver [from launchpad (version 0.8.1)]("https://launchpad.net/wizardpen/+download") 

2. Adding
```
#XP-pen G430
ENV{ID_VENDOR_ID}=="28bd", ENV{ID_MODEL_ID}=="0075", ENV{x11_driver}="wizardpen", ENV{ID_MODEL}="stylus"
```
to /etc/udev/rules.d/67-xorg-wizardpen.rules, after the last UC-Logic device entry. (the file is generated when installing the driver using make install; I got the modelnumber using cat /proc/bus/input/devices)

3. Changing /usr/share/X11/xorg.conf.d/70-wizardpen.conf to
```
Section "InputClass"
   Identifier "stylus"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/event*"
   MatchVendor "UGTABLET"
   MatchTag "wizardpen"
   Driver "wizardpen"
   Option          "Device"       "/dev/input/by-id/usb-UGTABLET_TABLET_G3_4x3-event-mouse"
   Option          "TopX"          "518"
   Option          "TopY"          "735"
   Option          "BottomX"       "32767"
   Option          "BottomY"       "32767"
EndSection
Section "InputClass"
   Identifier "wizardpen ignore mouse dev"
   MatchIsTablet "on"
   MatchDevicePath "/dev/input/by-id/usb-UGTABLET_TABLET_G3_4x3-event-mouse"
   MatchVendor "UC-LOGIC|KYE Systems|Ace Cad|WALTOP|Waltop|UGTABLET"
   Driver ""
EndSection
```
Again, most of this is a copy-paste from what I linked earlier, except the "/dev/input/by-id/usb-UGTABLET_TABLET_G3_4x3-event-mouse" part, which I got from cat /proc/bus/input/devices.
(file also generated when installing the driver, I commented out the default settings instead of removing it, but that shouldn't matter).

I hope this helps someone, and otherwise at least I will know where to find this information next time.

---

### Post by dasankir on 2017-02-21
Thanks for the info!

Just in case someone is having issues compiling Wizardpen, here is a detailed guide: [https://digimend.github.io/support/howto/drivers/wizardpen/](https://digimend.github.io/support/howto/drivers/wizardpen/)

---

### Post by dasankir on 2017-02-22
I wrote the guys at XP-pen forwarding them this post and asking for official linux support. They kindly answered:

[INDENT]"Thanks so much, it is very important for us. Actually, we also start developing linux driver.
When I got your mail, I also passed to our Engineer, it is very hopeful for us.
Thanks and Best Regards,
XP-Pen Team"
[/INDENT]

---

### Post by NoOneRuleZ on 2017-02-22
Hi,

I actually run Manjaro but since this is the first result you get when you searched "xp-pen g430 linux", I figured I'd post this here.

I had trouble getting WizardPen to work so I decided to debug the issue using [https://digimend.github.io/support/howto/trbl/locating_failure/](https://digimend.github.io/support/howto/trbl/locating_failure/) and it turns out the kernel driver works but the buttons are mapped wrong. It looks like someone fixed the issue for the G540 which also solved the problem for the G430: [https://github.com/DIGImend/digimend-kernel-drivers/commit/3335f96d9c1c3ed690fda583fcf381f9be0f7908](https://github.com/DIGImend/digimend-kernel-drivers/commit/3335f96d9c1c3ed690fda583fcf381f9be0f7908)

This fix will eventually be mainlined into the linux kernel so that it works out of the box but in the meantime, you can compile and install the digimend-kernel-drivers to get this tablet to work.

git clone [https://github.com/DIGImend/digimend-kernel-drivers.git](https://github.com/DIGImend/digimend-kernel-drivers.git)
cd digimend-kernel-drivers
make
sudo make install
sudo rmmod hid-kye
sudo rmmod hid-uclogic
sudo rmmod hid-huion

Reconnect the tablet or reboot and it should work.

---

### Post by NoOneRuleZ on 2017-02-24
One thing I should add to the above is that you'll need git, a compiler (such as clang or gcc) and the kernel headers installed.

---

### Post by dasankir on 2017-03-04
> **NoOneRuleZ said:**
> Hi,

I actually run Manjaro but since this is the first result you get when you searched "xp-pen g430 linux", I figured I'd post this here.

I had trouble getting WizardPen to work so I decided to debug the issue using [https://digimend.github.io/support/howto/trbl/locating_failure/](https://digimend.github.io/support/howto/trbl/locating_failure/) and it turns out the kernel driver works but the buttons are mapped wrong. It looks like someone fixed the issue for the G540 which also solved the problem for the G430: [https://github.com/DIGImend/digimend-kernel-drivers/commit/3335f96d9c1c3ed690fda583fcf381f9be0f7908](https://github.com/DIGImend/digimend-kernel-drivers/commit/3335f96d9c1c3ed690fda583fcf381f9be0f7908)

This fix will eventually be mainlined into the linux kernel so that it works out of the box but in the meantime, you can compile and install the digimend-kernel-drivers to get this tablet to work.

git clone [https://github.com/DIGImend/digimend-kernel-drivers.git](https://github.com/DIGImend/digimend-kernel-drivers.git)
cd digimend-kernel-drivers
make
sudo make install
sudo rmmod hid-kye
sudo rmmod hid-uclogic
sudo rmmod hid-huion

Reconnect the tablet or reboot and it should work.

I don't know why but after installing the digimend-kernel-drivers when I plug the tablet the system freezes and closes the session...

---

### Post by juanh5 on 2017-03-07
can confirm PinkShinyRose 's directions work fine in ubuntu 16.04, and also in fedora 25 (though compiling was harder, i'm kind of a newbie)
THANKS!
...note that for allowing pressure sensitivity in Gimp you must configure inputs, setting UGTABLET to "screen" mode... tried to use in Krita, but there is no pressure (nor settings visible) + buggy behavior

---

### Post by PinkShinyRose on 2017-06-06
> **NoOneRuleZ said:**
> Hi,

I actually run Manjaro but since this is the first result you get when you searched "xp-pen g430 linux", I figured I'd post this here.

I had trouble getting WizardPen to work so I decided to debug the issue using [https://digimend.github.io/support/howto/trbl/locating_failure/](https://digimend.github.io/support/howto/trbl/locating_failure/) and it turns out the kernel driver works but the buttons are mapped wrong. It looks like someone fixed the issue for the G540 which also solved the problem for the G430: [https://github.com/DIGImend/digimend-kernel-drivers/commit/3335f96d9c1c3ed690fda583fcf381f9be0f7908](https://github.com/DIGImend/digimend-kernel-drivers/commit/3335f96d9c1c3ed690fda583fcf381f9be0f7908)

This fix will eventually be mainlined into the linux kernel so that it works out of the box but in the meantime, you can compile and install the digimend-kernel-drivers to get this tablet to work.

git clone [https://github.com/DIGImend/digimend-kernel-drivers.git](https://github.com/DIGImend/digimend-kernel-drivers.git)
cd digimend-kernel-drivers
make
sudo make install
sudo rmmod hid-kye
sudo rmmod hid-uclogic
sudo rmmod hid-huion

Reconnect the tablet or reboot and it should work.

Using the digimend driver as you described works for me in ubuntu-mate 17.04 (which didn't include the hid-uclogic module in the first place).

By now I first installed ubuntu-mate 16.10, but after upgrading to ubuntu-mate 17.04 wizardpen no longer worked. It was removed upon upgrading, and upon reinstalling as I did previously, my session crashed whenever I plugged in my tablet (upon plugging in I got a flickering black screen until I remove, and after the first flicker I was back at the login screen, if I left it in for a few seconds the system would freeze entirely).

---

### Post by daluceson on 2017-06-10
i asked them when they will publish driver, 

[FONT=arial]>> Hi, Do you know when are you porting 22" arstist tablet driver to linux paradise world ?

[/FONT]>> Dear Sir,Sorry, XP-Pen doesn&#8217;t developer the Lunix drvier, so please use it on Windows or Mac system.
Thanks and Best Regards,
XP-Pen Team


HAHAHAHAHAH. he **** my day ! i dunno what s happens during this 4 month but they change litterally opinion about driver strategy.

i didnt know it was hard to produce driver for tablet. sure is not. they should give us something . . . . choose our resolution depends of tablet wehave, and a pen calibrate, that's it. no need button. 

I am very disappointed. What we can do ??? i am sad

---

### Post by ezra2 on 2018-02-17
Omg, 
This worked.
Unfortunatley, yet thankfully, it worked on Ubuntu Mate Only. I tried many flavors of linux and Ubuntu mate 17,10 came through.

@NoOneRuleZ thanks!
I have a question, hopfully it's not to late to ask (almost a year exactly), were you able to get some type of tablet settings to get working with the XP-PEN?
Any idea on how to get the sensitivity pressure to work?

I fear that my best bet would be to purchase a WACOM tablet. I love XP-PEN they're not as costly as Big companies are, yet offer well tablets.

---

### Post by mörgæs on 2018-02-17
It often takes some time for GNU/Linux to develop full support for hardware if the manufacturer does not cooperate.

Have you tried how it works in a live boot of 18.04?

---

### Post by the-seraphim on 2018-05-14
> **mörgæs said:**
> It often takes some time for GNU/Linux to develop full support for hardware if the manufacturer does not cooperate.

Have you tried how it works in a live boot of 18.04?

I have one of the XP-Pen tablets coming tomorrow, I plan to get it working under Ubuntu 18.04 but if it doesnt work with pressure I plan to dual boot windows instead.

Will report back my findings.

---

### Post by juanh5 on 2018-07-24
did anyone try the wizardpen driver in KDE? It gives me some trouble with pkg-config, can't compile correctly.

there's also a new beta driver provided by XP Pen
[https://www.xp-pen.com/download/index/cid/36.html]("https://www.xp-pen.com/download/index/cid/36.html")
can't make it in Kubuntu, maybe useful to some of you (their support claims to have tested it in Ubuntu 16.10)

---

