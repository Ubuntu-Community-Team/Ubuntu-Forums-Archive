---
title: "Painfully loud beeps"
date: 2005-11-22
forum: General Help
---

### Post by jonathanhayward on 2005-11-22
On my computer, the system beep is obnoxiously loud, and adjusting the volume control just left of the top menu bar's date doesn't make it any softer.

How can I reduce the system beep volume to something that's not painfully loud?

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail ( gmail.com) account, please tell me!

---

### Post by earobinson on 2005-11-22
I dont think so but you can turn it off (its comming from the pc speaker?), just go System -> preferences -> sound, there there you can turn of system beeps or system sounds (not on my *nix box so this might be wrong) If it is and someone has not corrected me repost and Ill check it when im next at my *nix box

---

### Post by jonathanhayward on 2005-11-22
[QUOTE=earobinson]I dont think so but you can turn it off (its comming from the pc speaker?), just go System -> preferences -> sound, there there you can turn of system beeps or system sounds (not on my *nix box so this might be wrong) If it is and someone has not corrected me repost and Ill check it when im next at my *nix box[/QUOTE]

Thank you; I chose a visual alternative. (Speaking as someone interested in usability, having a beep sound that people may experience as painfully loud seems a questionable default. The same goes with not having the obvious volume control as able to soften it.)

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail ( gmail.com) account, please tell me!

---

### Post by earobinson on 2005-11-22
I dont think that the programers have any control over this, I think that it is a system beep, and I do not think your system beep has a volume control.

During your boot up if your computer beeps is it just as loud?

---

### Post by db82 on 2005-11-22
Here's a quick fix - open up your case, locate the pc speaker cable and simply unplug it. I had this done with one of my old computers. Actually, the bleeping was so obnoxious and irritating that I might have cut with scissors:) It works, believe me.

---

### Post by SickTwist on 2005-11-22
[QUOTE=jonathanhayward]On my computer, the system beep is obnoxiously loud, and adjusting the volume control just left of the top menu bar's date doesn't make it any softer.

How can I reduce the system beep volume to something that's not painfully loud?

++ Jonathan Hayward, [email]jonathan.hayward@pobox.com[/email]
** To see an award-winning website with stories, essays, artwork,
** games, and a four-dimensional maze, why not visit my home page?
** All of this is waiting for you at [http://JonathansCorner.com](http://JonathansCorner.com)

** If you'd like a Google Mail ( gmail.com) account, please tell me![/QUOTE]

When do you hear this beep in Ubuntu? When you use a particular program? During boot? When an error occurs? When you're typing in a virtual terminal? There are many different programs that could send noise to the speaker.

---

### Post by earobinson on 2005-11-22
> Thank you; I chose a visual alternative. (Speaking as someone interested in usability, having a beep sound that people may experience as painfully loud seems a questionable default. The same goes with not having the obvious volume control as able to soften it.)

I think this means that the problem has been solved, open up a terminal and and hold down backspace then the comptuer will beep at you. (this volume is set by the computer and not ubuntu (As far as I know). and to turn if off go to system -> preferences -> sounds    then click the system bell and you can turn if off and on.

---

### Post by cowlip on 2005-11-22
I think there's  a file called /etc/inputrc where you put in "set bell-style none", but I don't know if it works anymore in Debian.

---

### Post by SickTwist on 2005-11-23
[QUOTE=earobinson]I think this means that the problem has been solved, open up a terminal and and hold down backspace then the comptuer will beep at you. (this volume is set by the computer and not ubuntu (As far as I know). and to turn if off go to system -> preferences -> sounds    then click the system bell and you can turn if off and on.[/QUOTE]

The noise from gnome-terminal can be disabled by right-clicking in the terminal, clicking on "Edit Current Profile..." in the context menu, unchecking "Terminal Bell", and clicking close.

---

### Post by Zeenomorph on 2008-03-07
I'm now having this problem.  The strange thing is that I didn't use to.  I had a 'normal' volume system beep, and now it has become annoyingly loud.  I guess there is no fix?

---

### Post by Oldsoldier2003 on 2008-03-07
> **db82 said:**
> Here's a quick fix - open up your case, locate the pc speaker cable and simply unplug it. I had this done with one of my old computers. Actually, the bleeping was so obnoxious and irritating that I might have cut with scissors:) It works, believe me.
edit:
/etc/modprobe.d/blacklist
append this line:
```
blacklist pcspkr
```

no more pc speaker in Ubuntu after the next reboot


to kill the beep in a non persistent fashion:

```
sudo modprobe -r pcspkr
```


digital scissors!

---

