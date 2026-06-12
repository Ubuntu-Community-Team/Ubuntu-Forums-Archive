---
title: "Adobe prints with wrong settings"
date: 2008-11-14
forum: General Help
---

### Post by Paddy Landau on 2008-11-14
I have a printer whose defaults are set as I want them (double-sided and in colour).

That works great from OpenOffice, Firefox, Thunderbird, Gimp, and so on.

Except...

When I print from Adobe Reader, it's always single-sided and in black-and-white.

Does anyone know how I can correct Adobe's print settings? I've found nothing in its preferences to indicate what to do. For some reason, Adobe Reader doesn't appear to use the standard print options that all the other programs use.

Ubuntu Hardy 8.04
Adobe Reader 8.1.2.06/21/2008
HP Officejet Pro L7780

---

### Post by igknighted on 2008-11-14
What if you use the default PDF viewers (evince i think?  I'm a kde guy, i forget what gnome defaults to).  The adobe viewer kinda sucks, I would use the ones that come with the default install

---

### Post by wylfing on 2008-11-14
I wouldn't say the Adobe reader "sucks," especially if you need to accomplish things like seeing markups others have done in Acrobat.

Anyway, more on point...If you choose File > Print, select your printer, and then click Properties, you will see a Printer Command box with the actual lpr command and its options specified. You can edit this manually. What you'll be interested in are things like "-o Duplex=DuplexNoTumble" (instead of "-o Duplex=None" for example).

To find out what options you can set, open a terminal and type
```
lpoptions -p <printer> -l
```
You can leave off specifying the printer if you want information about your default printer. For your duplex issue, the option I named above is probably what you want. For color, look under the Quality settings and find a color output mode that suits you, e.g., "-o Quality=300ColorCMYK" and see if that improves things.

---

### Post by Paddy Landau on 2008-11-14
> **igknighted said:**
> What if you use the default PDF viewers (evince i think?  I'm a kde guy, i forget what gnome defaults to).  The adobe viewer kinda sucks, I would use the ones that come with the default install
I disagree; it doesn't suck at all. I specifically need the "Shrink to Printable Area" option that Adobe Reader gives and that (as far as I know) Evince doesn't have.

---

### Post by Paddy Landau on 2008-11-14
> **wylfing said:**
>  ```
lpoptions -p <printer> -l
```
Thanks for letting me know about lpoptions.

I've set the settings that I want using lpoptions (there are a couple that aren't set even when doing them through System -> Administration -> Printing).

> **wylfing said:**
> If you choose File > Print, select your printer, and then click Properties, you will see a Printer Command box with the actual lpr command and its options specified. You can edit this manually.
However, Adobe Reader still won't print in colour!

And, for whatever reason, although the Adobe print options box says, "You can add/change the command line options", I can't. I put my cursor inside the Printer Command box, but I can't delete, change or add to the options after the lpr command.

Do you know what I can do?

---

### Post by wylfing on 2008-11-14
That's certainly a puzzler. Did you install the repository version or did you install the version from Adobe's web site?

If you installed from Adobe's site, you might try switching to the repository version.

In either case, you can also try this:
```
mv ~/.adobe/Acrobat ~/.adobe/backup
```
That will wipe out your personal settings for Reader. Run Reader again and you should get a brand-new set of default preferences. See if that helps. (If anything goes awry you can rename "backup" to "Acrobat" and it will restore all your old preferences.)

---

### Post by Paddy Landau on 2008-11-15
Well, I've managed to get it working. Unfortunately, I don't understand how!

I followed your suggestion of renaming the settings folder; no luck there.

I uninstalled the version that I had (which was from the Adobe website) and reinstalled from Synaptic Manger. I also redid the lpoptions setting, which strangely had gone back to grayscale.

That worked.

Thanks for you suggestions!

---

