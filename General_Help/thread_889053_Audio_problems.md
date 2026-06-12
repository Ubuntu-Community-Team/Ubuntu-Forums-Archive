---
title: "Audio problems"
date: 2008-08-13
forum: General Help
---

### Post by flipteo on 2008-08-13
When I'm listening to a radio stream with Exaile, and I then go to youtube to watch a video, the youtube video won't have any audio. If I then at this time stop the exaile stream, the youtube video still won't have audio, even if I refresh the page and close exaile. I have to close both exaile and my browser and restart it to get audio. Also, my browser never closes itself when I close it in these situations. It dissapears from the desktop, but it's still running in the processes's. I'm assuming it's some kind of conflict, but I don't know how to fix it.

---

### Post by trevelyan on 2008-08-13
close both programs (or any program using sound) and then type this in a terminal:
```

sudo killall pulseaudio

```
after that you should be able to hear sound from both exaile and your browser.

---

