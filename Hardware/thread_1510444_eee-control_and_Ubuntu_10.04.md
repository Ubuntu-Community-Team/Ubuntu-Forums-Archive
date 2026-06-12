---
title: "eee-control and Ubuntu 10.04"
date: 2010-06-15
forum: Hardware
---

### Post by octavius on 2010-06-15
Yet, another n00b question. Please bear with me on this.

As I've read all over this and other forums, there are quite some troubles with the eee-control package and the latest release of Ubuntu.

I did install it with out any hassle from the developer's webpage from a deb file. Synaptic recognizes it as installed. I installed the control and the applet (the ascpi package refused to install). The applet icon appears in my notification tray area. It asks for my password every time I execute it or make any change.

The thing is that nothing happens... The hotkeys do nothing at all. The performance profiles do nothing, the same goes for the fan speed and volume/brightness controls... It does nothing at all. There's no error thrown. No apparent problems during installation...

How do I configure it? How do I make it do its job? And how do I make it run at start up?

Thanks for helping me being less of a n00b :guitar:

Update: I have an Asus EeePC 1201n if that helps at all. The ethernet and WiFi work, such as the graphics and everything as far as I'm aware.

---

### Post by octavius on 2010-06-16
And bump it...

Bump it harder.... And bump it.... :guitar:

Not even a hint???

---

### Post by shihkster1015 on 2010-06-26
gedit 
>  /etc/default/grub add
 > acpi_osi=Linuxto the line
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"so it becomes
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"then update grub

---

