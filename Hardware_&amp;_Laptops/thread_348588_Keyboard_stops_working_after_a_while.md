---
title: "Keyboard stops working after a while"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by Absurd on 2007-01-29
After I've done a while of work with open office my keyboard stops working and I have to restart (the mouse still works). The same thing happens after using VIM for a while as well. Does anyone know why this happens? Is it a KDE bug? 

I am using the latest JRE btw.

Today was the fourth straight day it has happened.

---

### Post by mawhidby on 2007-02-26
I have been having the same problems. Mine usually stops working if I leave the computer for a while and the screensaver comes on and the laptop is locked. Then when I try to sign back in, I can't enter my password, but the mouse is still working. This is also a serious issue for me, because I usually keep papers and programs open...

@Absurd, I see you posted this about a month ago. Have you been able to figure it out?

---

### Post by slakkie on 2007-03-12
Same problem overhere.
Are you guys running KDE with kdm, gdm or xdm?

I currently run it with kdm. I'm thinking about switching to xdm to see wheter the problem occurs with other display managers as well.

BTW, it could be related to this bug: [https://bugs.launchpad.net/ubuntu/+bug/63024](https://bugs.launchpad.net/ubuntu/+bug/63024)

So far I haven't been able to reproduce the problem (on purpose)..
I have been able to produce the problem on 3 machines..

---

### Post by slakkie on 2007-03-13
Same result when running KDE with GDM. Yesterday I found some more bugs on Launchpad which describes the behaviour we are seeing.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/40711](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/40711)
[https://bugs.launchpad.net/ubuntu/+bug/58884](https://bugs.launchpad.net/ubuntu/+bug/58884)

---

### Post by unni on 2007-03-15
I too have the same problem. I had been using Mandriva 2007 for the past 3 months. I moved to Kubuntu 6.10 ten days ago. Initially, I didn't notice this problem. But, during the past 4 days, it has occured atleast 15 times. As I was typing this, it happened and I had to reboot and retype. But, in my case, **it _always happened_ when I am posting something in a forum, using Firefox 2.0.0.2** (downloaded from Mozilla site, not the one from repository). My keyboard is a Microsoft Comfort Curve USB keyboard. Thinking that it is a USB related problem, I attached my PS2 keyboard also. Even then, it occured. When this happens, I am unable to press key combinations except <Alt><SysRq><U> &  <Alt><SysRq><B>. I didn't try other  <Alt><SysRq> combinations. But (most) other combinations including <shift> don't work. Unlike your problem, my keyboard doesn't completely go dead. Instead, if I hold any key for sometime (about 4 seconds), the key press gets registered. This is true for both PS2 and USB keyboard. I didn't have any problem in Mandriva or in Windows. It has happened within 5 minutes of booting the system, and sometimes after 1 hour. There seems to be no relation with up time. I had chatted with my friends for 2 hours, and nothing happened. Despite this problem, I have decided to go with Kubuntu, because Ubuntu rocks:) .

---

### Post by blunile on 2007-03-15
have same problem with my kubuntu,

I was using Opera and pressed ctrl button for few seconds > it gave me some message that i didn't read ( about KDE shortcuts ) and then ..... its DEAD ..it doesn't type at all, no letters no shortcuts, just dead. [ I think i screwed the KDE keyboard configuration, but i'm not sure ]

the mouse works fine and every thing else is running smooth.

How can i know where is the problem ????

How can i fix this problem  ???  any help will be really appreciated  :(

---

### Post by netrati on 2007-04-09
I'm also having the same problems described in Bug #58884, [https://launchpad.net/ubuntu/+bug/58884](https://launchpad.net/ubuntu/+bug/58884). I've tried adding the notsc option to the kernel, but then my laptop fails to boot hanging on /scripts/init-bottom. I love Ubuntu, but I can't keep using it like this. :confused:

---

