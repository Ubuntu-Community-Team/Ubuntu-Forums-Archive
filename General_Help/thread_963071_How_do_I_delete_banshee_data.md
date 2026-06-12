---
title: "How do I delete banshee data"
date: 2008-10-29
forum: General Help
---

### Post by pedrotuga on 2008-10-29
Ok, i installed banshee and played around with it a bit. The only usage I ave for it is to transfer videos to my portable player.

Now... I imported all my mp3 files into banshee's library manager. I don't really need all that load of entries in banshee, whenever i need to transfer a file to my mp3 player I can add it manually to avoid all that clutter caused by tons of mp3 tracks.

I looked for ~/.Banshee or ~/.banshee, but none exists. Where's banshee's data sotered, I want to delete it.

---

### Post by Sam on 2008-10-29
> **pedrotuga said:**
> Ok, i installed banshee and played around with it a bit. The only usage I ave for it is to transfer videos to my portable player.

Now... I imported all my mp3 files into banshee's library manager. I don't really need all that load of entries in banshee, whenever i need to transfer a file to my mp3 player I can add it manually to avoid all that clutter caused by tons of mp3 tracks.

I looked for ~/.Banshee or ~/.banshee, but none exists. Where's banshee's data sotered, I want to delete it.

```
locate -i banshee |grep '^/home'
```

---

