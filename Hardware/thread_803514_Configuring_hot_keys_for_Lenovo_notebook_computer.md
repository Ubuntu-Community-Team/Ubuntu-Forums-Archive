---
title: "Configuring hot keys for Lenovo notebook computer"
date: 2008-05-22
forum: Hardware
---

### Post by PremiumName on 2008-05-22
Hi, I am using Debian 4.0r3 &#8220;etch&#8221; (stable).

I have a Lenovo 3000 N100 notebook computer with some function keys (Fn + <key>) on a Norwegian/Danish keyboard that I would like to have configured. I do not know the required configurations or syntax to achieve this.

Below I list the keycodes (at least those that are known) and the action I would like the keys to preform. I would really appreciate help with configuring this!

These keys register with keycodes (listing order) but with NoSymbol in $ xev:
[list][*]144 media previous
[*]153 media next
[*]160 mute audio
[*]162 media play / pause
[*]164 media stop
[*]174 decrease volume
[*]176 increase volume[/list]
These keys do not register a keycode, and I have listed them by the unique...whatever that shows up in $ dmesg when I press the buttons.
[list][*]e016 disable wireless interfaces (bluetooth and wi-fi)
[*]e017 sleep (to RAM)
[*]e018 hibernate (to harddrive)
[*]e034 Lenovo Care-button (lanuch konsole, and kcontrol in combination with shift)
[*]e041 something to do with dual screen[/list]
:wink: Thanks in advance for all help.

[color="Gray"]&#8212; originally posted at [Debian user forums](http://forums.debian.net/viewtopic.php?t=27062).[/color]

---

### Post by crazy ivan on 2008-08-22
As I see the situation in Germany (kind of close to Belgium, quoi?):

Asus ships the EEEEEE PCs
there are some Acer Notebooks with Linpus (both rather simplified distros)
and Lenovo comes with Suse Linux Enterprise Desktop (Gnome-compiz)


Anyhow I'd go for a preinstalled Dell - if I had a choice - since no distro even comes close to ubuntu. So you have to delete them just as you would Vista.

Since I could not wait for the notebook to be assembled by Dell, I bought a lenovo Thinkpad R 61 with SLED. After 5 hours of normal use (the "getting started tour" is neat though) and autoupdate it crashed the updatemanager, crashed nautilus, removed the video driver and I'm trapped to console until I figure out the syntax of textbased browsing and package installing (wget, lynx,rpm... ). Ready to format =D>

---

