---
title: "Inventec DVB-T USB Tuner (RTL2832U 1b80:d398) Xenial Driver Patch"
date: 2016-09-19
forum: Hardware
---

### Post by javimixet on 2016-09-19
[IMG]https://drive.google.com/uc?export=download&id=0B53LBwSsWUAIUlMwRTZnOGNtd28[/IMG]

[IMG]https://drive.google.com/uc?export=download&id=0B53LBwSsWUAIbnJVNm84WG1mT2s[/IMG][COLOR=#3F3F3F][FONT=&amp][B]


Working for linux kernel 4.4.0-36-generic (Lubuntu Xenial)[/B]

[/FONT][/COLOR]
[COLOR=#3F3F3F][FONT=&amp]mkdir dvb-[COLOR=#008800]2382u[/COLOR]
cd dvb-[COLOR=#008800]2382u[/COLOR]
git clone git:[COLOR=#888888]//linuxtv.org/media_build.git [/COLOR]
cd media_build
./build
[INDENT]***Important!!!*** as soon as the download of the sources and then the extraction of the new sources finish (after hitting enter at the .build command) hit Ctrl+c to interrupt the process of building the source. Even if the building of the modules is going to finish you will not do a make install… so by interrupting it you will save a couple of minutes.’
[/INDENT]
[/FONT][/COLOR]

[COLOR=#3F3F3F][FONT=&amp]**Patch**

Edit the file **linux/drivers/media/dvb-core/dvb-usb-ids.h** inserting the line:
[/FONT][/COLOR]
[COLOR=#3F3F3F][FONT=&amp][COLOR=#880000]    #**define** USB_PID_KWORLD2_TURBOX_USB2_DVB_T       0xd398

[/COLOR]Then you need to edit the file **linux/drivers/media/usb/dvb-usb-v2/rtl28xxu.c** 
Search for the line:
[/FONT][/COLOR]
[COLOR=#3F3F3F][FONT=&amp]**    static** **const** **struct** usb_device_id rtl28xxu_id_table[] = {

And then put your cursor after the { symbol and paste the lines:
[/FONT][/COLOR]
[COLOR=#3F3F3F][FONT=&amp]    { DVB_USB_DEVICE(USB_VID_KWORLD_2, [COLOR=#008800]0xd398[/COLOR],
        &rtl28xxu_props, [COLOR=#880000]"Realtek 2832U USB DVB-T Stick RC"[/COLOR], **NULL**) },
[/FONT][/COLOR]

[COLOR=#3F3F3F][FONT=&amp]**Finishing Compilation and install**

In ‘media_build’ folder:
[/FONT][/COLOR]
[COLOR=#3F3F3F][FONT=&amp]    make
    **    sudo** make install

[/FONT][/COLOR]
[COLOR=#3F3F3F][FONT=&amp]**Source**

[https://www.dfragos.me/2012/11/installation-of-rtl2832u-chip-based-dvb-t-usb-stick.html](https://www.dfragos.me/2012/11/installation-of-rtl2832u-chip-based-dvb-t-usb-stick.html)
[/FONT][/COLOR]

---

