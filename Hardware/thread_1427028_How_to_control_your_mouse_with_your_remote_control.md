---
title: "How to control your mouse with your remote control on HP tx2505 laptop"
date: 2010-03-11
forum: Hardware
---

### Post by hrimhari on 2010-03-11
Greetings!

**1) Ensuring that your remote is operational**

First you need to be sure that your remote control is operational. So open a Terminal window and type:

```
$ man man
```

That will give you the Manual page of the "man" command.

Now use the remote's arrows. If you press Down a few times, it should scroll down like if you pressed the Down arrow in your keyboard.

In the tx2505, you **don't** use LIRC. The remote control works as a "second" keyboard, meaning that it always generates the same events as some of the keyboard keys.

If nothing happens in your test, you'll have to go to Windows and upgrade your firmware.

**2) Enabling MouseKeys**

In newer versions of Gnome, you can enable MouseKeys through **System --> Keyboard --> Mouse Keys**

Hopefully you'll also be able to toggle it on and off using the sequence Shift+NumLock, which in this laptop means Shift+Fn+End

To test MouseKeys, be sure that it's enabled.

Now turn your Numeric keypad on by pressing Fn+End. The Numlock led should turn on.

Press the U and O keys (4 and 6 from the virtual keypad). The mouse pointer should move.

You can disable Mousekeys now.

**3) Remapping MouseKeys to use the real arrows and the Return key**

On a Terminal window, type:

```
$ sudo bash

```

You may need to type your password.

Now you're running a shell as the superuser.

Type:

```
$ cd /usr/share/X11/xkb/compat
```

The idea now is to add the arrows and the Return key to the "mousekeys" file. Here's what you need to add:

```
    interpret Left { 
        action = MovePtr(x=-19,y=+0); 
    };
    interpret Right { 
        action = MovePtr(x=+17,y=+0); 
    };
    interpret Up { 
        action = MovePtr(x=+0,y=-17); 
    };
    interpret Return { 
        action = PointerButton(button=default); 
    };
    interpret Down { 
        action = MovePtr(x=+0,y= +19); 
    };
```

Use the editor of your choice. I used "vi". Add the lines above before the last **};** of the file, and save the file.

**4) Restart X**

Close everything you have opened, then press Ctrl+Alt+Backspace.

**Remember:** to toggle MouseKeys, press Shift+Fn+End. You should be able to move the pointer with the remote control and "click" with the "Ok" button.

Unfortunately the pointer speed with the remote control [s]is reeeeeally slow[/s] *does not follow the same acceleration rules as with the keyboard. That's why I used 17 and 19 as pointer increments, so that it's at least usable.* Hopefully somebody will come up with a [s]nice[/s] *nicer* solution to this.

Best regards,
~hri

---

