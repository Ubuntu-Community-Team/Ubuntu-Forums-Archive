---
title: "Extra keys on 122-key 5250-style keyboard are not working"
date: 2024-04-23
forum: Hardware
---

### Post by neilwaldhauer on 2024-04-23
I am a beginner at Ubuntu. I apologize if I've posted in the wrong forum.

I have an Affirmative Unicomp model M 122 key keyboard. I intend to use it with IBM iAccess (ACS) to connect to an iSeries. iAccess seems to be written in Java and requires a JRE to run.

I have this working with a standard USB keyboard. But it has only 104 keys, and special keys for the iSeries, like F13 through F24 are simulated by shift F1 for F13, for example.

When I attach the model M (PS/2 connector), the standard keys work, but F13 through F24 don't do anything. I can still use shift-F1 for F13, but that is less desirable.

Is there some way to get the extra keys to function?

---

### Post by TheFu on 2024-04-23
You can create keyboard mapping for each key to the working using something built into the display server.  5-40 yrs ago, we could have assumed you were using X11. There might be an easier method, but I tend to do things 'old-school', so [https://wiki.archlinux.org/title/Xorg/Keyboard_configuration](https://wiki.archlinux.org/title/Xorg/Keyboard_configuration) is how I'd attack this sort of thing.

BTW, I used to program IBM mainframes using an IBM 3275 terminal.  132-characters wide green-screen with multiple rows of F and PF keys. Those keyboards are like cockroaches. They will outlast all of us. ;)

Today, you might be using Wayland.  I think there must be Wayland tools for this, but I've never used Wayland  [https://github.com/xremap/xremap](https://github.com/xremap/xremap) looks to be Xorg/X11 and Wayland capable. Could be the "easy way". IDK.

---

