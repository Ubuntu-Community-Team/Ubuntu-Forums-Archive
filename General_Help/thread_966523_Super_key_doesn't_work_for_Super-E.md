---
title: "Super key doesn't work for Super-E"
date: 2008-11-01
forum: General Help
---

### Post by chucknorris on 2008-11-01
I have set super+e to start nautilus, just like windows. It worked fine before upgrade to Intrepid. My super+t for terminal works though.

Any ideas?

---

### Post by excogitation on 2008-11-01
Does it work with a different shortcut like <Super>N?

Are you by any chance running Compiz so that the shortcut is already configured for sth else?

---

### Post by damers21 on 2008-11-01
If you use CompizConfig Settings Manager, then you can set keyboard shortcuts with that.  I was in the same boat as you were, addicted to opening Windows Explorer with that combination.

---

### Post by DizzyC on 2008-11-02
Well, i had the same problem i think. In my case no keyboard shortcut could start nautilus. Not just Super+e but no other shortcut would work.
So i figured it must be something 'wrong' with nautilus.

After some fiddeling around, i found that it would run ok if i specify a location for nautilus to open upon start.

So the **solution** was:
for **command** use '**nautilus [url]**' instead of only 'nautilus'

I use '**nautilus ~**' (without quoutes) so it opens my home folder (~)

Hope it helps!

---

### Post by loomsen on 2008-11-02
Jep, strange issue... Here the same, been trying to set Sup+E too, but no way. Then yesterday I've been fiddlin around and it worked. Doesn't today.

Most likely Super is set to another level I'd say. "e" has 3 Levels here.

e  E  &#8364;  

Only thing that would be somewhat reasonable is that Super is set to toggle, even if you hold...for what reason so ever. 
I for myself can use Super only in combo with other special keys. 
Super + <a-Z> won't do anything.

---

### Post by chucknorris on 2008-11-03
DizzyC: Your little trick worked like a champ! 

Thanks everybody, love this forum!

---

### Post by quazi on 2008-11-03
It worked for me as well.  What's odd is that I could still open just "nautilus" if I used a different shortcut.  I'm not sure why it was necessary to add the tilde in the case of Super+E.

---

