---
title: "Hauppauge MCE Remote Kit and LIRC"
date: 2010-07-22
forum: Hardware
---

### Post by M4he on 2010-07-22
Dear ubuntu community,

I've got a Hauppauge MCE Remote Kit, which looks like this:
[ATTACH]164242[/ATTACH]
and want to use it with LIRC to control Rythmbox.

It's an USB receiver and I don't know what transmitter to choose from the list when installing LIRC.
I randomly chose "Microsoft Windows Media Center V2 (usb) : Direct TV Receiver" as transmitter, "Hauppauge TV card" as remote and
```
sudo cat /dev/lirc0
```throws out some random symbols when pressing any button on my remote.

Does anybody know how to get this remote control kit working properly on ubuntu and what configs to choose for lirc?

Thanks in advance.

---

### Post by IcarusR on 2010-07-22
This page has info on getting lirc working.

[https://help.ubuntu.com/community/LIRC]("https://help.ubuntu.com/community/LIRC")

You need to create an .lircrc file to get it to control programs.

Some info & examples of .lircrc half way down this page in the section "Applications and LIRC Support"

[http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/]("http://www.g-loaded.eu/2006/01/10/how-to-configure-and-use-lirc/")

---

### Post by M4he on 2010-07-22
Tried that and chose different options with 'dpkg-reconfigure lirc' but still 'irw' has no output in the terminal...

---

### Post by m_duck on 2010-07-22
I've recently bought the same remote for my media centre (WIP!). It worked for me when I installed the **lirc** package (and its dependencies) from synaptic and then chose the remote option which was something along the lines of: "Windows Media Centre Receivers / Transmitters - All" near the bottom.

After that, firing up irw recognised all of the buttons.

HTH

---

### Post by M4he on 2010-07-23
Thanks a bunch m_duck! That was the hint I needed, it works now! And for all other ppl who have the same issue:
[SIZE=2]
[/SIZE] [SIZE=2]For the **Hauppauge MCE Remote Kit** you need to choose:[/SIZE]
```
Windows Media Center Transceivers/Remotes (all)
``` as Remote control and
```
Microsoft Windows Media Center V2 (usb) : Direct TV Receiver
``` as IR transmitter.

...solved.

---

