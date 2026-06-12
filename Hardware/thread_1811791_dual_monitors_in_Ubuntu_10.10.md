---
title: "dual monitors in Ubuntu 10.10"
date: 2011-07-25
forum: Hardware
---

### Post by Synoc on 2011-07-25
running 10.10 on an asus 72gx. I want to use a second monitor. I plug it in, turn on the PC go into my NVIDIA settings for my 270m dedicated card, click on the "X Server display configuration" tab, click on the second (disabled) monitor, selected Separate X screen, click Save to X configuration File. it saves it ( near as I can tell, going through the file ), hit apply, and get the (Cannot Apply screen.) s first question is, "how do I restart the X without restarting the system, the second question is, why won't it apply the whole thing? the THIRD question is "since this is my laptop, what happens when the second monitor is NOT connected?

thank you

---

### Post by realzippy on 2011-07-25
1.Since you run nvidia-drivers,you should not need to restart the
Xserver,restarting nvidia-settings should be enough:

```
nvidia-settings -l
```

If I am wrong (not at my nvidia-machine atm),restart
Xserver (as it was default in the good old times)
with Alt+Ctrl+Backspace.In Natty you have to enable it as shown [here]("http://www.hackourlife.com/enable-restart-x-server-ctrl-alt-backspace-in-ubuntu-11-04-natty-narwhal/")

2.Shouldn't you hit "apply" *before* "SaveToXConfigurationFile" ?

3.Check it out and report.. :D

---

### Post by Synoc on 2011-07-25
> **realzippy said:**
> 1.Since you run nvidia-drivers,you should not need to restart the
Xserver,restarting nvidia-settings should be enough:

```
nvidia-settings -l
```If I am wrong (not at my nvidia-machine atm),restart
Xserver (as it was default in the good old times)
with Alt+Ctrl+Backspace.In Natty you have to enable it as shown [here]("http://www.hackourlife.com/enable-restart-x-server-ctrl-alt-backspace-in-ubuntu-11-04-natty-narwhal/")

2.Shouldn't you hit "apply" *before* "SaveToXConfigurationFile" ?

3.Check it out and report.. :D

CTRL+ALT+BS doesn't work, tried that before. 
oh an n-vidia settings window is the one that says "restart X server"

I somehow got it working all the same, I have it set to twin displays to get extended desktop... I have no idea how that works like that... but right now, it;s not broke so I won't fix it. but if you have any more pointers lemme know.

---

