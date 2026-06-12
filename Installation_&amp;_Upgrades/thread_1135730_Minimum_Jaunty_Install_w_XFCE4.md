---
title: "Minimum Jaunty Install w/ XFCE4"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by humbug01 on 2009-04-24
Hi all,

I did this with Intrepid recently and it worked fine so I'm trying it with Jaunty and it's not working. Here's what I've done and what I'm trying to do.

I'd doing a barebones install of the ubuntu packages then adding xfce4. From there I'll only add 4-5 programs like Firefox and Thunderbird for an older laptop for a relative who will only use the box for emails.

I'm using the latest Jaunty alternate CD.

1. Intall the CLI, base system only.

2. Reboot.

3. Change the /etc/apt/sources.list only by enabling the CDROM as a source (i.e., remove the # in front of that line).

4. Then the main code to get the wm and main gui stuff:

```
sudo aptitude install xorg xfce4 gdm synaptic
```

What happens here is that xorg and gdm are installed but not xfce.

Any ideas?

Thanks in advance!

Steve

---

### Post by mwacky on 2009-04-24
is xfce4 ready for Jaunty?  Can you see any version of xfce in Synaptic Package Manager?

---

### Post by humbug01 on 2009-04-24
Well, I went through it again (i.e., install xfce4) and including updating aptitude and it downloaded lots of files though there was one aptitude failed to get.

When I reboot, all I get is the gdm login screen and a command line in a different screen resolution. I don't know how to run synaptic from here.... :(

EDIT: OK, typed "sudo synaptic" at the prompt and it came up and is working now. Thanks for the tip--I'll play with synaptic and see what happens....

---

### Post by humbug01 on 2009-04-24
Thanks to your suggestion MWacky, I could see through Synaptic that only about 20 of the 48 XFCE4 files were not not getting installed because of the volume of traffic today. I just kept at it and everything was finally downloaded and installed. Booted up with a nice, fast simple XFCE4.6. Looks great!

---

