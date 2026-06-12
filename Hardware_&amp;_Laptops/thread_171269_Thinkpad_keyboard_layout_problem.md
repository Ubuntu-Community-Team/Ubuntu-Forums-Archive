---
title: "Thinkpad keyboard layout problem"
date: 2006-05-06
forum: Hardware &amp; Laptops
---

### Post by num_one on 2006-05-06
Can any one tell how to configure this strange keyboard layout in Linux ? The story is that I want to buy a thinkpad, but it does not come with a standard "us" or "gb" keyboard map, so I want to be certain that I can configure the strange keyboard layout under Linux before buying the machine, In case I can not configure the keyboard layout that come with the laptop under Linux I will not buy it, by the way the keyboard layout is configured under Windows as :
(Us English Table for IBM Arabic 238_L) what a strange long name ?!!
this layout has the two (redirections) symbols "<" and ">" on the same key at the upper left corner of the keyboard (just under the Esc key.
any knowledge of is that keyboard layout is supported under Linux or not will be great help in making the decision to buy it or to buy another notebook.
Thanks in advance. :)
__________________
The State of the Mind. If you can dream it, you can do it.

---

### Post by num_one on 2006-05-06
In fact I am confused about which parameter is responsible of changing the behavior of the keyboard, Is it :
Option "XkbModel"
or
Option "XkbLayout" 
but I think that Option "XkbLayout" "us" is the parameter that change the keymap, and there for when we choose Option "XkbLayout" "gb" the behavior of the keyboard will change , but it will still in English, and because we want to configure an English language keyboard, so we need to specify a parameter like the following:
Option "XkbLayout" "xx"
in the /etc/X11/xorg.conf file like the following code:

section "InputDevice"
Identifier "Keyboard0"
Driver "kbd"
Option "XkbModel" "pc105"
Option "XkbLayout" "xx"
Option "XKbOptions" "grp:alt_shift_toggle"

where xx is the entry that represent our language/country, and these entries are listed in the file /etc/X11/xkb/rules/xorg.lst
Now the question is which entry of those entries will correctly represent our keymap?
As we mentioned above that we are configuring an English language keymap, so the entry that will correctly represent our keyboard must be one of those entries that belong to one of the countries that talk in English, like "us", "en_US", "us_intl", "gb"
I tried to change the parameter Option "XkbLayout" to represent each of the ("us", "en_US", "us_intl", "gb"), but no one of them matches with the strange keyboard layout of the Thinkpad R50e !!
Are there any other entries in the /etc/X11/xkb/rules/xorg.lst file that represent an English language/country, so I can try it in the xorg.conf file. I tried Kanada:
Option "XkbLayout" "kan" but no success.
any knowledge of oather English language/country listed in the layout section of the /etc/X11/xkb/rules/xorg.lst file will be helpfull in testing that entry in the xorg.conf file as following:
Option "XkbLayout" "New_Entry_That_Represent_English_Language/Country"
I think that this keymap is strange, but there must be a way to configure it under Linux, specially that this machine is one of the IBM Thinkpads which are known to be Linux Compatible laptops.
Thanks for your effort, and Good Luck.
All Linux users dream to success in configuring any thing related to Linux, and ...........The State of the Mind. If you can dream it, you can do it, So try to prove that:
__________________
The State of the Mind. If you can dream it, you can do it. :)

---

