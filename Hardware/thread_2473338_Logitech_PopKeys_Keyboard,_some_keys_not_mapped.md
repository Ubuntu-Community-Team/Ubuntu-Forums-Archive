---
title: "Logitech PopKeys Keyboard, some keys not mapped"
date: 2022-04-01
forum: Hardware
---

### Post by dovakin-poulet on 2022-04-01
Hi folks !
So, today i acquired the nice logitech pop keys keybord. ([https://www.logitech.com/en-us/products/keyboards/pop-keys-wireless-mechanical.920-010708.html](https://www.logitech.com/en-us/products/keyboards/pop-keys-wireless-mechanical.920-010708.html))
it works almost fine, because some keys are not even detected by the ```
xev
``` tool.
I'm talking about the four keys on the right column, from the top.
Avery other key is mapped, but not these four.
I tried to search a little, i thought about
`sudo dpkg-reconfigure keyboard-configuration`
but i can't find the correct config for the pop keys.
do you guys have any clues or leads ? 

I run a Ubuntu 20.04.4 LTS
thanks ! :)

---

### Post by DuckHook on 2022-04-01
Welcome to the forums, dovakin-poulet,

You probably noticed the following from their product specs, but:> 
**System Requirements**
Bluetooth Low Energy Wireless Technology

    Required: Bluetooth Low Energy
    Windows® 10,11 or later
    macOS 10.15 or later
    iPadOS 13.4 or later 7Emoji keys and software are not supported
    iOS 11 or later 8Emoji keys and software are not supported
    Chrome OS 9Emoji keys and software are not supported
    Android 8 or later 10
&#8230;Linux is not included in this list.

Moreover, Logitech is becoming notorious for their lack of support for Linux. If you buy their products, you need to be prepared for broken or incomplete functionality. Another user in [this thread]("https://ubuntuforums.org/showthread.php?t=2472848") just went through a sad experience in which Logitech's Linux deficiencies figured prominently.

The four buttons you are referring to appear to be custom meta&#8209;function buttons specific to Logitech alone. Unless you can find a Linux driver for this keyboard, I suspect that you are out of luck using them in the manner that Logitech intended.

You can probably use them for alternate functions (differently than intended by Logitech) but this would involve figuring out what keycodes they are actually generating and then changing your keymap. Doing so is a delicate exercise that may lock you out of your OS altogether, so if you decide to try, you need to proceed very carefully, with a LiveUSB that you can use to recover.

If the keycodes are recognized by Linux, you can avoid the dangers of monkeying around with the keymap by simply assigning them to shortcuts using your keyboard settings. This still doesn't make them work in the way intended by Logitech, but at least it makes them usable for something.

If still interested in the dangerous way, have a look at the link in my sig: Remapping Keys

---

### Post by QIII on 2022-04-01
I used to use Logitech (now Logi) products most of the time.  

The things I have now work just fine.

But of late is does seem that they are deliberately snubbing Linux, as is clear from their supported OS lists, and this for a few others above:  "Emoji keys and software are not supported"

---

### Post by dovakin-poulet on 2022-04-03
Thank you guys for the answers. Not as hoptimistic as i would have hoped though.
@Duckhook, would you have a link to how one could try and detech the keycode ? as i mentioned, xev didn't worked, and i don't see any other tool

---

### Post by DuckHook on 2022-04-05
> **dovakin-poulet said:**
> …@Duckhook, would you have a link to how one could try and detech the keycode ?l
Not easily done. The Desktop Environment GUI gets in the way.

Invoking xev within a terminal does not always work because the DE can steal the key first, especially if it is bound to some function. Such keybindings are often not obvious and they aren't well documented either.

Some have worked around this limitation by launching a pristine X11 session comprised only of the display server. This won't bring in any layers of the DE, which is what confuses xev. However, this is not a trivial exercise and especially not so for newcomers to Linux.

I don't really have any advice for you on this one, except to reuse the keys in a more limited fashion by assigning them to keyboard shortcuts, thereby exploiting the very DE keycode captures that are confusing xev.

---

