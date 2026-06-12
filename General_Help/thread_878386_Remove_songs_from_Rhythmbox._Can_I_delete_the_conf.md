---
title: "Remove songs from Rhythmbox. Can I delete the config file?"
date: 2008-08-02
forum: General Help
---

### Post by agim on 2008-08-02
I have two of every song on rhythmbox, due to my own mistake. I have two nearly identical folders that I imported, and now I can't have Rhythmbox remove the media from one of them.

I tried to remove Rhythmbox, I even followed the option that said "remove configuration files" with synaptic, but no luck.

Can anyone tell me how to remove the songs, or what the name of the config file is. It doesn't matter if I have to remove everything, as long as I just get it finished tonight.

Thanks

---

### Post by pytheas22 on 2008-08-02
Try this:
```

cd ~
rm -rf .gconf/apps/rhythmbox
rm -rf .gnome2/rhythmbox
```

I think that should do it (and yes, I am telling you to use the "rm -rf" command, which can be dangerous, but I promise I'm not being malicious; if you want me to explain what the command is doing let me know).

---

### Post by agim on 2008-08-02
No, I am familiar enough with the command line to know. I really just needed the address to the files.

And thanks for mentioning that you were using the 'dreaded' command, its always good to mention.

I will try it now.


Edit: Everything worked fine. Thanks.

---

### Post by davide4hire on 2009-08-26
This was a very helpful post. But I found one other location I had to clean out before rhythmbox would forget about my library. The directory ~/.local/share/rhythmbox contained some XML files that had to be removed.

```

rm ~/.local/share/rhythmbox/*

```

After that, rhythmbox had no songs in it and I could re-import my music directory.

Thanks!

---

