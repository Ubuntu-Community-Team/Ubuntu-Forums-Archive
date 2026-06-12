---
title: "what graphics card driver is used?"
date: 2014-09-17
forum: Hardware
---

### Post by demonic2 on 2014-09-17
Hi I would like to ask you something that is weird.

I am using ubuntu 14.04 on a dell laptop with an i7 onboard card and one amd extra gfx card.

In the Additional drivers it appears that my machine uses the amd card and has enabled (green light) on the [B]x org x server amd/ati dispplay driver wrapper xserver xorg video ati (open source tested)


[/B]But when I use the command: lspci -v | grep -i vga   it appears that I am using the intel intergrated one:[B]00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b) (prog-if 00 [VGA controller])


[/B]&#8203;Thanks in advance for any help!

---

### Post by gifford on 2014-09-17
You are using the open source driver instead of the AMD/ATI proprietary.

---

### Post by demonic2 on 2014-09-17
Yes thanks for your reply. I know that probably (not 100% sure) I am using the opensource ATI but why in the terminal output it is not appearing?

---

