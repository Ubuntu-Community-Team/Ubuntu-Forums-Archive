---
title: "[SOLVED] HELP!!! I screwed up my monitor! Ubuntu 8.04"
date: 2008-05-16
forum: Hardware
---

### Post by ThePHPguy on 2008-05-16
Hello I was trying to set up a dual monitor and ended up screwing up my laptop monitor :(

This is what I did.

1.) I went to (System > Preferences > Main Menu) 

2.) From here I chose (on the left) the option "Others" and checked "Screens And Graphics"

3.) Inside of the "Screens And Graphics" area I *think* I found my second monitor and changed its Model to match its model and changed the resolution.

4.) After that I clicked "Ok" and it said I must log out to see the changes so I did that.

5.) When I logged back in my background images was stretched across both monitors and on the second monitor I could move my mouse up down and to the right to pan inside.

6.) I didn't like that so I went back to the "Screens And Graphics" and tried to change it back... (this is where the BIG problem occurred.)

7.) I couldn't change my resolution back to "1280 X 800" I could only choose "640 X 480" :confused:

8.) So I started changing my model to get the correct resolution but I couldn't so here I am...

Right now I'm on my sisters laptop and its the same as my laptop (Acer Aspire 3690) and I'm wandering if I can just copy a file on her's and transfer it over to mine.

Thanks in advance.

EDIT: Also the color is different too.

---

### Post by overdrank on 2008-05-16
> **ThePHPguy said:**
> Hello I was trying to set up a dual monitor and ended up screwing up my laptop monitor :(

This is what I did.

1.) I went to (System > Preferences > Main Menu) 

2.) From here I chose (on the left) the option "Others" and checked "Screens And Graphics"

3.) Inside of the "Screens And Graphics" area I *think* I found my second monitor and changed its Model to match its model and changed the resolution.

4.) After that I clicked "Ok" and it said I must log out to see the changes so I did that.

5.) When I logged back in my background images was stretched across both monitors and on the second monitor I could move my mouse up down and to the right to pan inside.

6.) I didn't like that so I went back to the "Screens And Graphics" and tried to change it back... (this is where the BIG problem occurred.)

7.) I couldn't change my resolution back to "1280 X 800" I could only choose "640 X 480" :confused:

8.) So I started changing my model to get the correct resolution but I couldn't so here I am...

Right now I'm on my sisters laptop and its the same as my laptop (Acer Aspire 3690) and I'm wandering if I can just copy a file on her's and transfer it over to mine.

Thanks in advance.

EDIT: Also the color is different too.

HI and the acer laptop have intel graphics? You can always reconfigure your xorg with this command in the terminal
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` this should configure your xorg back to normal.

---

### Post by ThePHPguy on 2008-05-16
Thank you so much overdrank that fixed it.

---

### Post by overdrank on 2008-05-16
> **ThePHPguy said:**
> Thank you so much overdrank that fixed it.

Great and good luck! :popcorn:

---

