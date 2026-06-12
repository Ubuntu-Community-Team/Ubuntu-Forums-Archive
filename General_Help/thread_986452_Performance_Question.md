---
title: "Performance Question"
date: 2008-11-18
forum: General Help
---

### Post by Cool Javelin on 2008-11-18
During boot up, I know there are a few login screens created in the background normally accessed by pressing Ctrl-AltF1 .. Ctrl_AltF6.

There are a few more (desktops) seen in on the applications bar that I can switch to giving me new, clean desktops.

When I switch to one of the background processes (say Ctrl_AltF2 for example,) I am presented with a login screen.

I am using a slow processor and want to eek as much performance I can from it.

My first question, Are these 6 background screens taking CPU time? I assume part of the multitasking scheme devotes some processor time looking to see if someone is logging in. If so, is there any benefit to not starting those background processes, and, how do I go about doing that?

Second, About those multiple desktops in the corner (near the clock.) Do those take more processor time too, or are they only virtual screens. I know if I have 3 desktops and 4 things running, I have 4 things no matter the number of desktops, but do the desktops require processor time?

Thanks.

---

### Post by kerry_s on 2008-11-18
processor time no
memory yes

linux uses memory to store the programs used, you can see the programs running by running "top" or "pstree" in a terminal.

the best way to get performance is to do a custom install and don't use desktop environments, use a window manager instead.

for now i would suggest just installing a light weight window manager to get use to, there are many to choose from.
some popular ones:

lxde (sudo apt-get install lxde) is growing in popularity and comes with a lot of stuff you would expect in a desktop. 

anything else will require you to setup and maybe add programs to get the extra functions.

examples:

fluxbox
openbox
wmaker
jwm
icewm
etc...

i'm a jwm user, i run on 450mhz 256mb ram, i use debian lenny custom install. pic

---

