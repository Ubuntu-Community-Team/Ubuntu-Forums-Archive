---
title: "[SOLVED] Getting the message 'Composting is not supported on your system'"
date: 2008-10-30
forum: General Help
---

### Post by MobiusNZ on 2008-10-30
Hi guys,

I've just installed the latest kubuntu, and its really slick! One problem I'm having though is I can't enable desktop effects - everything is greyed out, with the text "Composting is not supported on your system. Required X extensions (XComposite and XDamage) are not available", with no information on how to enable these.

I have the latest nvidia driver from the restricted device manager installed, and libxdamage1 appears in apt as installed.

How do I enable these things?

---

### Post by eternalnewbee on 2008-10-30
Sorry, but I know little about Kubuntu. Just one thought: Maybe some repositories should be added, so you can download the needed extensions.
(Did you any trouble with the desktop effects with your previous version?)

---

### Post by MobiusNZ on 2008-10-30
I had no problems with Compiz in 8.04 (but I was running Ubuntu for that particular release). Desktop effects are mentioned in the Kubuntu release announcement, so I'd be suprised if I needed extra repos - but if anyone knows I'd be glad for the help...

---

### Post by MobiusNZ on 2008-11-03
I've found the solution: it appears you can't use desktop effects with Xinerama on nvidia. Switching my displays to TwinView did the trick.

---

