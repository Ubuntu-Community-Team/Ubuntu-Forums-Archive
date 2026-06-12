---
title: "Pidgin startup problem"
date: 2008-09-15
forum: General Help
---

### Post by stans on 2008-09-15
I'm on 8.04 - and found this morning that Pidgin just goes away after I enter passwords for my IM accounts. 

A search here found a suggestion to delete the .purple directories (rm -rf /home/$USER/.purple/) but it did not help in my case.

Entering 'pidgin' at a terminal prompt doesn't show anything - after a brief pause the prompt returns.

Any suggestions ?

---

### Post by ShaunByres on 2008-09-15
Try, this in terminal.

```
sudo apt-get upgrade pigdin
```

and secondly this, just to make sure your system is up to date.
```
sudo apt-get update
```

Perhaps going to synaptic package manager, search for pidgin and mark the following for re-installation.

Pidgin
Pidgin-data

Let me know if it works,

p.s You could also try alternatives such as aMSN?

---

### Post by hackapelite on 2008-09-15
For an MSN alternative, I think aMSN  is crap - it's just so cluttered and whatnot, I plain hate its looks (though it does work, which is, well, a bonus). So far I think Emesene (GNOME) is the best MSN clone for Linux, along with KMess for KDE.

---

### Post by howefield on 2008-09-15
> **ShaunByres said:**
> Try, this in terminal.

```
sudo apt-get upgrade pigdin
```

and secondly this, just to make sure your system is up to date.
```
sudo apt-get update
```

Perhaps going to synaptic package manager, search for pidgin and mark the following for re-installation.

Pidgin
Pidgin-data

Let me know if it works,

p.s You could also try alternatives such as aMSN?

Wouldn't you do the sudo apt-get update first ?

---

### Post by Dougie187 on 2008-09-15
You probably should do the update first, and then the upgrade.

If that doesn't work. See what/if it says anything in command line when you try to run it.
Just open up a terminal and type
```
pidgin
```

You can also look at your syslogs to see if they say anything helpful.

---

### Post by ShaunByres on 2008-09-15
> **howefield said:**
> Wouldn't you do the sudo apt-get update first ?

Yeah,  sorry I wasn't paying attention properly when I was typing it up but either way should produce the same results! (from personal experiance)

I use pidgin more often than any other messenger client but aMSN is good if you're looking for a Windows Live! messenger look which some people switching over from windows are looking for.  Change is good but it's best to ease into using something completely different.

However, thats a different topic!

---

### Post by stans on 2008-09-15
Thanks for all the replies.

I get nothing but another prompt when entering 'pidgin' at a terminal prompt. It did work fine this past Saturday when I laid down the Ubuntu 8.04 for the first time (freshly updated system).

Interestingly enough, when I got home from work today and booted up, brought up Pidgin I found that a message window had opened cause someone left me a message, but no Pidgin window was present.

Pidgin isn't on my list in Synaptic - so how to cleanly de-install and re-install ?

Guess I should read the manual.

I should add - apparently Pidgin is running in some sort of invisible mode as I just got another message window opened with a contact sending me messages. Why cannot I see Pidgin ?

---

