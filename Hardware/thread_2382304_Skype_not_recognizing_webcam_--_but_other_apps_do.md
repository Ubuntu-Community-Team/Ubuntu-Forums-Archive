---
title: "Skype not recognizing webcam -- but other apps do"
date: 2018-01-11
forum: Hardware
---

### Post by Blnd2Spll on 2018-01-11
I am trying to get my webcam working in Skype v 8.13.0.2 on Ubuntu 16.04. It's a Logitech c615 webcam, and it works fine in both Cheese and Google Hangouts. It was working previously, but somewhere over the last month it stopped working. Now when I go to audio and video settings in skype it says "No Device Found". 

The output of lsusb is:
```


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 413c:2113 Dell Computer Corp. 
Bus 001 Device 009: ID 046d:082c Logitech, Inc. 
Bus 001 Device 006: ID 0424:4060 Standard Microsystems Corp. Ultra Fast Media Reader
Bus 001 Device 004: ID 0424:2640 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
The device"046d:082c Logitech, Inc."  is the webcam.

Any thoughts on what to troubleshoot? I've tried purging skype, restarting, and reinstalling, but that didn't help. I've checked the forums for other problems but can't seem to find any easy fixes.

Thanks!

---

### Post by khelben1979 on 2018-01-12
If the web cam is still working with other applications and it is not working with Skype, I would recommend you find someone who can guide you to download a older version of Skype. I've read through some of the F.A.Q. from users experiencing issues with latest version of Skype with Linux and from the looks of it, it does not look good. Skype themselves would never recommend a older version, but to uninstall and and reinstall which is their official answer to this issue.

Skype is a mess on Linux right now, and I would never recommend people to just upgrade to the latest version. Newer isn't always better.

---

### Post by sawfish2 on 2018-01-13
Hi

I can recommend using Skype Online thought the browser as an alternative. I use it often through Google Chrome, but it has some problems with groups speaking, so make at test before. It can be depended on who starts the invitations. Sharing screen works better through the online version thought.

Kind regards
Sawfish2

---

### Post by sawfish2 on 2018-01-15
Hi

Did you solve the problem. It would be interesting to know, because both webcams and Skype are not easy to configure in Ubuntu.

Kind regards
Sawfish2

---

### Post by petro-ludoviko on 2018-02-13
Hi to everybody.
I have the same problem. Working on Kubuntu 17.04, but not on Skype 8.15.
For future searchers I'll put my information in any case someone could find a solution. The audio of the webcam normally works even in Skype.
Kubuntu 17.04, Skype 8.15, Webcam Ausdom.

```
[COLOR=#555555][FONT=Monaco]$ lsusb[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Bus 001 Device 005: ID 1bcf:2286 Sunplus Innovation Technology Inc.[/FONT][/COLOR]
```

```
[COLOR=#555555][FONT=Monaco]$ usb-devices[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  5 Spd=480 MxCh= 0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]P:  Vendor=1bcf ProdID=2286 Rev=01.00[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]S:  Manufacturer=Sunplus IT Co [/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]S:  Product=AUSDOM FHD Camera[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]C:  #Ifs= 4 Cfg#= 1 Atr=80 MxPwr=500mA[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]I:  If#= 3 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio[/FONT][/COLOR]
```

```
[COLOR=#555555][FONT=Monaco]$ lsmod | grep uvc[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]uvcvideo               90112  0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]videobuf2_vmalloc      16384  1 uvcvideo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]videobuf2_v4l2         24576  1 uvcvideo[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]videobuf2_core         40960  2 uvcvideo,videobuf2_v4l2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]videodev              172032  3 uvcvideo,videobuf2_core,videobuf2_v4l2[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]media                  40960  2 uvcvideo,videodev[/FONT][/COLOR]
```
[COLOR=#555555][FONT=Monaco]
With this command it gives these errors:

[/FONT][/COLOR]```
[COLOR=#555555][FONT=Monaco]$ dmesg | tail[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1338.956353] uvcvideo: Failed to query (GET_CUR) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1338.957235] uvcvideo: Failed to query (GET_CUR) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1338.958356] uvcvideo: Failed to query (GET_CUR) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1338.959486] uvcvideo: Failed to query (GET_CUR) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1712.654009] perf: interrupt took too long (10192 > 10142), lowering kernel.perf_event_max_sample_rate to 19500[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1826.623311] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1826.624433] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1826.625556] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1826.626676] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco][ 1826.627806] uvcvideo: Failed to query (GET_DEF) UVC control 2 on unit 1: -32 (exp. 1).[/FONT][/COLOR]
```[COLOR=#555555][FONT=Monaco]
[/FONT][/COLOR]

---

### Post by sawfish2 on 2018-02-14
According to this article in ZDNET ([http://www.zdnet.com/article/skype-cannot-fix-security-bug-without-a-massive-code-rewrite/](http://www.zdnet.com/article/skype-cannot-fix-security-bug-without-a-massive-code-rewrite/)) the user should be aware, that there might be security problems with at least the present version. I cant imagine this could be a problem for the online version, but I cant find any information on this.

Kind regards
sawfish2

---

