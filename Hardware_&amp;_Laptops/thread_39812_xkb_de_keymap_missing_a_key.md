---
title: "xkb de keymap missing a key"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by rioki on 2005-06-06
Hi, 

I have a litle problem / bug that is quite anoying. In the german xkb keymaps there is missing a key. It is the key with with the grater then, smaler then and pipe symbols. This is for alle 3 german keymaps. I checked if the key actualy works (with xkb) and with the english keymap it works. 

By the way, it works with the kernel map... on tty1 for example...

Anyone has a idea where the problem could be resolved? I would fix it and send a patch, but I haven't messed around with the X server and components (yet).

On the side I would like to note that the hadware suport is great. This is the only distro that suports my wifi kard out of the box (madwifi) and nvidia driver is zero hasle. Keep up the good work...

Sean Farrell aka rioki

---

### Post by rioki on 2005-07-03
Ok I got my problem solved... But I don't know how.

The problem seems to be somewhere betwen Gonome and Xkb.

What I did:

In the xorg.conf file I set
Option          "XkbDisable" 
for my Keyboard InputDevice. The Gnome complaind of not having Xkb. And I had a us keyboard. Then I put
Option          "XkbLayout"     "de"
 and I still had a us keyboard. (mmm that wasent like that XFree86) 
Comented Option          "XkbDisable" out so that Xkb would run. 
Then Gnome complained about having different settings. And asked if I wanted to use the Xkb or the Gonome settign. At first it didn't work. 
I then set the Keyboard in Gnome to German. 
Altough Gnome complainde once again, it now workd (By selecting use Xkb settigns). 

Since then I have no problems anymore. 

The odd thing is it can't be an update or something, because I did not update the system. 

This was realy odd.

---

