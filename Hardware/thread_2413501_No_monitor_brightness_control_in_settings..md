---
title: "No monitor brightness control in settings."
date: 2019-02-26
forum: Hardware
---

### Post by 0cs935-bill on 2019-02-26
I just transitioned from a laptop to a desktop setup to run a specific video board (Quadro P400/PCIe/SSE2) for CAD. Now, I have no monitor brightness control and the monitor itself (ASUS brand that displays as "Ancor Communications 19" via settings) has no control buttons. 

I can use :
  xrandr --output DP-1 --brightness 0.5
at a terminal but would like to have a control via the GUI.

I intend to run a 32" monitor in a dual monitor configuration soon, and would like to control its brightness also.

Why do I not have a control for the single monitor and how to get a control?

---

### Post by Autodave on 2019-02-26
I couldn't find a lot of info about that monitor. However, I personally have never see a monitor that did not have setup buttons on it.  You usually have to scroll through a few menus to get to it, but it is always there.

---

### Post by 0cs935-bill on 2019-02-28
With or without physical controls, I still want the software control via the GUI I was accustomed to on the laptop. 

As it is, I have to use the xrandr command several times a day as the screen brightens to max if I bring it out of blank screen mode. I've also seen it brighten to max while on YouTube. I can't explain these occurrences, but I need an agent to prevent these occurrences so as to not sear my eyeballs.

---

### Post by him610 on 2019-02-28
If you have Nvidia driver installed for Quadro P400 then you should also be able to navigate to Settings>Nvidia X Server Settings then adjust the configuration and controls of the monitor. Use xrandr to quickly observe monitor settings.
I have Nvidia gfxcards in four computers and monitors of various vintages and capabilities, all with Nvidia drivers downloaded from the repository. I use the Nvidia X Server Settings utility to adjust monitor settings on all of them.
Make sure you have good cables.

---

### Post by 0cs935-bill on 2019-03-01
I have the Quadro driver installed from the Nvidia site - version 410.93 . The Ubuntu driver was problematic.

I went through the Nvidia provided tool and see no way to set monitor brightness.

Today, I was web surfing the news and came to a site that wanted to play a video. As soon as I hit that site, my screen brightness flared to 100%. I used xrandr to reset brightness. This is annoying. I hoped the O/S would allow me to specify brightness and have it enforce it as was my experience on a laptop.

---

