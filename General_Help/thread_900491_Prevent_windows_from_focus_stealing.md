---
title: "Prevent windows from focus stealing"
date: 2008-08-25
forum: General Help
---

### Post by xlinuks on 2008-08-25
Hi,
This has been discussed and the only solution I found was to use compiz-fusion: the Windows Rules->No Focus option.
How exactly do I enable it? I tried different approaces like writing type=any but NetBeans and other apps still steal the focus of the current window once they load. So it looks like it doesn't work.
Any help would be appreciated.

---

### Post by _BugsBunny_ on 2008-08-25
Instead of Window Rules try:
General Compiz Options
Focus & Raise Behaviour
Focus Prevention Level -> Off

Edit: Ooops, misread. I think you want to set it to "Very High".

If that doesn't work you can try fine tuning the windows that still steal focus with Window Rules (use the grab feature to get the Window names/classes. A guess is that class would do the trick)

---

### Post by xlinuks on 2008-08-25
Hmm.. thanks!
By using the solution you suggested Pidgin doesn't steal the focus anymore, but NetBeans 6.1 still does. I think it might be just a bug in compiz since there are other visual bugs in compiz relating Java windows/dialogs.

---

### Post by carney1979 on 2008-10-10
On my system child windows get focus but their titlebars are "greyed" like they don't have focus. Using Emerald.

How do I fix that?  :confused:

David

---

### Post by loomsen on 2008-10-10
> **_BugsBunny_ said:**
> Instead of Window Rules try:
General Compiz Options
Focus & Raise Behaviour
Focus Prevention Level -> Off

Edit: Ooops, misread. I think you want to set it to "Very High".

If that doesn't work you can try fine tuning the windows that still steal focus with Window Rules (use the grab feature to get the Window names/classes. A guess is that class would do the trick)

Yep, and take care of the relations, as every single relations depends on the first argument, which is pretty logic.

So, assuming your first expression is "any", you'll have to specify windows that shouldnt. 
If you start with your first rule tho, you'll have to set rules for every single window.
For example, under window placements, I specified windows that should be sticky or always on my desktop or such. 
But when it comes down to, lets say window decorations, it's reasonable to start with any windows, and drop the ones you dont want to be decorated.

So, my lines in window rules look completely different than the ones in window decorations for example.

I'll attach two shots, guess this makes it easier to follow...

Left starting with any and specifying which one not. The right one the other way round.

Pretty much depends on what you actually want to do.

---

