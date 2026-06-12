---
title: "ZenBook UX431DA sound cracking"
date: 2020-05-02
forum: Hardware
---

### Post by axet2 on 2020-05-02
Hello!

I recently install recent version of windows on separate partition and got garbaged sound on booth OS! My old version of windows was 1803 and everying was ok, I updated to 1909 and it got broken sound. Probably due to some firmware configs / updates on sound chip. I let Windows to update drivers and notice my sound card driver got replaced by realtek drivers and sound got fixed on windows! But linux still not working propertly!

also-info.sh shows two devices:

[http://alsa-project.org/db/?f=6d80e374011ccba05d32c8a6e6bde57316cbf06d](http://alsa-project.org/db/?f=6d80e374011ccba05d32c8a6e6bde57316cbf06d)

 0 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe7c8000 irq 72
 1 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfe7c0000 irq 73

This how it was on booth Linux and Windows 1810 before update. Windows also used to show two devices "AMD High Definition Audio Device", "AMD High Definition Audio Device".
Something tells me alsa detect cards correctly. But now, something changed and alsa need to update configs...
Now Windows shows two devices: "AMD High Definition Audio Device" and second "Realtek(R) Audio".

AMD High Definition Audio Device/10.0.1.10/HDAUDIO\FUNC_01&VEN_1002&DEV_AA01&SUBSYS_00AA0100&REV_1007\5&14BACE15&0&0001
Realtek Semiconductor Corp./6.0.8757.1/HDAUDIO\FUNC_01&VEN_10EC&DEV_0294&SUBSYS_10431B11&REV_1000\5&7195807&0&0001
AMD Audio CoProcessor/1.16.0.86/PCI\VEN_1022&DEV_15E2&SUBSYS_15E21022&REV_00\4&28056CF2&0&0541



As you can see from new windows drivers it detects two devices 1002:AA01 and 10ec:0294, but alsa keep detecting [COLOR=#000000]1002:15de and [/COLOR][COLOR=#000000]1022:15e3[/COLOR][COLOR=#000000]
[/COLOR]
On Ubuntu machine sound still completely garbaged and sounds like broken speakers. My headphones makes even stranger sounds. Not sure what to do.

I found several links about this issue here:

[https://github.com/torvalds/linux/commit/60083f9e94b2f28047d71ed778adf89357c1a8fb](https://github.com/torvalds/linux/commit/60083f9e94b2f28047d71ed778adf89357c1a8fb)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1850439](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1850439)

[https://askubuntu.com/questions/1175095/asus-zenbook-ux534f-no-sound-from-speakers-headphones/1186977](https://askubuntu.com/questions/1175095/asus-zenbook-ux534f-no-sound-from-speakers-headphones/1186977)

Windows 1909 without updates shows those id's:

AMD High Definition Audio Device/10.0.1.10/HDAUDIO\FUNC_01&VEN_1002&DEV_AA01&SUBSYS_00AA0100&REV_1007\5&14BACE15&0&0001
High Definition Audio Device/10.0.18362.356/HDAUDIO\FUNC_01&VEN_10EC&DEV_0294&SUBSYS_10431B11&REV_1000\5&7195807&0&0001

Windows 1803 without updates (old external installation):

AMD High Definition Audio Device/10.0.1.6/HDAUDIO\FUNC_01&VEN_1002&DEV_AA01&SUBSYS_00AA0100&REV_1007\5&14BACE15&0&0001
High Definition Audio Device/10.0.17134.1006/HDAUDIO\FUNC_01&VEN_10EC&DEV_0294&SUBSYS_10431B11&REV_1000\5&7195807&0&0001
AMD Audio CoProcessor/1.17.0.94/PCI\VEN_1022&DEV_15E2&SUBSYS_15E21022&REV_00\4&28056CF2&0&0541

I create a bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1876459](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1876459)

---

