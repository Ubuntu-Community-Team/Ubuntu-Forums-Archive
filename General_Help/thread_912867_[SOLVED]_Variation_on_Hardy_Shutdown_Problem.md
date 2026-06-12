---
title: "[SOLVED] Variation on Hardy Shutdown Problem"
date: 2008-09-07
forum: General Help
---

### Post by daniel68 on 2008-09-07
I have just installed a duel boot ubuntu onto my laptop (Packard Bell EasyNote) for the first time. I know very little about using it (installing it was the start of my plan to learn). Because of this any instructions as to how to solve the problem need to assume I know little about using ubuntu.

 When I shutdown ubuntu it switches from what I believe is the splash screen to script finishing with:

```
halt: Unable to iterate IDE devices
```

The computer just holds there until I switch it off by pressing the power button.

I explored the forum and tried the following solutions people had to similar problems.

The closest match I had to my problem where ubuntu wouldn't shutdown at all was this thread: 
[http://ubuntuforums.org/showthread.php?t=906692&highlight=shutdown]("http://ubuntuforums.org/showthread.php?t=906692&highlight=shutdown")

I could not find the "acpi=off" in the file in question to replace though and I don't know where I would insert "acpi=force". If you want I can paste what I get when I type ```
sudo dmesg
``` into the terminal if that helps.

I also tried a few solutions to the more general shutdown problems as documented in this thread: [http://ubuntuforums.org/showthread.php?t=772733]("http://ubuntuforums.org/showthread.php?t=772733")

first I tried this solution:
> Go to "System" -> "Administration" -> "Login Window". In the "General" tab, press "Edit Commands...", which will launch a window titled "Reboot, Halt, Suspend and Custom Command Preferences". In this window, select "Halt command" in the drop-down box for "Command Type:". Underneath it, in the "Path:" box, cut the verbiage in quotes: "Shut Down via gdm." After doing so, press "Apply Command Change", then paste the quoted phrase back into the "Path:" box and hit the "Apply Command Change" button again. Finally, go through the same process for the "Reboot command" in the "Command Type:" drop-down, again cutting the quoted phrase, applying the change, pasting the quote, and applying the change.
I tried this (I assume when you paste the text back in you insert it back in the quotation marks and not replace the whole path).
This made no difference.

I also tried this: > Thank you very much. I haven't had problems with rebooting, only shutting down (no idea why), so in the file /etc/init.d/halt I changed the line
Code:

halt -d -f -i $poweroff $hddown

to
Code:

halt -d -f $poweroff $hddown

and my computer shut down for the first time in a week (or two, or whatever). It's rather amazing, and it's *buntu generic.

This actually changed something but didn't make it better. Instead of going to script it switched to an empty black screen with the flashing white underscore in the top left corner. It then went back to the splash screen and then back the the empty screen with the cursor. I had to manually turn the computer off again with the power button. EDIT - I undid this change.

I would appreciate any help. I've already solved a problem with the login screen being the wrong resolution but this is harder. Once I've solved this I will also need to find a way to stop the mouse from going crazy. If you want me to provide a full copy of the script that is printed onscreen when I shutdown I will do that.

---

