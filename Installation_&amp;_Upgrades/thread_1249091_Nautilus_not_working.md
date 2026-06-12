---
title: "Nautilus not working"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by anafshalom on 2009-08-24
After upgrading to Jaunty Jackalope nautilus does not work and I get this message:

   [SIZE="1"] Nautilus cannot be used now. Running the command "bonobo-slay" from the console may fix the problem. If not, you can try rebooting the computer or installing Nautilus again.

    Bonobo could not locate the Nautilus_shell.server file. One cause of this seems to be an LD_LIBRARY_PATH that does not include the bonobo-activation library's directory. Another possible cause would be bad install with a missing Nautilus_Shell.server file.

    Running "bonobo-slay" will kill all Bonobo Activation and GConf processes, which may be needed by other applications.

    Sometimes killing bonobo-activation-server and gconfd fixes the problem, but we do not know why.

    We have also seen this error when a faulty version of bonobo-activation was installed.[/SIZE]



I've tried bonobo-slay, I've tried purging Nautilus and reinstalling it. I've tried uninstalling ubuntu-desktop and reinstalling.
I've tried renaming the .Nautilus folder.

Everything else I do works fine, but I'd like to get Nautilus working again.

---

