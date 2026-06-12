---
title: "jp keyboard with deadkeys"
date: 2008-10-06
forum: General Help
---

### Post by otaniyul on 2008-10-06
hello all.

my problem involves dead keys with japanese layout keyboard, feel free to redirect to solution (even partial), and thanks!

I have a japanese layout keyboard and I use both japanese (with scim) and portuguese (altering the layout) writing at the same session, but the problem is that I can only get the deadkeys (to write in pt) switching to the USA-international layout which has a different keymap... so in example the shift-6 ("&" in the jp keybord) turns to be "^"...
is it possible to like get the Japanese-international input, with the jp-layout AND the deadkeys? Like putting an pt input in scim or something...

bonus [worth some extra points]: in doing so, there will always be the cedilla problem... ('+c producing &#263; and not ç)... solving that will be the same procedure to get it right with the us-international layout?

MANY THANKS!

---

### Post by VectorZero on 2009-06-24
Hi!

I have exactly the same problem and I am also looking for a way to use deadkeys with the Japanese keyboard.

But, for the time being I have found a partial solution: to activate "composite key".

Go to menu:/System/Preferences/Keyboard/Keyboard Preferences/Layouts

Select Keyboard model: Japanese 106-key
Select the appropriate layout. In my case it was Japan OADG 109A.

Then go to "Layout options" and look for "Compose key position". The default is no options marked. Mark the one corresponding to the key you want to use. I marked "Right Alt" (used to be called <AltGr> in some keyboards).

Now when you want to type an accute accented a, type <AltGr>+' then "a". (Actualy it will be <AltGr>+<Shift>+7 then "a".)

For "ç" type <AltGr>+, then "c".

Less practical then deadkeys (and a little bit annoying to be completely honest) but avoids the need to change layouts all the time.

I hope it helps.

IMPORTANTE: I'm still looking for a way to use deadkeys with Japanese keyboards, if somebody knows how to do it, please share the knowledge.:)

---

