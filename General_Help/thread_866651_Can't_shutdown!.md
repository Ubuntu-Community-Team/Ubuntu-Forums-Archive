---
title: "Can't shutdown!"
date: 2008-07-22
forum: General Help
---

### Post by Mattaus on 2008-07-22
Hi all,

(Mods feel free to move this if it should be in the Apple section - I wasnt sure as I think its more generic Ubuntu rather than apple related)

I recently got a dual boot of MAC OS X and Ubuntu 8.04 running on my Macbook and Ubuntu was working fine.

However I booted into Ubuntu this afternoon and the regular shutdown icon in the top right corner had been replaced by a little green man running. Now the only options available are hibernate, switch user or logout (plus some oddball ones I cannot remember off the top of my head) So I cannot shut the thing down without pulling the battery out of the laptop.

Any reason why this has happened and how I can fix it?

Thanks for any help.

---

### Post by iaculallad on 2008-07-22
After shutting your Ubuntu down improperly, Had you tried turning back on and observe if the "little green running man" icon appeared?

To properly shutdown your computer, drop to your terminal and issue the command below:

```
sudo shutdown -h now
```

---

### Post by Mattaus on 2008-07-22
doh! lol. Completely forgot about that command.

I'll have to check that out when I get a chance to fire my laptop back up...I'm about to board a plane :S

I'll obviously report back asap!

---

### Post by Mattaus on 2008-07-22
Right, after properly shutting down the little green man is still there, and no options to shutdown or restart exist....

---

### Post by Mattaus on 2008-07-24
Anyone?

It's kind of annoying having to use the terminal just to shut down...especially seen as my goal with ubuntu is to get it as user friendl (for me anyway) as possible...

---

### Post by iaculallad on 2008-07-24
Verify this:

Navigate to System->Administration->Login Window
In the first tab "Local" of "Login Window Preferences", check if "Menu Bar:
Show Actions menu" is selected.
If no, check it and close the form. If that was the problem it should re-appear.

---

### Post by Rocket2DMn on 2008-07-24
I thought that was a new thing in Intrepid.  Maybe you have the backports repository enabled?  Now in Intrepid development you go to System->Shut Down, though there is a bug with this only returning users to the login screen...

---

### Post by iaculallad on 2008-07-24
> **Rocket2DMn said:**
> I thought that was a new thing in Intrepid.  Maybe you have the backports repository enabled?  Now in Intrepid development you go to System->Shut Down, though there is a bug with this only returning users to the login screen...

Intrepid? Is the OP not using Hardy?

Excerpt:
*I recently got a dual boot of MAC OS X and Ubuntu 8.04 running on my Macbook and Ubuntu was working fine.*

---

### Post by Rocket2DMn on 2008-07-24
Yes, that is why I mentioned that he may have backports enabled.  Some newer package versions get sent there, but are not officially supported for the Ubuntu version they are being backported for.

---

### Post by Mattaus on 2008-07-24
Ah cheers iaculallad, the menu bar thing fixed the problem...though the icons appear different from before. Not complaining, just odd it ever dissapeared. Ah well.

---

