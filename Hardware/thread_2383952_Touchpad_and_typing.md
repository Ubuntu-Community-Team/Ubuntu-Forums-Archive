---
title: "Touchpad and typing"
date: 2018-01-31
forum: Hardware
---

### Post by whenelvisdied on 2018-01-31
Hi Folks,

Running Ubuntu 17.10 on an Asus Transformer TP300L. Everything has worked fine or has been easily fixable. Except...

When I am gaming (using WASD), my touchpad shuts off, which is kind of a problem in First Person games. 

I have scoured the net looking for a solution, but am still coming up empty. I have been made to understand that I need to fix something using xinput, but xinput does not show that I have a touchpad. Libinput does show a touchpad, however, which is strange to me. Here's my xinput output

```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:13                     	id=6	[slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:13            	id=7	[slave  pointer  (2)]
&#9116;   &#8627; xwayland-touch:13                       	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; xwayland-keyboard:13                    	id=8	[slave  keyboard (3)]
```

Unless I am mistaken, that is only showing the touchscreen on my Asus (which I don't use), not the touchpad. 

Here's my touchpad, visible on libinput, with "disable-w-typing" clearly "enabled", hence the problem:

```
Device:           ETPS/2 Elantech Touchpad
Kernel:           /dev/input/event5
Group:            11
Seat:             seat0, default
Size:             99x54mm
Capabilities:     pointer 
Tap-to-click:     disabled
Tap-and-drag:     enabled
Tap drag lock:    disabled
Left-handed:      disabled
Nat.scrolling:    disabled
Middle emulation: disabled
Calibration:      n/a
Scroll methods:   *two-finger edge 
Click methods:    *button-areas clickfinger 
Disable-w-typing: enabled
Accel profiles:   none
Rotation:         n/a

```

Any thoughts? What's going on here?

---

### Post by TheFu on 2018-01-31
X11 and xinput aren't used unless you use xorg.  17.10 uses Wayland by default and it appears there are a few issues with the xinput replacement.
[https://askubuntu.com/questions/1000985/alternative-to-xinput-for-wayland-ubuntu-17-10](https://askubuntu.com/questions/1000985/alternative-to-xinput-for-wayland-ubuntu-17-10) - nobody answered.

[https://wayland.freedesktop.org/libinput/doc/latest/faq.html](https://wayland.freedesktop.org/libinput/doc/latest/faq.html) has some xinput ideas.

It may be possible that if you switch back to X11/xorg instead of wayland, then it will work like before.

---

### Post by whenelvisdied on 2018-02-02
Thanks TheFu, those links helped. 

As near as I can tell, Wayland is configured either using gnome-control-center as a GUI or gsettings from the command line. There is unfortunately no GUI switch for touchpad disabling while typing. 

HOWEVER, gsettings allows you to configure the various schemas/aspects of gnome more directly. So here's what I did:

1.)open a terminal
2.)enter command gsettings list-schemas | grep touchpad
That pulled up the following entry:
> org.gnome.desktop.peripherals.touchpad

3.)enter command gsettings list-keys org.gnome.desktop.peripherals.touchpad
That showed the following list of adjustable keys within the schema:
```
touchpad
send-events
natural-scroll
tap-to-click
two-finger-scrolling-enabled
left-handed
click-method
speed
scroll-method
tap-and-drag
edge-scrolling-enabled
disable-while-typing

```

4.)The key "disable-while-typing" is true/false (you can find this out by entering gsettings get org.gnome.desktop.peripherals.touchpad disable-while-typing). On my machine it's set to true, so all you have to do is enter the command 
gsettings set org.gnome.desktop.peripherals.touchpad disable-while-typing false

Presto! Keys and touchpad should play nice together!

---

