---
title: "HH 8.04 Trouble setting Kate as the default text editor"
date: 2008-08-02
forum: General Help
---

### Post by mdlueck on 2008-08-02
Greetings-

I happen to prefer kate over the default text editor in Ubuntu.

In 7.04 I had no problems adjusting various text file extentions to open Kate instead of the default editor.

However, after a complete reload of my workstation, Kate via the Gnome desktop is giving me problems. Double click, nothing happens, nothing in "ps aux" either.

Adjusting the default editor back to what it was, file opens right up when double clicking.

I can open text files into Kate just fine from the bash prompt.

I deleted all kate* related files under ~/.kde/ and that did not solve the trouble either.

Any suggestions of how to track down this problem between Gnome and Kate?

TIA!

---

### Post by Jorge_C on 2008-10-24
Hi,

I had the same problem, I' running gnome but I wanted to try kde4, so I installed kubuntu-kde4-desktop to try it out and I really liked kate.
Any way, I use gnome as my main desktop environment and I wanted to set kate to be the default text editor but it would never open when double clicking.
Googling my problem I found your post, which gave me an idea that works!

Ok, that's what I did (there must be easier ways to do it, but this works for me):
Apps->Accessories and right click in kate -> add to panel
Now, if you right click the launcher you've just added to you panel and click on proprieties you'll get the command that does launch kate. For me, it's /usr/lib/kde4/bin/kate %U
Copy it, and now, for every file type you want kate to open, just right click the file, open with-> open with another application and you paste the command there (set custom command)
Double clicking those files should launch kate, and you can delete the launcher you previously added to the panel.

Hope it helps!

PS: Do you know an easy  way to change *all* file types gedit opens to be opened by another app, kate in this case? It really is a pain not being able to fully replace an app easily.

---

### Post by mdlueck on 2008-10-24
I ended up logging a bug against this problem:

"Kate does not start when set as the default editor for a particular file extension"
[https://bugs.launchpad.net/bugs/254656](https://bugs.launchpad.net/bugs/254656)

It seems this really is a bug.

I found a work around to this problem... in the file association dialog, create a new association, and type in "kate" into the "Use custom command" field.

No, I do not know of a global way to change the default text editor. I understand that older versions of Gnome did have a way to set the default text editor, and in Ubuntu 7.04 that even showed up in the help for application association... just not the dialog... so it seems that has been gone for some time already now.

---

### Post by Jorge_C on 2008-10-24
Yeah, your workaround is exactly like mine, except by the fact that I have kde4, not 3 and thus "kate-kde4" is installed instead of "kate", and that's why my command is longer.

By the way, I'm actually using "/usr/lib/kde4/bin/kate -u %U" in order to keep all the opened files in the same kate window.

---

### Post by mdlueck on 2008-10-24
Thanks for that `kate -u %U` suggestion, works great! And that was annoying me!

I thought it had to do with choosing "New Session" as the default, but this is really what turned out to fix it.

Now if I could discover where Gonme keeps track of that... Off to see what file now has `kate -u %U` in it! ;-)

---

### Post by Jorge_C on 2008-10-24
You're welcome mdlueck!
Do you know what does "%U" mean? It appears in many launcher's commands...

---

### Post by mdlueck on 2008-10-24
No I do not know what %U happens to be. I think either a Gnome or Nautilus thing.

I found the custom `kate` entry here...

~/.local/share/applications/userapp-kate-HTEAFU.desktop

(I thing the CAP letters are just random.)

---

