---
title: "HTPC configuration &amp; settings"
date: 2012-04-16
forum: Hardware
---

### Post by Palmer Eldritch on 2012-04-16
[COLOR=#333333][SIZE=3]Hello,[/SIZE][/COLOR]
 
[SIZE=3][COLOR=#333333]I build and configure a HTPC for my family and I need some advice about this.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]This is a DELL Optiplex GX620 with an Intel Pentium 4 520 HT 3 GHz processor.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]I installed the following components:[/COLOR][/SIZE] 
 
[SIZE=3][COLOR=#333333]- 4GB of DDR2 RAM[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- Samsung 120 GB SSD[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- Graphics Card Sapphire ATI Radeon HD 5450 1GB GDDR3 (Passive cooling)[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- DVD Reader / Writer[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- MCE USB IR Receiver / Remote Control[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]I installed Ubuntu 10.4.3 LTS OS and XBMC Dahrma 10.1.[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]I created a user account to use for Ubuntu interface and another dedicated for the exclusive use of XBMC.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]Now I have to integrate it into a home theater and this is where I would need help.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]The home theater includes:[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]- Amplifier Yamaha RXV463[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- HDTV 43" Samsung PS42A-466[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- DVX reader Philips DVP5990[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- Noxon iRadio[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]- Universal remote control Logitech Harmony One[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]The family network is connected with Gigabit Ethernet and there is a digital TV reception. (French TNT)[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]I can connect the HTPC to the amplifier HDMI input, (HDMI -> HDMI cable) for audio / video or to the 2nd TV HDMI input (DVI-> HDMI cable) and analog audio cable from the HTPC to the amplifier. (Jack-> 2 RCA cable)[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]I added the Media Center PC as a new device and a new task in the Logitech Harmony One program.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]One problem I did not have before with other HTPC using a monitor, is that Ubuntu does not recognize the specifications of the TV and the TV returns an error message: (Video) "Mode not supported".[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]How can the TV be recognized?[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]Thank you for your help.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333]Regards,[/COLOR][/SIZE]
[SIZE=3][COLOR=#333333]Palmer.[/COLOR][/SIZE]
 
[SIZE=3][COLOR=#333333][COLOR=#000000]**PS:**[/COLOR][/COLOR][/SIZE]
 
[COLOR=#333333][SIZE=3][COLOR=#333333]Before that I had built and set about the same HTPC, but with an analog HiFi stereo Yamaha amplifier and an iiyama 27'' monitor (1920x1080) and I had no problem.[/COLOR][/SIZE]
[/COLOR]

---

### Post by papibe on 2012-04-16
Hi Palmer Eldritch. Welcome to the forums!

Does it work if you connect the HTPC directly to the TV (not through the amplifier)?

If so, there may be a way to get the TV modes, save them on a file, and then when connected to the amplifier, tell the HTPC to use the settings in the file instead of requesting them over HDMI.

Regards.

---

### Post by Palmer Eldritch on 2012-04-16
[FONT=Verdana]Hi Papibe,[/FONT]
 
[FONT=Verdana]No, it don't works unfortunately...[/FONT]

---

### Post by papibe on 2012-04-16
There may be some clues on the X log file, which is this file:
```
/var/log/Xorg.0.log
```
Could you paste the content of that file here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/") and then post the link so we can take a look?

Regards.

---

### Post by Palmer Eldritch on 2012-04-16
[FONT=Verdana]Yes of course Papibe!

[/FONT][FONT=Verdana]I'll do it tomorrow because there is an 8 hours offset from my home to the Texas ...

Thank you and see you tomorrow,
Regards.[/FONT]

---

### Post by Palmer Eldritch on 2012-04-18
Hello,
 
I finally sccessed to resolve the concern, I connected a monitor and the TV, in the utilities for screen settings, ATI Driver, and XBMC, I set the appropriate parameters. After that and re-booting, the TV is correctly detected and the display is OK in 16/9 full screen.
 
Thank you very much for your advice!
 
Regards,
Palmer Eldritch.
 
**NB:**
 
With this TV, [COLOR=#333333]the HTPC must be connected directly to the TV (HDMI In2 or DVI are right, and not HDMI In1) with a DVI to HDMI or DVI to DVI cable for the video signal, and only the sound signal connected to the amplifier. (Jack to 2 RCA analog cable, or coaxial or optical digital cable)[/COLOR]

---

