---
title: "Remapping buttons on HUION H420 graphics tablet"
date: 2015-10-18
forum: Hardware
---

### Post by alex459 on 2015-10-18
Recently I purchased a Huion H420 graphics tablet, and although the pen works great, the default button mappings are weird (`Shift_L+KP_Subtract`, `Ctrl_L+s`, and `Alt_L+F4`). Since I couldn't find any existing packages or guides to accomplish this easily, I'm trying to accomplish this myself by configuring custom XKB files. (I'm running Ubuntu 15.04.)

Following the steps of [this excellent XKB guide]("http://www.charvolant.org/~doug/xkb/html/node5.html#SECTION00052000000000000000"), I created custom configurations for keycodes, symbols, and compatibilities. In short, I attempt to set the function keys 13–18 to keycodes 213–218, and then redirect the keybinds mentioned earlier to F13, F14, and F15 respectively. (I set aside the other F-keys in case I want to use more later.)

/usr/share/X11/xkb/compat/huion_h420:
```

default xkb_compatibility "huion_h420" {

  interpret Shift_L+KP_Subtract {
    action = RedirectKey(keycode=213);
  };


  interpret Ctrl_L+s {
    action = RedirectKey(keycode=214);
  };


  interpret Alt_L+F4 {
    action = RedirectKey(keycode=215);
  };


}

```

/usr/share/X11/xkb/keycodes/huion_h420:
```

xkb_keycodes "huion_h420" {


  min = 8;
  max = 255;


  <FK13> = 213;
  <FK14> = 214;
  <FK15> = 215;
  <FK16> = 216;
  <FK17> = 217;
  <FK18> = 218;


}

```

/usr/share/X11/xkb/symbols/huion_h420:
```

xkb_symbols "huion_h420" {


  name[Group1] = "Huion_H420";


  key <FK13> {[ F13 ]};
  key <FK14> {[ F14 ]};
  key <FK15> {[ F15 ]};
  key <FK16> {[ F16 ]};
  key <FK17> {[ F17 ]};
  key <FK18> {[ F18 ]};


}

```

Finally, I'm using an InputClass [as described in the guide]("http://www.charvolant.org/~doug/xkb/html/node4.html#SECTION00043000000000000000") to set the input mappings for my device:

/usr/share/X11/xorg.conf.d/09-huion-h420.conf:
```

Section "InputClass"
        Identifier "Huion_H420"
        MatchProduct "H420"
        Driver "evdev"


        Option "XkbKeycodes" "xfree86+huion_h420"
        Option "XkbTypes" "default"
        Option "XkbCompat" "basic+pc+huion_h420"
        Option "XkbSymbols" "en_US(pc_104)+huion_420"
        Option "XkbGeometry" "pc(pc_104)"
EndSection

```

However, the buttons continue to have their original mappings. Did I make a mistake in one of the configuration files, or in which files to use? Alternatively, is there an easier way to remap these buttons that I overlooked?

---

