---
title: "Asus PRIME B250M-A or ROG STRIX B250G GAMING"
date: 2017-04-29
forum: Hardware
---

### Post by sed_faster on 2017-04-29
Hello folks,

I am thinking buy one of this board to run Ubuntu: [https://www.asus.com/us/Motherboards/PRIME-B250M-A/](https://www.asus.com/us/Motherboards/PRIME-B250M-A/) or [https://www.asus.com/us/Motherboards/ROG-STRIX-B250G-GAMING/](https://www.asus.com/us/Motherboards/ROG-STRIX-B250G-GAMING/)
But I'm not sure which one is the best! 

Which would they choose?

Note:
I am thinking built this setup:
         [TABLE]
[TR]
[TD][COLOR=#000000]Asus ROG Strix B250G Gaming[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000000]Intel Core i5-7500 Quad-Core 3.4GHz c/ Turbo 3.8GHz 6MB Skt1151[/COLOR][/TD]
[/TR]
[TR]
[TD][COLOR=#000000]Corsair VS550W[/COLOR][/TD]
[/TR]
[/TABLE]

Thanks

---

### Post by ccmamer on 2017-04-30
I can't get the onboard sound to work on the Asus PRIME B250M-A, not sure about the other one but I would anticipate problems there too - boards are just too new yet. 
If you're going to go with one of these you might be best off to get a separate soundcard that is known to be linux compatible.

---

### Post by Yellow Pasque on 2017-04-30
> **ccmamer said:**
> I can't get the onboard sound to work on the Asus PRIME B250M-A, boards are just too new yet.

It uses a Realtek ALC887 codec. They've been around for a while and there's no reason the sound shouldn't work on any modern kernel, even if the mobo itself is very recent.

As for the ROG board, it uses a Realtek ALC1220, which requires kernel 4.11, or updating your current kernel with the latest HDA modules: [https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by sed_faster on 2017-05-03
Thanks for your comments!

I am thinking change the board to this one: [https://www.asus.com/Motherboards/PRIME-B250-PRO/specifications/](https://www.asus.com/Motherboards/PRIME-B250-PRO/specifications/)

The sound board and board lan it is:

Realtek® RTL8111H, 1 x Gigabit LAN Controller(s)
ASUS LAN Guard

and 

Realtek® ALC887 8-Channel High Definition Audio CODEC *[SUP]4

What do you think?

Note: I am change the board because with this product I can has three differents ways to connect my screens, through vga, hdmi and dvi :p

thanks
[/SUP]

---

### Post by sed_faster on 2017-05-06
HEllo folks,

I think I should keep the warning on this topic.

My current setup is

Asus Prime B250 Pro
I5 intel 7500
8 GB Ram

After I install through usb Lubuntu 16.10 my system started so good! But, after I ran the first biggest - sudo apt-get update - the system started without panel, lxpanel -- where has the menu and clock and another stuffs! And my layout keyboard changes, to a different which I chose when I put my name and name computer, during installation system.

This is result from my uname -a
Linux enoworld 4.8.0-51-generic #54-Ubuntu SMP Tue Apr 25 16:32:21 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by asbc-paulista on 2018-03-29
I'm in the same situation! I intend to buy one of those motherboards and I have the same doubt! One year passed since this post. Do somebody has an answer to the question? Does it work or not?

---

### Post by sed_faster on 2018-03-29
Hello, I bougth the setup:

Asus Prime B250 Pro
I5 intel 7500
8 GB Ram
Two SSD 120GB Kingston

If do you know any battery test, like benchmark or commands to certificate if all drivers are installed on the system, which I can do my system (lubuntu 16.04 LTS) I appreciate the share.

---

### Post by asbc-paulista on 2018-03-30
I am about to buy a ROG STRIX B250G GAMING, but I still had no a final response about compatibility with Linux (sound, video and lan). What do you think?

---

