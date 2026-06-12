---
title: "Internal audio not working - ALC887-VD (Ubuntu 18.04.1)"
date: 2018-10-23
forum: Hardware
---

### Post by michaelkey253 on 2018-10-23
Goodmorning everyone,

I have installed Ubuntu 18.04.1 on an assembled PC for a few days, and unfortunately I can not get the motherboard's internal sound card to work. I have an additional USB sound card but it works, while the internal one does not. I have an ASUS Prime H270-PLUS motherboard that has an ALC887-VD internal sound card and I would need to make it work both for the rear sockets and especially for the two front sockets (headphones and microphone). Can you give me a hand? If you need some output I will be more than available. 


Thanks in advance

---

### Post by dino99 on 2018-10-23
Goto SystemSetting icon (top right bar) then click on Tool icon (bottom left menu) and set or test each tab settings

[https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en](https://help.ubuntu.com/stable/ubuntu-help/sound-nosound.html.en)

---

### Post by michaelkey253 on 2018-10-24
[COLOR=#212121][FONT=arial]I tried but it still does not work. I also tried to add the string "options snd-hda-intel model = generic" or Auto, but the same does not work...[/FONT][/COLOR]

---

### Post by nlona on 2019-03-31
> **michaelkey253 said:**
> Goodmorning everyone, e

I have installed Ubuntu 18.04.1 on an assembled PC for a few days, and unfortunately I can not get the motherboard's internal sound card to work. I have an additional USB sound card but it works, while the internal one does not. I have an ASUS Prime H270-PLUS motherboard that has an ALC887-VD internal sound card and I would need to make it work both for the rear sockets and especially for the two front sockets (headphones and microphone). Can you give me a hand? If you need some output I will be more than available. 
Thanks in advance

Try ```
 sudo apt remove timidity -y
``` 
Reboot & pray for &#127926;. If It did not work post some logs. 
```

alsamixer -V all 
``` with arrow keys move to mm & press m to enable them, then increase with pageup the bars to highest level, press esc. Now 
```

wget http://www.alsa-project.org/alsa-info.sh && sudo sh alsa-info.sh 
```

This will create a file in /tmp/ post it between   code tags

---

### Post by him610 on 2019-03-31
Please show the results, between code tags, of *inxi -F*

In your Volume Control utility, make sure you have the correct audio output device selected. Mine shows: (1) Built-in Audio Analog Stereo (motherboard chip, ALC892) and (2) GK104 HDMI Audio Controller Digital Stereo (graphics card). The audio through the output connectors on the backside of the motherboard and the front panel of your case originate from your motherboard chip, ALC887.

---

### Post by him610 on 2019-04-02
michaelkey253,

Here is a screen shot of two utilities, Alsamixer and Volume Control. Your system should look similar. My headphones are connected to the front panel. On this computer, I have an ALC887-VD audio chip.

---

### Post by shalemaci on 2020-01-20
Hello,

I have got also a problem with this ALC887 card (I am using Ubuntu 18.04.3 LTS):

The sound works but it switch automatically from speakers to headphones during few micro sec.
When I put a headphone in the front panel it works fine, also when I put the speackers jack in front panel it also works.
So this switch trouble only occurs when the jack's speackers is in the green line out, rear (audio interne - HDA intel PCH).

Please find a video below with the Alsamixer.

[https://streamable.com/j2w5q](https://streamable.com/j2w5q)

Thank you very much for your help,

---

