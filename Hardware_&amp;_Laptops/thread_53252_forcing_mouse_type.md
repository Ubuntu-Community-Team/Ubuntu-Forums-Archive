---
title: "forcing mouse type"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by thegrayarea on 2005-07-30
new user and this is my first post.....so here goes my situation i am using a 5 year old KVM which i really like alot, and don't want to give up, an equivulant USB KVM would be about $179 and i dont' have that now. So what i am looking to do is force Ubuntu to use the MS intellimouse Ps/2 Driver for my mouse, so when i switch back and forth between my computers, the mouse doens't go all crazy on my. can someone plz tell me where i am supposed to change the mouse type?

thank you, 
thegrayarea

---

### Post by woedend on 2005-07-31
[QUOTE=thegrayarea]new user and this is my first post.....so here goes my situation i am using a 5 year old KVM which i really like alot, and don't want to give up, an equivulant USB KVM would be about $179 and i dont' have that now. So what i am looking to do is force Ubuntu to use the MS intellimouse Ps/2 Driver for my mouse, so when i switch back and forth between my computers, the mouse doens't go all crazy on my. can someone plz tell me where i am supposed to change the mouse type?

thank you, 
thegrayarea[/QUOTE]
 setting up your mouse is done in xorg.conf.  in terminal you would type -
cd /etc/X11
sudo gedit xorg.conf

then enter password.  Find the section relating to 'mouse'.  I'm guessing this is what you are looking for, but don't quote me on this.  Should look similar to this.  I wouldn't copy and paste, just make changes where necessary.
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"IMPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

This, however, is how ubuntu set up my 5 button and 8 button logitech mice both, was guessing it was default.  I have since changed to the ExplorerPS/2 protocol for the 8 button mouse, although both mice worked perfectly fine with that setting(except some of the extra buttons weren't set up)

---

