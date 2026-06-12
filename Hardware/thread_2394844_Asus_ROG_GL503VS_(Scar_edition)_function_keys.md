---
title: "Asus ROG GL503VS (Scar edition) function keys"
date: 2018-06-22
forum: Hardware
---

### Post by animator34 on 2018-06-22
Hello there,

I would like to use this laptop with ubuntu for programming, but have hard times to get function keys to work. With generic hid driver only volume and multimedia keys are working. Cant increase or decrease brightness, turn off display, turn off touchpad, put nb to sleep, etc...

It is notebook from asus gaming ROG series.

I found out that drivers for ROG series are in latest linux kernel 4.17 as asus-hid. This driver is not loaded after ubuntu starts, only the generic one. I searched for the problem in the source code in hid-asus.c. Found out that this keyboard has different deviceId (1866). I've added this deviceId to hid-ids so it can be identified by the driver. I recompiled the kernel and installed it successfully. In login screen the keyboard is dead. **After login keyboard works**. 

Almost every function key is now registered (sleep, touchpad disable). Brightness was still not working... I tried ```
acpi_listen
``` if the function keys are registered. They are! So brightness can be somehow controlled I think. This laptop does not have optimus and neither IGPU graphics. Only nvidia gtx 1070 pascal dedicated graphics (driver nvidia-driver-396).

Can someone point me to the right direction how to get this to work also in login screen ?

Also keyboard backlight can't be increased or decreased but the event is being triggered.

Here is dmesg output:
```

[FONT=arial][COLOR=#333333][    [/COLOR][COLOR=#008080]8.951491[/COLOR][COLOR=#333333]] asus [/COLOR][COLOR=#008080]0003[/COLOR][COLOR=#333333]:[/COLOR][COLOR=#008080]0B05[/COLOR][COLOR=#333333]:[/COLOR][COLOR=#008080]1866.0006[/COLOR][COLOR=#333333]: Asus failed to request [/COLOR][COLOR=#0086B3]functions[/COLOR][COLOR=#333333]: -[/COLOR][COLOR=#008080]75
[/COLOR][COLOR=#333333][    [/COLOR][COLOR=#008080]8.951511[/COLOR][COLOR=#333333]] asus [/COLOR][COLOR=#008080]0003[/COLOR][COLOR=#333333]:[/COLOR][COLOR=#008080]0B05[/COLOR][COLOR=#333333]:[/COLOR][COLOR=#008080]1866.0006[/COLOR][COLOR=#333333]: Failed to initialize backlight.[/COLOR][/FONT]

```

So the backlight is obviously not working with the driver. Also there is some error as it failed to request functions, maybe that is the reason the keyboard is not working in the login screen ?

Maybe I could make the driver work but I don't have any documentation for the asus keyboard, i don't even know how can i dump it from windows (mainly the initalization byte sequence and function request sequence, maybe it differs).

If there is someone who can help me I would appreciate it.

---

### Post by fsacrini on 2018-10-14
Hey Man, did you have any news? I would like to install ubuntu on my GL503vs again but I had the same issue....Just Linux Deepin worked well in my computer to be honest.... Almost everything works... Just the keyboard lights that didn't...

---

### Post by kitegx on 2018-10-25
Hi! First of all, thanks @animator34. I was able to solve my own keyboard issue by doing the same as you. My Laptop is a slightly different model, so my mute key doesn't work.

I'm not on Ubuntu, but I had the same issue: No brightness control on Gnome (either by FN keys or slider). I tried many things but it turns out brightness controls work just fine on KDE Plasma so I'm using that now. I thought that maybe it was an Nvidia/Wayland issue since I think Gnome uses Wayland by default, but I ran Gnome without Wayland (Xorg session) and brightness still didn't work, so I gave up and started using KDE Plasma instead.  I'm also using the proprietary Nvidia drivers btw.

---

### Post by kitegx on 2018-10-30
Hi again! here's the fix for the screen brightness: [https://askubuntu.com/questions/1057783/no-brightness-control-18-04-lts-sys-class-backlight-is-empty](https://askubuntu.com/questions/1057783/no-brightness-control-18-04-lts-sys-class-backlight-is-empty)

With that I can finally switch back to gnome, brightness works like a charm. Hopefully it'll work for you :D

---

### Post by animator34 on 2018-12-03
Hi @kitegx. When you applied my fix to make your keyboard work, did you manage to solve the issue with keyboard being dead in the login screen ? Or did you even have that problem ?

Thanks for the screen brightness fix, will look into it later :)

---

### Post by lpalazzotto on 2018-12-29
> **kitegx said:**
> Hi again! here's the fix for the screen brightness: [https://askubuntu.com/questions/1057783/no-brightness-control-18-04-lts-sys-class-backlight-is-empty](https://askubuntu.com/questions/1057783/no-brightness-control-18-04-lts-sys-class-backlight-is-empty)

With that I can finally switch back to gnome, brightness works like a charm. Hopefully it'll work for you :D

It does not work with my Xps 15. Is that because of the different machine? It is so frustrating this FN keys issue.

---

