---
title: "One folder won't die from trash can!"
date: 2008-07-11
forum: General Help
---

### Post by yosumi on 2008-07-11
i'm not sure why this folder won't destroy. i've selected "empty trash" many times. i've tried again after rebooting. same thing. it was folder containing some windows wireless drivers i used for ndiswrapper. does this happen to you? it's so annoying. is there a way to force delete it? thanks.

---

### Post by NullHead on 2008-07-11
This will happen when you put a file with reed-only file permissions in the trash. You can manually remove it from the .local/share/Trash/files directory. 

You can remove your file with the terminal or from a root nautilus file browser.

---

