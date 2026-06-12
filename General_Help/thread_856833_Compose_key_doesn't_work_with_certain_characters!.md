---
title: "Compose key doesn't work with certain characters!"
date: 2008-07-11
forum: General Help
---

### Post by UnsungBovineHerd on 2008-07-11
I have activated the Compose key (System / Preferences / Keyboard / Layouts / Layout Options / Compose key position).

However I cannot input a number of Unicode characters using the expected key press sequences. Among them are them A and a macron (U+0100 and U+0101), O (U+014C and U+014D), and surprisingly, the left and right double quotations marks (normally mapped as "smart quotes" in English language locales.

I think these are bugs because if, for example, I type "<ComposeKey> I _" or "<ComposeKey> u _" I get &#298; (capital i with macron) or &#363; (lowercase u with macron), respectively. Also if I type "<ComposeKey> ' <", I get ‘ (single left quote).

However, if I type "<ComposeKey> a _" or "<ComposeKey> o _" I get ª (U+00AA or Feminine Ordinal Indicator) or º (U+00BA or Masculine Ordinal Indicator), respectively. On the other hand, typing "<ComposeKey> " <" merely produces a beep (error alert) and not the expected "double left quote".

Is there a way to input such characters without memorizing their Unicode character code? Should this be filed as a Launchpad bug?

---

### Post by eythian on 2009-08-16
> **UnsungBovineHerd said:**
> However, if I type "<ComposeKey> a _" or "<ComposeKey> o _" I get ª (U+00AA or Feminine Ordinal Indicator) or º (U+00BA or Masculine Ordinal Indicator), respectively. On the other hand, typing "<ComposeKey> " <" merely produces a beep (error alert) and not the expected "double left quote".

Hmm, I see the same thing with the macrons. ª&#275;&#299;º&#363; is what I get, when they should all be macroned characters.

The “quotes” work for me correctly though.

---

### Post by CatKiller on 2009-08-17
I think you're [supposed]("http://www.hermit.org/Linux/ComposeKeys.html") to do the modifier first. There does seem to be a problem somewhere with those characters, though. Firefox gets ª for the correct sequence to do &#257; (which works everywhere else).

---

