---
title: "Keyboard Scroll Lock Button"
date: 2024-06-09
forum: Hardware
---

### Post by janvi2 on 2024-06-09
The classic IBM PS2 keyboard features 3 specialized lock buttons: Caps Locks (also known as Shift Lock), Num Lock and Scroll Lock. All of them act as a toggle switch and have a hardware LED on some keyboard what shows the state. Most known is the caps lock key, as it prevents from login with a correct password if activated while Scroll Lock has only little use and Num Lock is not available for keyboards without seperate number block keys. 

For the USB area HID keyboards also have this 3 lock buttons. Unlike PS keyboards, USB allows to have more than one keyboard for any target PC. Therefore the USB endpoint of all keyboards receive the lock state of each key. With other words: If you have 2 keyboards and press Caps Lock at one of them, the appropriate LED will lid on both keyboards. This feature might be used to transmit lock key sequences from a keyboard to another HID device what might be not a keyboard. 

For my Ubuntu 22.04.4 LTS installation, caps and num lock are working fine while scroll lock shows no functionality. You might reproduce this using a cheap Cherry KC1000 oder other full feature keyboard what comes with 3 LEDs and appropriate lock switches therefore. Num-Lock and caps-lock toggle the LED while the scroll lock led is always off. 

During the boot process, caps lock works fine as it is controlled by the bios code at a time we do not know what OS will boot. The moment Ubuntu makes the HID enumeration Scroll Lock will stop working. 
I used this java script to see what happens:

[https://www.toptal.com/developers/keycode](https://www.toptal.com/developers/keycode)

here we see event code 20 for caps lock, event code 144 for num lock and 145 for scroll lock. All my Windoz machines transmit the LED state to HID endpoint correct. Ubuntu is doing so only for the caps lock and num lock states while the scroll lock state  will be dropped. What I heard about MacOS, it will transmit the lock states only to the own HID endpoint but not to any parallel HID keyboards. Maybe there is a reason why Ubuntu drops the scroll lock or there is any possibility for configuration ?

---

### Post by Holger_Gehrke on 2024-06-13
A short search for 'Scroll lock in linux' leads to various posts which all end up recommending ```
xmodmap -e 'add mod3 = Scroll_Lock'
``` to activate the Scroll Lock key. As long as you're using X11 and not Wayland this will work. The LED toggles on and off and the only program I know in which the state of scroll lock has an actual influence reacts as expected (LibreOffice Calc, the state of scroll lock changes the function of the cursor keys; scroll lock off -> move the cursor, on -> move the viewport).

Holger

---

### Post by janvi2 on 2024-06-22
Thanks, it works. One thing I wonder about: Caps-Lock toggles with the rising edge of the keypress. Num-Lock and Scroll-Lock use rising edge to switch the toggle on and falling edge to switch the toggle off. With other words: Caps-Lock LED goes off if you press the num lock key second time while Num-Lock and Scroll-Lock LEDs goes off if you release the key second time. 
Further, Scroll-Lock toggle its not working before login Gnome Desktop and associations are lost for each suspend - login. What is the correct method to make the xmodmap changes permanent to be used before login ?

Dont worry about the scroll lock behavior in LibreOffice. I found, all 3 lock LED signals are transmitted by system from each USB keyboard to all other HID endpoints (keyboards) what I like to use in own application.

---

### Post by Holger_Gehrke on 2024-06-22
xmodmap modifies the mapping of the keyboard in the running X-server (which is why I said '... not using Wayland ...' in my last post). To make the change permanent just write a desktop file that has an exec-line running xmodmap and put it in '~/.config/autostart/'. This will not change the keyboard behaviour while the greeter is running, but will run as soon as you're logged in. The Display Manager and the greeter it runs are very much their own thing and I have no idea how to change keyboard behaviour there.

Holger

---

### Post by janvi2 on 2024-06-23
Add the modifier mapping for Scroll_Lock will do the job perfect. See last line of my modifier mappings in /usr/share/X11/xkb/symbols/pc

 // Beginning of modifier mappings.
    modifier_map Shift  { Shift_L, Shift_R };
    modifier_map Lock   { Caps_Lock };
    modifier_map Control{ Control_L, Control_R };
    modifier_map Mod2   { Num_Lock };
    modifier_map Mod4   { Super_L, Super_R };
[B]    modifier_map Mod3   { Scroll_Lock };

[/B]The only disadvantage seems the use of the falling edge of the Scroll-Lock (and Num-Lock) key at switch off what is diffrent to Windows (and the BIOS)  behavior. Caps-Lock is always rising edge. Possibly a bug in X11?

---

