---
title: "Laptop battery and ACPI problem"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by christhemonkey on 2006-06-18
My laptop (Smart-tec NX6000) does not give the correct time readings for the batteries remaining life.

It always just leaves me with a:
> [INDENT]Power critically low[/INDENT]
You have approximately **3 minutes remaining** battery life (100%).

I have disabled the automatic shutdown when battery life is low, but still error messages like this are very, very frequent.

I have been following the advice of [this post]("http://www.ubuntuforums.org/showpost.php?p=387628&postcount=18").
But my dsdt.dsl is not particularly helpful...


My dsdt.dsl:
> **** Exception AE_SUPPORT during execution of method [NULL NAME]

Method Execution Stack:
[INDENT]Method [NULL] executing: Store (TP1H, CTOS)[/INDENT]

No method node (Executing subtree for buffer or opregion)

No method node (Executing subtree for buffer or opregion)

Could not parse ACPI tables, AE_SUPPORT


Which does not fill me with hope...
When installing, i had ACPI turned off in the BIOS (if that affects anything!)
It is now turned on and enabled and all that sort of stuff.

Have tried the advice of [this]("http://forums.gentoo.org/viewtopic.php?t=122145") gentoo forums page and [the wiki ]("https://wiki.ubuntu.com/ACPIBattery")but the wiki does not particularly help on this issue, as my laptop is relatively obscure and so no corrected dsdt has been uploaded to [here]("http://acpi.sourceforge.net/dsdt/view.php").

I suppose that i should mention that hibernate and suspend dont work. Just bring me straight back to screen i hibernate from.

Should i just disable acpi in my bios?
Or am i stuck always using the laptop when plugged in?

(Which just sucks and defies the point of me having this laptop...)

Any help really appreciated!

---

### Post by christhemonkey on 2006-06-21
Did i mention any help was really appreciated.... :p

Also just thought to mention, that when plugged in, the battery constantly reports that the battery is fully charged.  With one pop up after another after another....

Is there anyway of disabling these popups (if it is not possible to fix my dsdt)?

---

