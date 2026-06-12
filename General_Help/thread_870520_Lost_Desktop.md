---
title: "Lost Desktop"
date: 2008-07-25
forum: General Help
---

### Post by gnarf on 2008-07-25
I've lost my ubuntu desktop, I originally started with the server distro but added the gui desktop after a while. The power went off last night during a storm and now I no longer have my desktop. Ubuntu checked the HDDs after I booted up but no gui. The GUI load screen with the orange load bar is visible but after that a few loaded processes are briefly shown (like apache) then I get a command line login. Anyone with any ideas? I'm not very proficient with ubuntu/linux so small words are appreciated.

---

### Post by Sef on 2008-07-25
from the command line:  ```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```

---

