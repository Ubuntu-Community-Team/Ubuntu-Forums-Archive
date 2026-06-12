---
title: "One install handles firefox plugins differently, spec. Smart Bookmarks Bar"
date: 2008-08-20
forum: General Help
---

### Post by Niels Olson on 2008-08-20
Hello,

I have Ubuntu Hardy installed on two Dell laptops, both are upgrades from Gutsy. Both have the [Smart Bookmarks Bar]("https://addons.mozilla.org/en-US/firefox/addon/4072") extension installed in Firefox, along with many other extensions. Smart Bookmarks Bar works in FF3 in WinXP, OS X, SuSE, *and* the other Ubuntu Hardy Dell laptop. It's just this one install that's giving me a problem.

I have tried reinstalling the plugin. I have tried reinstalling firefox. I have tried manually copying libxpcom.so from the mozilla repos. The one thing that worked was, on a lark, I moved my ~/.mozilla directory to ~/.mozilla.bak an then restart firefox and reinstall my extensions. So I'm pretty sure the issue was in that directory. I guess my question is where within .mozilla should I look for the issue as 1) I don't want to reinstall all my extensions, 2) I want to know how it works, and 3) even if I do reinstall my extensions, that's a lot of stuff to diff for what is probably one line.

Suggestions?

---

### Post by yeremiya on 2009-08-17
I have exactly the same problem. I use FF 3.0.13 and Ubuntu 8.04 and all the extensions except SmartBookmarks Bar are working. The extension in question installs normally, it's options dialog works, but the extension itself is not working (it should "faviconize" bookmarks on bookmarks bar, but it doesn't).

I hope someone finds the solution to this issue. (Yes, I know, it's probably extension issue, and not for ubuntu forums, but still...)

---

### Post by yeremiya on 2009-10-27
Bump. It's happening exactly the same in FF 3.5.2

---

