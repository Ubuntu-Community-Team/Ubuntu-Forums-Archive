---
title: "ATI all i wonder 128 pro tv capture support"
date: 2005-01-06
forum: Hardware &amp; Laptops
---

### Post by buzst on 2005-01-06
I am trying to setup an ATI all in wonder 128 Pro AGP video card (The card currently works fine in warty as a display device) to support its capture and tuner functions. 

Downloaded and installed Gatos via synaptic from the repository without problem.
When I run Gatos-config it returns Unable to open /etc/XF86Config or /etc/X11/XF86Config. This I understand because warty seems to use XF86config-4 not XF86config (please correct me if I'm wrong I am new to linux). Anyway, gatos-config  includes the option -X to allow changing the path to xfconfig, but i can not get it to allow changing the path the new target file xfconfig-4. 

Anyone have any ideas?

 has anyone setup this card and software successfully in warty? 

Am I going down the wrong path with gatos and should I be using something else? 

Thanks in advance for the help.

Buz

---

### Post by tiiim on 2005-01-06
[QUOTE=buzst]I am trying to setup an ATI all in wonder 128 Pro AGP video card (The card currently works fine in warty as a display device) to support its capture and tuner functions. 

Downloaded and installed Gatos via synaptic from the repository without problem.
When I run Gatos-config it returns Unable to open /etc/XF86Config or /etc/X11/XF86Config. This I understand because warty seems to use XF86config-4 not XF86config (please correct me if I'm wrong I am new to linux). Anyway, gatos-config  includes the option -X to allow changing the path to xfconfig, but i can not get it to allow changing the path the new target file xfconfig-4. 

Anyone have any ideas?

 has anyone setup this card and software successfully in warty? 

Am I going down the wrong path with gatos and should I be using something else? 

Thanks in advance for the help.

Buz[/QUOTE]
 im not an expert in this area but the obvious question will be are you doing this as root or just you? in order to change important files you need to be root.

So in terminal you have to write

sudo [command]

or open up a root terminal.

If you are then i pass the baton to someone else :)

---

### Post by buzst on 2005-01-06
Tiim,
Thanks for the quick reply, 

yes I ran "sudo gatos-config =x /path". Sorry I should have made that clear.
Thanks,
Buz

---

