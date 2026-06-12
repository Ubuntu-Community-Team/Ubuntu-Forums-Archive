---
title: "Emerald issues"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by ady_bluefresh on 2009-09-07
Hi!:)I have compiz installed and working;I also have emerald installed, but it just won't autostart unless I run emerald --replace.I went to Sartup applications and made a new entry with the same command(emerald --replace), but still emerald won't load.I also modified the file "compiz-decorator" from USE_EMERALD="no" to USE_EMERALD="yes" and no result!!!!!!:confused:What could I do?

---

### Post by howefield on 2009-09-07
Try opening up compiz settings manager, and click on the Window Decoration plugin, change the "Command" field to /usr/bin/emerald

---

### Post by ady_bluefresh on 2009-09-10
I have tried that but emerald still won't replace [FONT="Book Antiqua"]gtk windows decorator[/FONT]
Is there anything I can do?:confused:

---

### Post by User3k on 2009-09-26
I was having the same problem as you. I did all the same steps as well. This is wjat worked for me. In the command line in the compiz settings manager, window decorations type "emerald --replace" instead of "/usr/bin/emerald"

This worked perfectly for me.

---

