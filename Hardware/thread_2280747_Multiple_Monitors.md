---
title: "Multiple Monitors"
date: 2015-06-02
forum: Hardware
---

### Post by spinner101 on 2015-06-02
Hi,

I've got a oldish Dell XPS L501X i3 based 64bit laptop with a GeForce GT 420M/PCIe/SSE2 graphics card.

I'm running 14.04 desktop ubuntu with default desktop settings except I've installed the recommended Nvidia display drivers.

I've got a separate Phillips 24 inch monitor that I'm plugging into the HDMI cable.

What I would like is to have two separate workspaces running on each monitor at each of the monitors optimal resolution.

What I've currently got is the desktop mirrored across both monitors with both monitors running at their optimal resolution.

If I change the settings as in to extend the desktop or really any other setup than this I get massive stretching of either display as it tries to extend on onto the other but they are so different in resolution that it's never going to work. 

I've moved from Windows 7 and the setup I had there was that I could have an application in one window and it was at it's resolution and then drag that application over to the other window and it would be at it's own resolution, this is the setup I would like to replicate if possible.

Thanks,

Tim.

---

### Post by snip3r8 on 2015-06-02
First question , What are you using to set the display settings? I would suggest maybe playing around with the Nvidia Settings manager to see if you can get an extended desktop with independant resolutions.

---

### Post by spinner101 on 2015-06-02
thanks for your reply.

I've tried using the NVIDIA X Server Settings application and I've noticed when I plugin the HDMI cable it just has the one screen so initially X Screen 0 is the laptop screen with the correct resolution, then when I plug in the second larger monitor X Screen 0 is now the only screen available and the resolution on both monitors which are mirrored is wrong. I would of thought there would be two monitors on the layout screen but there isn't.

---

### Post by snip3r8 on 2015-06-05
Hey , sorry about taking so long to reply. Have we solved the issue or do we need to dig a little deeper?

---

### Post by spinner101 on 2015-07-05
Unfortunately not, I've attached two screen shots one from the Screen Display settings and one from the NVIDIA X Server settings display. 

[IMG]http://s23.postimg.org/xthpr7jcb/Screenshot_from_2015_07_05_09_40_27.png[/IMG]

[IMG]http://s24.postimg.org/j03xlthlh/Screenshot_from_2015_07_05_09_43_09.png[/IMG]

So both screens are displaying at the correct resolution, the issue is I would like to have them either extend the same desktop or run two different desktops. When I move the smaller monitor in the display settings dialog to the left of the larger one it seems to stretch the display of both of them and they both become unusable. At the moment they just duplicate the same desktop at their own resolution with the smaller one being duplicated over the top of the larger one in the larger display but everything that is displaying is at the correct resolution. Seem's like it's almost there but I'm missing some vital last part.

---

### Post by spinner101 on 2015-07-29
bump - does anyone have any ideas on what I'm doing wrong with this ? I've tried what I think are most of the settings I can change and they never end up with the desired outcome which is each screen the one on the laptop and the external monitor running at their optimum screen resolution either as an extended single desktop or as two separate desktops.

---

