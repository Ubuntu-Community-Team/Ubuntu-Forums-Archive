---
title: "[SOLVED] How do i activate the &amp;amp;amp;quot;Burn&amp;amp;amp;quot; effect when closing a window"
date: 2008-10-15
forum: General Help
---

### Post by GumpTron on 2008-10-15
Can anyone help me activate the burn effect for only when I X out of a program? I would also like to know how i can enable the minimizing effect that looks like Apples minimize effect. Thank you.

---

### Post by eternalnewbee on 2008-10-15
Assuming you have compiz running, you can do that in the animations section of compiz manager.
Good luck

---

### Post by Victormd on 2008-10-15
You need to have Compiz running to do this. Assuming you have compiz working - if you haven't done so, open a terminal and type:
```
sudo apt-get install compizconfig-settings-manager
```
This will install the Compiz settings manager that allows you to play around with the different effects. What you're looking for will be under ANIMATIONS and you can select what will be the effect when closing, minimizing, etc.

To check if you have compiz running/enabled, right click on your desktop and go to CHANGE DESKTOP BACKGROUND then go to the VISUAL EFFECTS tab and choose EXTRA if you don't get any error msgs, then you're ok and the above command will work just fine to get you started. If you do get an error msg, post back so we can try to help you with it.

---

### Post by GumpTron on 2008-10-15
> **eternalnewbee said:**
> Assuming you have compiz running, you can do that in the animations section of compiz manager.
Good luck

yes i do have it running but i don't know how to set it. Every time I get it to work it makes a lot of other menus burn as well. I simply want the X'ed out menus to burn.

---

### Post by Victormd on 2008-10-15
> **GumpTron said:**
> yes i do have it running but i don't know how to set it. Every time I get it to work it makes a lot of other menus burn as well. I simply want the X'ed out menus to burn.

You can choose what is affected under the WINDOW MATCH options. See the attached image. Where it says ((type=Normal | Unknown) | name=...) on the first line where the Burn effect is setup. The way I have it (the default), the menus and tooltips don't burn, they fade (second and third lines) and everything else, when closed, burns...

---

### Post by GumpTron on 2008-10-15
> **Victormd said:**
> You can choose what is affected under the WINDOW MATCH options. See the attached image. Where it says ((type=Normal | Unknown) | name=...) on the first line where the Burn effect is setup. The way I have it (the default), the menus and tooltips don't burn, they fade (second and third lines) and everything else, when closed, burns...

i do appreciate the help but i dont really know what all those things mean. I tried "grabbing" the X that you see on each screen next to minimize but i wasn't able to. I guess what I need to know is, how do I get it to burn when I X out of a window?

---

### Post by GumpTron on 2008-10-15
I figured it out through some trial and error.

I was able to make the burn effect work solely for Xing out windows by putting this in the "close animation"

type=Normal | Dialog |

---

### Post by Victormd on 2008-10-15
Ok, open your Compizconfig settings manager, go to animations, click on the "close animation" tab and double click the first line "burn    150   ...." (equivalent to the first line on the image I posted). Then under window match, copy and paste this:
> ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1)
Then, on the second and third lines (if you have them), change the effect to fade. If you don't have them, click on NEW, choose FADE as the effect, and under Window match, copy and paste this:
> (type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog | Normal) & !(type=Tooltip | Notification | Utility) & !(name=compiz)
Note that I've combined the second and third lines (of my screenshot) into one.

---

### Post by Victormd on 2008-10-15
> **GumpTron said:**
> I figured it out through some trial and error.

I was able to make the burn effect work solely for Xing out windows by putting this in the "close animation"

type=Normal | Dialog |

That will do the trick. :)
In my previous post, I don't limit the windows just to normal. Other frames (have the X but don't classify as a window) will burn as well... It's the default so I can't say what would actually fall under this category... hehehe

---

