---
title: "Japanese Input/Anthy"
date: 2008-10-25
forum: General Help
---

### Post by erikyuu on 2008-10-25
I've been working to get SCIM/Anthy up and running for Japanese input, but no matter what I try, SCIM won't toggle into Anthy or anything else I have enabled. 

I've tried a complete removal and reinstall and that didn't work. I've looked through the forums and tried the wiki and haven't found anything that solves the problem. 

The only explanation I can think of is that I'm running the intrepid RC and the ja repositories may not be updated for intrepid yet. 

Anyhoo, I'll keep fiddling, but I would appreciate another opinion/solution/thought.

---

### Post by erikyuu on 2008-10-25
Something worked, since SCIM is properly toggling between Anthy and english. 

Weird. I don't know which tweak fixed it.

---

### Post by riesengreen on 2008-11-02
Wow! I wish that SCIM/ANTHY would mysteriously start working on my computer. I can't even make the SCIM toolbar appear at this point!

I tried the uninstall/install trick too; I even kept track of all changes that I made, here:

[http://spreadsheets.google.com/pub?key=pp5bGT_cutU1skzwIbJG7Gw]("http://spreadsheets.google.com/pub?key=pp5bGT_cutU1skzwIbJG7Gw")

Spent quite a bit of time in the package manager, admittedly not really knowing what I was doing. But I kept track of all the changes!

Basically, first I uninstalled every package that it seemed might be connected to SCIM/ANTHY in any way, and then re-installed them. 

One random note:
When  I went to re-install packages, some of those that I had previously uninstalled were still, well...installed.

I realize that this isn't the most concise message, I need to stop drinking coffee and eat. I will check back later. But in any case, I would really appreciate any advice!

Thanks everyone!

:confused:

---

### Post by mdurham on 2008-11-02
Have you setup System->Administration->Language support?

---

### Post by riesengreen on 2008-11-02
Hi and thanks for the response.
Actually, yes I have. English and Japanese are both selected for language support. 
In fact, one curious note is that no matter how many times I check the box for complex language input and restart, the box remains unchecked.

---

### Post by mdurham on 2008-11-02
I don't know if this is any use but here are the scim things that I have installed for Chinese.

---

### Post by riesengreen on 2008-11-03
Thanks all!

Looked over the screenshot that mdurham kindly sent and realized that I had forgotten to reinstall the "bridge" packages, etc.!

So in retrospect, I suppose, the "uninstall everything and then reinstall everything" strategy was a success!

Everything seems to be working fine now. 

One random, possibly unconnected note:I deselected all input methods under Japanese except ANTHY.

---

