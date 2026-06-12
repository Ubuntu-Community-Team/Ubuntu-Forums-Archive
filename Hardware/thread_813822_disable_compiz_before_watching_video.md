---
title: "disable compiz before watching video"
date: 2008-05-31
forum: Hardware
---

### Post by guimenez on 2008-05-31
Hi people.

i know that you can help me ;)

i want to make a script that when i open a video, it first run the compiz-switch then open the video, when i close, it open again the compiz switch to start compiz again.

Please help me

because my notebook hanks when whatching videos with compiz enabled

Thanks

---

### Post by 505 on 2008-05-31
Should be that difficult. Just create a script with:
```

#!/bin/sh
compiz-switch;vlc $@;compiz-switch

```
It will run the switch command, then run vlc with the selected file. After you close VLC Player the switch command runs again. Then set this script as the default action to open when you doubleclick a video file.

---

### Post by guimenez on 2008-05-31
Many thanks ;);););)

now i can work without freezing my computer

many thanks once again

---

