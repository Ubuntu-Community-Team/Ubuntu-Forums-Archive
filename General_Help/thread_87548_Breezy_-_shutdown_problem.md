---
title: "Breezy - shutdown problem"
date: 2005-11-08
forum: General Help
---

### Post by Optiker on 2005-11-08
I posted this to the Kubuntu forum, but haven't had any replies, so thought I'd post here as well.

When I logoff/restart, I get an error window indicating a crash. I didn't copy message exactly, but  salient info is...

KDE Panel (klicker)
signal 11
sigsegv

If I click the other tab of teh error window, "Backtrack" I get a failure message that says "debugger not found"

After I close the window, logoff proceeds cleanly with no apparent consequences.

What is going on? Anything I need to be concerned about? I'd prefer to fix it rather than ignore it - so suggestions?

Thanks!
Optiker

---

### Post by mlomker on 2005-11-08
I had the same problem when Breezy was first released, but it was fixed with one of the updates since then.  Have you updated your system recently?

```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by daller on 2005-11-08
[QUOTE=Optiker]I posted this to the Kubuntu forum, but haven't had any replies, so thought I'd post here as well.

When I logoff/restart, I get an error window indicating a crash. I didn't copy message exactly, but  salient info is...

KDE Panel (klicker)
signal 11
sigsegv

If I click the other tab of teh error window, "Backtrack" I get a failure message that says "debugger not found"

After I close the window, logoff proceeds cleanly with no apparent consequences.

What is going on? Anything I need to be concerned about? I'd prefer to fix it rather than ignore it - so suggestions?

Thanks!
Optiker[/QUOTE]

You upgraded to KDE3.5, right?

Look here:

[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems?highlight=%28Known%29%7C%28KDE3%29](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems?highlight=%28Known%29%7C%28KDE3%29)

...It's a known bug, and you can solve it by following the guide on the above page...

---

### Post by daller on 2005-11-08
[QUOTE=mlomker]I had the same problem when Breezy was first released, but it was fixed with one of the updates since then.  Have you updated your system recently?

```

sudo apt-get update
sudo apt-get upgrade

```[/QUOTE]

Okay, mlomker :)

I'll start with the eldest ones then :)

---

### Post by Optiker on 2005-11-08
daller...ah...let's see, did I update to KDE 3.5? Danged if I know! I DLed the Breezy ISO and installed it. DL was on 18 Oct. I believe in my ignorance and not knowing how to install packages once I selected them, I probably hit the "update all" or "upgrade all" button (don't recall which it is), so unless that updated KDE, I did nothing else that would have updated it.

Sorry guys...I'm just a Linux greenhorn - still tyring to find a distro that I like (tried Redhat, Mandrake, Libranet, Knoippix, and now am finding Kubuntu to my liking) - so please bear with my lack of expertise.

mlomker...I think I can handle that.

Sounds like you and daller agree on the diagnosis and fix, so must be right. Will try it!

Thanks very much!
Optiker

---

### Post by mlomker on 2005-11-08
[QUOTE=Optiker]daller...ah...let's see, did I update to KDE 3.5? [/QUOTE]

3.5 is a beta, so you won't have that unless you went out of your way to install it.

---

### Post by goombah88 on 2006-01-27
i'm having the same problem as Optiker.  I'm running KDE 3.5 and everything else is up-to-date.  I'd really love to know what's causing this cause it is pretty annoying.  which log file is it that contains the details of the crash?  is it xorg.log?  any info you guys need from me to help figure this out just lemme know and i'll post it as soon as i get back home to linux-sweet-linux (my work computer is XP Pro :( )

---

