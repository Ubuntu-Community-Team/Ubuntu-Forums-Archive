---
title: "[SOLVED] Forgotten hotkey, or what?"
date: 2008-10-07
forum: Hardware
---

### Post by 4nick8or on 2008-10-07
Not quite sure what's going on here. 8.04 has been running decent lately, other than the touchpad bug where tapping is turned on for no apparent reason.
   Now this - the key combination of "<shift> a" has stopped working. That is to say, I cannot type a capital a unless I use caps lock.!? I've checked the key assignments in gnome configuration editor, and the keyboard settings. This is bugging me. Both the left and the right shift modifiers work with every key on the board EXCEPT "a". Also, when I invoke <shift a> it doesn't type a lowercase 'a', it simply types nothing, and doesn't advance one character space.
   Has anyone else had a similar problem? I'd really like to hear any ideas as to what can cause this effect.
   Finally, is there a way to display all assigned hotkeys in the system?
It's not earth shattering, but puzzling, ain't it? 

Thanks

---

### Post by 4nick8or on 2008-10-12
Posting to say I solved the problem myself (like most problems with Ubuntu, no one replies to questions not found in the documentation) Maybe I should roll it into some poll and give it a catchy title, like - "Ubuntu keyboard better than Windows keyboard?" ... Jeez..
    Anyways maybe someone searching with a siimiliar problem can reference this as a possible help. 
    Turns out I was using klipper for clipboard management because glipper has always locked my processor at 100% since the upgrade to 8.04. Klipper default hotkeys had set <shift>a to toggle actions, and it remained a global hotkey. Simple as that.Problem solved. 
    It could have saved a lot of trouble if there was a way in Ubuntu to list all asigned hotkeys, but if there is such a way, I don't know it, and the community must have decided this was beneath investigation.
   If I can help anyone, please direct message me, and I'll at least tell ya "I don't have a clue", or maybe suggest something helpful.
   Regards

---

