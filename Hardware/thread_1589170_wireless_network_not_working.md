---
title: "wireless network not working"
date: 2010-10-06
forum: Hardware
---

### Post by aneesha on 2010-10-06
i just installed the new ubuntu 10.04 desktop edition .. i cant connect ot the internet .. it doesnt detect wireless networks and btw do i need to install any packages for that>?? .. were do i find packages?

---

### Post by Elaztic on 2010-10-06
Most wireless work out of the box but you can be unfortunate that you have a wireless card with poor support.

There are however several things you can do to diagnose the problem.

First of all please post information about your wireless card:
Is it internal e.g. in a laptop or is it a usb or pci-card in a desktop?

If it is an internal card or a pci-card you can find info about it with the command lspci from the commandline (look for Terminal in applications -> accessories).
If it is a usb dongle use the command lsusb.

The command dmesg will also provide valuable info.

First of all try to find the wireless applet in your taskbar. Is it there with an exclamation mark or not there at all? If there can you see other networks?
You can start it from the terminal with the command nm-applet.

Before we do further diagnosing please post the output of the above commands and provide as much info as you can.

---

