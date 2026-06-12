---
title: "Nvidia 8800"
date: 2014-09-13
forum: Hardware
---

### Post by michael170 on 2014-09-13
Hello,

I am taking my first steps into Linux.

I have an old Dell Insprion 530 with onboard graphics.

I downloaded Ubantu and ran it off a 2 gig USB stick  ..... no problems.

I then installed an nvidia 8800 board because I wanted to use dual monitors.

Problem .... when I start by having only one monitor plugged into the card, no problems.  The single monitor comes up fine.

I then plug in the second monitor ... no problem, acts line one seamless screen.

The  problem arises when I have both monitors plugged in and try to boot.   The ubantu symbol comes up with the dots but then just sits there for a while, then nothing.

How can I fix this so that I can leave both monitors plugged in and boot????


Thanks so much .... Mike

---

### Post by redrumrogue on 2014-09-13
Hi,

While it's hanging on that boot screen, if you press ESC on the keyboard it should hide the boot screen and show you the terminal output for the boot process.  This might give you a clue as to where it's got stuck.

---

### Post by grahammechanical on 2014-09-13
If you are using an Nvidia proprietary video driver, then you will have an Nvidia Xserver settings manager utility also installed. It will have an option to detect displays. If you are using the Nouveau open source video driver, then System Settings will have a Display utility that will also have a detect displays option. Have you used either of those utilities to detect the displays?

Regards.

---

