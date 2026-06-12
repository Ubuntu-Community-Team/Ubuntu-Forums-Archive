---
title: "Image Previews (NOT)"
date: 2008-09-21
forum: General Help
---

### Post by JemW on 2008-09-21
Yeah, I know - this old chestnut.

Hardy 8.04. Trying to attach images to an e-mail in Evolution. Nautilus is STILL not providing an image preview in the file selector. List of thumbnails so small they're useless - yes. Any kind of preview - no. I've searched and searched on this, and even seen mysterious screenshots of exactly what I (and many others) want, but for the life of me I can't see that you can do this.

If I'm wrong I'd be eternally grateful if someone would tell me how to do it.

Thanks...

---

### Post by howefield on 2008-09-21
try deleting your thumbnail folder. If the system doesn't recreate it, then you can manually.

---

### Post by IanW on 2008-09-21
The folder you need to empty is located at
```

~/.thumbnails/fail/gnome-thumbnail-factory

```
Delete everything in there and you should be able to refresh the thumbnails.

Also you can change thumbnail size in Nautilus. Look where it says **% to the left of the "View as Icons" button at far right of the Nautilus toolbar. This can be changed to scale thumbnails up to 400%.

---

### Post by JemW on 2008-09-21
> **IanW said:**
> The folder you need to empty is located at
```

~/.thumbnails/fail/gnome-thumbnail-factory

```
Delete everything in there and you should be able to refresh the thumbnails.

Also you can change thumbnail size in Nautilus. Look where it says **% to the left of the "View as Icons" button at far right of the Nautilus toolbar. This can be changed to scale thumbnails up to 400%.

Ummm...misunderstanding? I have no thumbnail problem. I need a larger preview of any thumbnail I choose to click on in the file selector list. Very much like Vista... I understood that this had been provided for in 8.04, but it seems I'm wrong. Many have asked for this...

P.S Also that folder you mention doesn't exist. I have this: ~/.thumbnails/normal with a load of .png files in there...

---

