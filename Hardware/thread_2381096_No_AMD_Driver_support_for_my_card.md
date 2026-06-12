---
title: "No AMD Driver support for my card"
date: 2017-12-26
forum: Hardware
---

### Post by m.squared on 2017-12-26
Hi guys,

I'm running Ubuntu Mate 17.10 on a Dell Inspiron 15 5999 that I bought in 2015, with an AMD Radeon R5 M335 graphics card. Having checked with AMD, they only support my card if I use Windows, which I'm not prepared to do, and so I'm looking for someone to point me in the right direction of open source drivers for my card, if they exist, and how I might go about installing them. At the moment I'm relying on my Intel integrated graphics chip and the screen-tearing is horrendous, even if I scroll too fast on something as simple as a webpage, for example. Any help would be appreciated.

Thanks!

---

### Post by Yellow Pasque on 2017-12-26
They're probably already installed. Look at output of:
```
xrandr --listproviders
glxinfo
DRI_PRIME=1 glxinfo
```

---

### Post by m.squared on 2017-12-27
I'm not entirely sure what I'm looking for, but there aren't any AMD-related outputs jumping out at me. What should I see if the are installed? Is there a way to activate the card if it is installed?

---

### Post by Yellow Pasque on 2017-12-27
You're supposed to run the commands and copy/paste the output here.
> Is there a way to activate the card if it is installed? 
It may already be available, and then you can run programs on it using DRI_PRIME. Need to see output from commands to advise further...

---

### Post by m.squared on 2017-12-28
xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x64 cap: 0x9, Source Output, Sink Offload crtcs: 3 outputs: 2 associated providers: 1 name:modesetting
Provider 1: id: 0x3f cap: 0x4, Source Offload crtcs: 0 outputs: 0 associated providers: 1 name:HAINAN @ pci:0000:01:00.0

glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4

DRI_PRIME=1 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4


I'm sorry I'm new to this kind of thing. There was also a huge list of glx extensions listed in the outputs of the glxinfo commands, do you need those too?

---

### Post by Yellow Pasque on 2017-12-28
My apologies. I should have trimmed the output of glxinfo.
```
glxinfo | grep string
```

Anyway.. The important part is that the AMD card is available ("Hainan" is an AMD codename). If you want to run something on the AMD card:
```
DRI_PRIME=1 programname
```

---

### Post by m.squared on 2017-12-29
Thank you very much! Just out of curiosity, is there some way to have it in the DRI_PRIME=1 state by default?

---

### Post by Yellow Pasque on 2017-12-29
Yes, but you should note that it will probably eat more battery and make more heat/noise:
[https://askubuntu.com/questions/922877/run-a-command-line-program-with-an-environment-variable](https://askubuntu.com/questions/922877/run-a-command-line-program-with-an-environment-variable)

---

### Post by m.squared on 2017-12-31
I was thinking as much, but this laptop is more of a workstation machine than a portable notebook anyway. Thanks so much Temujin!

---

