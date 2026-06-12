---
title: "Hardware functionality problems with Lenovo S10-2"
date: 2010-01-17
forum: Hardware
---

### Post by MilchFlasche on 2010-01-17
Hi All,

I had an Asus Eee PC 901 which works almost flawlessly with Kubuntu 9.10 --- before last week, when suddenly my second SSD seemed to have some bad sectors :(

Anyway, last week I have bought a Lenovo S10-2, which looks more pretty than Eee PC classic models. But I had also been getting prepared to face some hardware incompatibility during the transition, and I hope to get support and advice on the forum. Below I will list a summary regarding the performance of most of hardwares and hotkeys of this netbook with Kubuntu 9.10 (I'm not sure if all of the status are applicable to Ubuntu, which are to be confirmed by Ubuntu users).
[SIZE="5"][B][U]
Things working:[/U][/B][/SIZE]
[LIST]
[*]Touchpad: works okay, although Synaptics driver does not support multi-finger tapping and scrolling (which work great on Eee PC 901 with Elantech touchpad) without emulation.
[*]Camera: not yet tested, since I haven't installed Cheese yet.
[*]Wireless: works after installing b43-fwcutter and Broadcom STA restricted driver.
[*]Sound: HDA Intel, ALSA or PulseAudio, no problems.
[*]LCD brightness: can be adjusted with hotkeys well. Only that I hope the minimum brightness can be darker, so that more power can be saved.
[*]Wired LAN: no problem at all.
[*]Suspending and hibernating: working, but Fn+F1 has no effect.
[/LIST]
_**[SIZE="5"]Things with problems:[/SIZE]**_
[LIST]
[*]**_Update: no problem with suspension/hibernation. But if we use PulseAudio, be sure to install pulseaudio-util so that the system can suspend successfully._**[COLOR="Wheat"]**_Suspension and hibernation:_** now this is a big problem. With newly installed Kubuntu 9.10, this netbook suspends and hibernates without problem, but these days I have no idea which package or update is blocking the whole mechanism, because now I can't even suspend the laptop with the Powerdevil (power manager) applet. Can anyone instruct me how to debug with the suspension procedure to see where the problem is? Without suspension to RAM, I have to turn off the computer every time I finish using it, and booting it next time with KDE+Compiz still takes some more than one minute (while I was used to the immediate resume with Eee PC).[/COLOR]
[*]_**Fan**_: It seems to be spinning all the time, but I don't think the temperature inside the cover needs such heavy vantilaiton. Is there any method to get it working dynamically? I don't like feeling that so many devices draining my battery, especially when the HDD is not SSD any more.
[*]_**Some Fn hotkeys**_:
[LIST]
[*]Fn+F1: not doing suspending or hibernating
[*]Fn+F5: not toggling wireless card on/off (the hard switch on the right side of the machine works well, though)
[/LIST]
[/LIST]

So may main concerns for the hardware support by Ubuntu to this netbook are the four problems above (suspending, its hotkey toggler, fan, and wireless toggler). If anyone can show me how to debug on anyone of them so that I am able to figure out if they are Ubuntu bugs or my local errors, I'd be appreciating :)

I don't know if there are any regression between Jaunty and Karmic, because I was using Mandriva 2009 then. But I do hope that (K)Ubuntu can support my newly bought S10-2 as well as the Eee PC family.;)

---

### Post by lev-unr on 2010-01-17
Hey congrats on the new purchase. I have the same netbook running ubuntu netbook remix.

I didnt see you mention anything about the mic. Does yours work?

---

### Post by MilchFlasche on 2010-01-18
> **lev-unr said:**
> Hey congrats on the new purchase. I have the same netbook running ubuntu netbook remix.

I didnt see you mention anything about the mic. Does yours work?
Hi pal, thanks for reminding. I have just installed Cheese and Audacity to test the camera and the mic, and here are the results:
**_Camera:_** works well, can be toggled through Fn+Esc (although no notification displayed)
_**Front Mic:**_ working, I can hear my voice recorded during playback in Audacity.
_**Mic (socket):**_ not yet tested, but I guess it won't be a problem.

Are you having problems with the mics? I have set Audacity to use PulseAudio as the playback and recording device (I have been using it as my main sound server for since Mandriva 2009.0, and find it working well, so you have to install it first if you don't have it.)

Does your S10-2 suspends and hibernates normally now? I can't make this functionality work since last week, and I can't find the reason. Every time I press the button in the Powerdevil applet, the HDD indicator only flashes a little, and then no response anymore. No trace can be found in dmesg.

---

### Post by MilchFlasche on 2010-01-19
I have found the reason why I couldn't suspend my laptop: I have installed PulseAudio, but without the pulseaudio-util package, so a "pacmd" command is missing which is essential for the pm-suspend scripts to work (because every hardware and service has to be suspended when doing suspension/hibernation. So there is no problem with the suspending mechanism of Ubuntu (actually it is very delicate and complete). Only that I still can't toggle suspending/hibernating through Fn+F1. I will update my previous post and the [wiki page](http://s10lenovo.com/wiki/index.php/Ubuntu_9.10).

---

