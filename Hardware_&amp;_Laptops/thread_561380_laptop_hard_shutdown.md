---
title: "laptop hard shutdown"
date: 2007-09-27
forum: Hardware &amp; Laptops
---

### Post by oldsalt on 2007-09-27
Hello
I have Feisty installed on a Packard Bell Easy note laptop. It has always needed a hard shutdown, 6+ seconds holding down the power button.
Will this be the same in Gutsy ?
Is it detrimental long term to shutdown in this way?

Do the Dell laptops installed with Ubuntu require hard shutdowns?

tia

---

### Post by bloodfox on 2007-09-27
it may be other reasons

---

### Post by ajgreeny on 2007-09-27
If you do a search on "poweroff" problems you will see that this has been a problem for several users of ubuntu and kubuntu, including myself.  There are a number of possible ways to try and overcome the problem by editing various system files, but I didn't find any of them solved it.  However, having added **kubuntu-desktop** to ubuntu when I first installed, I think it could just be something to do with the usplash and incompatibilities between the two that were on my system, ie ubuntu-usplash and kubuntu-usplash.  I have now got rid of ubuntu-usplash (and ubuntu-desktop metapackage) and haven't had the problem since, now about a month or more.  If you have added another desktop with its own usplash, it could be worth uninstalling one of them to see if it also works for you.

---

### Post by floke on 2007-09-27
> **bloodfox said:**
> it may be other reasons

What a fantastic piece of advice.

You could try some other live cds (eg pardus, pclos, fedora etc) and see if they give you shutdown issues - if not then it sounds like an ubuntu issue. Have you also tried shutting down from the terminal? = sudo shutdown -h now

Or try searching the forum for this topic - there's a few threads on it

eg

[http://ubuntuforums.org/showthread.php?t=5193](http://ubuntuforums.org/showthread.php?t=5193)

You might have to try different power management options - eg boot with acpi=off, or noapic etc.

---

### Post by Linicks on 2007-09-27
As to the Dell Ubuntu offerings (I have a Inspiron 6400 UK model), no problems shutting down, everything works perfectly.

BUT, being a sysadmin with wary eyes on getting things right I noticed I was getting 'apm not supported in BIOS' messages in syslogs, and as I fixed this years ago on my home desktop running Slack, I added to xorg.conf the line:

```
Section "ServerFlags"
    Option     "NoPM"  "true"
EndSection
```

That stopped the syslogs reporting the message, but it also made shutdown hang and a hard reset was the only way 3 times out of 4.  Removing that, all is OK again

So maybe not your case, but perhaps could help debug this issue (it does seem it is a power management thing here).

In any case, a hard shutdown is not the way to go...

Nick

---

### Post by oldsalt on 2007-09-27
Thanks forall the information.

I found the same problem with pclos.

Using a terminal shutdown was unsuccessful.

Will need to investigate further.

---

