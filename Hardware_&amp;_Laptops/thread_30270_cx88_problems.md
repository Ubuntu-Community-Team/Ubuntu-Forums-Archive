---
title: "cx88 problems"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by echoz on 2005-04-27
Hi,

I'm not entirely sure if this is hardware related or a ubuntu problem, but since the related hardware doesn't really work with the software, I suppose I could push this here.

I've a WinTV card that refuses to work properly in ubuntu. Either there would be no sound, or the signal that the tv apps scan for seems to be wrong. (I'm supposed to get PAL-B, but everything lacks colour and is how say... hazy.)

tvtime, kdetv, xawtv, ever popular tv app for linux won't work well. and has the same problem.

Also, I seem to get lots of errors related to its driver in my dmesg out put.

An example of dmesg output.

```

cx88[0]/0: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_FORCE_MONO1
cx88[0]/0: AUD_STATUS: 0xfffa [mono/pilot c2] ctl=A2_FORCE_MONO1
cx88[0]/0: AUD_STATUS: 0xfff2 [mono/no pilot] ctl=A2_FORCE_MONO1
cx88[0]/0: AUD_STATUS: 0xfff6 [mono/pilot c1] ctl=A2_FORCE_MONO1

```

Anyone help?

Additonally, lspci output

```

0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corp. 82801EB (ICH5) Serial ATA 150 Storage Controller (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4800 SE] (rev a1)
0000:02:02.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
0000:02:02.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 03)
0000:02:02.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
0000:02:03.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 03)
0000:02:03.1 Multimedia controller: Conexant: Unknown device 8811 (rev 03)
0000:02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

```

And related lsmod output,

```

cx8800                 31340  0
cx88xx                 49396  1 cx8800
i2c_algo_bit           10024  1 cx88xx
video_buf              21956  2 cx8800,cx88xx
v4l1_compat            14468  1 cx8800
v4l2_common             5888  1 cx8800
btcx_risc               4936  2 cx8800,cx88xx
videodev               10080  2 cx8800,cx88xx
i2c_core               22720  4 tuner,cx88xx,i2c_algo_bit,i2c_i801

```

---

### Post by drummer on 2005-04-28
Hi, i'm using the same card (expert) and had the same problems.. what i did was this:
 
- first I ran ```
sudo gedit /etc/modules
``` and added ```
cx8800
tda9887
videodev
``` to make sure those modules loaded at boot
 
- then in tvtime made sure the settings were all correct (in 'channel management' and 'input configuration' -> 'change frequency table', 'enable signal detection', then 'reset all channels as active' and 'scan channels for signal')
 
- to get some colour in my picture i edited " ~/.tvtime/tvtime.xml " and changed the value of 'DefaultHue' to 100 (about line 5). I was watching tv in B&W for quite a while before i found this tip.. :) 
 
- lastly the sound sometimes went fuzzy which was fixed by toggling 'Use PAL-DK audio decoding' on then off in 'Channel Management'
 
TV works like a charm now, hope this helps.

---

### Post by echoz on 2005-04-28
nice.

thanks a lot. will check it out once i boot back into ubuntu. had to boot into XP to record a tv program :/

inccidentally, and quite off topic, what kinda PVR software do you use (if you even use one at all). MythTV doesn't work for me because it requires some tvxml thing that my country doesn't provide for its programs (Singpaore).

---

### Post by buz on 2005-04-28
I did what you pointed out drummer but my display remains black and white... How can I figure out what tuner I have???

---

### Post by echoz on 2005-04-28
[QUOTE=buz]I did what you pointed out drummer but my display remains black and white... How can I figure out what tuner I have???[/QUOTE]

you could do a lspci to get a listing of all your PCI devices.

---

### Post by echoz on 2005-04-28
[QUOTE=drummer]Hi, i'm using the same card (expert) and had the same problems.. what i did was this:
 
- first I ran ```
sudo gedit /etc/modules
``` and added ```
cx8800
tda9887
videodev
``` to make sure those modules loaded at boot
 
- then in tvtime made sure the settings were all correct (in 'channel management' and 'input configuration' -> 'change frequency table', 'enable signal detection', then 'reset all channels as active' and 'scan channels for signal')
 
- to get some colour in my picture i edited " ~/.tvtime/tvtime.xml " and changed the value of 'DefaultHue' to 100 (about line 5). I was watching tv in B&W for quite a while before i found this tip.. :) 
 
- lastly the sound sometimes went fuzzy which was fixed by toggling 'Use PAL-DK audio decoding' on then off in 'Channel Management'
 
TV works like a charm now, hope this helps.[/QUOTE]

Okay. I tried everything. Only the Colour bit worked. The rest didn't seem to have any effect at all. Its weird that I can't even get a clear signal for any channel considering WinTV and snapstream on windows xp managed to get the channels correct.

---

### Post by echoz on 2005-04-28
My bad. the colour bit only worked slightly. i got the sound working though.

compare the two attached files. is there anything i can do within tvtime's settings?

---

### Post by drummer on 2005-04-29
Have a play with the saturation in tvtime and also the brightness/contrast. At first, my reception and colour was a bit chageable and couldn't make up its mind about the colour but it has settled down after tweaking these settings.

For the frequency, chech that the correct frequency table is being used in tvtime. And also that the card is being detected as the correct make/brand.

