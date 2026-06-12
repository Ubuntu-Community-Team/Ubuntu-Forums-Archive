---
title: "[SOLVED] If I uninstall wine will it uninstall the ..."
date: 2008-08-11
forum: General Help
---

### Post by Spaceman9 on 2008-08-11
If I uninstall wine will it uninstall the programs I installed into wine? I installed iTunes and QuickTime and iTunes doesn't work at all in Ubuntu. Thankx for any help

---

### Post by Victormd on 2008-08-11
You will need to manually delete wine related folders...

Open a terminal window and type
```
sudo rm -r ~/.wine
```
This will delete any program trace from wine.

There's another folder that contains some wine related info but I can't remember where it is... not very important though.

EDIT: Ok, found it. Sometimes you'll remove wine and the menu items remain so this will remove them:
```
sudo rm -r ~/.local/share/applications/wine
```

---

### Post by Spaceman9 on 2008-08-11
Thankx for your help Victormd. I have a question. Could I use Nautilus to remove the folders instead of the command line?

---

### Post by Victormd on 2008-08-11
Sure. Open the nautilus window and press CTRL + H to show the hidden folders and delete from there. However, you might run into permission issues. If so, running from the terminal would be easier.

---

### Post by Spaceman9 on 2008-08-11
I press Alt+F2 and type gksudo nautilus and hit Enter to get root Nautilus. With the CL I'm always worried it might do more that I think it's doing. I know that sounds strange. May be I used winblowz for too long.

---

### Post by Victormd on 2008-08-11
> **Spaceman9 said:**
> I press Alt+F2 and type gksudo nautilus and hit Enter to get root Nautilus. With the CL I'm always worried it might do more that I think it's doing. I know that sounds strange. May be I used winblowz for too long.

Ultimately you have to feel comfortable using whatever OS+environment you're using. I used windows for way to long as well and took me a while to "trust" my terminal instincts, that's very normal! hehehe :)

---

