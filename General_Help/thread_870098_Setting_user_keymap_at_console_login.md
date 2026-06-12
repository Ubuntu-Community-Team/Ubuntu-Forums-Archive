---
title: "Setting user keymap at console login"
date: 2008-07-25
forum: General Help
---

### Post by Pablo89 on 2008-07-25
Hi folks!
I would like to set the user-specific console keymap on my machine. I mean, in text console login (like after ctrl+alt+f2 :) ), I would like to change the keyboard layout when I log in with my username. Just for a try, I'm testing some commands on logged account before making it work.
Unluckily, 'setupcon pl' command (no matter of parameter '-k' or not) does nothing (a bug? maybe I should report?), and 'loadkeys' command provided by 'console-tools' package tells me about denied permissions (it works only from root account, but I'm not interested in it!). Is there any working way to change the console keymap from the user account? Problem happens on hardy (probably it's common for *ubuntu, because the console-connected packages are similar); I have no data about older editions...

---

### Post by pauper on 2008-07-25
> Is there any working way to change the console keymap from the user account?

No.

```
sudo dpkg-reconfigure console-setup
```

---

### Post by Pablo89 on 2008-07-25
Reconfiguring console-setup affects all users... So sorry, but it doesn't solve the problem :(.

EDIT: But I don't agree, that is is technically impossible. I've managed to set multiple keyboard layouts in console setup, and I'm able to switch to my layout witch Alt+Shift (this combination is just my choice). So, definitely, it have to be possible to send similar signal with some command :-). Extract from my /etc/default-console-setup:

```
XKBMODEL="pc105"
XKBLAYOUT="us,pl,ru"
XKBVARIANT=",,phonetic"
XKBOPTIONS="lv3:ralt_switch,grp:alt_shift_toggle"
```

---