EDIT: i just re-read your first post and you said it was a WinTV card.. but in your lspci output the card is listed as ```
Conexant Winfast TV2000 XP (rev 03)
```
There is quite a detailed article here: [http://www.linuxjournal.com/article/8116](http://www.linuxjournal.com/article/8116) about setting up the Hauppauge WinTV card (conexant chipset) which may be a useful read. It also tells you how to pass options such as tuner/card type to the modules being loaded in /etc/modules.

If you are using the Hauppauge WinTV card (sorry, i though u had the winfast TV2000 as in ur lspci, which is what i have) that article will hopefully get the right lines in /etc/modules to correctly detect your card at boot. The author refers to /etc/modules.conf as he is using Fedora Core but the same should apply to /etc/modules (someone please correct me if i'm wrong).

---

### Post by echoz on 2005-04-29
This is the one i'm using.
[http://www.hauppauge.com/Pages/products/data_gofm.html](http://www.hauppauge.com/Pages/products/data_gofm.html)

Anyways, when I run tvtime from terminal, i get the following message. 

```

jeremy@colin:~$ tvtime
Running tvtime 0.9.15.
rtctimer: Cannot set periodic interval: Permission denied

    Failed to get 1024 Hz resolution from your RTC device.  High
    resolution access is necessary for video to be smooth.  Please
    run tvtime as root, set tvtime as SUID root, or change the
    maximum RTC resolution allowed for user processes by running this
    command as root:
        sysctl -w dev.rtc.max-user-freq=1024
    See our support page at http://tvtime.net/ for more information.

Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/jeremy/.tvtime/tvtime.xml
videoinput: Tuner refuses to tell us the current frequency: Invalid argument
videoinput: Please file a bug report at http://tvtime.net/
Thank you for using tvtime.

```

Its quite weird. Will give the linuxjournal article a short later.

---

### Post by drummer on 2005-04-29
[QUOTE=echoz]This is the one i'm using.
[http://www.hauppauge.com/Pages/products/data_gofm.html](http://www.hauppauge.com/Pages/products/data_gofm.html)

Anyways, when I run tvtime from terminal, i get the following message. 

```

jeremy@colin:~$ tvtime
Running tvtime 0.9.15.
rtctimer: Cannot set periodic interval: Permission denied

    Failed to get 1024 Hz resolution from your RTC device.  High
    resolution access is necessary for video to be smooth.  Please
    run tvtime as root, set tvtime as SUID root, or change the
    maximum RTC resolution allowed for user processes by running this
    command as root:
        sysctl -w dev.rtc.max-user-freq=1024
    See our support page at http://tvtime.net/ for more information.

Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/jeremy/.tvtime/tvtime.xml
videoinput: Tuner refuses to tell us the current frequency: Invalid argument
videoinput: Please file a bug report at http://tvtime.net/
Thank you for using tvtime.

```

Its quite weird. Will give the linuxjournal article a short later.[/QUOTE]
 sorry, not sure what that error means, but i'd start with the article and get the card recognised correctly first and see if that makes any difference to the colour. Then if tvtime is playing up, possibly try what the message says.. furthur than that i'm not sure if i can be of much help, i'm only speaking out of personal experiences.. not expertness.
 
If you are still stuck after my advice, the people on #ubuntu at irc.freenode.net are really helpful.

---

### Post by echoz on 2005-04-29
[QUOTE=drummer]sorry, not sure what that error means, but i'd start with the article and get the card recognised correctly first and see if that makes any difference to the colour. Then if tvtime is playing up, possibly try what the message says.. furthur than that i'm not sure if i can be of much help, i'm only speaking out of personal experiences.. not expertness.
 
If you are still stuck after my advice, the people on #ubuntu at irc.freenode.net are really helpful.[/QUOTE]
 thanks for all your trouble man.

---

### Post by drummer on 2005-04-29
[QUOTE=echoz]thanks for all your trouble man.[/QUOTE]
 no problem, sorry i can't be of more help

---

### Post by drummer on 2005-04-30
one final note: i just ran tvtime from the terminal and received the same error you posted previously but tvtime is still working fine for me, so i guess you could safely ignore that for the moment.. There is also a bug report posted on the tvtime sourceforge page for a similar looking error, but maybe you could post another (i probably will as well, just as soon as i get internet access on my ubuntu box ;))

---

### Post by buz on 2005-04-30
[QUOTE=echoz]you could do a lspci to get a listing of all your PCI devices.[/QUOTE]


Well I obviously did that.

000:00:0a.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 03)
0000:00:0a.1 Multimedia controller: Conexant: Unknown device 8811 (rev 03)


Not really helpful I guess... I know I got a CX881on that card, but no idea how to find out what tuner a PAL card would have. I DO get a picture, only it's in black and white, retuning it gives some *slight* colors but a lot of noise in it.

---

### Post by buz on 2005-04-30
[QUOTE=echoz]My bad. the colour bit only worked slightly. i got the sound working though.

compare the two attached files. is there anything i can do within tvtime's settings?[/QUOTE]


Yeah that's exactly how it looks for me as well

---

### Post by pt123 on 2005-07-08
I found a solution to the colour problem. When its black and white , choose to fine tune the channel. I went up to +17 and the picture became colour \\:D/ 


For some reason tvtime is under-tuning the Winfast 2000xp expert tv card. Maybe they can fix it in the future.

---

