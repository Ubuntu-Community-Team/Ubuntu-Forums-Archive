---
title: "After installing pubkey and js2-mode, update manager now says I need many packages"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by david.karr on 2009-02-25
Ubuntu 8.10.

I was going along ok when I decided that I wanted to install "dos2unix" and "js2-mode", which is a JavaScript mode for Emacs.  I looked up the procedures for adding them.  I added the repository in synaptic, but I saw that it didn't have the pubkey, so I added the pubkey.  I was then able to install dos2unix and js2-mode, and they're running fine.  Everything's fine so far.

Right after completing that, the orange gear appeared saying that "There are 530 updates available".  That seemed a little coincidental and disturbing.

When I brought up Update Manager, it presented a dialog saying:

  "Not all updates can be installed ...", giving me the choice to run a "Partial Upgrade", or just continue (the choice of which is ambiguous).

I'm hesitant to install anything at this point.  Is there an obvious answer here, or is there a next step I should take?

---

### Post by cariboo on 2009-02-25
You obviously haven't been doing regular updates, there are two things you can do, just keep on ignoring the updates until the dependencies are met, or open an Applicatins-->Accessories-->Terminal and type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

THis will only install the updates that are installable, and leave the packages that ae missing dependencies.

Jim

---

### Post by david.karr on 2009-02-25
Sorry, but that's an invalid assumption.  I've been installing updates immediately after the orange gear appears.  Does your answer still apply, then?

For another data point, I scrolled through the suggested updates, looking for one where the list of changes was available (many of them are not).  I found "ca-certificates-java", and it's saying that the last update was for 20081028 (Oct 10, 2008).  There is no way that I hadn't had that installed already.  Something is making it think it wasn't installed anymore, or somehow uninstalled it, when I installed dos2unix or js2-mode, or the pubkey installation.

---

### Post by david.karr on 2009-02-25
Ok, well, I just spent about 2 hours running that command line, installing updates to 530 packages (I saved the output in a file).  When it was finally done, instead of an orange gear, I had the red bang downarrow, saying that "There are 531 updates available".

Inspecting the output file, it appears that only one package failed to install, which was "x11proto-input-dev".  Apparently that package tried to overwrite /usr/include/X11/extensions/XInput.h', which is also in package "libxi-dev".

When I bring up the aptitude GUI, it says again that not all updates can be installed.  I didn't look through the entire list of 531 updates, but it now lists a security update for the Flash plugin at the top, which wasn't in the list before.  The second one in the list is "acpi", which WAS the first entry in the list when I did this 3 hours ago.

Now what?

---

### Post by david.karr on 2009-02-25
I got this resolved with help from the ubuntu-users mailing list.  I never should have run that update command line as you suggested, but it doesn't appear to have caused any obvious harm.

The problem was that the repo that I added to get js2-mode was a debian repo.  I should have removed that repo right after installing js2-mode, but it didn't occur to me.  Once I finally removed that repo, the only suggested update left was the flash plugin, which was a "real" update.

Thanks for the help.

---

### Post by cariboo on 2009-02-25
You didn't mention in your original post hat you had added a debian repository, if you had my advice would have been totally different.

When asking for help include as much info as possible.

Jim

---

