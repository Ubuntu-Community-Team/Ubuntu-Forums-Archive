---
title: "thinkpad g40 freezes after lid reopening"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by prazeres on 2007-11-05
My thinkpad g40 freezes when I reopen the lid. Pinging from the net, I've verified that the problem occurs just after the opening.

I tried some suggestions:

1) the grub parameter "nmi_watchdog=0"
2) adding "blacklist video" in /etc/modprobe.d/blacklist
3) "/usr/sbin/vbetool dpms off/on" in /etc/acpi/lid.sh

neither worked.

I'am running Ubuntu 7.10 - 2.6.22-14-generic kernel.

Any help?

Thanks,
Manoel

---

### Post by deleonjavier on 2008-01-08
hey i'm having the exact same problem, i also have a g40, do you get this resolved. i can't fix either. i'm just not closing my laptop lid, kinda sucks.

---

### Post by stoparrr on 2008-02-02
The same problem here. Any ideas or suggestions would help.

---

### Post by pupeno on 2008-03-29
Another one with the problem here :( Any solutions? :confused:

---

### Post by sikobabel on 2008-06-23
Hi everyone,

I've been struggling with this for awhile now but I believe I have this solved specifically for the G40.  Solutions I've found for other thinkpads did not seem to help.  I will try to cross-post this at the thinkwiki site as well.  

Here's what experiments I have tried:

1 - I tried removing all actions from /etc/acpi/lid.sh but this did not help.  I tried changing the action to "do nothing" for the lid closing, but this did not help either.  The only difference is that when I use "do nothing", I can see my mouse pointer when I reopen the lid, but it won't move and nothing responds.

2 - I tried using KDE instead of Gnome, but the problem stays exactly the same.

3 - I modified my kernel parameters to turn of ACPI (acpi=off).  This actually works, but with ACPI completely turned off I couldn't see other things like my battery level.  So this is one option, but I don't recommend it because I don't know what all of its implications might be.  For more information [see this link]("http://www.thinkwiki.org/wiki/Kernel_parameters").  I turned ACPI back on because I wanted to find a more elegant solution if possible.

4 - Knowing now that acpi is somehow part of the problem I started tooling around with the options for acpi.  I found a number of different versions of /etc/default/acpi-support for thinkpads, but could not find a magic combination to make these work.  If someone can fix this problem in this way, please feel free to post your version.

5 - I [revisited this site]("http://david.hardeman.nu/documents/thinkpad/single.html"), which is a bit out of date and for Debian on a G40.  It was helpful for getting Thinkpad Buttons and On-Screen display working before, this time I focused on the ACPI section.

If you look closely at his lid button script under the Suspend section, it has this interesting comment:

> This script changes to a text console, as required by vbetool, saves the current state of the video card to /etc/acpi/vbestate and then continues to suspend. 

After reading this, I tried switching to a text console (ctrl-alt-f1) and closing/opening the lid.  Everything worked fine.  No hang!  So I stole one line from his script:

```
/usr/bin/chvt 1
```

I put this in my /etc/acpi/lid.sh as the first command in the 'if' block where the lid is closed.

I put this line as the last thing in the 'else' branch of the same script:

```
/usr/bin/chvt 7
```

I restarted acpid (sudo /etc/init.d/acpid restart) and tried closing the lid.  When I opened it back up, everything was black.  I touched a key and was presented with a KDE lock prompt.  I logged in and everything came up just fine.

So these two little changes basically switch you to a plain text terminal and back again and avoid whatever it is about acpi that causes the laptop to freeze.

Good luck to you all!

---

### Post by sikobabel on 2008-06-26
Update on the above:  When I start a session with Gnome, the above fix no longer seems to work.  I have not yet figured out why this is the case, but I'm content for now to continue using KDE.

If anyone knows whether or not Gnome causes ACPI to react differently to events such as the lid being closed, please help me understand how and/or why?  Perhaps installing KDE caused a conflict?

---

