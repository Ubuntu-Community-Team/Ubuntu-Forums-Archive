---
title: "Compiz does not work with NVIDIA GeForce 7300"
date: 2008-09-30
forum: Hardware
---

### Post by Fhernd on 2008-09-30
Hi!


I'm using Ubuntu ver. 8.04 Hardy Heron. Ubuntu installed all drivers for each device, but the graphic card does not run correctly. Because when I activate the **Visual Effects** (Normal or Extra), the window borders does not appear on each window.

What's happens?

Laptop model: Toshiba Satellite A205-S4639


So long!

---

### Post by alan34 on 2008-09-30
Go System -Administration - Synaptic Package Manager then search for **compiz** and install
it all especially compizconfig-settings-manager. then search for **emerald** and install.

Then go to System - Preferences - Sessions and Add

Name Compiz
Command [B]compiz --replace
[/B]
Then click OK and Add again

Name Emerald
Command [B]emerald --replace
[/B]
Then click OK - you should now have two new entries in the list Compiz and Emerald.

Restart your computer

This should get your border back and give you more control over compiz

Ps I have a GeForce 7300 LE card myself

Good luck

---

### Post by Fhernd on 2008-10-01
Thanks for the answer, **alan34**!


I followed your steps. Then, some effects are actived, meanwhile some problems persists:

i.e.:

**[Title bar disappears]("http://softvaina.googlepages.com/DoesNotWorkCorrectly.jpg")** (Image).

What's happening?

Thanks for information!

---

### Post by NickLanam on 2008-10-01
Same thing as he just described. Window manager's decorations aren't taking hold. If you installed what he said to install, you should be able to go to system->preferences->advanced desktop settings and scroll down to the "window decorations" pluging. make sure it's checked. if it already is, click it's name and go through the settings until you find a field called "command" that should read "/usr/bin/compiz-decorator".

---

### Post by alan34 on 2008-10-01
Hi again here is my setup in screenshots. You should then have Compiz Setting Manager under System - Preferences then as the last post.

Hope this all helps

---

### Post by Fhernd on 2008-10-01
**alan34**. The problem persists. I follow your suggestions, but the problem continues... :(

Again, thanks for your information!

---

### Post by emshains on 2008-11-03
I don't have a freaking idea of what are you talking about !!!

You must have these packages installed ```
sudo apt-get install compizconfig-settings-manager emerald
```
All I did was go to the compiz settings manager, search for it in the repos, went to window decoration, and added this line to the field "command"```
emerald --replace
```


That works for me!

It all works for me with: 1.6ghz/768mb ram and the 7300GT on agp 8x

---

