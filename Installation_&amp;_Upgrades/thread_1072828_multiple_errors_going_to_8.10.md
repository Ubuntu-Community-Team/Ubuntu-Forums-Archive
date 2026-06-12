---
title: "multiple errors going to 8.10"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by jhaefner on 2009-02-17
Hello,
As usual for me upgrading ubuntu was a nightmare: I upgraded from 7.10 to 8.04 with errors, but a bootable system.  So I upgraded from 8.04 to 8.10 hoping the errors would go away.  They didn't.  Here are 3 that I need fixing soonest.  If you  know where to look for the problem, please let me know:

1. Texlive upgrade failed with lots of errors, most seem to come from texlive-base-bin.  Removing and reinstalling does no good.

This failure at the very end of the upgrade to 8.10 caused upgrade-manager to fail in the last steps, which may account for the next 2 errors.

2.  "Can not open display :0.0":  many others have seen this.  What is the fix?

3. Now I can not mount removeable devices.  E.g., when I attempt to mount a firewire external harddrive, I get:

mount point cannot contain the following characters: newline,G_DIR_SEPARATOR (usually /)

what is this all about?

Is it possible to force upgrade-manager to retry the entire upgrade?

thanks in advance.

Jim

---

### Post by Jadifabbio on 2009-02-17
Do you have a 8.04 disk or 7.10?  you can install that and then update from there.  I think it will start fresh so you will need to back up what you want if you want to try that.

---

### Post by jhaefner on 2009-02-18
I think you are right.  Had to do it on my laptop that also failed to install 8.10.  Now I'm thinking that if I want ubuntu I'll have to upgrade via fresh installs.  Fortunately, I'm a backup freak.

cheers,
Jim

---

