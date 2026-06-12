---
title: "Global Hotkey Actions"
date: 2010-08-01
forum: Hardware
---

### Post by abeam89 on 2010-08-01
Hello,
I have been working on a script to enable global hotkeys for Pandora in Ubuntu. I had no problem getting the script working with Pandora, but I want to complete the functionality of the script. To do this, I need to make the hotkeys which will be mapped to the script perform their normal operation if Pandora is not running on the machine. I thought this would be pretty simple, but it turns out I am struggling to find a way to do this without a third-party application. Now I know that it is possible because the default behaviors of the XF86Audio* keys are exactly what I want them to do when Pandora is not running. Trouble is, I can't simply send the keys themselves because they will have been remapped.

So, for example, 'xdotool key XF86AudioPlay' doesn't help in this instance, because that is simply a recursive call of the script.

Let me know if anybody knows what Gnome/Ubuntu maps XF86Audio* keys to by default. Thanks in advance for your assistance!

---

