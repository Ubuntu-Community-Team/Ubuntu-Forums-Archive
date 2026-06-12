---
title: "Installink DisplayLink device for Xorg"
date: 2017-08-17
forum: Hardware
---

### Post by zoltan-zorgo on 2017-08-17
Hello,

I need to configure an ELO 0700L touch device as the single display for a boxpc based solution. Well, I am unable to make it work at all.
I am using Ubuntu 16.04.03 LTS minimal server with Xorg installed but not window manager.
I was following the official documentation from DisplayLink: [http://support.displaylink.com/knowledgebase/articles/684649-how-to-install-displaylink-software-on-ubuntu](http://support.displaylink.com/knowledgebase/articles/684649-how-to-install-displaylink-software-on-ubuntu) (for 14.04) and the instructions from here: [https://help.ubuntu.com/community/DisplayLink](https://help.ubuntu.com/community/DisplayLink)
These two are a little bit different. 
[ATTACH=CONFIG]276426[/ATTACH]
As I there is systemd in 16.04, there is no service started. So I started it manually:
[ATTACH=CONFIG]276427[/ATTACH]
I have also checked that the device is seen by the system (according to this: [http://support.displaylink.com/knowledgebase/articles/683672-my-displaylink-device-does-not-work-on-ubuntu):](http://support.displaylink.com/knowledgebase/articles/683672-my-displaylink-device-does-not-work-on-ubuntu):) 
[ATTACH=CONFIG]276428[/ATTACH]

I don't want to run XServer on my regular display, only on the ELO DisplayLink device, with a bare Chromium, nothing else, even no window manager. This is why I have chosen a server installation, and I have installed Xorg. 
But [FONT=courier new][/FONT][FONT=courier new]xrandr[/FONT][FONT=courier new] [/FONT]tells me, that it can't open display :(
I suppose Xorg is not configured. Can you give advice how to proceed, how to configure Xorg for this device?
Thank you!

---

