---
title: "Uninstalling Flash 9 without synaptic"
date: 2008-08-26
forum: General Help
---

### Post by soggydoggy on 2008-08-26
Hello all,

I'm new to the forum and think I have the hang of Ubuntu a bit more now.

I (stupidly) decided to install the Flash9 plugin from Adobe's website rather than using Synaptic.

It causes a few problems for me on flash based sites, so I wish to remove it and reinstall it from the repository instead (as I should have done in the first place!).

I have no idea how to remove it, and the automated uninstallers from Adobe are not designed for a Linux OS.

Please help!

Thanking you muchly.

Soggy.

---

### Post by ibuclaw on 2008-08-26
Which folder did you install it in?

If you can remember, then just "cd" to that directory and "rm" it.

Regards
Iain

---

### Post by soggydoggy on 2008-08-26
Thanks for the response.

I did a search for "Flash" and "Adobe" and the only thing it brought back was "/etc/adobe" so I completely removed that folder and its contents, but it's still working in Firefox!

I'm guessing it is installed somewhere else that I can't see.

Sometimes you miss "add/remove programs" lol. Though I guess Synaptic would show it if I'd installed it correctly in the first place - my bad.

If all else fails I guess I could just reinstall Ubuntu from scratch, though that seems a bit overkill tbh.

Any other suggestions?

Thanks,

Soggy.

---

### Post by soggydoggy on 2008-08-26
Cancel that!

I found where it installed to.

It was "/home/<me>/.mozilla". It didn't look in the hidden folder as I didn't have it set to show hidden folders and files.

Thanks for your help Iain, worked a treat!

Soggy.

---

### Post by ajgreeny on 2008-08-26
It could be worth trying the flash 10rc which is working well for me on nearly all sites.  There are a few which insist that I have no flash installed at all, but they are few and far between, and using the Tools >>Add Ons menu of firefox I can disable that, and enable version 9 which is also installed but only in my home .mozilla folder.  (v10 is in /usr/lib/flashplugin-nonfree)

---

