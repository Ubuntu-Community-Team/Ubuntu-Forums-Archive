---
title: "When pushing a key... mouse can't move"
date: 2008-05-14
forum: Hardware
---

### Post by PauGNU on 2008-05-14
Hi

I have an annoying problem with my mouse and keyboard on my MacBookPro. When I'm pushing a key (anyone), I can't move the pointer, there is no reponse until I stop pushing that key.

Could someone help me?

Thanks!

---

### Post by AcidicChip on 2008-05-23
I am having the SAME issue right now, and it's really aggravating. I have a DELL XPS M1710... Does ANYONE have a solution to this?

---

### Post by AcidicChip on 2008-05-23
I think I found the issue. I didn't realize this happening until I tried to setup the wii remote as a mouse.

After removing mouseemu, everything was fine again.

```
sudo apt-get remove mouseemu
```

---

### Post by Rhubarb on 2008-06-10
This problem can be fixed easily.
```
gksu gedit /etc/default/mouseemu
```

So it looks like:
```
# Defaults for mouseemu initscript (/etc/init.d/mouseemu)
# These are the default values on PowerPC. On all other architectures
# middle and right click are disabled by default. 
# Key codes can be found in include/linux/input.h in the kernel headers
# or by using `showkey` in a console.


#MID_CLICK="-middle 0 87"         # F11 with no modifier
#MID_CLICK="-middle 125 272"      # Left Apple Key (LEFTMETA) + click
#RIGHT_CLICK="-right 0 88"        # F12 with no modifier
#RIGHT_CLICK="-right 29 272"      # Left Ctrl + click
#SCROLL="-scroll 56"              # Alt key
TYPING_BLOCK="-typing-block 000"  # don't block mouse after a keypress
```
Note the typing block has been reduced from 300ms to 0.
Then just restart X / Ubuntu and all should be good again.

---

