---
title: "more fps in glxgears in old driver -- meaning?"
date: 2009-10-12
forum: Hardware
---

### Post by thekronisk on 2009-10-12
Hi.

I'm currently running Ubuntu Hardy.
My graphics card is ATi Radeon X850X Platinum Edition.

Recently I installed the ATi drivers using Envy. Everything went fine, and I ran glxgears > Envy and got logged fps ~9000.

Then I found a guide ([http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method))
for installing the newest driver (I knew from 3rd part that ATi Catalyst 9.3 was the latest functioning driver for my legacy card) on your system. I then tried that. Everything went fine, and I ran glxgears > ATi9.3 and got logged fps ~5000.

I then read on wikipedia, that the opengl drivers were substantially updated for 3rd. So my question is this:

Can I by the fps from glxgear be certain that a certain driver is better than another? I am a bit of a gamer, and it's to that im curious -- is it possible the newer drivers (with lower fps) actually is better for my games?

Thank you for reading, I'm looking forward for your input

Regards,


Thomas

PS. If you were wondering what games: StarCraft: Brood War (ICCUP), Warcraft TFT (DotA), Counter-Strike 1.6, Quake 3 Arena.

EDIT:
I just ran cat /var/log/Xorg.0.log | grep 'Driver Version'

And got:
(II) ATI Proprietary Linux Driver Version Identifier:8.59.2

Does this mean I'm not running ATi Catalyst 9.3? The driver from EnvyGT says 8.6 ..hmm

---

