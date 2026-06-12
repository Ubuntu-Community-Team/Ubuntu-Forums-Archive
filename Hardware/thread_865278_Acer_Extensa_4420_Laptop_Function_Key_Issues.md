---
title: "Acer Extensa 4420 Laptop Function Key Issues"
date: 2008-07-20
forum: Hardware
---

### Post by SuperMike on 2008-07-20
Fn+F5 is supposed to toggle the screens between internal LCD and external attached display, but it has absolutely no effect.

Fn+F4 is supposed to suspend the laptop but instead it turns off the internal LCD, leaves the external attached display on, and gives me no option to undo it.

Fn+F6 is supposed to turn off the internal LCD but instead it just blanks video on it (not external display) and there's no way to undo.

The Euro key near the arrow keys doesn't do anything and when I go into /var/log/messages, I get the typical "Use 'setkeycodes e033 <keycode>' to make it known." message. I'd like to have that key working because I have European clients.

Next to the Euro key is a $ key. I'd love to reprogram that to be the British Pound symbol because I have British clients, but instead I get the typical "Use 'setkeycodes e034 <keycode>' to make it known." message.

---

### Post by SuperMike on 2008-07-20
In lieu of getting the British Pound key programmed on the $ key next to the arrow keys, and in lieu of getting the Euro enabled, I found a workaround. Just go to System, Preferences, Keyboard, Layout, and add in a new default layout of USA International AltGr Deadkeys. I have no idea what AltGr means except to think of it as your "International Key" and it is your right-most Alt key. I have no idea what Deadkeys means, so I leave that up to your imagination.

Note I'm a USA citizen. If you live somewhere else, you may need a different keyboard configuration.

Don't forget to click the radio button in that dialog to select it as your default.

Anyway, with that selected, you can then do AltGr + Shift + 4 to get a British Pound symbol, and AltGr + 5 to get a Euro symbol. However, note this won't work in FF3 when I tested -- but works in other applications. However, I noticed I could cut and paste from other applications and into FF3 and it worked okay.

And you might be wondering -- will that mess up your keyboard? No, it won't. You can still use your keys like normal -- it's just your right alt key now has a little more power to do extra things on your keyboard, especially if combined with shift.

---

