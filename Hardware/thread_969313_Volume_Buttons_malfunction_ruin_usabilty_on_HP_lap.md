---
title: "Volume Buttons malfunction ruin usabilty on HP laptop"
date: 2008-11-03
forum: Hardware
---

### Post by portach king on 2008-11-03
Hey,
I'm using Ubuntu 8.10 and I'm having a lot of trouble with the volume buttons. If I push up or down the volume buttons react as if the buttons are being held down infinitely. What happens then is the volume icon stays on the screen all the time and I can't use my keyboard at all or click my any icons or menus with my touchpad. I have to Crtl+Alt+Backspace and log in again just to restore usability. My laptop is a hp pavilion zv6000.
I'd love some help,
Thanks in advance.

---

### Post by jdeszell on 2008-11-03
I'm having some issues with my volume buttons as well.  I'm a new Ubuntu user.  When I use my volume buttons it does change the volume, but then my keyboard stops working and I have to restart my laptop.  My trackpad still works and I can do everything else, other than use the keyboard.

Slightly different than your problem, but I wonder if related.

---

### Post by portach king on 2008-11-03
Good to see it's not just me. My keyboard stops working and my mouse is limited. I can move the cursor using navigate buttons and icons, but I cannot open any dropdown menu's when the computer gets like this (including the new Shutdown-Log Out menu).
Hopefully someone an help.

---

### Post by pellegrini on 2008-11-04
It happens to me too. On 8.04 used to work well. 

If you press Esc the moment the icon appears it stops blinking. But still can't use the keyboard.

I have a Toshiba Satellite U300-10S.

---

### Post by ktemkin on 2008-11-05
I'm sorry to report that at this time there's no simple solution that I know of or have been able to find. 

This is a result of a particular hardware quirk in certain PS2 (laptop) multimedia keyboards. Most keyboard keys, when pressed, report a KEYDOWN event, and then a KEYUP event when the key is released. This lets the driver know for how long the key has been held, so it can perform tasks like autorepeat.

These media keyboard buttons, however, were designed to report a KEYDOWN, but no KEYUP. Thus, the EvDEv driver assumes they are being held. Hopefully, this will be addressed in a future update, however, the developers, at current, are not completely sure where to implement the fix. (Kernel, driver, etc.)

I am pleased to report that there are three workarounds I can mention to help you at this time. I understand they're not ideal, but they're all I have to work with.

1) To regain control of your keyboard after entering an infinite volume loop, simply switch to one of the Virtual Terminals and switch back. This can be accomplished by hitting CTRL+ALT+F1, then hitting CTRL+ALT+F7 to switch back to X-Server. Occasionally I've found that X-Server will be on the CTRL+ALT+F9 terminal, but this is a small fraction of cases.

2) If you still want volume keys, you can try remapping it to either another key or another hardware button. This can be done in System->Preferences->Keyboard Shortcuts in GNOME. 

3) There is a 'fix' for the solution, but it requires you downloading the source of the old 'kbd' drivers, modifying the code to suit your keyboard, recompiling, and configuring HAL to use the resultant driver. While it does make the volume keys work, you lose all of the advantages of the EvDev driver, and you gain all the disadvantages of having your system run off custom code (i.e lack of supportability). 

Here's a sample modification, from [/xf86-input-keyboard-1.2.2/src/kbd.c]:

```


  /*
   * check for an autorepeat-event
   */

/*  if (down && KeyPressed(keycode)) {
      int num = keycode >> 3;
      int bit = 1 << (keycode & 7);

	REPLACED for laptop keyboard quirk
*/

  if (down && KeyPressed(keycode) && keycode < 146) {
       int num = keycode >> 3;
       int bit = 1 << (keycode & 7);


      if ((pKbd->autoRepeat != AutoRepeatModeOn) ||
	  keyc->modifierMap[keycode] ||
	  !(kbdfeed->ctrl.autoRepeats[num] & bit))
	  return;
  }

   if (UsePrefix) {
      xf86PostKeyboardEvent(device,
              keyc->modifierKeyMap[keyc->maxKeysPerModifier*7], TRUE);
//      xf86PostKeyboardEvent(device, keycode, down); [quirk]
	if (keycode < 146) {
	      xf86PostKeyboardEvent(device, keycode, down);
        } else if (down) {
	      /* If it's a key down event, send a down and up. Otherwise
		 drop it */
	      xf86PostKeyboardEvent(device, keycode, TRUE);
	      xf86PostKeyboardEvent(device, keycode, FALSE);
       }

      xf86PostKeyboardEvent(device,
              keyc->modifierKeyMap[keyc->maxKeysPerModifier*7], FALSE);
   } else {
//      xf86PostKeyboardEvent(device, keycode, down); [quirk]
      if (keycode < 146) {
	      xf86PostKeyboardEvent(device, keycode, down);
      } else if (down) {
	      /* If it's a key down event, send a down and up. Otherwise
		 drop it */
	      xf86PostKeyboardEvent(device, keycode, TRUE);
	      xf86PostKeyboardEvent(device, keycode, FALSE);
      }
   }
}

```

It replaces the code that was previously commented out. The code is not originally mine; it was contributed to an older Ubuntu distribution a while ago.  [ (source) ](http://lists.freedesktop.org/archives/xorg/2007-June/025347.html)

Some users may not have to modify their 'kbd' drivers; I believe several older distributions had similarly modified kbd drivers.

I'm as sorry as you are that there's no quick fix.

---

### Post by ecadman on 2008-11-27
I'm also looking forward to the fix. Two more workarounds that seem slightly better than full restart--assuming one can stop the volume up or down loops by hitting the mute button once, which works for me on my zv6000.

1. CTRL-ALT-DEL seems to give the ability to log out. Logging back in will restore all functionality.

2. Good ol' CTRL-ALT-Backspace is also lovely at killing the problem, allowing another login as well.

My apologies if these are obviously objectionable to the initiated. I have been working and playing with Linux for 10 years and have successfully cultivated only a paltry understanding of what I'm doing in it.

---

